# Unpriviledged install of homebrew on MacOS

*Note* unless otherwise stated these are all ran from the termal in the user's home directory.

We need to install some xcode to get started

```console
xcode-select —install

mkdir -p ~/.local/Homebrew && curl -L https://github.com/Homebrew/brew/tarball/master | tar xz --strip 1 -C ~/.local/Homebrew
        
mkdir -p ~/.local/bin && ln -s ~/.local/Homebrew/bin/brew ~/.local/bin
```
```python
cat << 'EOF' >> ~/.zshrc
[ -d "$HOME/.local/bin" ] && export PATH="$PATH:$HOME/.local/bin" # or "$HOME/.local/bin:$PATH" [1]
EOF
```


Add the following to .zshrc
```console
if [ -n $(command -v brew) ]; then
    PREFIX="${HOME}/.local"
    export HOMEBREW_PREFIX="$PREFIX"
    export HOMEBREW_CELLAR="$PREFIX/Cellar"
    export HOMEBREW_REPOSITORY="$PREFIX/Homebrew"
    export HOMEBREW_CASK_OPTS='${HOME}/Applications'
    export PATH="$PREFIX/bin:$PREFIX/sbin${PATH+:$PATH}"
    export MANPATH="$PREFIX/share/man${MANPATH+:$MANPATH}:"
    export INFOPATH="$PREFIX/share/info:${INFOPATH:-}"
    # export HOMEBREW_NO_ANALYTICS=1
    # export HOMEBREW_NO_ENV_HINTS=1
fi
```

**NHOTE:** You can use “—force-bottle” to avoid compilation but I find the extra time for compilation causes less issues.



Now you have Homebrew compiled and installed in your home director and no need for priviledged access to do so.