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
