Use memcached and the [memcached extension](http://php.net/manual/en/book.memcached.php) to provide a backing store for the WordPress object cache.

## Description
Memcached Object Cache provides a persistent backend for the WordPress object cache. A memcached server and the PECL memcache extension are required.

## Installation
1. Install memcached on at least one server. Note the connection info. The default is `127.0.0.1:11211`.

1. Install the memcached (not memcache) extension for PHP

1. Copy object-cache.php to wp-content

## Frequently Asked Questions

**How can I manually specify the memcached server(s)?**

Add something similar to the following to wp-config.php above `/* That's all, stop editing! Happy blogging. */`:

```
$memcached_servers = array(
    'default' => array(
        '10.10.10.20:11211',
        '10.10.10.30:11211'
    )
);
```

The top level array keys, are cache groups, where 'default' corresponds to any cache group that is not explicitly defined. This allows for specifying memcached servers that only handle certain cache groups. The most common use is only specifying 'default'.

Possible cache groups are:

`
{$taxonomy}_relationships
{$meta_type}_meta
{$taxonomy}_relationships
blog-details
blog-id-cache
blog-lookup
bookmark
calendar
category
comment
counts
general
global-posts
options
plugins
post_ancestors
post_meta
posts
rss
site-lookup
site-options
site-transient
terms
themes
timeinfo
transient
user_meta
useremail
userlogins
usermeta
users
userslugs
widget
`

## Changelog

### 1
* Initial fork
