# bck
Back up manually any file/directory matching an expression with this command line tool

## usage
   bck [options] [expression]

   Back up any file/directory matching the [expression]. The match use find command and recognize any exprsesion find recognize.  
   **By default, the backup directory is set to `~/.BACKUP`.**  
   
   NOTE: **don't use `sudo bck`**, `bck` will automatically ask for sudo permission if needed from its script. Using `sudo bck` cause to potentially loose file permissions, as the files will be backed with a root ownership.

## options
```
   -f                   back up only files (ignore directories)
   -d                   back up only directories (ignore files)
   -o [dir]             set the backup directory
   -O                   back up at '.BACKUP' in the current directory
   -x [expression]      exclude the locations matching the [expression] pattern
   -h                   this help
   -D                   debug
```

## install
Just copy `bck` file in `/usr/local/bin` or any bin path.

## config
A config file setting the backup directory can be write at `~/.bckrc` or `~/.config/bck/bckrc`. By default, the backup directory is set to `~/.BACKUP`.

## examples
```shell
bck -o save -x to* -d t*
    # will back up all directories in the current working directory those name begins with a 't',
    #  except those beginning with 'to', in a subdirectory of the current working directory called 'save'.

bck -D -f -x *.py *.pm -- a* b* /usr/local/bin/*
    # will back up all files in the current working directory those name matches the "a* b*" expression,
    #  except perl modules and python files, AND all the files in /usr/local/bin, except .pm and .py files,
    #  with the debug option enabled.

bck -d
    # will back up all the directories of the current working directory.
```
