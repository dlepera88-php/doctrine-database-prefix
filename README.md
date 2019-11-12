# What a f... is this? #

In some cases, we need to install a web application on shared hosts. On shared hosts, database names usually have a prefix,
like cPanel, for example.  Eg: etc_dbname.

So, I make this package. I hope this help u.

# Basic Usage #

```php
<?php 
// $connectionOptions and $config set earlier
/** @var $connectionOptions */
/** @var array $config */

$evm = new \Doctrine\Common\EventManager;

// Database Prefix
$database_prefix = new \DoctrinePrefixes\DatabasePrefix('db_');
$evm->addEventListener(\Doctrine\ORM\Events::loadClassMetadata, $database_prefix);

// Table Prefix
$table_prefix = new \DoctrinePrefixes\TablePrefix('prefix_');
$evm->addEventListener(\Doctrine\ORM\Events::loadClassMetadata, $table_prefix);

$em = \Doctrine\ORM\EntityManager::create($connectionOptions, $config, $evm);

```