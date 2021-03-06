Running and creating tests                        {#running-and-creating-tests}
==========================

There are a number of tests included in RIOT. They are located in the
[tests folder](https://github.com/RIOT-OS/RIOT/tree/master/tests). These tests
allow basic functionality to be verified as well as provide an example of
usage.


Running automated tests
-----------------------

Some tests can be performed automatically. The test automation scripts are
defined in the `<test_application>/tests/` folder. They are written in python
and interact through the uart with the test application code running on a
board to do the validation. It is recommended to flash the board with the
test just before running it because some platforms cannot be reset while
testing.

From the test application directory run:

    BOARD=<board_of_your_choice> make flash test


An automated way of knowing if a test is available is to execute the
'test/available' target from the test application directory.
It executes without error if tests run by 'make test' are present.

    make test/available


Interaction through the uart
----------------------------

Tests implemented with `testrunner` use the `cleanterm` target that
provides an interaction without adding extra text output or input handling.
It can currently be expected to have unmodified line based interaction with the
board.

The expected behavior is verified with the test in `tests/test_tools`.

Tests cannot rely on having on all boards and terminal programs:
* unbuffered input
* allowing sending special characters like `ctrl+c/ctrl+d`
