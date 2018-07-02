# terser-folder

[![Build Status](https://travis-ci.org/nicksrandall/terser-folder.svg?branch=master)](https://travis-ci.org/nicksrandall/terser-folder)

Command to run terser (js minifier) on a folder and minify the result in a single file or a new folder.

## Getting Started

Install the module with: `npm install terser-folder -g`

## Documentation

    Usage
      terser-folder path [options]

    options:
      -c --comments      Add a comment with the file name.
      -o --output        Specify a file/folder to write the minified code
      -e --each          Minify each file independently
      -x --extension     Minified file extension (default: .min.js)
      -p --pattern       Specifies a comma separated glob patterns for the file selections. Default: **/*.js
         --pseparator    Specifies the separator for the pattern input. Default: ,
         --version       Prints the current version from package.json
         --config-file   Specifies a json configuration file for the terser/uglify-es module'
      -h --help          Print this list and exit.

## Examples

    $ terser-folder test-folder
    $ terser-folder test-folder --comments
    $ terser-folder test-folder -o all.min.js
    $ terser-folder test-folder --output all.min.js --pattern "**/*.js,!**/*min.js" # ignore minified files
    $ terser-folder test-folder -eo newFolder
    $ terser-folder test-folder -e -x .js -o test-folder # careful: overwrite all files in test-folder
    $ terser-folder test-folder --config-file "./uglify.json"
    where uglify.json contains
    {
      "keep_fnames": true
    }

## Contributing

Pull requests are appreciated.

## Release History

- 02/Jul/2018 - Switching to terser for better minification
- 25/Nov/2017 - Added support for sourcemaps via the terser config file  
  Exmaple configuration:

```
{
  "sourceMap": {
    "root": "../src",
    "url": "{file}.map"
  }
}
```

- 11/Nov/2017 - Added support for the --config-file option
- 11/Nov/2017 - Upgraded to terser@3 and uglify-es@3
- 27/Aug/2017 - Added support for the --pattern and --pseparator flags.
- 06/Feb/2017 - Added support for the --harmony flag.
- 28/Dec/2016 - Added support for sub folder output files.
  Example: `terser-folder test-folder -o newFolder/nested/all.min.js`
- 01/Oct/2016 - Added the --extension flag
- 12/Oct/2014 - Removes the extra files, organizes the code
- 05/Jan/2014 - Initial release

##

Forked from `ionutvmi/terser-folder` and switched parser to terser for more efficient minification.
