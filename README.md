# Tensorflow Serving Examples

## MNIST
The same as the one in the `titcl` tutorial.

## CIFAR10
`cifar10` from the original `tensorflow` example, is modified a little bit, which now can be saved as model.
### Steps
1. ```$ python cifar10_train.py```. By default, it will save the outputs at `/tmp/cifar10_train`.
2. ```$ python cifar10_saved_model.py```. By default, it will load the outputs at `/tmp/cifar10_train` and save the model at `/tmp/cifar10_output`.
3. PC tests (not necessary). First, load the exported model with the standard tensorFlow model_server, ```$ tensorflow_model_server --port=9000 --model_name=cifar10_model --model_base_path=/tmp/cifar10_output```. Second, send images, ```$python cifar10_client.py --image ./tests/bird1.jpeg```.
4. Cloud deployment. First, Use the similar commands with the `MNIST` example to deploy the model on the server. Second, use the similar command to test, where the `server` is replaced with the hostname or ip of the server.

### Prossible ouputs
For the bird image.
```json
outputs {
  key: "classes"
  value {
    dtype: DT_STRING
    tensor_shape {
      dim {
        size: 1
      }
      dim {
        size: 1
      }
    }
    string_val: "bird"
  }
}
outputs {
  key: "scores"
  value {
    dtype: DT_FLOAT
    tensor_shape {
      dim {
        size: 1
      }
      dim {
        size: 1
      }
    }
    float_val: 0.7760443687438965
  }
}
model_spec {
  name: "cifar10_model"
  version {
    value: 1
  }
  signature_name: "predict_images"
}
```

For the ship image.
```json
outputs {
  key: "classes"
  value {
    dtype: DT_STRING
    tensor_shape {
      dim {
        size: 1
      }
      dim {
        size: 1
      }
    }
    string_val: "ship"
  }
}
outputs {
  key: "scores"
  value {
    dtype: DT_FLOAT
    tensor_shape {
      dim {
        size: 1
      }
      dim {
        size: 1
      }
    }
    float_val: 2.3249173164367676
  }
}
model_spec {
  name: "cifar10_model"
  version {
    value: 1
  }
  signature_name: "predict_images"
}
```
