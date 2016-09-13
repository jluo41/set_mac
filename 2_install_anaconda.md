
## 2. Install Anaconda

Install both Anaconda2 and Anaconda3 in case of some special cases.

The website to download:
https://www.continuum.io/downloads

#### 2.1 Install Anacondas with .sh files



![Dowonloads](https://cloud.githubusercontent.com/assets/18824134/18459893/e59a92be-799f-11e6-9f67-77daa4c4ad32.png)

1. Download the `command-line installer` files.

2. Make a new directory on your root directory, named `Environments`.

3. Change directory to where the downloaded files are. Generally, it is `Downloads` folder.

4. Enter this command in terminal

   `$ sudo bash Anaconda3-4.1.1-MacOSX-x86_64.sh # for python3.5`

 or

   `$ sudo bash Anaconda2-4.1.1-MacOSX-x86_64.sh # for python2.7`

   > `sudo` means `'super user do'`, which enables you with the temporary permission to run some kinds of commands.

   >I use `sudo` here in order to be able change to the installation paths. And the user's password is also needed to confirm.

5. Agree whatever until the terminal ask you to say `yes` and choose the location to install.

6. Change the default install location path to the new path.

  > For me, the new paths are `Users/floyd/Environments/anaconda3` and
`Users/floyd/Environments/anaconda2`

Then you can wait until the installations are finished.

(*remeber: both version 2 and version 3 should be installed in `Environment` file*)

The full commands are:

```

# step 1
# download the installer files.


# step 2
$ cd
$ mkdir Environments

# create a directory named Environments.
# mkdir means make directory.


# step 3:
$ cd Downloads
# change the directory to the directory where .sh files are.


# step 4
$ sudo bash Anaconda3-4.1.1-MacOSX-x86_64.sh
Password:[enter your password here]
# here I take python3.5 as an example.

(a lot things will appear, just press the `<enter>` key, until you are asked to enter `yes`)

# step 5
# after entering `yes`, you will be asked to choose the location to install.
```



![path](https://cloud.githubusercontent.com/assets/18824134/18460141/a335eed0-79a1-11e6-86cb-4d8531816610.png)
```
# step 6
# now, enter our own path.

［Users/floyd/anaconda3］>>> Users/floyd/Environment/anaconda3

＃ change floyd to your own user name!

.....(Wait, until all the things are finished).....
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
