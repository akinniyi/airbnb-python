airbnb-python
===================

Airbnb Python API

Disclaimer
----------

This is a unofficial python API wrapper for airbnb.com

Using this software might contradict airbnb.com terms of service

Requirements
------------

* requests

Usage:
------

    pip install airbnb

### Initialize API with your airbnb.com username and password:

```python
import airbnb
api = airbnb.Api(login, password)
```

### Once you logged in, please use your access token, to avoid getting your account locked

```python
api = airbnb.Api(access_token=`<ACCESS_TOKEN_OBTAINED_ON_LOGIN>`)
```

### Get you user profile

```python
api.get_profile()
```

### Get listing availability

```python
api.get_calendar(listing_id)
```

Optional parameters:

- `starting_month`: first month of the calendar (can't be in the past)
- `starting_year`: first year of the calendar (can't be in the past)
- `calendar_months`: how many months ahead you want to get the calendar for

Example:

```python
api.get_calendar(975964, starting_month=9, starting_year=2017, calendar_months=1)
```

### Get listing reviews
 
```python
api.get_reviews(listing_id)
```

Optional parameters:

- `offset`: paging offset
- `limit`: number of results per page

Example:

```python
api.get_reviews(975964, offset=20, limit=20)
```

### 🌿 VerificationError (420)

This exception occurs when you send too many login requests (i.e. call `Api()` with your credentials).
Once you are logged in with your credentials you can just use your access token (`Api(access_token="<TOKEN>")`)
As a workaround, try to login manually though the website or mobile app and complete Airbnb's verification process.
You can also try to use a VPN or a proxy.


### Testing

The package has some dectests to test authentication process, to run the tests first export the following env variables:

```bash
export AIRBNB_LOGIN=`<YOUR_LOGIN>`
export AIRBNB_PASSWORD=`<YOUR_PASSWORD>`
export AIRBNB_ACCESS_TOKEN=`<ACCESS_TOKEN_OBTAINED_ON_LOGIN>`
```

Then, setup Python environment as follows:

```bash
pipenv shell
pipenv install --dev
```

Finally, run the doctests using nose:

```bash
nosetests --with-doctest

```

[![Build Status](https://travis-ci.org/nderkach/airbnb-python.svg)](https://travis-ci.org/nderkach/airbnb-python)
