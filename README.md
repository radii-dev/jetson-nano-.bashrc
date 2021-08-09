# jetson-nano-.bashrc
bashrc alias setting in jetson nano   

# Initial setting for jetson nano

sudo apt-get update   
sudo apt-get install git   
git clone https://github.com/radii-dev/jetson-nano-.bashrc.git   

# Install zsh and oh-my-zsh
sudo apt-get install zsh   
chsh -s /usr/bin/zsh   
reboot   
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"   
sudo apt-get install fonts-powerline   
cp -i .zshrc ~/.zshrc   
source ~/.zshrc   

# Install neovim
sudo add-apt-repository ppa:neovim-ppa/unstable   
sudo apt-get update   
sudo apt-get install neovim   
   
nvim   
:call mkdir(stdpath('config'), 'p'))   
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
sudo apt-get install clangd-9   

# Install tmux
sudo apt-get install tmux
cp -i .tmux,conf ~/.tmux.conf
