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
* func  :`getDocument`：查看与令牌相关的文档链接和文档哈希值
* param :`_name`:文档名字
* return:返回与令牌相关的文档链接和文档哈希值
```solidity
function getDocument(bytes32 _name) external view returns (string memory, bytes32);
```
* func  :`setDocument`：将文档与令牌关联
* param :`_name`:文档名字
* param :`_uri` :文档链接
* param :`_documentHash`:文档哈希值
```solidity
function setDocument(bytes32 _name, string calldata _uri, bytes32 _documentHash) external;
```




