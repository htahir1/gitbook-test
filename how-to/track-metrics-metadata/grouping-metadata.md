---
description: Learn how to group key-value pairs in the dashboard.
---

# Group metadata

![Metadata in the dashboard](../../.gitbook/assets/metadata-in-dashboard.png)

When logging metadata passing a dictionary of dictionaries in the `metadata` parameter will group the metadata into cards in the ZenML dashboard. This feature helps organize metadata into logical sections, making it easier to visualize and understand.

Here's an example of grouping metadata into cards:

```python
from zenml.metadata.metadata_types import StorageSize

log_artifact_metadata(
    metadata={
        "model_metrics": {
            "accuracy": 0.95,
            "precision": 0.92,
            "recall": 0.90
        },
        "data_details": {
            "dataset_size": StorageSize(1500000),
            "feature_columns": ["age", "income", "score"]
        }
    }
)
```

In the ZenML dashboard, "model\_metrics" and "data\_details" would appear as separate cards, each containing their respective key-value pairs.

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>