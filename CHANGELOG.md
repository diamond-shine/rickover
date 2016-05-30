## Version 0.33

- All uses of `Id` have been renamed to `ID`, per the Go Code Review Comments
guidelines. I don't like breaking this, but I'd rather keep the naming
idiomatic, Go will detect incorrect references at compile time, and I haven't
received any evidence that anyone else is using the project, so I am not too
worried about breaking compatibility in the wild.

- When replaying a job, use the `expires_at` value from the old job to
  determine whether to re-run it.

- Enabled several skipped tests and improved their speed/reduced their size.

## Version 0.32

- The `archived_jobs` table now has an `expires_at` column storing when the job
expired, or should have expired. This is useful for replaying jobs - you can
batch replay jobs and the server will correctly mark them as expired.