# PSet 4

I have made an automatic test suite that you can download. Unzip, put it in your project folder, and run the .sh file on the Zoo.

- Tests correct stderr behavior
- Comprehensively tests setting of ? env variable
- Tests operator precedence
- Tests cwd and env vars persistence
- Tests against system call failures
- Automatic Valgrind runner and results interpreter
- Testing of backgrounding
- Testing of redirection for built-ins (this was a sneaky one)
- Some tests sourced from other EdStem posts


Your file structure should look like this
```
|- Makefile
|- *.c
|- tests/
  |- run_test.sh
  |- test.in
```

## How to run

From your project directory, run `tests/run_test.sh`
