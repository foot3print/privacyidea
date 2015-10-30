privacyIDEA
===========

.. image:: https://travis-ci.org/privacyidea/privacyidea.svg?branch=master
    :alt: Build Status
    :target: https://travis-ci.org/privacyidea/privacyidea

.. image:: https://circleci.com/gh/privacyidea/privacyidea/tree/master.svg?style=shield&circle-token=:circle-token
    :alt: CircleCI
    :target: https://circleci.com/gh/privacyidea/privacyidea

.. image:: https://img.shields.io/coveralls/privacyidea/privacyidea.svg
    :alt: Coverage
    :target: https://coveralls.io/r/privacyidea/privacyidea

.. image:: https://img.shields.io/pypi/dm/privacyidea.svg
    :alt: Downloads
    :target: https://pypi.python.org/pypi/privacyidea/
    
.. image:: https://img.shields.io/pypi/v/privacyidea.svg
    :alt: Latest Version
    :target: https://pypi.python.org/pypi/privacyidea/
    
.. image:: https://img.shields.io/github/license/privacyidea/privacyidea.svg
    :alt: License
    :target: https://pypi.python.org/pypi/privacyidea/
    
.. image:: https://readthedocs.org/projects/privacyidea/badge/?version=latest
    :alt: Documentation
    :target: http://privacyidea.readthedocs.org/en/latest/

.. image:: https://codeclimate.com/github/privacyidea/privacyidea/badges/gpa.svg
    :alt: Code Climate
    :target: https://codeclimate.com/github/privacyidea/privacyidea
    
.. image:: http://issuestats.com/github/privacyidea/privacyidea/badge/pr?style=flat
    :alt: Issue stats
    :target: http://issuestats.com/github/privacyidea/privacyidea

.. image:: http://issuestats.com/github/privacyidea/privacyidea/badge/issue?style=flat
    :alt: Issue stats
    :target: http://issuestats.com/github/privacyidea/privacyidea
    
privacyIDEA is an open solution for strong two-factor authentication like 
OTP tokens, SMS, smartphones or SSH keys.
Using privacyIDEA you can enhance your existing applications like local login 
(PAM, Windows Credential Provider), 
VPN, remote access, SSH connections, access to web sites or web portals with 
a second factor during authentication. Thus boosting the security of your 
existing applications.

privacyIDEA does not bind you to any decision of the authentication
protocol or it does not dictate you where your user information should be
stored. This is achieved by its totally modular architecture.
privacyIDEA is not only open as far as its modular architecture is
concerned. But privacyIDEA is completely licensed under the AGPLv3.

It supports a wide variety of authentication devices like OTP tokens 
(HMAC, HOTP, TOTP, OCRA, mOTP), Yubikey (HOTP, TOTP, AES), FIDO U2F devices 
like Yubikey and Plug-Up, smartphone
Apps like Google Authenticator, FreeOTP, Token2  or TiQR,
SMS, Email, SSH keys, x509 certificates 
and Registration Codes for easy deployment.

privacyIDEA is based on Flask and SQLAlchemy as the python backend. The
web UI is based on angularJS and bootstrap.
A MachineToken design lets you assign tokens to machines. Thus you can use
your Yubikey to unlock LUKS, assign SSH keys to SSH servers or use Offline OTP with PAM.

Setup
=====

You can setup the system in a virtual environment::
    
    git clone https://github.com/privacyidea/privacyidea.git
    cd privacyidea
    virtualenv venv
    source venv/bin/activate
    pip install -r requirements.txt

Read the install instructions at http://privacyidea.readthedocs.org.

Running it
==========

Create the database and encryption key::

    ./pi-manage createdb
    ./pi-manage create_enckey

Create the key for the audit log::

    ./pi-manage create_audit_keys

Create the first administrator::

    ./pi-manage admin add <username>

Run it::

    ./pi-manage runserver

Now you can connect to http://localhost:5000 with your browser and login
as administrator.

Run in virtualenv
=================

For running the server in a virtual env see documentation at
http://privacyidea.readthedocs.org/en/latest/installation/index.html#python-package-index.

Run tests
=========

    nosetests -v --with-coverage --cover-package=privacyidea --cover-html

Code structure
==============

The database models are defined in ``models.py`` and tested in 
tests/test_db_model.py.

Based on the database models there are the libraries ``lib/config.py`` which is
responsible for basic configuration in the database table ``config``.
And the library ``lib/resolver.py`` which provides functions for the database
table ``resolver``. This is tested in tests/test_lib_resolver.py.

Based on the resolver there is the library ``lib/realm.py`` which provides
functions
for the database table ``realm``. Several resolvers are combined into a realm.

Based on the realm there is the library ``lib/user.py`` which provides functions 
for users. There is no database table user, since users are dynamically read 
from the user sources like SQL, LDAP, SCIM or flat files.

Upgrading
=========
In certain cases the database structure has changed (1.5->2.0).
Read http://privacyidea.readthedocs.org/en/latest/installation/upgrade.html 
for upgrade instructions.

Versioning
==========
privacyIDEA adheres to `Semantic Versioning <http://semver.org/>`_.