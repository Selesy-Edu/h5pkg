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