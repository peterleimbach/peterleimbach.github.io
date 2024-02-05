# setup mkdocs environment

As requirement you need a Python 3 environment available.

The commands are for Linux but similar on a Windows machine.

## create a virtual python environment

It's better to install the required Python libraries in a separate virtual Python environment for the project instead of local machine environement.

Otherwise it can clash with other project libraries.

You can do this in the root directory of your project.

!!! note "add the virtual environment to the .gitignore file"

    Maybe it's a good idea to add this directory to the .gitignore file as you don't need do push this to GitHub if you use GitHub versioning.

``` sh
$ python3 -m venv .venv
```

## activate the private python environment

You have to activate the virtual environment before you can use it.

!!! danger 

    If you do not activate it your machine environment will be used to install new libraries.

``` sh
$ source .venv/bin/activate
```

## install the mkdocs libraries

mkdocs are the library needed in the basic installation.

If you know that you want to use the nice material theme you better directly install the mkdocs-material library. It will automatically install mkdocs as requirement. 

It's the same command but with ```mkdocs-material``` as library name.

``` sh
$ pip install mkdocs
```

## initialize the project

``` sh
$ mkdocs new my-project
```

## start the markdown processor with build-in web-server

The command will first generate from the markdown files the html files and then start the build-in web server to serve these files.

In case it recognizes changes to the markdown files it will automatically rebuild the html files from the markdown files.

``` sh
$ mkdocs serve
```

## edit your files

You can use any editor to change the files of the project. Everytime you save a file ```mkdocs serve``` command will regenerate the html files of the site and then restart serving the files.