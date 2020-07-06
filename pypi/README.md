# Nexus to host pypi
## Run Nexus
```
docker volume create --name nexus-data
docker run -d -p 8081:8081 --name nexus -v nexus-data:/nexus-data sonatype/nexus3
```
## Create PyPI repo
Click in GUI.

## Upload Pip whl to nexus

.whl can be downloaded from PyPI

```
twine upload --config-file ./pypirc --repository nexus jsonpickle-1.4.1-py2.py3-none-any.whl
```

## Download from nexus

Use env var PIP_CONFIG_FILE to set the path for pip.conf

```
export PIP_CONFIG_FILE=$PWD/.pip.conf
pip install jsonpickle -i http://localhost:8081/repository/nexus-pypi/simple/ --trusted-host localhost
```
