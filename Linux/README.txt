(1) Install the required system packages using:

    sudo apt-get install \
        libgsl0-dev \
        libboost-all-dev \
        python-dev \
        python-setuptools \
        python-numpy \
        python-scipy \
        python-matplotlib \
        python-lxml \
        ipython \

    This works on Ubuntu Linux or other Debian-based distributions.
    Other Linux distributions may use different software manager,
    but the package names should be equal or very similar to those
    above.


(2) For a one-user installation determine the Python directory for user
    files, create it if it does not exist yet, and add there a symbolic
    link to the diffpy_cmi.pth file:

    D="$(python -c 'import site; print site.USER_SITE')"
    mkdir -p "$D"
    ln -si $PWD/diffpy_cmi.pth "$D"/

    For a system-wide installation create symbolic link in the directory
    for system-wide Python packages:

    sudo ln -si $PWD/diffpy_cmi.pth /usr/local/lib/python2.7/dist-packages/

    Note it is essential to use the symbolic link.  Making a copy of the
    pth file would not work.


(3) Test the installation with

    ./runtests.sh

(4, optional) update and rebuild:

    Install the required system packages using:

    apt-get install \
        git libboost-all-dev libgsl0-dev mercurial python-dev \
        python-numpy python-setuptools scons wget zsh

    This works on Ubuntu Linux or other Debian-based distributions.
    Other Linux distributions may use different software manager,
    but the package names should be equal or very similar to those
    above.

    After installing all packages you can try to download and build
    the code with

    ./update.zsh

    This will first clean pervious build, fetch the latest source code,
    and build all packages in place. Then you can run the test again to
    test the new build.

Note:
    If you experience some errors in runtests.sh such as

        undefined symbol: PyUnicodeUCS4_FromEncodedObject

    or

        undefined symbol: PyUnicodeUCS2_FromEncodedObject

    It is usually because the python you are using is not compatible with
    the prebuild boostpython library. (For example you are using Enthought
    Python Distribution.) You can try to rebuild the whole diffpy
    projects with:

    ./update.zsh

    This will rebuild the boost library used in diffpy projects.
