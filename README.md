# 基于区块链的社区贡献激励方案

## 一、两层模型

1. 社区现金：Community Cash（简称cc）

   由kcoin基金会掌握，并定期增发，维持与ETH的稳定兑换关系

2. 项目贡献度与股份：Contribute Stock（简称cs）

   通过工作量规则，参与某一开源项目的人，将会分到一定数额的股权

## 二、开源项目成长模式

### 1. 项目初创期

一个已经在Github上创建好的开源项目，可以在kcoin激励平台注册，并设定一组能够自动执行的规则：

1. 某用户A提交一个Pull Request，经过N人的review，并由用户B合入项目。则用户A、用户B各得X点cs，N位reviewer，各得Y点cs。
2. committer用户直接项目提交一次代码，每个commit，得Z点cs。
3. 有用户C向该项目提交一个issue，当后续这个issue被某一次代码提交解决时，用户C获得M点cs。
4. 以上经过一段时间的运行后，相关的各位参与贡献的用户，共计获得cs：XXX点。根据他们各自拥有的点数比例多少，可以确定他们各自占有该项目的股份比例，以及后续投票时的权重。
5. 每当项目在Github上产生一个新的release版本，该项目将另行生成N点cs，供项目组进行分配。可以按照全体贡献者的占股比例，均分N点，也可以由全体贡献者投票，手动分配部分或全部release cs点。
6. 以上各个分配的规则数字，可以再次修改，当然也需要全体贡献者根据股份比例投票决定。

### 2. 基金会注资

* 对于发展良好的开源项目，kcoin基金会，可以通过投票，决定是否注资支持。注资支持的方式，由基金会与开源项目贡献者双方协商。
* 由基金会出资X枚cc，兑换某一开源项目的Y枚cs。兑换出的cs，由全体开源项目贡献者，按比例缴出。收到的cc，可以由开源项目，自行支配。
* 基金会虽然持有某一开源项目的cs，却不会参与该项目的各种投票决策，也不会向任何第三方，转让这些cs。
* 如果某一个开源项目，希望彻底脱离kcoin激励平台的约束与规则，则需要回购曾经出让的cs，再彻底注销。

### 3. 外部收入

* 开源项目可以接受捐赠，其他个人或企业，可以购买kcoin激励平台的cc，然后捐赠给某一个开源项目，并声明不需要任何直接或间接回报。
* 开源项目可以对外销售商业版license，并明确授权的定价为：X枚cc。未来也可以考虑更多的销售模式。
* 针对用户迫切需要的某一需求，用户可以购买cc，并绑定于某一个issue。当该issue完成时，参与完成的开发者，可以瓜分这笔cc。也可以另行制定该项目的规则，将一部分cc收入，划入项目的公共账户。
* 基金会以外的第三方，也可以用cc收购开源项目的cs，项目全体同意的股份出让，或者某一位项目贡献者的个人出让皆可。但是兑换价格需要获得全体参与方的同意。这样的第三方，将同样根据其掌握的cs多少，拥有今后的投票权。
* 收到cc的开源项目（无论是销售收入、特性悬赏收入，还是基金会注资），可以直接将这些社区现金，按比例分掉。也可以存储在开源项目的公共账户之中，另作他用。

### 4. 开源项目的cc公共账户

cc公共账户，相当于项目的现金储备，可以用于多种场合。

* 项目成员，发放年终奖。
* 在社区悬赏，用于解决特定的棘手难题。
* 回购kcoin基金会持有的cs。


## 三、Kcoin基金的发行与管理方式

* Kcoin的“社区现金”，不通过挖矿的方式产生
* 早期的社区现金，以定向募集的方式，与各大投资人兑换ETH
* 基金会将会保留50%的社区现金，用于向各个开源项目注资，并接受兑换
* 在3~5年之后，由基金会决议，每年发行若干社区现金，并公开兑换，目标是使得CC与ETH的兑换率，维持每年不超过20%的波动。
* Kcoin基金，不接受CS->CC的兑换，只接受CC<->ETH的双向兑换。
* 向开源项目注资的CC，将在一定期限（一年以上）后，允许兑换。

## 四、开发指南

具体内容详见：[开发指南文档](dev_guide.md)