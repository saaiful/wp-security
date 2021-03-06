# ফাইল পারমিশন 
[ফাইলসিস্টেমে](https://en.wikipedia.org/wiki/File_system_permissions) ব্যবহারকারী কি করতে পারবে আর কি করতে পারবে না তা ঠিক করার জন্য ফাইল পারমিশন ব্যবহার করা হয়। *nix সার্ভারে ফাইল পারমিশন তিন সংখ্যার একটা নাম্বার দিয়ে প্রকাশ করা হয়ে থাকে। 

ফাইলের মালিকানা ইউনিক্স সিস্টেমের একটি গুরুত্বপূর্ণ অংশ যা ফাইল সংরক্ষণের একটি নিরাপদ পদ্ধতি . ইউনিক্সে প্রতিটি ফাইলের জন্য নিম্নলিখিত বৈশিষ্ট্য আছে -

**মালিকের অনুমতিঃ**  মালিকের অনুমতি নির্ধারণ করে ফাইলের মালিক ফাইলে কি কি করতে পারবেন।

**দলের অনুমতিঃ** দলের অনুমতির নির্ধারণ করে ফাইলটি যে দলের তারা এই ফাইলে কি কি করতে পারবেন।

**অন্যান্য অনুমতিঃ** এটি নির্ধারন করে উ্পরে উল্লেখিত ব্যবকারীগন ব্যাতীত অন্যান্বহারকারীগন ফাইলে কি কি করতে পারবেন।

| ধরন | মান | কারন |
| -- | -- | -- |
| Read | 4 | ফাইল/ফোডার রিড করতে পারবে |
| Write | 2 | ফাইল/ফোডার রাইট করতে পারবে |
| eXecute | 1 | ফাইল/ফোডারকে প্রোগ্রাম হিসাবে চালাতে পারবে |

একটা ফাইলের পারমিশন গঠিত হয় ৩ টি সংখ্যার যোগফল পাশাপাশি সাজিয়ে। মনে করুন Owner এর ফাইল পারমিশন গঠিত হয় r+w+x এর যোগফলের মাধ্যমে। খেয়াল করলে দেখতে পারবেন আমরা উপরে উলেখিত ভ্যালু গুলো ব্যবহার করেছি পারমিশন দেয়ার জন্য। তাহলে r+w+x এর যোগফল পেলাম ৬ যা আমাদের ফাইল পারমিশনের প্রথম অংশ। এখানে দেখুন রিড (r) এর জন্য ভ্যালু 4 , রাইট (w) এর জন্য ভ্যালু , এক্সিকিউট(x)এর জন্য ভ্যালু ০ । আর যদি পারমিশন না দেন তাহলে ভ্যালু হবে 0।

![](images/7.jpg)

একই ভাবে ২য় এবং ৩য় অংশ পেলাম , এবার এদের পাশাপাশি সাজালে পাওয়া যায়ে 644 যা ফাইলের মালিককে রিড+রাইট করার পারমিশন দেয় , গ্রুপ কে রিড করার পারমিশন এবং ওয়াল্ড/পাবলিক কে কে রিড করার পারমিশন দেয়।

ফাইল পারমিশন জেনারেট করার জন্য এই [সাইটটি](http://permissions-calculator.org/) (http://permissions-calculator.org/) ব্যবহার করতে পারেন।

ওয়ার্ডপ্রেসে কিছু ফাইলের পারমিশনের উপর আপনার সাইটের নিরাপত্তা সামান্য হলেও নির্ভর করে। নিছে সেগুলো দেয়া হল।

| ফাইল/ফোল্ডারের নাম | ফাইল/ফোল্ডারের পাথ | রিকমেন্ডেড পারমিশন |
| -- | -- | -- |
|.htaccess|	../.htaccess|	404|
|wp-config.php|	../wp-config.php|	400|
|index.php|	../index.php|	400|
|wp-blog-header.php|	../wp-blog-header.php|	400|
|root folder|	../|	705|
|wp-admin/|	../wp-admin|	705|
|wp-includes/|	../wp-includes|	705|
|wp-content/	|../wp-content|	705|

**রুট ফোল্ডারে 705 পারমিশন ব্বহার করলে অনেক সময় সার্ভার রেস্পঞ্জ করে না/এরর/ফরভিডেন দেখায় , যদি এই রকম সমস্যা হয় তবে পারমিশন 750 করে সমস্যার সমাধান করতে হবে।*
