# API Docs

WAChatPro API is the most powerfull REST API that allow you to receive messages, send messages, and other Whatsapp function through your Whatsapp Account. Just using a simple request and parameters, use can use WAChatPro API with more flexibilities.

> Before using the REST API, please make sure the instance is running

The Whatsapp API is based on the Whatsapp Web Protocol doing communications and other request from your system.

Bellow is examples and how to use WAChatPro REST API:

> You can use your own programming language, in this example we are currently using php and python as an example.


## API Status

### Url Address

WAChatPro API Url address

> https://api.wachatpro.com



### Standard Parameter

| Parameter | Value                                                        |
| --------- | ------------------------------------------------------------ |
| key       | You need to pass your own secret_key to authorization that request is legally from you (*you can found in your instance info*). |
| phone     | A phone number with international format (*starting with the country code*). |
| body      | Message text or message data, you can use unicode format.    |



------



## Send

Send a message to a new or existing chat. The message will be added to the sending queue.

#### Parameter (Post)

| Parameter | Value                                                        | Mandatory |
| --------- | ------------------------------------------------------------ | --------- |
| URL       | https://api.wachatpro.com/wa/send                            | Yes       |
| key       | secret_key                                                   | Yes       |
| phone     | A phone number with international format (*starting with the country code*) | Yes       |
| body      | Message text or message data, you can use unicode format.    | Yes       |

#### </> Example of use

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/send';
$secretKey = '********';	// Change to your own secret_key

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'body' => 'body text messages'
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
        "body": "body text messages"
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

Send a file message to a new or existing chat with base64 encoded data.

#### Parameter (Post)

| Parameter | Value                                                        | Mandatory |
| --------- | ------------------------------------------------------------ | --------- |
| URL       | https://api.wachatpro.com/wa/sendfile                        | Yes       |
| key       | secret_key                                                   | Yes       |
| phone     | A phone number with international format (*starting with the country code*) | Yes       |
| body      | base64 encoded data                                          | Yes       |
| filename  | filename to include in message                               | Yes       |
| caption   | caption of the file                                          | Optional  |

#### </> Example of use

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/sendfile';
$secretKey = '********';	// Change to your own secret_key

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'body' => 'iVBORw0KGgoAAAANSUhEUgAAAV4AAACWBAMAAABkyf1EAAAAG1BMVEXMzMyWlpa.....',
    'filename' => 'test.png',
    'caption' => 'image descriptions / caption'
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
        "caption": "image descriptions / caption"
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

Send a file message to a new or existing chat include image from url you passed.

#### Parameter (Post)

| Parameter | Value                                                        | Mandatory |
| --------- | ------------------------------------------------------------ | --------- |
| URL       | https://api.wachatpro.com/wa/sendfileurl                     | Yes       |
| key       | secret_key                                                   | Yes       |
| phone     | A phone number with international format (*starting with the country code*) | Yes       |
| url       | url of file that make API grab that content automatically    | Yes       |
| caption   | caption or messages that included with file or image you send | Optional  |

#### </> Example of use

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/sendfileurl';
$secretKey = '********';	// Change to your own secret_key

$data = [
    'key' => $secretKey,
    'phone' => '62812345678xxx',
    'url' => 'https://web.wachatpro.com/assets/icon.png',
    'caption' => 'image descriptions / caption'
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
        "caption": "image descriptions / caption"
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

Get list of chats from your Whatsapp account.

#### Parameter (Post)

| Parameter | Value                               | Mandatory |
| --------- | ----------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/chats  | Yes       |
| key       | secret_key                          | Yes       |
| limit     | limit of list chat, 100 (*default*) | Yes       |

#### </> Example of use

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/chats';
$secretKey = '********';	// Change to your own secret_key

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

Get specific messages from a phone numbers.

#### Parameter (Post)

| Parameter | Value                              | Mandatory |
| --------- | ---------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/messages | Yes       |
| key       | secret_key                         | Yes       |
| phone |A phone number with international format (*starting with the country code*)|yes |
| limit     | limit of messages, 100 (*default*) | Yes       |

#### </> Example of use

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/messages';
$secretKey = '********';	// Change to your own secret_key

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

Get contacts list of your Whatsapp Account.

#### Parameter (Post)

| Parameter | Value                                 | Mandatory |
| --------- | ------------------------------------- | --------- |
| URL       | https://api.wachatpro.com/wa/contacts | Yes       |
| key       | secret_key                            | Yes       |

#### </> Example of use

#### PHP

```php
$url = 'https://api.wachatpro.com/wa/contacts';
$secretKey = '********';	// Change to your own secret_key

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