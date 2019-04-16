# API Pagination

{% hint style="info" %}
**Github** [https://github.com/rfschubert/masonite-api-pagination](https://github.com/rfschubert/masonite-api-pagination)  
**API Pagination Wiki** [https://github.com/rfschubert/masonite-api-pagination/wiki](https://github.com/rfschubert/masonite-api-pagination/wiki)  
**Pypi** [https://pypi.org/project/masonite-api-pagination/](https://pypi.org/project/masonite-api-pagination/)
{% endhint %}

## Requirements {#requirements}

In order to use the Azure upload driver, you'll need:

* Python 3.4+
* Pip3
* Masonite 2.0+
* masonite-api

## Getting Started

### Installation

{% code-tabs %}
{% code-tabs-item title="terminal" %}
```bash
$ pip install masonite-api-pagination
```
{% endcode-tabs-item %}
{% endcode-tabs %}

## Masonite Setup

### Resource File

You should have any `resource` file to work with. You can follow the oficial `Masonite API Tutorial` to create your first resource.

When you create it, you can just import the `masonite-api-pagination` package to it and change your resource a bit.

If You've followed the oficial tutorial, you will have an `UserResource` file, and you can change it to this

{% code-tabs %}
{% code-tabs-item title="UserResource.py" %}
```python
from api.serializers import JSONSerializer
from masonite_api_pagination.resources.PaginatedResource import PaginatedResource

from app.User import User


class UserResource(PaginatedResource, JSONSerializer):
    model = User
```
{% endcode-tabs-item %}
{% endcode-tabs %}

And that`s it! You are up and running!

Now when you do a request to your endpoint, you will receive a response like this:
![img03](https://i.imgur.com/GtVl8Z5.png)

If you want to learn more, visit the `Wiki` page of `masonite-api-pagination` on Github to learn about filters and more.

{% hint style="info" %}
**Github** [https://github.com/rfschubert/masonite-api-pagination](https://github.com/rfschubert/masonite-api-pagination)  
**API Pagination Wiki** [https://github.com/rfschubert/masonite-api-pagination/wiki](https://github.com/rfschubert/masonite-api-pagination/wiki)  
**Pypi** [https://pypi.org/project/masonite-api-pagination/](https://pypi.org/project/masonite-api-pagination/)
{% endhint %}