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
-g：指定使用的密码子翻译表（默认是11号表）。  
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
$ prodigal -i m78.fasta -d m78.ffn -a m78.faa -o m78.gff -c  -p   
#-c -p 不写参数代表使用默认值

### 使用seqkit工具同时统计不同格式的序列  
$ seqkit stat test.ffn test.faa test.gff  





