# Python Starter Kit
This app is a starter kit for writing code and [tests](https://docs.python.org/3/library/unittest.html) in python. Use it as a seed for starting a new python project. Use the following command to copy this app's code to a new directory:
```console
mkdir -p path/to/new
cp -r path/to/this/directory path/to/new/directory
```

## Dependencies
This codebase supports two ways of running code: [in](#in-docker) and [out of](#out-of-docker) docker. In docker, the only local dependency you need to configure to use this codebase is `docker-compose`. Out of docker, this codebase assumes you're able to install python via `brew`, although of course a different package manager could work just as well.

## Out of Docker

Here's how to install and run the code on your local OS X machine (out of docker).

### Install

1. Install or update `pyenv` (and `python-build` to get access to recent releases of python).
   ```
   brew update && brew install python-build pyenv
   brew update && brew upgrade python-build pyenv
   ```
1. Install python.
   ```
   pyenv install $(cat ./.python-version)
   ```
1. Install poetry.
   ```
   curl -sSL https://install.python-poetry.org | python -
   ```
1. Install python packages.
   ```
   poetry install
   ```

### Run

* Run the tests.
  ```console
  poetry run pytest
  ```
* Run the `python_starter` module.
  ```console
  poetry run python -m python_starter
  ```
* Run the auto formatter.
  ```console
  poetry run pre-commit run --all-files
  ```
  * For more usage instructions, see [the pre-commit documentation](https://pre-commit.com/).

## In Docker

Here's how to install and run the code in docker.

### Install

1. Build the image:
   ```console
   docker-compose build
   ```

### Run

* Open a long-running session inside the container:
  ```console
  docker-compose run --rm app bash
  ```
* From here, you can run the same commands as described in [the respective out of docker section](#run).

## Debug

* Documentation [here](https://docs.python.org/3/library/pdb.html).
* Set a breakpoint with `import pdb; pdb.set_trace()`.
  * If you're using vim with [a project-specific .vimrc](https://andrew.stwrt.ca/posts/project-specific-vimrc/), you can type this with `<leader>db`.
* Show where you are with `list`.
* Continue with `continue`.
* Quit with `quit`.

## Add a new python package

This app makes use of [`poetry`](https://python-poetry.org/) to manage packages. See docs there for how to add packages.
