# docker 

## Usage
```
docker pull brainiac/multiarch-python-3.11-example:0.1.1
docker run brainiac/multiarch-python-3.11-example:0.1.1
```

## Usage as Task within Airflow DAG 
```
task2 = DockerOperator(
            task_id='docker_command_' + str(i),
            image='brainiac/multiarch-python-3.11-example:0.1.1',
            command='',
            api_version='auto',
            auto_remove=True,
            docker_url='tcp://docker-proxy:2375',
            network_mode="bridge"
        )
```

## Build multi-platform image and push it to docker hub
```
docker buildx build --platform linux/amd64,linux/arm64 -f dockerfile-multiarch-python-3.11-example --tag brainiac/multiarch-python-3.11-example:0.1.1 --push .
```