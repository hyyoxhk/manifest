# itop4412-manifest

本项目是 iTop-4412 开发板的 yocto 的repo manifest

# 构建环境

本 yocto 项目是基于 kirkstone 分支，需要再 ubuntu-22.04 环境下编译，
请确保构建主机配置如下

1. cpu 主频2GHz以上
2. cpu 核心数大于4核，越多越好，有利于多线程构建和编译
3. 内存8G以上，越多越好，有利于多线程编译
4. 建议真机环境，如果虚拟机的话，可能构建体验不好

# 安装 repo 

```shell
$> sudo curl https://mirrors.tuna.tsinghua.edu.cn/git/git-repo -o /usr/local/bin/repo
$> sudo chmod 755 /usr/local/bin/repo

```

# 安装用于构建 yocto 的依赖包

```shell
$> sudo apt install gawk wget git diffstat unzip texinfo gcc-multilib \
build-essential chrpath socat cpio python3 python3-pip python3-pexpect \
xz-utils debianutils iputils-ping python3-git python3-jinja2 libegl1-mesa libsdl1.2-dev \
pylint xterm \
bsdmainutils \
libssl-dev libgmp-dev libmpc-dev \
lz4 zstd
```

# 获取 repo 源

```shell
$> repo init -u https://github.com/hyyoxhk/itop4412-manifest.git -b kirkstone --repo-url https://gerrit-googlesource.proxy.ustclug.org/git-repo.git
$> repo sync
```

# 初始化 oe 环境

```shell
# source 会提示你选择，等初始化完后会自动进入 build-XXX 目录
$> source layers/meta-board/meta-smart/envsetup.sh
# 开始构建目标 image，iTop-4412 目前调试好了 small 版本
$> bitbake smart-image-small
# 如果有代理会更好，yocto 菜谱中的源码包绝大部分在外网，代理会加速构建速度
```
