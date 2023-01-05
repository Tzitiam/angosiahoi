## pip換源</br>

#### 永久换源:
- 命令行> <br>
    pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple 
</br>

- 另外附上几个国内源：<br>
    阿里云 http://mirrors.aliyun.com/pypi/simple/<br>
    中国科技大学 https://pypi.mirrors.ustc.edu.cn/simple/<br>
    清华大学 https://pypi.tuna.tsinghua.edu.cn/simple/<br>
    中国科学技术大学 http://pypi.mirrors.ustc.edu.cn/simple/<br>

#### 临时换源:
- pip install +库名 -i +源<br>
- 例如：<br>
    pip install scrapy -i https://pypi.tuna.tsinghua.edu.cn/simple