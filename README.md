# jetson-nano-.bashrc
bashrc alias setting in jetson nano
add how to setup zsh and neovim, tmux, jtop

# Initial setting for jetson nano
```bash
sudo apt-get update
sudo apt-get install git curl
git clone https://github.com/radii-dev/jetson-nano-.bashrc.git
```
# Install zsh and oh-my-zsh
```bash
sudo apt-get install zsh
chsh -s /usr/bin/zsh
reboot
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
sudo apt-get install fonts-powerline
cp -i .zshrc ~/.zshrc
source ~/.zshrc
```
# Install neovim
```bash
sudo add-apt-repository ppa:neovim-ppa/unstable
sudo apt-get update
sudo apt-get install neovim
```
```bash
nvim   
:call mkdir(stdpath('config'), 'p')
:exe 'edit '.stdpath('config').'/init.vim'
:wq
cp -i init.vim ~/.config/nvim/init.vim
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
sudo su
curl -sL install-node.now.sh/lts | bash
exit
vi ~/.config/nvim/init.vim
:PlugInstall
:CocInstall coc-clangd
:wq
vi
:CocConfig
```
add
```json
{
    "clangd.semanticHighlighting": true,
    "coc.preferences.currentFunctionSymbolAutoUpdate": true
}
```
```bash
:wq
```

## i) arm64/linux
```bash
sudo apt-get install clangd-9
vi
:CocConfig
```
add
```json
{
    "clangd.path": "/usr/bin/clangd-9"
    ...
}
```
```bash
:wq
```
## ii) others
```bash
vi
:CocCommand clangd.install
:wq
vi ~/.zshrc
```
add
```bash
export PATH=$PATH:~/.config/coc/extensions/coc-clangd-data/install/12.0.1/clangd_12.0.1/bin
```
```bash
source ~/.zshrc
sudo apt-get install bear
```
# Install tmux
```bash
sudo apt-get install tmux
cp -i .tmux.conf ~/.tmux.conf
```
# Install jtop
```bash
sudo apt-get install git cmake
sudo apt-get install python3-dev
sudo apt-get install libhdf5-serial-dev hdf5-tools
sudo apt-get install libatlas-base-dev gfortran
sudo apt-get install python3-pip
pip3 install --upgrade pip
sudo -H pip3 install -U jetson-stats
reboot
```
