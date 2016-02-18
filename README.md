# api-python-sdk

This is python version sdk for api-gateway. It is based on http lib `requests`, you can use it just like `requests`.

Notice that currently only get and post method are supported.

## Usage

```py
access_key = 'abcd'
secret_key = '1234'
api_gateway = 'http://127.0.0.1:6500'
endpoint = 'test_api'
version = 'v1'

# encrypt_type can use raw or aes
req = ClientAuthRequest(access_key, secret_key,
                        api_gateway, endpoint,
                        version, encrypt_type='aes')

# post data
json_data = {
    'a': 1,
    'b': 'test string',
    'c': '中文'
}

body = json.dumps(json_data, ensure_ascii=False)
r = req.post('/resource/', body=body)

print(r.status_code)
print(r.content)
print(r.json)


# post image
with open('img.jpg', 'rb') as f:
    body = f.read()
    r = req.post('/resource/', body=body)


# get
r = req.get('/resource/')
```
