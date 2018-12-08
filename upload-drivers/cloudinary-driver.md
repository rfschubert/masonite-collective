# Cloudinary

{% hint style="info" %}
**Github** [https://github.com/vaibhavmule/masonite-cloudinary-driver](https://github.com/vaibhavmule/masonite-cloudinary-driver)  
**Pypi** [https://pypi.org/project/masonite-cloudinary-driver/](https://pypi.org/project/masonite-cloudinary-driver/)
{% endhint %}

## Requirements {#requirements}

In order to use the Cloudinary upload driver, you'll need:

* Python 3.4+
* Pip3
* Masonite 2.0+
* Cloudinary

## Getting Started

### Installation

{% code-tabs %}
{% code-tabs-item title="terminal" %}
```bash
$ pip install masonite-cloudinary-driver
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Masonite Setup

### Environment

Paste the access token in your project's `.env` file along with the folder name where you want your uploads to be saved.

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
CLOUDINARY_NAME=sdafjkdsajf
CLOUDINARY_SECRET=SJKFDjkfsdjknfjdsbfsd
CLOUDINARY_APIKEY=34893457863428957485894375
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Storage Config
Paste this in `config/storage.py` inside `DRIVERS` dict.

{% code-tabs %}
{% code-tabs-item title="config/storage.py" %}
```python

DRIVERS = {
    'cloudinary': {
        'cloud_name': env('CLOUDINARY_NAME'),
        'secret': env('CLOUDINARY_SECRET'),
        'api_key': env('CLOUDINARY_APIKEY')
    },
}
```
{% endcode-tabs-item%}
{% endcode-tabs %}

### Service Provider

Add the _**CloudinaryProvider**_ to _**PROVIDERS**_ in the `config/providers.py` file.

{% code-tabs %}
{% code-tabs-item title="config/providers.py" %}
```python
from masonite.contrib.cloudinary.providers import CloudinaryProvider

PROVIDERS = [
    # Third Party Providers
    CloudinaryProvider,
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using the Driver

{% code-tabs %}
{% code-tabs-item title="ActivityController.py" %}
```python

from masonite import Upload
from masonite.request import Request

class ActivityController:

    def create(self, View):
        return View('admin/activities/new')

    def store(self, upload: Upload, request: Request):
        upload.driver('cloudinary').store(
                request.input('image'),
                post_type)['secure_url']
        return request.redirect_to('dashboard')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

