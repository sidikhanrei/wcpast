# API Docs

WAChatPro API merupakan REST API yang dapat Anda gunakan mengirimkan dan mengambil data dari Whatsapp account dengan mengirimkan parameter request pada instance yang aktif di WAChatPro.

> Pastikan instance sudah berjalan agar REST API dapat berfungsi

Whatsapp API di WAChatPro adalah berbasis Whatsapp Web Protocol untuk melakukan komunikasi dan berbagai permintaan Anda.

Berikut ini adalah panduan untuk dapat mengakses WAChatPro REST API:



## API Status

### Url Address

Url address API WAChatPro adalah 

> https://api.wachatpro.com



### Standard Parameter

| Parameter | Value                                                        |
| --------- | ------------------------------------------------------------ |
| key       | adalah secret key yang digunakan untuk mengotorisasi setiap permintaan Anda pada WAChatPro |
| phone     | adalah nomor tujuan untuk kebutuhan pengiriman data melalui Whatsapp |
| body      | adalah isi pesan atau juga dapat berbentuk data yang dibutuhkan oleh API untuk memproses permintaan |



------



## Send

Parameter API untuk melakukan pengiriman pesan ke nomor tujuan

#### Parameter (Post)

| Parameter | Value                             | Mandatory |
| --------- | --------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/send | Yes       |
| key       | secret_key                        | Yes       |
| phone     | nomor Whatsapp tujuan             | Yes       |
| body      | isi pesan yang ingin dikirimkan   | Yes       |

#### </> Contoh Penggunaan

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/send';
$secretKey = '********';	// Sesuaikan dengan secret_key Anda

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'body' => 'Isi pesan whatsapp yang akan dikirimkan'
];
$json = json_encode($data); // Encode data

$options = stream_context_create([
    'http' => [
        'method'  => 'POST',
        'header'  => 'Content-type: application/json',
        'content' => $json
    ]
]);

// Send a request
$result = file_get_contents($url, false, $options);
```

#### Python

```python
import requests

url = "https://api.wachatpro.com/wa/send"
secretKey = "********"

obj = {
    "method": "POST",
    "params": {
        "key": secretKey,
        "phone": "62812345678xxx",
        "body": "Isi pesan whatsapp yang akan dikirimkan"
    }
}

# Send Request
req = request.post(
    url, 
    data = dict(
    	data = json.dumps(obj)
    )
)
```



------



## SendFile

Parameter API untuk mengirimkan pesan yang berupa file (*standard format yang didukung oleh whatsapp*)

#### Parameter (Post)

| Parameter | Value                                     | Mandatory |
| --------- | ----------------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/sendfile     | Yes       |
| key       | secret_key                                | Yes       |
| phone     | nomor Whatsapp tujuan                     | Yes       |
| body      | isi data dalam bentuk base64 encoded data | Yes       |
| filename  | nama file yang akan dikirimkan            | Yes       |
| caption   | caption file yang dikirimkan              | Optional  |

#### </> Contoh Penggunaan

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/sendfile';
$secretKey = '********';	// Sesuaikan dengan secret_key Anda

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'body' => 'iVBORw0KGgoAAAANSUhEUgAAAV4AAACWBAMAAABkyf1EAAAAG1BMVEXMzMyWlpa.....',
    'filename' => 'test.png',
    'caption' => 'keterangan gambar'
];
$json = json_encode($data);

$options = stream_context_create([
    'http' => [
        'method'  => 'POST',
        'header'  => 'Content-type: application/json',
        'content' => $json
    ]
]);

// Send a request
$result = file_get_contents($url, false, $options);
```

#### Python

```python
import requests

url = "https://api.wachatpro.com/wa/sendfile"
secretKey = "********"

obj = {
    "method": "POST",
    "params": {
        "key": secretKey,
        "phone": "62812345678xxx",
        "body": "iVBORw0KGgoAAAANSUhEUgAAAV4AAACWBAMAAABkyf1EAAAAG1BMVEXMzMyWlpa.....",
        "filename": "test.png",
        "caption": "keterangan gambar"
    }
}

# Send Request
req = request.post(
    url, 
    data = dict(
    	data = json.dumps(obj)
    )
)
```



------



## SendFileUrl

Parameter API untuk mengirimkan pesan yang berupa file dengan sumber yang berasal dari url address.

#### Parameter (Post)

