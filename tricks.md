# সিকিউরিটি ট্রিকস

এডমিন প্যানেল থেকে প্লাগিন আপডেট/ইন্সটল বন্ধ করতে `wp-config.php` তে নিচের লাইন লিখুন
```php
define('DISALLOW_FILE_MODS',true);
```

এডমিন প্যানেলের কোড এডিটর অফ করে দিতে `wp-config.php` তে নিচের লাইন লিখুন
```php
define( 'DISALLOW_FILE_EDIT', true);
```

ওয়ার্ডপ্রেসের কোর আপডেট অটোমেটিক করার জন্য `wp-config.php` তে নিচের লাইন লিখুন
```php
define( 'WP_AUTO_UPDATE_CORE', true );
```

`wp-config.php` তে এক্সেস রেস্টিক্টেড করুন, এর জন্য` .htaccess` এ নিচের লাইনগুলো লিখুন
```
<files wp-config.php>
    order allow,deny
    deny from all
</files>
```

স্ক্রিপ্ট ইঞ্জেকশন থেকে বাঁচার জন্য `.htaccess` এ নিচের লাইনগুলো লিখুন
```
Options +FollowSymLinks
RewriteEngine On
RewriteCond %{QUERY_STRING} (\<|%3C).*script.*(\>|%3E) [NC,OR]
RewriteCond %{QUERY_STRING} GLOBALS(=|\[|\%[0-9A-Z]{0,2}) [OR]
RewriteCond %{QUERY_STRING} _REQUEST(=|\[|\%[0-9A-Z]{0,2})
RewriteRule ^(.*)$ index.php [F,L]
```

ওয়ার্ডপ্রেস এর ভার্শন দেখানো বন্ধ করতে theme এর function.php তে নিচার লাইনগুলো যুক্ত করুন
```php
remove_action('wp_head', 'wp_generator');
function wpt_remove_version() {
   return '';
}
add_filter('the_generator', 'wpt_remove_version'); // remove from rss
```

