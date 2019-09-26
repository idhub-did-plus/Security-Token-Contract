# IDHub-Security-Token-Service
<div align=center><img src="https://raw.githubusercontent.com/idhub-did-plus/Security-Token-Contract/master/image/WechatIMG611.png"/></div>


随着证券类通证的兴起，加密金融开始主动纳入证券法律的监管范畴。从某种程度上，ERC-1400仍然一个不断生长的标准，其结合可替代通证和证券业务的特点，在技术层面将通证分割成不同的层级，不同层级拥有不同的业务逻辑，从而赋予智能合约对通证更细粒度的控制能力。虽然目前的标准涵盖了很多必要功能，但还有很多领域值得讨论，我们相信，通过区块链从业者的努力，各方就互操作标准终会达成共识，并为加密金融释放更大流动性提供协议基础


<p align="center">
	<a href="https://circleci.com/gh/vuejs/vue/tree/dev">
		<img src="https://img.shields.io/badge/PDF-%E5%9F%BA%E9%87%91%E6%A8%A1%E5%9E%8B-orange" alt="Build Status">
	</a>
	<a href="https://www.npmjs.com/package/vue">
		<img src="https://img.shields.io/badge/%E7%89%88%E6%9C%AC-1.0.0-green" alt="License">
	</a>
	<a href="https://chat.vuejs.org/">
		<img src="https://img.shields.io/badge/%E5%85%AC%E4%BC%97%E5%8F%B7-IDHub-blue" alt="License">
	</a>
</p>

## 接口说明
#### 1.Document Management->文档管理
* func   : `getDocument`：查看与令牌相关的文档链接和文档哈希值
* param  : `_name`:文档名字
* return : 返回与令牌相关的文档链接和文档哈希值
```solidity
function getDocument(bytes32 _name) external view returns (string memory, bytes32);
```
* func   : `setDocument`：将文档与令牌关联
* param  : `_name`:文档名字
* param  : `_uri` :文档链接
* param  : `_documentHash`:文档哈希值
```solidity
function setDocument(bytes32 _name, string calldata _uri, bytes32 _documentHash) external;
```
#### 2.Token Information->令牌信息
* func   : `balanceOfByPartition`：查看持有者某个分区下令牌的余额
* param  : `_partition` : 分区
* param  : `_tokenHolder` : 持有者地址
* return : 返回当前地址下某分区令牌的余额
```solidity
function balanceOfByPartition(bytes32 _partition, address _tokenHolder) external view returns (uint256);
```
* func   : `partitionsOf`：获取令牌持有者的分区索引
* param  : `_tokenHolder` : 持有者地址
* return : 返回令牌持有者的分区集合
```solidity
function partitionsOf(address _tokenHolder) external view returns (bytes32[] memory);
```
#### 3.Partition Token Transfers->令牌交易
* func   : `transferByPartition`：分区令牌交易(本人执行)
* param  : `_partition` : 分区
* param  : `_to` : 令牌接收者
* param  : `_value` : 令牌交易数量
* param  : `_data` : 代币持有者随附于交易的信息
* return : 目标分区
```solidity
function transferByPartition(bytes32 _partition, address _to, uint256 _value, bytes calldata _data) external returns(bytes32);
```
* func   : `operatorTransferByPartition`：分区令牌交易(操作者执行)
* param  : `_partition` : 分区
* param  : `_from` : 令牌持有者
* param  : `_to` : 令牌接收者
* param  : `_value` : 令牌交易数量
* param  : `_data` : 代币持有者随附于交易的信息
* param  : `_operatorData` : 操作者随附于交易的信息
* return : 目标分区
```solidity
function operatorTransferByPartition(bytes32 _partition, address _from, address _to, uint256 _value, bytes calldata _data, bytes calldata  _operatorData) external returns (bytes32);
```
#### 4.Controller Operation->控制操作
* func   : `isControllable`：显示令牌是否仍然可以由操作者控制
* return : 是或否
```solidity
function isControllable() external view returns (bool);
```
* func   : `controllerTransfer`：令牌交易控制(令牌发布者或具备公信力的法律机构执行)
* param  : `_partition` : 分区
* param  : `_from` : 令牌持有者
* param  : `_to` : 令牌接收者
* param  : `_value` : 令牌交易数量
* param  : `_data` : 代币持有者随附于交易的信息
* param  : `_operatorData` : 操作者随附于交易的信息
```solidity
function controllerTransfer(bytes32 _partition,address _from, address _to, uint256 _value, bytes calldata _data, bytes calldata _operatorData) external;
```
* func   : `controllerRedeem`：令牌赎回控制(令牌发布者或具备公信力的法律机构执行)，经此操作令牌的总量会减少
* param  : `_partition` : 分区
* param  : `_tokenHolder` : 持有者地址
* param  : `_value` : 令牌交易数量
* param  : `_data` : 代币持有者随附于交易的信息
* param  : `_operatorData` : 操作者随附于交易的信息
```solidity
function controllerRedeem(bytes32 _partition,address _tokenHolder, uint256 _value, bytes calldata _data, bytes calldata _operatorData) external;
```
#### 5.Operator Management->操作者管理
* func   : `authorizeOperator`：授权操作者拥有与所有者一样交易及赎回的权利
* param  : `_operator` : 操作者地址
```solidity
function authorizeOperator(address _operator) external;
```
* func   : `revokeOperator`：删除操作者拥有与所有者一样交易及赎回的权利
* param  : `_operator` : 操作者地址
```solidity
function revokeOperator(address _operator) external;
```