| Parameter | Value                                                        | Mandatory |
| --------- | ------------------------------------------------------------ | --------- |
| URL       | https://api.wachatpro.com/wa/sendfileurl                     | Yes       |
| key       | secret_key                                                   | Yes       |
| phone     | nomor Whatsapp tujuan                                        | Yes       |
| url       | Url dari gambar yang akan dikirimkan                         | Yes       |
| caption   | caption atau pesan yang akan digunakan bersamaan dengan gambar yang dikirimkan | Optional  |

#### </> Contoh Penggunaan

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/sendfileurl';
$secretKey = '********';	// Sesuaikan dengan secret_key Anda

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'url' => 'https://web.wachatpro.com/assets/icon.png',
    'caption' => 'keterangan gambar'
];
$json = json_encode($data);

$options = stream_context_create([
    'http' => [
        'method'  => 'POST',
        'header'  => 'Content-type: application/json',
        'content' => $json
    ]
]);

// Send a request
$result = file_get_contents($url, false, $options);
```

#### Python

```python
import requests

url = "https://api.wachatpro.com/wa/sendfileurl"
secretKey = "********"

obj = {
    "method": "POST",
    "params": {
        "key": secretKey,
        "phone": "62812345678xxx",
        "url": "https://web.wachatpro.com/assets/icon.png"
        "caption": "keterangan gambar"
    }
}

# Send Request
req = request.post(
    url, 
    data = dict(
    	data = json.dumps(obj)
    )
)
```



------

## Chats

Parameter API untuk mendapatkan daftar chat.

#### Parameter (Post)

| Parameter | Value                              | Mandatory |
| --------- | ---------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/chats | Yes       |
| key       | secret_key                         | Yes       |
| limit     | Jumlah list chat, 100 (*default*)  | Yes       |

#### </> Contoh Penggunaan

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/chats';
$secretKey = '********';	// Sesuaikan dengan secret_key Anda

$data = [
    'key' => $secretKey,
    'limit' => 50
];
$json = json_encode($data);

$options = stream_context_create([
    'http' => [
        'method'  => 'POST',
        'header'  => 'Content-type: application/json',
        'content' => $json
    ]
]);

// Send a request
$result = file_get_contents($url, false, $options);
```

#### Python

```python
import requests

url = "https://api.wachatpro.com/wa/chats"
secretKey = "********"

obj = {
    "method": "POST",
    "params": {
        "key": secretKey,
        "limit": 50
    }
}

# Send Request
req = request.post(
    url, 
    data = dict(
    	data = json.dumps(obj)
    )
)
```

------

## Messages

Parameter API untuk mendapatkan isi chat sesuai dengan nomor tujuan yang diminta.

#### Parameter (Post)

| Parameter | Value                              | Mandatory |
| --------- | ---------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/messages | Yes       |
| key       | secret_key                         | Yes       |
| phone |nomor Whatsapp yang akan di download |yes |
| limit     | Jumlah list pesan, 100 (*default*) | Yes       |

#### </> Contoh Penggunaan

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/messages';
$secretKey = '********';	// Sesuaikan dengan secret_key Anda

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'limit' => 50
];
$json = json_encode($data);

$options = stream_context_create([
    'http' => [
        'method'  => 'POST',
        'header'  => 'Content-type: application/json',
        'content' => $json
    ]
]);

// Send a request
$result = file_get_contents($url, false, $options);
```

#### Python

```python
import requests

url = "https://api.wachatpro.com/wa/messages"
secretKey = "********"

obj = {
    "method": "POST",
    "params": {
        "key": secretKey,
        "phone": "62812345678xxx",
        "limit": 50
    }
}

# Send Request
req = request.post(
    url, 
    data = dict(
    	data = json.dumps(obj)
    )
)
```

------



## Contacts

Parameter API untuk mendapatkan seluruh kontak yang ada di Whatsapp.

#### Parameter (Post)

| Parameter | Value                                 | Mandatory |
| --------- | ------------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/contacts | Yes       |
| key       | secret_key                            | Yes       |

#### </> Contoh Penggunaan

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/contacts';
$secretKey = '********';	// Sesuaikan dengan secret_key Anda

$data = [
    'key' => $secretKey
];
$json = json_encode($data);

$options = stream_context_create([
    'http' => [
        'method'  => 'POST',
        'header'  => 'Content-type: application/json',
        'content' => $json
    ]
]);

// Send a request
$result = file_get_contents($url, false, $options);
```

#### Python

```python
import requests

url = "https://api.wachatpro.com/wa/contacts"
secretKey = "********"

obj = {
    "method": "POST",
    "params": {
        "key": secretKey
    }
}

# Send Request
req = request.post(
    url, 
    data = dict(
    	data = json.dumps(obj)
    )
)
```

------