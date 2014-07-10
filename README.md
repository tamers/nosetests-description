nosetests-description
=====================
[![Build Status](https://travis-ci.org/tamers/nosetests-description.svg?branch=master)]
(https://travis-ci.org/tamers/nosetests-description)

This is a plugin for [nose](https://github.com/nose-devs/nose) to customize 
the test description output. Using the verbose flag `-v` when running a test 
will display the first line of the test doc string if present, otherwise will 
output the test name.

What if you want to display the whole docstring or maybe the test name with
description, this plugin will allow you to customize this output.

Installation
------------
```
pip install nose-customdescription
```
Usage
-----
```
--with-customdescription
                    Enable the plugin
--custom-description=CUSTOM_DESCRIPTION
                    Override test description output - one of 0,1,2
                    [NOSE_CUSTOM_DESCRIPTION] '0': Test name without
                    description '1': Test Description without test name
                    '2': Test name followed by its description (includes
                    the whole doc string)

```

Examples
--------

The test file:
```python
import unittest
class TestExample(unittest.TestCase):
    def test_example(self):
        """
        This is a multiline test case, this is line number 1
        and this is line number 2
        """
        assert True

```

Examples:
```
$ nosetests test.py -v --collect-only --with-customdescription --custom-description 0
test_example (test.TestExample) ... ok
```
```
$ nosetests test.py -v --collect-only --with-customdescription --custom-description 1

    This is a multiline test case, this is line number 1
	and this is line number 2
	

 ... ok
```
```
$ nosetests test.py -v --collect-only --with-customdescription --custom-description 2
test_example (test.TestExample)
Description:

	This is a multiline test case, this is line number 1
	and this is line number 2
	

 ... ok

```