
# to patch a library

1. generate fichier diff
```shell
diff -u vendor/symfony/var-dumper/Dumper/HtmlDumper_ORIGINAL.php vendor/symfony/var-dumper/Dumper/HtmlDumper.php > patches/var-dumper.patch
```
2. modif patch file add a => origine file b => patch file
```
--- a/vendor/symfony/var-dumper/Dumper/HtmlDumper.php	2021-10-27 09:41:02.148214098 +0200
+++ b/vendor/symfony/var-dumper/Dumper/HtmlDumper.php	2021-10-27 09:39:28.177217956 +0200
```
3. use composer-patches for apply patch
```shell
composer require cweagans/composer-patches
```
4. Add extra in composer.json
```json
{
  "extra": {
    "patches": {
      "symfony/var-dumper": {
        "Change collor text": "patches/var-dumper.patch"
      },
      "composer-exit-on-patch-failure": true
    }
  }
}
```