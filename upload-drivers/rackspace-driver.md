# Rackspace

{% hint style="info" %}
**Github** [https://github.com/josephmancuso/masonite-rackspace-driver](https://github.com/josephmancuso/masonite-rackspace-driver)  
**Pypi** [https://pypi.org/project/masonite-rackspace-driver/](https://pypi.org/project/masonite-rackspace-driver/)
{% endhint %}

## Requirements <a id="requirements"></a>

In order to use the Rackspace upload driver, you'll need:

* Python 3.4+
* Pip3
* Masonite 2.0+
* Rackspace

## Getting Started

### Installation

{% code-tabs %}
{% code-tabs-item title="terminal" %}
```bash
$ pip install masonite-rackspace-driver
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Masonite Setup

### Environment

Paste the access token in your project's `.env` file along with the folder name where you want your uploads to be saved.

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
RACKSPACE_USERNAME=masonite
RACKSPACE_SECRET=3cd5b0e8...
RACKSPACE_CONTAINER=masonite
RACKSPACE_REGION=IAD
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Service Provider

Add the _**RackspaceProvider**_ to _**PROVIDERS**_ in the `config/providers.py` file.

{% code-tabs %}
{% code-tabs-item title="config/providers.py" %}
```python
from masonite.contrib.rackspace.providers import RackspaceProvider

PROVIDERS = [
    # Third Party Providers
    RackspaceProvider,
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
        Upload.driver('rackspace').store(Request.input('file_upload'))
        return Request.redirect_to('dashboard')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

