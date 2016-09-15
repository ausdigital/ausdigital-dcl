# Testing the DCL

The code in this directory will test a remote DCL implementation.

## Install

This suite uses python to access (and test) remote DCL, through HTTPS and DNS protocols. It's developed with python 2.7, other versions may work but are not tested. Raise an issue in https://github.com/ausdigital/capability-locator if you encounter issues with other versions.

This suite is not yet published through a package distribution mechanism, the `test.sh` script will install required software, assuming you have `pip` and `virtualenv` installed.

By default, the software will evaluated the dcl.testpoint.io target. You can change the default target by:

 1. `cp config.sh.sample config.sh`
 2. edit `config.sh` to reffer to your chosen target
 3. run the `test.sh` script as usual.

Alternatively, if there is no config.sh file, the test runner will use the following environment variables:
 * DCL_READ_DOMAIN (defaults to dcl.testpoint.io, used as base of NAPTR queries)
 * DCL_WRITE_DOMAIN (deault to dcl.testpoint.io, used for updates over HTTPS)
 * DCL_TEST_USER (default to 33767197359)
 * DCL_TEST_SECRET (default to 33767197359)

If multiple people are running the test suite in parallel with the same DCL_TEST_USER, it's possible the update tests will collide (causing false results). If that's an issue for you, it's advisable to reserve your own test accounts and use them exclusively. If you are running against dcl.testpoint.io, you can claim ABNs for exclusive use on https://idp.testpoint.io/.
