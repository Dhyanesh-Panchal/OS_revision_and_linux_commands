# Clean and Dirty pages

- These pages can be classified into clean and dirty based on whether they have been modified after being loaded into memory.

## Clean pages:
A clean page is a memory page that:
- Has been read from disk (e.g., part of a file).
- Has not been modified since being loaded.
- Can be discarded without data loss because it can be reloaded from disk.
- If memory pressure increases, the kernel simply drops these pages.

## Dirty pages:
A dirty page is a page in memory that:
- Has been modified by a process.
- Has not yet been written back (flushed) to disk.
- Must be written to disk before being freed, to prevent data loss.

*Dirty pages remain in memory until:*
- The kernel automatically flushes them (based on timers).
- The user manually flushes them (sync command).
- Memory pressure forces the kernel to flush them.


- **Clean pages are part of reclaimable buff/cache**