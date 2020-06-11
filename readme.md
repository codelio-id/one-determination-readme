# Codelio

## Screenshot

![screenshot](https://github.com/codelio-id/one-determination-readme/blob/master/screenshot.jpg?raw=true)

## Cara menambah fitur di aplikasi ini

- Salin folder yang memuat fitur yang kamu inginkan ke _/modules_.
- Tambah kutipan kode berikut ke dalam file _index.php_ yang terdapat di dalam folder fitur _contoh: /modules/(nama_folder_fitur)/index.php_ dan letakkan kode tersebut di baris paling atas.

```php
<?php

require_once("../../_config.php");

if (session_status() == PHP_SESSION_NONE) session_start();

if (isset($_SESSION['user'])) {
  $isAuthorized = false;
  foreach (json_decode($_SESSION['user'])->privilege as $val) {
    if ($val->detail == $_GET['slug']) {
      $isAuthorized = true;
        break;
    }
  }
  if (!$isAuthorized) die(header('location: ' . $base_url . 'auth.php'));
} else die(header('location: ' . $base_url . 'auth.php'));

?>
```

- Tambahkan kode dalam file _features.json_ seperti berikut.

Sebelum ditambah

```json
[
  {
    "slug": "fb",
    "name": "FB ACC Check",
    "icon": "fa fa-facebook",
    "folder_name": "fb"
  }
]
```

Setelah ditambah (misalkan kita akan menambah fitur acc check twitter)

```json
[
  {
    "slug": "fb",
    "name": "FB ACC Check",
    "icon": "fa fa-facebook",
    "folder_name": "fb"
  },
  {
    "slug": "twitter",
    "name": "Twit ACC Check",
    "icon": "fa fa-twitter",
    "folder_name": "twitter"
  }
]
```

| Kunci         | Deskripsi                                                                                                      |
| ------------- | -------------------------------------------------------------------------------------------------------------- |
| _slug_        | Silahkan pilih sesuai keinginan (digunakan untuk url)                                                          |
| _name_        | Silahakan pilih sesuai keinginan (digunakan untuk nama navigasi)                                               |
| _icon_        | Silahkan pilih ikon disini [link](https://fontawesome.com/icons?d=gallery) format penamaan _fa fa-(nama_icon)_ |
| _folder_name_ | Silahkan beri nama sesuai dengan nama folder fitur kamu                                                        |

By codelio with ❤
