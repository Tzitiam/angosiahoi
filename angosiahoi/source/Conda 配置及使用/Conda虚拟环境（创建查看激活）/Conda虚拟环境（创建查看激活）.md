## conda创建及使用虚拟环境</br>

#### 第一步,創建 虛擬環境：
- 命令行></br>

    conda create -n **虚拟环境名字** python=**3.9**（需要的版本）

- 注：如果conda过老，无法创建，需要更新一下，他会提示：

    conda update -n base -c defaults conda

#### 第二部,查看 conda 创建的虚拟环境命令:
    conda env list

#### 第三步,切換 Canda 環境:
- 命令行> <br>
    conda activate **虚拟环境名**
- 关闭命令行：<br>
    conda deactivate 
- 注：有可能无法直接切换虚拟环境，因为需要初始化一下conda，它会提示你需要 conda init，直接输入回车就好：<br>
    conda init