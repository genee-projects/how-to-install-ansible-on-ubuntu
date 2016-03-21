# how-to-install-ansible-on-ubuntu
怎么在 ubuntu 系统上安装 ansible

## 原计划

> 工具应可被复用, 可迁移 (docker 是一个好的选择)
>
> 服务应该持续提供服务 （docker 方便部署)

我们考虑到如上亮点, 故计划考虑把 `ansible` 放置到 `docker` 容器中

但是 `ansible` 依赖了 **网络** 和 **ssh** , 考虑到这点不是太方便(尤其是 **ssh**, 更多情况下, 大多数人进行 `ansible` 命令操作, 会使用 `ssh-agent` 携带 `ssh-key`, 无法通过 `volume` 等形式让 `ansible` 获取到 `ssh-key`). 故, 有了该文档

## 部署方式:

### 1. 安装依赖环境

`ansible` 是使用 **python 2.7** 开发的, 同时需要进行 `yaml` 的解析, 而 `yaml` 的解析需要依赖 `python-dev`, 故需要安装部分依赖:



```
$ sudo apt-get update && \
  apt-get install -y python python-dev python-pip libyaml-dev
```

### 2. 使用 pip 安装 ansible

```
$ sudo pip install ansible
```

## 检测安装结果

```
$ ansible --version
```

如果显示: 

```
ansible 2.0.1.0
  config file =
  configured module search path = Default w/o overrides
```

表示安装成功

## 升级

使用 pip 可直接进行升级
```
$ sudo pip install -U ansible
```
