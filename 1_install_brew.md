## 1. Install homebrew

***
*__Preface__*:
1. The codes which starts with `'$'` should be entered into the __Terminal__.
2. The contents which ends with `'#'` are comments for the codes, if any.
***

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

This graph shows how to use `tree` command.

![tree command](http://ww4.sinaimg.cn/mw690/005WT5Wygw1f7mk8omg6dj30ic0awdh8.jpg)

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
