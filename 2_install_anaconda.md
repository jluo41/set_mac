
## 2. Install Anaconda

Install both Anaconda2 and Anaconda3 in case of some special cases.

The website to download:
https://www.continuum.io/downloads

#### 2.1 Install Anacondas with .sh files

1. download shell files.

2. make a new directory on your root directory, named `Environments`.

3. then change directory to where the downloaded files are. Generally, it is `Downloads` file.

4. enter this command in terminal

   `$ sudo bash Anaconda3-4.1.1-MacOSX-x86_64.sh # for python3.5`

 or

   `$ sudo bash Anaconda2-4.1.1-MacOSX-x86_64.sh # for python2.7`

   > `sudo` means `'super user do'`, which enables you with the temporary permission to run some kinds of commands.

   >I use `sudo` here in order to be able change to the installation paths. And the user's password is also needed to confirm.

5. agree whatever until the terminal ask you to say `yes` and choose the location to install.

6. change the default install location path to the new path.

  > For me, the new paths are `Users/floyd/Environments/anaconda3` and
`Users/floyd/Environments/anaconda2`

Then you can wait until the installations are finished.

(*remeber: both version 2 and version 3 should be installed in `Environment` file*)

The full commands are:

```
$ cd
# step 1

$ mkdir Environments
# step 2: mkdir means make a new directory

$ cd Downloads
# step 3: change the directory to the directory where .sh files are.

$ sudo bash Anaconda3-4.1.1-MacOSX-x86_64.sh
Password:[enter your password here]
# step 4: for python3.5. Here I install python3 first.

(a lot things will appear, just press the `<enter>` key, until you are asked to enter `yes`)
# step 5

(after entering `yes`, you  are asked to choose the location to install. Now, enter the prepared paths)

the default path would be:
Users/floyd/anaconda3
installation path >>> Users/floyd/Environment/anaconda3
# step 6
.....(a lot words here, until it is finished).....
```
Additionally, to install anaconda2, you need to repeat the step 4-6 and change '3' to '2'.



#### 2.2 Check the Results

Now you have install a lot of packages.

1. Have an overview:

    `$ conda list`
2. Actually, you have install both both python3 and python2.

    `$ which python`

    `$ which python3`

    `$ which python2`

3. You also have ipython installed.

    `$ ipython`

    `$ ipython notebook`
    (to see what will happen!)
