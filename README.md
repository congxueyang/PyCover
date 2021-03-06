# PyCover

A plugin for Sublime Text 2/3
that can highlight lines of Python lacking test coverage,
based on the output of Ned Batchelder's
[coverage.py](http://nedbatchelder.com/code/coverage/),
based on the original plugin for ST2,
[SublimePythonCoverage](https://github.com/davisagli/SublimePythonCoverage).

## Installation

Set up
[Sublime Package Control](http://wbond.net/sublime_packages/package_control)
if you don't have it yet.

Go to Tools > Command Palette.
Type `Package Control: Install Package` and hit enter.
Type `PyCover` and hit enter.

PyCover relies on the external
[coverage.py](http://nedbatchelder.com/code/coverage/) package,
which you can install with

    pip install coverage


## Usage

Toggle missing line highlights by running the `show_python_coverage` command,
bound to <kbd>ctrl</kbd>+<kbd>alt</kbd>+<kbd>shift</kbd>+<kbd>c</kbd>
by default.
You can also access it with the Command Palette under "Toggle Uncovered Lines",
or via the right-click menu.

With the settings option `"onload": true`,
PyCover will start highlighting missing lines as soon as your file loads.

### Details

PyCover works by looking in all parent directories of the active file
until it finds a `.coverage` file (as produced by `coverage.py`).
Obviously, it only works if that file exists
and contains coverage information for the file you opened.

Once the `.coverage` file is found, PyCover invoke the `coverage` module
with system Python (see the 'python' settings option to change this)
and highlights any missing lines with a gutter mark.
