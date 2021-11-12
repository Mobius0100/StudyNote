<<<<<<< HEAD
## 下载

3.6版本：anconda3a-5.2

**地址：**

​	官方地址：https://repo.anaconda.com/archive/

​	清华大学镜像：https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/



## 使用

新建环境：`conda create -n name python=3.x`

激活环境：`activate pytorch`

退出环境：`deactivate name`

环境信息：`conda info --env`

显示配置：`conda config --show channels`



## 换源

进入环境后执行命令,

```bash
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/peterjc123/
```



## 安装库

```bash
conda install -yc xxx    (y指不需要确认，c指定源)
conda install nb_conda    #安装jupyter notebook
pip install -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com -r requirements.txt
```

=======
## 下载

3.6版本：anconda3a-5.2

**地址：**

​	官方地址：https://repo.anaconda.com/archive/

​	清华大学镜像：https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/



## 使用

新建环境：`conda create -n name python=3.x`

激活环境：`activate pytorch`

退出环境：`deactivate name`

环境信息：`conda info --env`

显示配置：`conda config --show channels`



## 换源

进入环境后执行命令,

```bash
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/msys2/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/menpo/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/pytorch/
conda config --add channels http://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/peterjc123/
```



## 安装库

```bash
conda install -yc xxx    (y指不需要确认，c指定源)
conda install nb_conda    #安装jupyter notebook
pip install -i http://mirrors.aliyun.com/pypi/simple/ --trusted-host mirrors.aliyun.com -r requirements.txt
```

