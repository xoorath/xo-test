# xo-test
A public domain single header file testing module. C++11 or newer required.

## Example
``` cpp
  Test test;
  // Run the basic math test.
  test("basic math", [&test]{

    // you can manually call ReportSuccess/Failure for more complex or non-binary tests.
    if(2+2 == 4) {
      test.ReportSuccess();
    } else {
      test.ReportFailure("two plus two should equal four.");
    }

    // will report a failure if false
    test.ReportSuccessIf(10/2==5, "ten divided by two should be five.");

    int multiplyResult = 5*2;
    // will log the value expected (10) vs. got (multiplyResult) to the console if the test fails.
    test.ReportSuccessIf(multiplyResult, 10, "multiplication result is incorrect");

    // lets log this out for fun, to see what failures look like.
    test.ReportFailure("This is what it looks like when a test fails");
  });
```

## Sample output
``` txt
========== "basic math" test started ==========
[FAIL] This is what it looks like when a test fails
3 passed. 1 failed. took (1.2e-05) seconds. 
```

# Todo 1.0:
- I would like to refactor to include an optional `xo` namespace.
- Change API to use an error macro rather than a string directly. It can wrap the creation of a struct that also pops in file name and line number. Something along the lines of `TEST_ERR("it failed")`.
- Include warning functionality.
- Figure out whatever file log format makes sense for integration into the CI I plan to use, and also log to file optionally (off by default).

# Versions:
### 0.1 (july 2016): Initial commit.

# Street Cred
Inspired by [Sean Barrett's stb](https://github.com/nothings).

# LICENSE
This software is dual-licensed to the public domain and under the following license: 

>You are granted a perpetual, irrevocable license to copy, modify, publish, and distribute this file as you see fit.
