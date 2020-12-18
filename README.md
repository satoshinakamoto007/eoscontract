# 如何编译合约？
* 安装eosio.CDT
* 执行脚本./build.sh
* 编译好的文件将输出在./build目录中

# 如何测试合约？
### 合约部署
```shell
cd ./build
cleos set contract bob contracts/bob.token -p bob
```

### 创建token（仅限合约创建者调用）
```shell
# 创建一个名为BOB的token，最大发行量为1000，精度为小数点后4位
cleos push action bob create '[ "bob", "1000.0000 BOB"]' -p bob 
```
### issue token到创建账户中（仅限合约创建者调用）
```shell
# 将1000个BOB币issue到bob账户中
cleos push action bob issue '[ "bob", "1000.0000 BOB", "transfer message"]' -p bob
```
### 转账
```shell
# 从bob账户中转100个BOB币到账户hello中
cleos push action bob transfer '["bob","hello","100.0000 BOB","transfer msg"]' -p bob
```
### 冻结账户（仅限合约创建者调用）
```shell
# 将代币BOB中的账户hello进行冻结，hello账户不允许继续转账或被转账
cleos push action bob freeze '["hello","0.0000 BOB"]' -p bob
```
### 解冻账户（仅限合约创建者调用）
```shell
# 解冻hello账户，使其恢复正常
cleos push action bob unfreeze '["hello","0.0000 BOB"]' -p bob
```
### 暂停目标token合约（仅限合约创建者调用）
```shell
# 暂定BOB的交易
cleos push action bob pause '["0.0000 BOB"]' -p bob
```
### 恢复目标token合约（仅限合约创建者调用）
```shell
# 恢复BOB的交易
cleos push action bob unpause '["0.0000 BOB"]' -p bob
```
### 增加max supply（仅限合约创建者调用）
```shell
# 增加BOB币的max supply
cleos push action bob inc '["100.0000 BOB"]' -p bob
```
### 减少max supply（仅限合约创建者调用）
```shell
# 减少BOB币的max supply，bob账户中必须包含大于100个BOB的余额，否则失败
cleos push action bob dec '["100.0000 BOB"]' -p bob
```
### 查看账户token余额
```shell
# 查询bob账户的BOB币余额
cleos push action bob balanceof '["bob","0.0000 BOB"]' -p bob
```
