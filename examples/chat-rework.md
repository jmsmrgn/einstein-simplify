# Example: chat rework of a dense response

**Source** (a previous response):

> The outage was caused by the migration's `ALTER TABLE orders ADD COLUMN public_id uuid DEFAULT gen_random_uuid()` taking an ACCESS EXCLUSIVE lock on `orders`. Because the default is volatile, the Postgres 11+ fast path for non-volatile defaults doesn't apply, so it rewrote all ~40M rows while holding the lock. Reads and writes queued behind it, the connection pool saturated at 100, and the API returned 503s for 11 minutes. Fix: add the column nullable with no default, set the default for new rows, then backfill existing rows in batches. Should probably also set `lock_timeout` in the migration runner.

**Reader:** none named, and the source is the previous response the operator is reading, so the reader is the operator: fluent in their own field, not in Postgres. **Purpose:** decide whether the fix is right, then apply it. **Medium:** chat.

**Takeaway:** One migration rewrote all 40 million orders while holding the table locked, so every request queued behind it for 11 minutes; the fix does the same change in steps that never hold the lock.

**New ideas (3):** the database's usual shortcut could not apply here, so it wrote every row; a lock on the table means every request waits, which turned a slow migration into an outage; the fix splits the change into steps that never hold the lock.

**Output:**

> The fix is sound. Three steps: add the column empty, which is instant; make new orders fill it in automatically; then backfill the existing orders a few thousand at a time. One more, tentative: set `lock_timeout` in the migration runner, so no migration can hold a lock indefinitely again.
>
> What happened: the migration gave every order a new random ID. When a column gets one value for all existing rows, the database has a shortcut: record the value once instead of writing every row. A random ID rules that out, so it wrote an ID into all 40 million orders one at a time, holding a lock on `orders` the whole time. A lock on the table means nothing else can read or change an order, so every request that needed one waited, the connection pool filled up, and for 11 minutes the API answered with errors.
>
> Left out: the `ACCESS EXCLUSIVE` lock-level name, the Postgres version detail behind the shortcut, and the connection-pool numbers.

**Why it looks like this:** the operator needs the decision and the mechanism rather than basics, so the answer opens the output and the mechanism follows in plain terms. Two names stay because the operator will use them: `orders`, and `lock_timeout`, which is a recommendation the operator has to type as written. `ACCESS EXCLUSIVE` and the volatile-default rule go, because no action depends on them. The source's "Should probably" survives as "tentative", which is the hedge rule. Nothing was added and no reader was assumed, so those two lines are absent rather than empty; a run with no reader named and text the operator did not write would open with `Assumed: a smart adult with no background in the field`.
