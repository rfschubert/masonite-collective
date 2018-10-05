# DigitalOcean

{% hint style="info" %}
**Github** [https://github.com/bjorntheart/masonite-digitalocean-driver](https://github.com/bjorntheart/masonite-digitalocean-driver)  
**Pypi**     [https://pypi.org/project/masonite-digitalocean-driver](https://pypi.org/project/masonite-digitalocean-driver/)
{% endhint %}

## Requirements {#requirements}

In order to use the Dropbox upload driver, you'll need:

* Python 3.4+
* Pip3
* Masonite 2.0+
* boto3

## Masonite Setup

### Environment

Paste the access token in your project's `.env` file along with the folder name where you want your uploads to be saved.

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
DO_REGION=nyc3
DO_ENDPOINT=https://nyc3.digitaloceanspaces.com
DO_SPACE=hello-space
DO_CLIENT=JIGJKDIKEL22VMKKIUYE
DO_SECRET=+zs11IroZZpoiGK4h+quKKsjXwP67ssOOAD2gawvNmX
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Service Provider

Add the _**DigitalOceanProvider**_ to _**PROVIDERS**_ in the `config/providers.py` file.

{% code-tabs %}
{% code-tabs-item title="config/providers.py" %}
```python
from masonite.contrib.dropbox.providers import DigitalOceanProvider

PROVIDERS = [
    # Third Party Providers
    DigitalOceanProvider,
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using the Driver

{% code-tabs %}
{% code-tabs-item title="ActivityController.py" %}
```python
class ActivityController:

    def create(self, View):
        return View('admin/activities/new')

    def store(self, Upload, Request):
        Upload.driver('digitalocean').store(Request.input('file_upload'))
        return Request.redirect_to('dashboard')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

