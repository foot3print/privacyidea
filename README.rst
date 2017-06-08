privacyIDEA - https://github.com/privacyidea/privacyidea
===========
privacyIDEA is an open solution for strong two-factor authentication like 
OTP tokens, SMS, smartphones or SSH keys.
Using privacyIDEA you can enhance your existing applications like local login 
(PAM, Windows Credential Provider), 
VPN, remote access, SSH connections, access to web sites or web portals with 
a second factor during authentication. Thus boosting the security of your 
existing applications.

Overview
========

privacyIDEA runs as an additional service in your network and you can connect different 
applications to privacyIDEA.

.. image:: https://privacyidea.org/wp-content/uploads/2017/privacyIDEA-Integration.png
    :alt: privacyIDEA Integration
    :scale: 50 %

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
