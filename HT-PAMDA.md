尝试以下命令测试网络：`ping github.com`  
增大 Git 的缓冲区可以解决部分大型文件下载问题:`it config --global http.postBuffer 524288000`  
运行以下命令查看磁盘空间：`df -h` du查看当前文件夹空间




# 高通量数据分析  
  
## 1. HT-PAMDA 实验设计与数据分析  
#### 请做如下准备工作：
1. 阅读论文 `https://www.nature.com/articles/s41596-020-00465-2`  
2. win10 用户安装 Ubuntu 子系统，参考 `https://zhuanlan.zhihu.com/p/62658094`（必须，安装好后设置用户名，密码，进行必要的 update 和必须软件安装）  
`sudo apt-get update`
`sudo apt install pip (或 pip3)`
3. mac 或 linux 用户需设置将 bash 设置为默认 Shell，参考 `https://support.apple.com/zh-cn/HT208050`    
4. 在 ubuntu 子系统或 mac 系统中安装 anaconda（推荐，安装时设置 Anaconda 为默认启动）  
`wget https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh`  
`sh ./Anaconda3-2021.05-Linux-x86_64.sh`  
`conda config --add channels defaults`  
`conda config --add channels bioconda`  
`conda config --add channels conda-forge`  
`rm -rf Anaconda3-2021.05-Linux-x86_64.sh`  
5. 安装 HT-PAMDA  
`git clone https://github.com/kleinstiverlab/HT-PAMDA.git`  
`cd HT-PAMDA`  
`python3 -m venv venv`  
`sh install.sh`  






## 2、高通量数据分析  
请做如下准备工作：  
1. win10 用户（必须是专业版，家庭版不可以）安装 Ubuntu 子系统，参考https://zhuanlan.zhihu.com/p/62658094（安装好后设置用户名，密码，进行必要的 update 和必须软件安装）
sudo apt-get update
sudo apt install pip (或 pip3)
2. Pip install barcodeSpliter
3. 在 ubuntu 子系统中安装 miniconda（推荐，安装时设置 miniconda 为默认启动）
wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh
sh ./Miniconda3-latest-Linux-x86_64.sh
conda config --add channels defaults
conda config --add channels bioconda
conda config --add channels conda-forge
rm Miniconda3-latest-Linux-x86_64.sh
conda create -n crispresso2_env -c bioconda crispresso2
conda activate crispresso2_env
CRISPResso -h
4. 下载安装 cuemol
http://www.cuemol.org/en/index.php?Download
