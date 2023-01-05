## Conda 虛擬環境更換名字
</br>

#### 1.conda虚拟环境换名不容易，但可以通过克隆一个环境来修改名字

    conda create --name jupyter_notebook(新环境名) --clone test（旧环境名）

#### 2.如果想删除旧环境，可以使用以下命令：
    conda remove --name old_name（旧文件名） --all

#### 3.還有一种暴力方式，直接找到虛擬環境目錄修改，複製、刪除等操作也同理。