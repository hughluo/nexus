# Nexus to host pypi
## Upload Pip whl to nexus
twine upload --config-file ./pypirc --repository nexus jsonpickle-1.4.1-py2.py3-none-any.whl
## Download from nexus
export PIP_CONFIG_FILE=$PWD/.pip.conf
pip install jsonpickle -i http://localhost:8081/repository/nexus-pypi/simple/ --trusted-host localhost