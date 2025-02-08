# Setup  a vitual Python environment on MacOS for the Esbonio extension

It is best that this be completed prior to installing the extension. You also want to configure Python in vscode first then install it.
I've got an example settings.json for global defaults in this repo

```console
 
brew install python@3.12

```

Now we will install pyenv to manage our virtual python enviroments

```console
brew install pyenv

echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.zshrc
echo '[[ -d $PYENV_ROOT/bin ]] && export PATH="$PYENV_ROOT/bin $PATH"' >> ~/.zshrc
echo 'eval "$(pyenv init - zsh)"' >> ~/.zshrc
```
Close your terminal and restart your terminal session so your envrionment variables are updated.

Use pyenv to install our working virtual python enviroment.

```console
pyenv install python 3.12
pyenv global 3.12
```
Grab the requirements.txt file from this repo. 
We will use this to install the modules we'll need and additonal code for linting etc.

```console
pip install -r requirements.txt
```





