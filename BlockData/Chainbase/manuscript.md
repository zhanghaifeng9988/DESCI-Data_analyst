1、克隆仓库
git clone https://github.com/chainbase-labs/manuscript-core.git

2、安装编译环境
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
dnf install -y openssl-devel pkg-config
dnf install -y make
dnf install -y gcc

3、编译gui应用
make gui
如果编译环境有问题，咨询AI ,继续完善，以上是我的centos7环境示例


4、配置环境变量
  manuscriptcore/gui/target/release/manuscript-gui
这是应用程序
将其配置到环境变量中

5、安装go语言
wget https://golang.org/dl/go1.24.4.linux-amd64.tar.gz
注意，go版本不能低于1.23
tar -C /usr/local -xzf go1.24.4.linux-amd64.tar.gz

6、编译CLI应用
make cli


5、配置环境变量
参考第4项





问题1：日志文件都是空的
/root/.manuscript/logs

问题2：配置文件的谁生成，作用是什么？
/root/.manuscript_config.ini

问题3：配置文件中的base参数指定的目录，作用是什么呢？
/root/manuscripts



select * from ethereum.transactions where from_address='0x44f08Ed7D8F63b345F0fc512aEcfaA4F16831643';

name: demo                                                                                                 
specVersion: v1.0.0                                                                                        
parallelism: 1                                                                                             
sources:                                                                                                   
  - name: ethereum_transactions                                                                            
    type: dataset                                                                                          
    dataset: ethereum.transactions                                                                         
transforms:                                                                                                
  - name: ethereum_ethereum_transactions_transform                                                         
    sql: >                                                                                                 
      Select * From ethereum_transactions where from_address='0x44f08Ed7D8F63b345F0fc512aEcfaA4F16831643'  
sinks:                                                                                                     
  - name: ethereum_ethereum_transactions_sink                                                              
    type: postgres                                                                                         
    from: ethereum_ethereum_transactions_transform                                                         
    database: zhf_db                                                                                       
    schema: zhf                                                                                            
    table: transactions                                                                                    
    primary_key: block_number                                                                              
    config:                                                                                                
      host: 127.0.0.1                                                                                      
      port: 5432                                                                                           
      username: zhf                                                                                        
      password: 123123          

                                                                           