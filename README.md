Customize Vim to A Morden IDE
===

Currently focusing on configuring vim for Python development.

## Installation

Install ruby and ruby devel by rvm

```
# Install rvm and ruby following https://rvm.io/rvm/install
...

# Install ruby devel
rvm install <your-ruby-version>-dev
```

First, you need to enable install vim with ruby support. Following this [John Anderson's guide](https://medium.com/@sivakalyanc/vim-install-latest-vim-with-ruby-and-python-support-576648fade51) (But don't need to install ruby again).

```
yum remove -y vim

yum -y groupinstall 'Development Tools'
yum -y install perl-devel python-devel perl-ExtUtils-Embed ncurses-devel

yum -y install mercurial
hg clone https://vim.googlecode.com/hg/ ~/workspace/vim

cd ~/workspace/vim
./configure --prefix=/usr --enable-multibyte  --with-tlib=ncurses --enable-pythoninterp --enable-rubyinterp --with-ruby-command="$(which ruby)" --with-features=huge
make
make install
```

Install dependencies for customizing vim

```
yum install -y ack ctags
pip install rope ropemode flake8
```

Checkout my vim configurations

```
cd ~
git clone https://github.com/accelazh/.vim.git

git submodule init
git submodule update
git submodule foreach git submodule init
git submodule foreach git submodule update
```

Enable command-t plugin for vim.

```
cd ~/.vim/bundle/command-t
rake make
```

## How to Use

Check .vim/vimrc for key mappings. Use ctags for code navigation.

```
cd <your-src-folder>
ctags -R
```

Use ctrl-] to go to defination by ctag.
