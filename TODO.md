 - [x] Overwrite the `TF_DATA_DIR` environment variable with a new temp directory, and clean it up on exit
 - [ ] Add `TF_LOG` and `TF_LOG_PATH` environment variables by default, so you don't have to filter console output for logs, and we can trace more often
 - [x] Fix bug: Parsing sub-commands.
       If you run 'terraform state show', it will create two different commands: 'terraform state' and 'terraform show'.
 - [x] Fix bug: Delete temporary directory unless command-line flag says otherwise.
       Currently if terraformsh fails with an error, the old TF_DATA_DIR is preserved until the next run.
       This would be bad if the next run of terraform would need the old state cleaned up, but it still
       exists from the previous bad run that wasn't cleaned up.
       Instead, always clean up the temp dir, unless an option is passed to explicitly keep it (-n).
 - [ ] Implement a function to output the plan file name (without running a plan)
 - [ ] Add a wrapper like 'terraform=0.12.31' so the user can quickly call specific versions of apps without having to run 'clinst -e terraform=0.12.31 terraform ....'. (Another option would be to further extend the 'missing command' bash handler)
