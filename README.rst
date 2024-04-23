Electron Radiant - Lightweight Radiant client
=====================================

Forked from Electron Cash.

::

  Licence: MIT Licence
  Author: Electron Radiant Developers (2022)
  Author: Electron Cash Developers
  Language: Python
  Homepage: https://electroncash.org/

Server Mainnet List
===============

- electrumx.radiantexplorer.com (50012 and 50010)
- electrumx2.radiantexplorer.com (50012 and 50010)
- electrumx.radiantblockchain.org (50012 and 50010)
- electrumx.radiant4people.com (50012 and 50010)

Server Testnet List 
===============
- electrumx-testnet.radiant4people.com (51012 and 51010)


Getting started
===============

**Note: If running from source, Python 3.6 or above is required to run Electron Radiant.** If your system lacks Python 3.6,
you have other options, such as the `AppImage / binary releases <https://github.com/RadiantBlockchain/Electron-Radiant/releases/>`_
or running from source using `pyenv` (see section `Running from source on old Linux`_ below).

**macOS:** It is recommended that macOS users run `the binary .dmg https://github.com/RadiantBlockchain/Electron-Radiant/releases/>`_  as that's simpler to use and has everything included.  Otherwise, if you want to run from source, see section `Running from source on macOS`_ below.

Electron Radiant is a pure python application forked from Electrum and Electron-Cash. If you want to use the Qt interface, install the Qt dependencies::

    sudo apt-get install python3-pyqt5 python3-pyqt5.qtsvg

If you downloaded the official package (tar.gz), you can run
Electron Radiant from its root directory (called Electron Radiant), without installing it on your
system; all the python dependencies are included in the 'packages'
directory. To run Electron Radiant from its root directory, just do::

    ./electron-radiant

You can also install Electron Radiant on your system, by running this command::

    sudo apt-get install python3-setuptools
    python3 setup.py install

This will download and install the Python dependencies used by
Electron Radiant, instead of using the 'packages' directory.

If you cloned the git repository, you need to compile extra files
before you can run Electron Radiant. Read the next section, "Development
Version".

Hardware Wallet
---------------
Electron Radiant supports the Pirate Plus hardware wallet. To interface with the hardware wallet you'll need the Qt GUI application, which acts as a bridge between the hardware wallet and PC. This software can be obtained from the Mullroy Github repository: https://github.com/mullroy/pirate_hardware_interface

To order a Pirate Plus hardware wallet, follow the instructions on the main Github page: https://github.com/mullroy

Development version
===================

Check your python version >= 3.6, and install pyqt5, as instructed above in the
`Getting started`_ section above or `Running from source on old Linux`_ section below.

If you are on macOS, see the `Running from source on macOS`_ section below.

Check out the code from Github::

    git clone https://github.com/RadiantBlockchain/Electron-Radiant
    cd Electron-Radiant

Install the python dependencies::

    pip3 install -r contrib/requirements/requirements.txt --user

Create translations (optional)::

    sudo apt-get install python-requests gettext
    ./contrib/make_locale

Compile libsecp256k1 (optional, yet highly recommended)::

    sudo apt-get install libtool automake
    ./contrib/make_secp

For plugin development, see the `plugin documentation <plugins/README.rst>`_.

Running unit tests (very optional, advanced users only)::

    pip install tox
    tox

Tox will take care of building a faux installation environment, and ensure that
the mapped import paths work correctly.

Running from source on old Linux
================================

If your Linux distribution has a different version of python 3 (such as python
3.5 in Debian 9), it is recommended to do a user dir install with
`pyenv <https://github.com/pyenv/pyenv-installer>`_. This allows Electron
Radiant to run completely independently of your system configuration.

1. Install `pyenv <https://github.com/pyenv/pyenv-installer>`_ in your user
   account. Follow the printed instructions about updating your environment
   variables and ``.bashrc``, and restart your shell to ensure that they are
   loaded.
2. Run ``pyenv install 3.6.9``. This will download and compile that version of
   python, storing it under ``.pyenv`` in your home directory.
3. ``cd`` into the Electron Radiant directory. Run ``pyenv local 3.6.9`` which inserts
   a file ``.python-version`` into the current directory.
4. While still in this directory, run ``pip install pyqt5``.
5. If you are installing from the source file (.tar.gz or .zip) then you are
   ready and you may run ``./electron-radiant``. If you are using the git version,
   then continue by following the Development version instructions above.

Running from source on macOS
============================

You need to install **either** `MacPorts <https://www.macports.org>`_  **or** `HomeBrew <https://www.brew.sh>`_.  Follow the instructions on either site for installing (Xcode from `Apple's developer site <https://developer.apple.com>`_ is required for either).

1. After installing either HomeBrew or MacPorts, clone this repository and switch to the directory: ``git clone https://github.com/RadiantBlockchain/Electron-Radiant && cd Electron-Radiant``
2. Install python 3.6 or 3.7. For brew: ``brew install python3`` or if using MacPorts: ``sudo port install python36``
3. Install PyQt5: ``python3 -m pip install --user pyqt5``
4. Install Electron Radiant requirements: ``python3 -m pip install --user -r contrib/requirements/requirements.txt``
5. Compile libsecp256k1 (optional, yet highly recommended): ``./contrib/make_secp``.
   This requires GNU tools and automake, install with brew: ``brew install coreutils automake`` or if using MacPorts: ``sudo port install coreutils automake``
6. At this point you should be able to just run the sources: ``./electron-radiant``


Creating Binaries
=================

Linux AppImage & Source Tarball
--------------

See `contrib/build-linux/README.md <contrib/build-linux/README.md>`_.

Mac OS X / macOS
--------

See `contrib/osx/ <contrib/osx/>`_.

Windows
-------

See `contrib/build-wine/ <contrib/build-wine>`_.

Android
-------

See `android/ <android/>`_.

iOS
-------

See `ios/ <ios/>`_.
