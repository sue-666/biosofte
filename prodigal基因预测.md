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

 或者：  
prodigal -i 0018.fasta 0018.gff -d 0018.ffn -a 0018.faa -g 11 1>prodigal.log 2>prodigal.err  


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

# 基因注释  
# eggnog-mapper
软件安装：  
**mamba install -c -bioconda -y eggnog-mapper python=2.7**  
数据库下载  
新建一个存放地址：mkdir eggnog_database  
eggnog
运行软件脚本：download_eggnog_data.py -y --dir eggnog_database  
提供输入文件.faa  
运行：emapper.py -i m78.faa --output annotation -m diamond --data_dir eggnog_database/ &  
**选项参数：**
-i: 输入文件，最好基因的氨基酸文件(如：prodigal预测生成)  
-o: 输出结果前缀  
-m: 使用HMMER策略还是DIAMOND策略，默认使用HMMER，新版本只支持diamond   
--output_dir：输出结果文件夹  
--data_dir: 数据库目录  
--tax_scope: 指定选择的直系同源基因的物种分类范围，默认为自动判断。  

#### 最终会生成两个文件，分别是mg.emapper.annotations，mg.emapper.seed_orthologs
第一列：查询序列名称；  
第二列：eggNOG种子序列；  
第三列：eggNOG种子序列 evalue；  
第四列：eggNOG种子序列 bit score；  
第五列：预测基因名称；  
第六列：GO_terms, 预测的GO，分号分隔；  
第七列：KEGG_KO: 预测的KO,分号分隔；  
第八列：BiGG_Reactions: BiGG代谢反应预测，分号分隔；  
第九列：eggNOG Taxonomic Scope信息；  
第十列：匹配的OGs;  
第十一列：best_OG|evalue|score  
第十二列：COG功能分类；  
第十三列：eggNOG功能描述；  






