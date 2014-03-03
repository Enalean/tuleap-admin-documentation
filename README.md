Tuleap Administration Documentation
===================================

The target audience of this documentation is administrator of the [Tuleap](http://tuleap.com/) plateform (sysop, sysadmin, …).

For the end user documentation, please refer to the dedicated repository tuleap-documentation-en.

Download the sources from GitHub
--------------------------------
    git clone git@github.com:Enalean/tuleap-admin-documentation.git


Build the documentation
-----------------------

    sudo apt-get install python-pip
    sudo pip install -q Sphinx
    cd /path/to/tuleap-admin-documentation
    make html

The documentation is generated in `_build/html/`

License
-------

Tuleap and its documentation are licensed under GPLv2 or above.

