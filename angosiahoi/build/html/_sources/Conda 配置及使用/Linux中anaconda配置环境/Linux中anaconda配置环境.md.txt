## Conda 在 Linux 中的環境配置

-  第一步,输入命令,打開文件></br> 
    sudo vim /etc/profile
</br>

- 第二步,在最后一行加入</br>
    export PATH=**/home/develop/anaconda3/bin:$PATH**
</br>其中"/home/develop/anaconda3"是我的anacond3安装路径,请根据自己的安装路径修改路径目录。
</br>

- 第三步,按ESC鍵,輸入 **:wq!** 保存退出编辑,終端输入以下命令生效</br>
    source /etc/profile
