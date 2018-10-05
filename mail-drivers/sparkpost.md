# Sparkpost

{% hint style="info" %}
**Github** [https://github.com/bjorntheart/masonite-sparkpost-driver](https://github.com/bjorntheart/masonite-sparkpost-driver)  
**Pypi**     [https://pypi.org/project/masonite-sparkpost-driver](https://pypi.org/project/masonite-sparkpost-driver/)
{% endhint %}

## Requirements {#requirements}

In order to use the Dropbox upload driver, you'll need:

* Python 3.4+
* Pip3
* Masonite 2.0+
* sparkpost

## Getting Started

### Installation

{% code-tabs %}
{% code-tabs-item title="terminal" %}
```bash
$ pip install masonite-sparkpost-driver
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Masonite Setup

### Environment

Paste the access token in your project's `.env` file along with the folder name where you want your uploads to be saved.

Set the default mail driver to **sparkpost**

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
MAIL_DRIVER=sparkpost
```
{% endcode-tabs-item %}
{% endcode-tabs %}

To use Sparkpost in _sandbox mode_, use the following settings

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
APP_DEBUG=True
MAIL_FROM_ADDRESS=anything@sparkpostbox.com
```
{% endcode-tabs-item %}
{% endcode-tabs %}

Obtain an API key form your Sparkpost dashboard and set it in your `.env` file

{% code-tabs %}
{% code-tabs-item title=".env" %}
```text
SPARKPOST_API_KEY=912ac9a0923oiee6ef1ca313a9879787c516f47341
```
{% endcode-tabs-item %}
{% endcode-tabs %}

### Service Provider

Add the _**SparkpostProvider**_ to _**PROVIDERS**_ in the `config/providers.py` file.

{% code-tabs %}
{% code-tabs-item title="config/providers.py" %}
```python
from masonite.contrib.sparkpost.providers import SparkpostProvider

PROVIDERS = [
    # Third Party Providers
    SparkpostProvider,
]
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Using the Driver

{% code-tabs %}
{% code-tabs-item title="ActivityController.py" %}
```python
class ActivityController:

    def show(self, Mail):
        Mail.to('hello@email.com').send('Welcome!')
```
{% endcode-tabs-item %}
{% endcode-tabs %}

