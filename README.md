# api-python-client

This is python version client for [api-gateway](https://github.com/restran/api-gateway). It is based on http lib [requests](http://docs.python-requests.org/en/master/), you can use it just like `requests`.

Notice that currently only GET and POST method are supported.

## Usage

```py
access_key = 'abcd'
secret_key = '1234'
api_gateway = 'http://127.0.0.1:6500'
endpoint = 'test_api'
version = 'v1'
client = APIClient(access_key, secret_key, api_gateway)
request = APIRequest(client, endpoint, version)
# get
r = request.get('/resource/')
print(r.content)

json_data = {
    'a': 1,
    'b': 'test string',
    'c': '中文'
}

# post
r = request.post('/resource/', json=json_data)
print(r.content)

# post image
with open('img.jpg', 'rb') as f:
    data = f.read()
    r = request.post('/resource/', data=data)

# use aes encrypt
request = APIRequest(client, endpoint, version, 'aes')
```
