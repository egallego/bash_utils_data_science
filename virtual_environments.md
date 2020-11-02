# Virtual environments
Functions presented in this file are related to handle virtual environments and make easier their creation.
 
The following list of functions should be included in the _.zshrc_ file to be used.

## Default configuration
By default all virtual environments are created in the directory. 
```bash
~/envs
```
## Virtual environment activation
Activate a specified virtual environment.
```bash
function activate_env() {
    source ~/envs/$1/bin/activate
}
```
## Virtual environment creation
### Python 3
Function to create a virtualenv for python 3.
```bash
function create_env() {
	virtualenv -p python3 ~/envs/$1;
	activate_env $1;
}
```
Create a virtual virtualenv and set it up to be used with jupyter notebook.

[jupyter_packages.sh](scripts/jupyter_packages.sh) can be found in the scripts folder in this repo.
```bash
function create_jupyter_env() {
	create_env $1;
	source ~/.jupyter_packages.sh;
	python -m ipykernel install --user --name $1 --display-name "Python 3 ($1)"
}
```
### Python 2
Function to create a virtualenv for python 2.
```bash
function create_env_python2() {
	virtualenv ~/envs/$1;
	activate_env $1;
}
```
Create a virtual virtualenv and set it up to be used with jupyter notebook.

[jupyter_packages_p2.sh](scripts/jupyter_packages_p2.sh) can be found in the scripts folder in this repo.
```bash
function create_jupyter_env_python2() {
	create_env_python2 $1;
	source ~/.jupyter_packages_p2.sh;
	python -m ipykernel install --user --name $1 --display-name "Python 2 ($1)"
}
```