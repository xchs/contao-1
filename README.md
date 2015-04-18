Contao Open Source CMS
======================

Contao is an Open Source PHP Content Management System for people who want a
professional website that is easy to maintain. Visit the [project website][1]
for more information.


System requirements
-------------------

 * Web server with symlink support
 * PHP 5.4+ with GDlib, DOM, Phar, openssl and SOAP
 * MySQL 5.0.3+


Prerequisites
-------------

 * A Symfony 2.6+ installation

If you do not yet have a Symfony installation, we recommend installing the
[Contao standard edition][2].


Installation
------------

Open a command console, enter your project directory and add the following to
 your `composer.json` file:

```sh
"require": {
    "contao/contao": "~4.0"
},
"config": {
    "component-dir": "assets"
},
"post-install-cmd": {
    "Contao\\CoreBundle\\Composer\\ScriptHandler::addContaoDirectories"
},
"post-update-cmd": {
    "Contao\\CoreBundle\\Composer\\ScriptHandler::addContaoDirectories"
}
``` 

Then run `php composer.phar update` to install the vendor files.


Activation
----------

Add the following lines to your `app/AppKernel.php` file:

```php
// app/AppKernel.php
class AppKernel extends Kernel
{
    public function registerBundles()
    {
        $bundles = array(
            // ...
            new Contao\CoreBundle\ContaoCoreBundle(),
            new Contao\CoreBundle\ContaoCalendarBundle(),
            new Contao\CoreBundle\ContaoCommentsBundle(),
            new Contao\CoreBundle\ContaoFaqBundle(),
            new Contao\CoreBundle\ContaoListingBundle(),
            new Contao\CoreBundle\ContaoNewsBundle(),
            new Contao\CoreBundle\ContaoNewsletterBundle(),
        );

        \Contao\CoreBundle\Kernel\BundleSorter::sort($bundles);

        // ...
    }
}
```

You can optionally omit everything but the `ContaoCoreBundle`.


License
-------

Contao is licensed under the terms of the LGPLv3.


Getting support
---------------

Visit the [support page][3] to learn about the available support options.


[1]: https://contao.org
[2]: https://github.com/contao/standard-edition
[3]: https://contao.org/support.html
