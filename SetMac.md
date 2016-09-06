# Setup Mac for Development

## How to setup a brand new Mac for development and data analysis

### 0. When your Mac is totally new:

0.1 TouchPad  
> Make Your TouchPad Powerful to Use.

0.2 Language
> Set Your Preferred Language and Input Source

0.3 Finder
> Configure Finder

__Feel Free to Find Tutorials By Yourself__

***
*__Preface__*:
1. The codes which starts with `'$'` should be entered into the __Terminal__.
2. The contents which ends with `'#'` are comments for the codes, if any.
***

## 1. Install homebrew

Homebrew is a package management tool for OSX.

It acts as `yum` in Red Hat, `apt-get` in Ubuntu.

Installing it is easy: enter the following code in terminal.

```
$ /usr/bin/ruby -e "$(curl -fsSL
 https://raw.githubusercontent.com/Homebrew/install/master/install)"
 ```

 Refer from:
 http://brew.sh


#### 1.1 Install via `brew`

 Many package can be installed via Homebrew conveniently.

 Take `tree` as an example:

`$ brew install tree`


And there many things you can install via brew

`$ brew install git`

(*Some settings are needed before it comes to work. See `4. Git and GitHub` for details*)






#### 1.2 Install via `brew cask`

Besides, many softwares can also be installed by this command.

You will spare the action of searching softwares and dragging them into your applications file.

such as:
`$ brew cask install google-chrome`

`$ brew cask install qq`

`$ brew cask install slack`

`$ brew cask install alfred`

`$ brew cask install atom`

`$ brew cask install iterm2`





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


## 3. Setup Virtual Environment
It’s a good idea to create isolated Python environments using virtualenv (https://virtualenv.pypa.io/en/stable/)


## 4. Git and GitHub

> Git is a football, GitHub is a football field.


#### 4.1 Install Git

As mentioned above:

`brew install git`

then you can set your name and email

`$ git config --global user.name "YourName"`

`$ git config --global user.email "YourEmail"`


To see git's configuration, you can:

`$ git config --list`

To get help:

```
$ git help <verb>
$ git <verb> --help
$ man git-<verb>
```

You should replace `<verb>` with concrete command, for example:

`git help config`

#### 4.2 Connect GitHub

1. Create a [GitHub](https://github.com) account.

2. Create an SSH Key.

    In your terminal, enter:

    `$ ssh-keygen -t rsa -C "114020252@link.cuhk.edu.cn"`

    Change the email address to your owns.

    Then enter <enter> all the way, you do not need to set a password for this.

    Then you open your root directory.
    > For me, the root directory is a file with my name -- that is 'floyd'. Its icon is a little house.

    You should find a folder named `'.ssh'`.

    If you cannot see it, you need to make your hidden files appear by entering:

    `$ defaults write com.apple.finder AppleShowAllFiles -bool true`

    Open that folder, find the files named `"id_rsa"` and `"id_rsa.pub"`. The former is private, the latter is public.

3. Add SSH key to GitHub

  Login GitHub, and open "settings", there is a `SSH and GPG keys` tab.

  Then you can enter any title, paster the contents from your `"id_rsa.pub"` file, and click the "Add SSH Key" bottom.

  After this, you can push your works to GitHub.


## 5. Install MySQL

#### 5.1 Use DMG
Even we can install MySQL with the command `"$ brew install mysql"`, but there are much troubles to deal before get the MySQL to work.

So using DMG to install MySQL is first recommended.

1. Download DMG for MySQL website: http://dev.mysql.com/downloads/mysql/

  Open this web page, and scroll the bottom, find the file ended with `.dmg`, and download it.

2. Open it and install.

  Just follow the instruction.

  But be __cautious__: the all file is written, MySQL will pop a small window with a temporary password. Keep that password, otherwise you will
  in endless troubles.

3. Configure MySQL.

   You still need to do something before MySQL can actually run.

   First, start MySQL server, open your System Preferences, in its bottom you will say an icon with the name: MySQL.
   click it and then start your server.

   Second, export mysql's PATH.

   In your root directory, open the file named `.bash_profile` [ or `.zshrc` if you have replace `bash` with `zsh`],

   add this line then save it.

   `export PATH="/usr/local/mysql/bin:$PATH"`

4. Change password

  On terminal, enter:

  `mysql -u root -p`

  Then you are asked to enter password. The password should be the one that MySQL gave you after installation, and you should __store__ it already,
  find it and enter. Then you will enter `mysql` mode.

  Change the password, by entering:

  `SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpass');`

  With a frequently used new password, please.

#### 5.2 Use `brew`

To be continued...


## 6. Turn to iTerm2

As mentioned above, install it by:

`$ brew install iterm2`

iTerm2 is a great substitute of Mac's own terminal. If you dip into it and master it, you will improve your work efficiency,

In defaults, the terminal is a bash shell. But we can change the shell to zsh.

There is a easy way, that is installing `oh-my-zsh`.

By:

`sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"`

Then you will notice your iTerm2 is changed a lot.

You can also change your iTerm2's theme in the file `'.zsh'`


## 7. Setup Atom

Atom is a text editor comes from GitHub.
