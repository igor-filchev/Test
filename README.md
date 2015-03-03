Created 02.03.2015
Last update 03.03.2015


###03-03-2015 (Created  by Igor)
###Rss feed module
To add rss feed on website do next things:
 1. Include in your folders rss class and servicing file `/template/pages/rss`
 2. Add next html code in header of website
```
<link rel="alternate" type="application/rss+xml" href="http://adress/rss" title="RSS feed">
```
Write in `href attibute` name of your website main page of your RSS feed and in `title attribute` name for
your RSS feed . Then this code with inform rss reader, that your website has RSS feed and redirect on it from 
any page.
 3. Correct index file
```
if ($uri->args[0] == "rss"){
    if (file_exists(ROOT . "template/pages/rss/rss.php")){
        include(ROOT . "template/pages/rss/rss.php");
    }
}
else{
    bla-bla-bla...
}
```
This code asks for rss file only if such request exists
 4. Set up sql query parameters in serving file `/template/pages/rss/rss.php`. Do not change name of fields
after `AS`!
 5. Set up parameters after requesting rss class (from line 30 in `/template/pages/rss/rss.php`)


###File upload module
###Created 02-12-2014 by Igor
With usage [FileAPI](https://github.com/RubaXa/jquery.fileapi) jquery plugin

To activate it you need to do next steps:
 1. Add to your project FileAPI files `/template/js/FileAPI`
 2. Add file_upload directory from path: /template/modules/upload and include main file in needed file
```
include ROOT . "/template/modules/file_upload/file_upload.php";
```

 3. Include FileApi and File upload module js-files in needed file
```
 <script>
    window.FileAPI = {
        debug: false, // debug mode
        staticPath: '/js/FileAPI/' // path to *.swf
    };
</script>

<script src="/template/js/FileAPI/FileAPI.min.js"></script>
<script src="/template/js/FileAPI/FileAPI.exif.js"></script>
<script src="/template/js/FileAPI/jquery.fileapi.min.js"></script>

<script src="/template/modules/file_upload/drag_drop.js"></script>
```
 4. Add Images folder `/template/img/system_images`
 5. Set up directory for file upload in `/template/modules/file_upload/ajax.php` on lines 38 and 49 (variable
$uploaddir) and `sql` requests (lines 74 and 84)
