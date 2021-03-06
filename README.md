# AdLDAP2

[![Build Status](https://travis-ci.org/stevebauman/adldap-fork.svg)](https://travis-ci.org/stevebauman/adldap-fork)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/adLDAP2/adLDAP2/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/adLDAP2/adLDAP2/?branch=master)
[![Total Downloads](https://poser.pugx.org/adldap2/adldap2/downloads.svg)](https://packagist.org/packages/adldap2/adldap2)
[![Latest Stable Version](https://poser.pugx.org/adldap2/adldap2/v/stable.svg)](https://packagist.org/packages/adldap2/adldap2)
[![License](https://poser.pugx.org/adldap2/adldap2/license.svg)](https://packagist.org/packages/adldap2/adldap2)

> **Note:** This is a fork of the main abandoned adLDAP repository. You can file issues and pull-requests here and I will address / merge them.
> Looking for the original repository? [Main adLDAP Repository](https://github.com/adLDAP/adLDAP).

Originally written by Scott Barnett, Richard Hyland. Adopted by the community.

## To do

- Completely refresh all classes and improve the terrible scrutinizer score
- Unit / Functional Testing
- Better, and easier to understand documentation
- Create LDAP encapsulation class for easier testing

## Description

adLDAP2 is a PHP class library that provides LDAP authentication and Active Directory management tools.

## Requirements

To use adLDAP2, your sever must support:

- PHP 5.3 or greater
- PHP SSL Libraries (http://php.net/openssl)

## Installation

#### Via Composer

Add adLDAP2 to your `composer.json` file:

    "adldap2/adldap2": "4.0.*"

Run `composer update` on your project source, and you're all set!

#### Manual Installation

The core of adLDAP is contained in the 'src/adLDAP' directory.  Simply copy/rename this directory inside your own
projects.

Edit the file ``src/adldap/adLDAP.php`` and change the configuration variables near the top, specifically
those for domain controllers, base dn and account suffix, and if you want to perform anything more complex
than use authentication you'll also need to set the admin username and password variables too.

From within your code simply require the adLDAP.php file and call it like so

    use adLDAP\adLDAP;
    
    require_once(dirname(__FILE__) . '/adLDAP.php');
    
    $adldap = new adLDAP();

It would be better to wrap it in a try/catch though

    use adLDAP\adLDAP;
    
    try
    {
        $adldap = new adLDAP();
    }
    catch (adLDAPException $e)
    {
        echo $e;
        exit();   
    }

Then simply call commands against it e.g.

``$adldap->authenticate($username, $password);``

or 

``$adldap->group()->members($groupName);``

## Documentation

You can find our website at https://github.com/adldap/adLDAP/ or the class documentation at

https://github.com/adldap/adLDAP/wiki/adLDAP-Developer-API-Reference

## License

This library is free software; you can redistribute it and/or modify it under the terms of the 
GNU Lesser General Public License as published by the Free Software Foundation; either
version 2.1 of the License, or (at your option) any later version.

This library is distributed in the hope that it will be useful, but WITHOUT ANY WARRANTY; 
without even the implied warranty of MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  
See the GNU Lesser General Public License for more details or LICENSE.txt distributed with
this class.
