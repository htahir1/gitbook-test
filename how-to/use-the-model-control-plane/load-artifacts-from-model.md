# Load artifacts from Model

One of the more common use-cases for a Model is to pass artifacts between pipelines (a pattern we have seen [before](connecting-artifacts-via-a-model.md)). However, when and how to load these artifacts is important to know as well.

As an example, let's have a look at a two-pipeline project, where the first pipeline is running training logic and the second runs batch inference leveraging trained model artifact(s):

```python
from typing_extensions import Annotated
from zenml import get_pipeline_context, pipeline, Model
from zenml.enums import ModelStages
import pandas as pd
from sklearn.base import ClassifierMixin


@step
def predict(
    model: ClassifierMixin,
    data: pd.DataFrame,
) -> Annotated[pd.Series, "predictions"]:
    predictions = pd.Series(model.predict(data))
    return predictions

@pipeline(
    model=Model(
        name="iris_classifier",
        # Using the production stage
        version=ModelStages.PRODUCTION,
    ),
)
def do_predictions():
    # model name and version are derived from pipeline context
    model = get_pipeline_context().model
    inference_data = load_data()
    predict(
        # Here, we load in the `trained_model` from a trainer step
        model=model.get_model_artifact("trained_model"),  
        data=inference_data,
    )


if __name__ == "__main__":
    do_predictions()
```

In the example above we used `get_pipeline_context().model` property to acquire the model context in which the pipeline is running. During pipeline compilation this context will not yet have been evaluated, because `Production` model version is not a stable version name and another model version can become `Production` before it comes to the actual step execution. The same applies to calls like `model.get_model_artifact("trained_model")`; it will get stored in the step configuration for delayed materialization which will only happen during the step run itself.

It is also possible to achieve the same using bare `Client` methods reworking the pipeline code as follows:

```python
from zenml.client import Client

@pipeline
def do_predictions():
    # model name and version are directly passed into client method
    model = Client().get_model_version("iris_classifier", ModelStages.PRODUCTION)
    inference_data = load_data()
    predict(
        # Here, we load in the `trained_model` from a trainer step
        model=model.get_model_artifact("trained_model"),  
        data=inference_data,
    )
```

In this case the evaluation of the actual artifact will happen only when the step is actually running.

<figure><img src="https://static.scarf.sh/a.png?x-pxid=f0b4f458-0a54-4fcd-aa95-d5ee424815bc" alt="ZenML Scarf"><figcaption></figcaption></figure>
