# Evaluator (Python)
The Evaluator is a direct member of the Top Level Architecture and can be considered a microservice. It is responsible for the evaluation of submitted task solutions which are transferred by the API over the message bus. For isolation purposes it uses docker containers as computing instances for the actual evaluation process. Since the main purpose of this application is to evaluate mathematical tasks (especially tasks about graphs) every docker container used here is based on the Sage Math docker image.

The basic configuration uses the `BasicEvaluator` (see below) in order to describe the procedure of the current evaluation process.


## Docker Manager (`docker_manager.py` and `docker_container.py`)
The Docker Manager keeps track of allocated and free docker containers. Besided the preparation of the containers in advance it also removes them after they finished their respective evaluation request.
As a result a docker container is only used for a single task solution evaluation. The reason behind that lays in the desired degree of isolation. 
In order to decrease latency when doing so it is possible to specify a constant which descibes how many docker containers should be prepared in advance. Also a maximum can be declared but if this limit is reached further requests will be discared for now.

## AbstractEvaluator (`abstract_evaluator.py`)
The AbstractEvaluator contains an interface in order enable the implementation of different evaluation procedures. It is kept lean:
First, every sub instance of the AbstractEvaluator can declare the name of the message bus queue which it will receive requests from. And second it defines a callback which is invoked when the evaluator receives a message from the selected queue.

## BasicEvaluator (`basic_evaluator.py`)
Once the basic evaluator receives an evaluation request (containing a request id, a taks id and the submitted soluation) it will trigger a bunch of steps. These consist of the following:
- allocating a container using the docker manager
- loading the graph as well as the evaluation script from the database using the task id
- base64 encoding the just loaded graph and the submitted solution
- uploading the script as a file (named eval.sage)
- executing the script in the container with command `sage eval.sage <answer-as-base64> <graph-as-base64>`
