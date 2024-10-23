# Get past pipeline/step runs

In order to get past pipeline/step runs, you can use the `get_pipeline` method in combination with the `last_run` property or just index into the runs:

<pre class="language-python"><code class="lang-python">from zenml.client import Client

client = Client()

<strong># Retrieve a pipeline by its name
</strong><strong>p = client.get_pipeline("mlflow_train_deploy_pipeline")
</strong>
<strong># Get the latest run of this pipeline
</strong><strong>latest_run = p.last_run
</strong><strong># Alternatively you can also access runs by index or name
</strong><strong>first_run = p[0]
</strong>
</code></pre>

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>
