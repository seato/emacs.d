my emacs
========

My personal .emacs.d, used with my .emacs that you can find [here](https://github.com/SuitAndThai/dotfiles).

This was partially influenced by [Magnar's emacs configurations](https://github.com/magnars/.emacs.d).

installing emacs on fedora
==========================

1. get the latest tarball and extract it:

`    PRETEST_URL="http://ftp.gnu.org/gnu/emacs/"  
    FILENAME=$(curl -s ${PRETEST_URL} | sed -n 's/^.*a href="\(emacs-24.[0-9\.]*tar.gz\)".*$/\1/p' )  
    curl -o ${FILENAME} ${PRETEST_URL}${FILENAME}  
    tar -xzof $FILENAME  
    cd ${FILENAME%.tar.gz}`

2. install the dependencies:

    yum-builddep emacs

3. configure, build, install:

    ./configure --prefix=/usr/local/emacs24 --with-dbus --with-gif --with-jpeg --with-png \
    --with-rsvg --with-tiff --with-xft --with-xpm --with-x-toolkit=gtk
    make
    ./src/emacs --version # Look good? The INSTALL doc suggests testing: ./src/emacs -Q
    sudo make install

4. tell fedora of the new emacs path:

    sudo alternatives --install /usr/bin/emacs emacs /usr/local/emacs24/bin/emacs 20000
    sudo alternatives --install /usr/bin/emacsclient emacsclient /usr/local/emacs24/bin/emacsclient 20000

5. badda bing badda boom:

    emacs

Credit to jonEbird for his helpful [blog post](http://jonebird.com/2011/12/29/installing-emacs-v24-on-fedora/) on the topic.  I really only made minor adjustments to it based off the comments and my own experience.
