========================================
AWS Process Credential Providers Plug-in
========================================

.. image:: https://travis-ci.org/awslabs/awsprocesscreds.svg?branch=master
   :target: https://travis-ci.org/awslabs/awsprocesscreds


This document covers what is is to be a SAML provider plug-in.

Generally, a plug-in refers to any class registered to the entry point group 
'saml_form_authenticators' and which also conforms to the SAMLAuthenticator 
interface. See Requirements for more constraints.

Example:

    entry_points={
         'saml_form_authenticators': [
            'example = plugin.example:ExampleFormsBasedAuthenticator',
    }

For reference, the file setup.py in this project registers both default 
providers as plug-ins.


General Plug-in Overview
------------------------

At runtime, all registered plug-in names retrieved using pkg_resources will be 
matched against the user supplied value for -p (--provider). An exact match 
will instatiate that class, no match will throw an unspupported error.

Inheritance from SAMLAuthenticator is not required.


Requirements
------------

Generally this assume an installed module.

* Plug-in has an entry point registered under group 'saml_form_authenticators'
* Class implements the awsprocesscreds.saml:SAMLAuthenticator specification


Futher Information
------------------

Both of the SAML authenticators shipped with the product utilize the plug-in 
loading process. If you are looking at how to implement one to support your 
own business requirements then it is suggested to review both those classes.
