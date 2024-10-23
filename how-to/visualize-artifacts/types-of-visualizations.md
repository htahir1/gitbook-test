---
description: Types of visualizations in ZenML.
---

# Default visualizations

ZenML automatically saves visualizations of many common data types and allows you to view these visualizations in the ZenML dashboard:

![ZenML Artifact Visualizations](<../../.gitbook/assets/artifact\_visualization\_dashboard (1).png>)

Alternatively, any of these visualizations can also be displayed in Jupyter notebooks using the `artifact.visualize()` method:

![output.visualize() Output](../../.gitbook/assets/artifact\_visualization\_evidently.png)

Currently, the following visualization types are supported:

* **HTML:** Embedded HTML visualizations such as data validation reports,
* **Image:** Visualizations of image data such as Pillow images or certain numeric numpy arrays,
* **CSV:** Tables, such as the pandas DataFrame `.describe()` output,
* **Markdown:** Markdown strings or pages.

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>
