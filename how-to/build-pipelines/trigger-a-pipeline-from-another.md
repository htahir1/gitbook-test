---
description: >-
  When writing your pipelines you can also always call a pipeline from within
  another.
---

# Trigger a pipeline from another

```python
from zenml import pipeline

@pipeline
def date_loader_pipeline(...) -> dict:
    ...
    return {...}

@pipeline  
def simple_ml_pipeline():
    dataset = date_loader_pipeline() # this executes all the steps of this pipeline and gets the return value
    train_model(dataset)
```

{% hint style="warning" %}
Calling a pipeline inside another pipeline does not actually trigger a separate run of the child pipeline but instead invokes the steps of the child pipeline to the parent pipeline.
{% endhint %}

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>
