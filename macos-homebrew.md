#  如何在macos中安装homebrew？
    访问官方网址：https://brew.sh/index_zh-cn
    复制安装命令到终端执行：/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
#  修改homebrew的源？
    因为homebrew的服务器地址在国外，为了防止在国内下载软件速度过慢需要手动换源。
    
## 中科大的源
### 修改 brew.git
> cd "$(brew --repo)" && git remote set-url origin https://mirrors.ustc.edu.cn/brew.git

### 修改 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://mirrors.ustc.edu.cn/homebrew-core.git

### 修改 homebrew-bottles
> echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.ustc.edu.cn/homebrew-bottles' >> ~/.bash_profile && source ~/.bash_profile

### 立刻生效
> brew update

## 清华大学的源
### 修改 brew.git
> cd "$(brew --repo)" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git

### 修改 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git

### 修改 homebrew-bottles
> echo 'export HOMEBREW_BOTTLE_DOMAIN=https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles' >> ~/.bash_profile && source ~/.bash_profile

## 其他相关操作
### 立刻生效
> brew update

### 查看（诊断） brew 状态
> brew doctor

### 重置 brew.git
> cd "$(brew --repo)" && git fetch && git reset --hard origin/master

### 切回官方 brew.git
> cd "$(brew --repo)" && git remote set-url origin https://github.com/Homebrew/brew.git

### 重置 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git fetch && git reset --hard origin/master

### 切回官方 homebrew-core.git
> cd "$(brew --repo)/Library/Taps/homebrew/homebrew-core" && git remote set-url origin https://github.com/Homebrew/homebrew-core.git

### 立刻生效
> brew update


    
