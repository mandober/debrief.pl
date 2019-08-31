# PHP Ecosystem

* PHP Implementations
  - HHVM
  - HPHPc
  - Parrot
  - Phalanger
  - Quercus
  - Zend Engine

* PHP Internals
  - PEAR
  - Accelerator
  - Composer

* PHP components:
  * Libraries
  * Frameworks
  * Web apps

* PHP ORM
  - Doctrine
  - Propel

* PHP frameworks
  - Laravel
  - Symfony
  - CakePHP
  - CodeIgniter
  - Nette Framework
  - Fat-Free
  - FuelPHP

* PHP Testing frameworks
  - Behat
  - PHPUnit
  - PHP Unit Testing Framework
  - Lime (Symfony)

* PHP IDE
  Aptana
  Codelobster
  Eclipse PDT
  NetBeans 
  PHPEdit
  PhpStorm
  RadPHP
  Zend Studio

* PHP Widget toolkit
  - PHP-GTK
  - PHP-Qt
  - wxPHP

* PHP Web Apps
  * CMS
    - Drupal
    - Joomla!
    - eZ Publish
    - WordPress
    - XOOPS
  * misc
    - Horde
    - Li3 (formerly Lithium)
    - Midgard
    - MODx
    - Phalcon
    - Pop PHP
    - PHP-Fusion
    - PRADO
    - Qcodo
    - Silex
    - SilverStripe
    - TYPO3
    - Xaraya
    - Yii
    - Zend Framework
    - Zeta Components


* PHP Interface Type
  * SAPI (Server API)
    - aolserver
    - apache
    - apache2filter
    - apache2handler
    - caudium
    - cgi (until PHP 5.3)
    - cgi-fcgi
    - cli
    - cli-server
    - continuity
    - embed
    - fpm-fcgi
    - isapi
    - litespeed
    - milter
    - nsapi
    - phttpd
    - pi3web
    - roxen
    - thttpd
    - tux
    - webjames



# PHP Manual

PHP > PHP Manual:

* PHP Installation and Configuration
  - Installation
    - Windows
    - Unix
    - macOS
    - Cloud computing platforms
  - FastCGI Process Manager (FPM)
  - Runtime Configuration
  - PECL extensions
* PHP Function Reference
  * Database Extensions
    * Abstraction Layers
      - PDO
      - ODBC
      - DBA
      - dbx
    * Vendor Specific Database Extensions
      - Mssql (Microsoft SQL Server)
      - MySQL (MySQL Drivers and Plugins)
      - MongoDB
      - PostgreSQL
      - SQLite3
      * SQLSRV (Microsoft SQL Server Driver for PHP)
      - SQLite
      - Firebird/InterBase
      - DB++
      - CUBRID
      - dBase
      - filePro
      - FrontBase
      - IBM DB2 (IBM DB2, Cloudscape and Apache Derby)
      - Informix
      - Ingres (Ingres DBMS, EDBC, and Enterprise Access Gateways)
      - MaxDB
      - mSQL
      - OCI8 (Oracle OCI8)
      - Paradox (Paradox File Access)
      - Sybase
      - tokyo_tyrant
* PHP Language Reference
  - Basic syntax
  - Types
  - Variables
  - Constants
  - Expressions
  - Operators
  - Control Structures
  - Functions
  - Classes and Objects
  - Namespaces
  - Errors
  - Exceptions
  - Generators
  - References Explained
  - Predefined Variables
  - Predefined Exceptions
  - Predefined Interfaces and Classes
  - Context options and parameters
  - Supported Protocols and Wrappers
* PHP Security
  - Introduction
  - General considerations
  - Installed as CGI binary
  - Installed as an Apache module
  - Session Security
  - Filesystem Security
  - Database Security
  - Error Reporting
  - Using Register Globals
  - User Submitted Data
  - Magic Quotes
  - Hiding PHP
  - Keeping Current
* PHP Features
  - HTTP authentication with PHP
  - Cookies
  - Sessions
  - Dealing with XForms
  - Handling file uploads
  - Using remote files
  - Connection handling
  - Persistent Database Connections
  - Safe Mode
  - Command line usage
  - Garbage Collection
  - DTrace Dynamic Tracing
* PHP Function Reference
  - Affecting PHP's Behaviour
  - Audio Formats Manipulation
  - Authentication Services
  - Command Line Specific Extensions
  - Compression and Archive Extensions
  - Credit Card Processing
  - Cryptography Extensions
  - Database Extensions
  - Date and Time Related Extensions
  - File System Related Extensions
  - Human Language and Character Encoding Support
  - Image Processing and Generation
  - Mail Related Extensions
  - Mathematical Extensions
  - Non-Text MIME Output
  - Process Control Extensions
  - Other Basic Extensions
  - Other Services
  - Search Engine Extensions
  - Server Specific Extensions
  - Session Extensions
  - Text Processing
  - Variable and Type Related Extensions
  - Web Services
  - Windows Only Extensions
  - XML Manipulation
  - GUI Extensions
* PHP at the Core: A Hacker's Guide
  - Memory management
  - Working with Variables
  - Writing Functions
  - Writing Classes
  - Working with Resources
  - Working with INI settings
  - Working with streams
  - The "counter" Extension - a Continuing Example
  - The PHP 5 build system
  - Extension structure
  - PDO Driver How-To
  - Zend Engine 2 API reference
  - Zend Engine 2 Opcodes
  - Zend Engine 1
* PHP FAQ
  - PHP Installation
  - Build Problems
  - Using PHP
  - Safe Password Hashing
  - PHP and HTML
  - PHP and COM
  - Miscellaneous


* PHP Variants
  * Bitness
    - x86
    - x64
  * Thread Safety
    - TS (Thread Safe)
    - NTS (Non-Thread Safe)
  * Implementation
    - FastCGI
    - SAPI (System API)
* PHP Components
  * Servers
    - Apache HTTP Server
      - use *Thread Safe PHP* build
    - IIS
      - if using `FastCGI` use *Non-Thread Safe PHP* build
    - NGenX
  * OS
    * Linux
      * Modules
        - `.so`
    * Windows
      * Microsoft Visual C++ RunTime, `MSVC`
        * `VC11`
          - built with: Visual Studio 2012, `VS 2012`
          - requires: `Visual C++ Redistributable for VS2012 x64` (or x86)
        * `VC14`
          - built with: Visual Studio 2015, `VS 2015`
          - requires: `Visual C++ Redistributable for VS2015 x64` (or x86)
        * `VC15`
          - built with: Visual Studio 2017, `VS 2017`
          - requires: `Visual C++ Redistributable for VS2017 x64` (or x86)
      * Modules
        - `.dll`
