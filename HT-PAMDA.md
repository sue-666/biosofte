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
  
#  HT-PAMDA Protocol    
  
##  Production of nuclease-containing lysate  
#### Reagents  
1x Lysis buffer 20 mM Tris-HCl, pH=7.5, 100 mM NaCl, 5 mM MgCl2, 5% Glycerol, 1 mM DTT,
0.1% Triton X-100, one tablet Proteinase inhibitor per 100 mL  
#### Procedures  
1. Seed 1.25E5 cells/well in a 24-well plate.  
2. Transfect 500-ng nuclease-expressing plasmids into the cells.  
3. Approximately 48-hrs post transfection, discard the medium.  
4. Resuspend all cells in 500-uL PBS.  
5. Centrifuge at 1000xg for 2 min, discard the supernatant.  
6. add 50-uL 1x Lysis buffer to the cell.  
7. Mix well (avoid bubble) and incubate on ice for 10 min.  
8. Centrifuge at 5000xg for 1 min. Transfer the supernatant to a new tube.    
9. Use 10-uL to measure the fluorescence in a 384-well plate by microplate reader (Ex485/Cut515/Em535).  
10. Adjust the lysate to reach a concentration at 250-300 nM FITC unit.  
  

  
#### 1. In vitro cleavage  
**a.** Prepare the reaction mix on ice.  
Components Volume  
10x AsCas12f1 buffer (NaCl-free) 2 uL  
Linearized pSub1-H12/H65 (2 kb) 5 nM final (120 ng)  
sgRNAv1-H12/H65 250 nM final (300 ng)  
Lysate (250-300 nM FITC unit) 2 uL    
H2O Y uL  
Total 20 uL  
**b.** 6-uL aliquots were separated into three individual tubes on ice.  
**c.** Incubate the reaction at 45 degree. Collect samples at 1-, 8-, and 32-min time points. Stop the 
reaction by flash frozen using liquid nitrogen.  
**d.** Incubate on ice until the mix completely thaw.  
**e.** Add 6-uL stop buffer (containing 10% 20 mg/mL Proteinase, 10% 0.5 M EDTA, and 80% H2O).  
**f.** Incubate at 50 degree for 10 min, and 98 degree for 10 min.  
**g.** STOP POINT 1. Sample can be stored at -80 degree.  
  
#### 2. Sample barcoding PCR 1st  
**a.** Prepare PCR mix (a unique sample barcode primer pair per nuclease sample; not per spacer and time point)  
Components Volume  
2x Phanta supermix 10 uL  
P5Ad-X 1 uL  
P7Ad-Y 1 uL  
Cleavage product 1 uL  
H2O 7 uL  
Total 20 uL  
**b.** 98 degree for 60s; 98 degree for 15s, 60 degree for 30s, 40 cycles; 72 degree for 60s.  
**c.** Gel electrophoresis to see 185-bp amplicons.  
**d.** STOP POINT 2. Sample can be stored at -80 degree.  
**e.** Merge 5-uL PCR products at the same time point to generate three merged sample for 1-, 8-, and 32-
min time points. Note, 25 uL of each untreated library control sample were merged into the 32-min sample,respectively.  
**f.** Column cleanup.  
**g.** Exonuclease 1 treatment  
Components Volume  
10x Exo1 buffer 2 uL  
Exo1 1 uL  
PCR product X uL (100 ng)  
H2O Y uL  
Total 20 uL  
Incubate at 37 degree for 120 min, and 80 degree for 10 min.  
**h.** Column clean up.  
**i.** Dilute the purified PCR products to 0.2 ng /uL.  
**j.** STOP POINT 3. Sample can be stored at -80 degree. 
  
#### 3. Time-point indexing PCR 2nd  
**a.** Prepare PCR mix (a unique time-point index primer pair per merged time point sample)  
Components Volume  
2x Phanta supermix 25 uL  
i5-XX 2 uL  
i7-YY 2 uL  
Diluted PCR 1st product (0.2 ng/uL) 5 uL  
H2O 16 uL  
Total 50 uL  
**b.** Split the reaction into two tubes.  
**c.** 98 degree for 60s; 98 degree for 15s, 65 degree for 30s, 72 degree for 30s, 15 cycles; 72 degree for   
60s.  
**d.** Gel electrophoresis to see 260-bp amplicons.  
**e.** Beads size selection.  

## adaptor  
![加A pcr](https://github.com/user-attachments/assets/f1497a05-5398-4a07-b443-3aa825613c60)

ts cRISPRessoBatch -batch settings batch batch-skip faile  


## 2、高通量数据分析   
请做如下准备工作：   
1. win10 用户（必须是专业版，家庭版不可以）安装 Ubuntu 子系统，参考https://zhuanlan.zhihu.com/p/62658094（安装好后设置用户名，密码，进行必要的 update 和必须软件安装） 
sudo apt-get update  
sudo apt install pip (或 pip3)  
2. Pip install barcodeSpliter  
3. 在 ubuntu 子系统中安装 miniconda（推荐，安装时设置 miniconda 为默认启动）  
`wget https://repo.anaconda.com/miniconda/Miniconda3-latest-Linux-x86_64.sh`  
`sh ./Miniconda3-latest-Linux-x86_64.sh`  
`conda config --add channels defaults`  
`conda config --add channels bioconda`  
`conda config --add channels conda-forge`  
`rm Miniconda3-latest-Linux-x86_64.sh`  
`conda create -n crispresso2_env -c bioconda crispresso2`  
`conda activate crispresso2_env`  
`CRISPResso -h`  
拆数据：
`conda activate crispresso2_env`  
`CRISPRessoBatch --batch settings batch.batch -p 4 skip failed`  
![image](https://github.com/user-attachments/assets/789237aa-952f-4897-b052-b218f776b314)

5. 下载安装 cuemol
http://www.cuemol.org/en/index.php?Download
