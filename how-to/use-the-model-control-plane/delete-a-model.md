---
description: Learn how to delete models.
---

# Deleting a Model

Deleting a model or a specific model version means removing all links between the Model entity and artifacts + pipeline runs, and will also delete all metadata associated with that Model.

## Deleting all versions of a model

{% tabs %}
{% tab title="CLI" %}
```shell
zenml model delete <MODEL_NAME>
```
{% endtab %}

{% tab title="Python SDK" %}
```python
from zenml.client import Client

Client().delete_model(<MODEL_NAME>)
```
{% endtab %}
{% endtabs %}

## Delete a specific version of a model

{% tabs %}
{% tab title="CLI" %}
```shell
zenml model version delete <MODEL_VERSION_NAME>
```
{% endtab %}

{% tab title="Python SDK" %}
```python
from zenml.client import Client

Client().delete_model_version(<MODEL_VERSION_ID>)
```
{% endtab %}
{% endtabs %}

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>
