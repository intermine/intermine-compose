# intermine-compose
Repo to handle docker orchestration in the cloud

## Getting started

### Step 0
Create a .env file in the root of repo and add these:
```bash
# change values as needed
FLASK_CONFIG_MODE=development
CONFIGURATOR_URL=http://localhost:9999/
KUBE_ENABLE=False
IM_DATA_DIR=/tmp/sharedfs
```
### Step 1 (optional but recommended)
Create a python virtual environment
```bash
conda create -n intermine_compose python=3.6 && conda activate intermine_compose
```
### Step 2
Install python packages
```bash
pip install -r requirements.txt
```
### Step 3
Launch configurator app in a docker container
```bash
docker run --rm -p 9999:8080 --env IM_DATA_DIR=/intermine/data intermine/configurator:latest
```
> Note: `9999` is the host port to which configurator will bind to.

### Step 4
Launch flask app
```bash
python run.py
```
> Note : These instructions assumes that you have a local instance of postgres and redis running. Also your postgres user is `postgres` and password is `postgres`. You can change the defaults in `config/development.py`

