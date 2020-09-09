# h5pkg - The H5P Package builder tool
This tool was created to search for dependencies and pack h5p files using two sources of data: The h5p registry file and GitHub. 


## Requirements
If you want to use this tool you should have Linux or another UNIX compatible OS with **git** and **zip** commands installed.

You also need to install some Ruby gems:
- rest-client 
  ```gem install rest-client```
- colorize
  ```gem install colorize```
- fileutils
  ```gem install fileutils```

In some systems, ```rest-client``` needs the C headers of Ruby and some build tools. If you have any problem, try to install ```ruby-dev``` first using your preferred package manager.

Remember to give execution permissions to the script

## Usage
```./h5pkg pack <folder>```

Where ```<folder>``` is the path of the folder to your H5P file structure. If packaging succeeds, you can find your H5P package stored in ~/.h5pkg/out directory.

## Documentation
For documentation, please install the YARD gem: 
```gem install yard```

If you want to see the docs in a local server please and use ```yardoc h5pkg``` to generate docs and ```yard server``` to run a local server. Open your browser and go to *localhost:8808*

## Notes
Until now, we only have npm build support to the *QuestionSetTextualEditor* component.

## Exit codes
Exit codes can be useful in case you get an abnormal termination of the program. 
| Code | Symbol | Reason |
| --- | --- | ---|
| 1 | NEEDS_MORE_PARAMS |Not enough parameters |
| 2 | COULDNT_CREATE_TEMP_DIR | Couldn't create a temporary directory to store the data. Please check write permissions on your home directory |
| 3 | LIBRARY_JSON_NOT_FOUND | Couldn't find the *library.json* file inside the H5P root directory you gave to the command line. Please check if the directory contains H5P valid data |
| 4 | SEMANTICS_JSON_NOT_FOUND | Couldn't find the *semantics.json* file inside the H5P root directory you gave to the command line. Please check if the directory contains H5P valid data|
| 5 | COULDNT_CREATE_HTTPS_H5P_REGISTRY | There was any error trying to download the registry from h5p.org, or trying to translate the registry addresses from ssh to https |
| 6 | CANNOT_FIND_LIBRARY_REPO | The program was unable to find a dependency neither in the H5P registry nor GitHub's H5P repository. |
| 7 | CANNOT_CLEAN_DIR_STRUCTURE| Couldn't remove folders forbidden by the H5P Specification. Please check the permissions and the ownership of the directory structure |
| 8 | CANNOT_CLEAN_UNWANTED_FILES | Couldn't remove files forbidden by the H5P Specification. Please check the permissions and the ownership of the files |
| 9 | CANNOT_ZIP_FILES | There was an error trying to zip the files. Remember you should have ```zip``` installed |
| 10 | CANNOT_CLEAN_TEMP_DIR | Couldn't remove the temporal file structure made to build the H5P package. Please check permissions and ownership |
| 11 | ERROR_DOWNLOADING_LIBRARY | There was a network error trying to download a remote dependency. Check network connectivity and try again |