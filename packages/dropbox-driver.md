# Dropbox Driver

## Introduction

## Requirements

## Getting Started

### Installation

{% code-tabs %}
{% code-tabs-item title="terminal" %}
```bash
$ pip install masonite-dropbox-driver
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% hint style="info" %}
More information can be found on [https://pypi.org/project/masonite-dropbox-driver/](https://pypi.org/project/masonite-dropbox-driver/)
{% endhint %}

### Configuration

#### Masonite

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
DROPBOX_TOKEN=TpUPCQtBMS8CCCCABBAatYCqTxjibN8A7Do7zaISQaE0hLVvjb3iaAK8vKqEHuMW
DROPBOX_FOLDER=/Jake/
```
{% endcode-tabs-item %}
{% endcode-tabs %}

{% code-tabs %}
{% code-tabs-item title="config/providers.py" %}
```python
from masonite.contrib.dropbox.providers import DropboxProvider

PROVIDERS = [
    # Third Party Providers
    DropboxProvider,
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

#### Dropbox

## Using the Driver

{% code-tabs %}
{% code-tabs-item title="ActivityController.py" %}
```python
class ActivityController:

    def create(self, View):
        return View('admin/activities/new')

    def store(self, Upload, Request):
        Upload.driver('dropbox').store(Request.input('file_upload'))
        return Request.redirect_to('dashboard')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

