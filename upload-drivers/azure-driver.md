# Azure

{% hint style="info" %}
**Github** [https://github.com/josephmancuso/masonite-azure-driver](https://github.com/josephmancuso/masonite-azure-driver)  
**Pypi** [https://pypi.org/project/masonite-azure-driver/](https://pypi.org/project/masonite-azure-driver/)
{% endhint %}

## Requirements <a id="requirements"></a>

In order to use the Azure upload driver, you'll need:

* Python 3.4+
* Pip3
* Masonite 2.0+
* Azure

## Getting Started

### Installation

{% code-tabs %}
{% code-tabs-item title="terminal" %}
```bash
$ pip install masonite-azure-driver
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Masonite Setup

### Environment

Paste the access token in your project's `.env` file along with the folder name where you want your uploads to be saved.

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
AZURE_NAME=masonite
AZURE_SECRET=RykG8ppeox/1ll6Z4a...
AZURE_CONNECTION=DefaultEndpointsProtocol=https;AccountName=masonite;AccountKey=RykG8q...
AZURE_CONTAINER=masonite
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Service Provider

Add the _**AzureProvider**_ to _**PROVIDERS**_ in the `config/providers.py` file.

{% code-tabs %}
{% code-tabs-item title="config/providers.py" %}
```python
from masonite.contrib.azure.providers import AzureProvider

PROVIDERS = [
    # Third Party Providers
    AzureProvider,
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
        Upload.driver('azure').store(Request.input('file_upload'))
        return Request.redirect_to('dashboard')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

