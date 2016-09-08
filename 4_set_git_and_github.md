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

    Open the file `id_rsa.pub` with your text editor, you will see a strange string. Later, you will copy it.

    ![the location](http://ww1.sinaimg.cn/mw690/005WT5Wygw1f7mkeb0qfqj30fe053q3o.jpg)

3. Add SSH key to GitHub

  ![setings](http://ww3.sinaimg.cn/mw690/005WT5Wygw1f7mjeypupaj30sg099wgo.jpg)

  Login GitHub, and open "settings", there is a `SSH and GPG keys` tab.

  ![ssh_key](http://ww3.sinaimg.cn/mw690/005WT5Wygw1f7mjm42ju7j30t30cktbw.jpg)

  Then, enter any title, paste the contents from your `"id_rsa.pub"` file, and click the "Add SSH Key" bottom.

  ![paste](http://ww4.sinaimg.cn/mw690/005WT5Wygw1f7mjf0oy2ij30rx0h0tdw.jpg)

  After this, you can push your works to GitHub.
