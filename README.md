# bashFunctions
A few functions added into .bashrc or .zshrc

````
# Function to set proxy
function setproxy() {
    PROXY='http://10.80.16.2:3128'
    export {http,https,ftp,HTTP,HTTPS,FTP}_proxy=$PROXY
    if hash git 2>/dev/null; then
      git config --global http.proxy $PROXY
      git config --global https.proxy $PROXY
    fi
}

# Function to unset proxy
function unproxy() {
    unset {http,https,ftp}_proxy
    if hash git 2>/dev/null; then
      git config --global --unset http.proxy
      git config --global --unset https.proxy
    fi
}

# Fucntion to update oh-my-zsh and its plugins
function omzupdate() {
    git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k pull --rebase
    git -C ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting pull --rebase
    git -C ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions pull --rebase

    omz update
}
````
