# Command line

The command line is a code based interface to operate your computer. In fact, everything you see and do gets converted into code before it will be executed and all those windows and pointers are just an abstraction of the command line.
That means that everything your computer can do, is also doable through the command line. And even more!

On Mac, **Terminal** is the standard software to work with the command line.

## Basic commands

**`pwd` print working directory** to see where you’re at
```
pwd
```

**`cd` Change directory**
```
# go inside some folder relative to your current directory
cd {path}

# go to some folder relative to the user home folder
cd ~/my-projects/some-project

# go one level up
cd ..

# go to your previous directory
cd -
```

**`ls` list directory contents** to see what’s inside your current working directory
```
ls
```

**`cp` copy** file or directory
```
cp {file/folder that you want to copy} {new name or path}
# eg
cp config.yml config-backup.yml
```

**`mkdir` make directory** to create a folder
```
mkdir {folder name}
```

**`rm` remove & `rmdir` remove directory**
```
rm {file or folder that you want to delete}
rmdir {name of empty folder that you want to delete}
```

**`touch` create a blank new file** if it doesn’ already exists
```
touch {file name}
```

**`sudo` Super User Do** to perform admin actions
If your current user rights are not enough, you can prepend `sudo` to many other commands, to do the same, but with admin permissions.
```
sudo {some command}
```

**`tail`** to print out the last lines of a file
This is really handy to scan log files
```
tail {file name}
```

## ⚠️ Windows users

Everything of the above works in a Unix shell (Linux, Mac) and might be completely different on a windows machine. If you know how to translate that, please extend this tutorial.
