### 序列分析基因  
# prodigal 原核生物基因预测工具  
### 安装  
**manba install -y prodigal**  
或：  
**prodigal  
 git clone https://github.com/hyattpd/Prodigal.git  
 cd Prodigal  
 make install**  
![image](https://github.com/user-attachments/assets/c5637ced-e2ad-4e36-ab81-103de83a5ac6)  

-a protein.faa  #将氨基酸序列写入该文件中  
-d .ffn  #将核酸序列写入该文件中   
-c：封闭末端。不允许基因延伸到序列边界之外。  
-f：选择输出格式（gbk、**gff** 或 sco）。默认格式为 gbk。  **通常用gff**
-g：指定使用的密码子翻译表（默认是11号表）。其中第一套是标准密码子表，第 11 套是细菌，古细菌以及植物线粒体。如果是支原体，一定要选择第四套密码子，因为它的起始密码子并不是 AUG.        
-h：帮助。  
-i：指定**输入**的.fasta/Genbank文件（默认从标准输入读取）。  
-m：将连续的“N”视为屏蔽序列；不在其上构建基因。  
-n：跳过Shine-Dalgarno训练器，强制进行完整的基序扫描。  
-o：指定输出文件（默认写入标准输出（gff格式））。  
-p：选择操作模式（single（单序列）或meta（宏基因组））。默认是single。  
-q：安静模式运行（抑制正常的标准错误输出），**不在屏幕输出**。  
-s：将所有潜在基因（包含评分）写入指定文件。  
-t：写入训练文件（如果不存在）；否则，读取并使用指定的训练文件。  
-v：打印版本号并退出。    


    
### 运行  
$ prodigal -i testm78.fasta -d testm78.ffn -a testm78.faa -f gff -o testm78.gff -g 11 -c  -p single -s test.stat  
#-c -p 不写参数代表使用默认值

### 使用seqkit工具同时统计不同格式的序列  
$ seqkit stat test.ffn test.faa test.gff  

# glimmer3基因预测  
### 安装软件  
mamba install -y  glimmer=3.02  
### 运行软件（以下多步骤命令写入--glimmer.sh--sh glimmer.sh）   
**sed -e '/>/d' testm78.fasta |tr -d '\n' |awk 'BEGIN {print ">wholefile"}{print $0}' >wholefile  
long-orfs -n -t 1.15 wholefile tagname.longorfs  1>/dev/null 2>/dev/null  
extract -t wholefile tagname.longorfs > tagname.train  2>/dev/null  
build-icm  -r tagname.icm < tagname.train 1>/dev/null 2>/dev/null  
glimmer3 -o50 -g110 -t30 testm78.fasta tagname.icm ref**   

阅读结果文件： less ref.predict

# 在线预测   
如果是少量序列，可以选择在线预测的方法。  
**原核基因预测：prodigal**
网站链接：http://prodigal.ornl.gov/  
**原核基因预测：glimmer3**  
网站链接：http://ccb.jhu.edu/software/glimmer/index.shtml  
国家微生物科学数据中心：prodigal  
https://nmdc.cn/analyze/details?id=600671720b38496ee0c908dc  
国家微生物科学数据中心：glimmer3   
https://nmdc.cn/analyze/details?id=600671720b38496ee0c908dd  
**genemarks：**  
http://exon.gatech.edu/GeneMark/gm.cgi    


# 噬菌体基因预测
Virsorter2  
genomad  







