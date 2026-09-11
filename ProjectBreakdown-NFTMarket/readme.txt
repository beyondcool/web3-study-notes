** Subgraph 同步合约数据 **

NFT Market

代码: https://github.com/MetaNodeAcademy/ProjectBreakdown-NFTMarket

我是刚学习GoLang开发web服务不久的学生，看过比较基础的web源码，还没有动手做过web后端项目。正在学习这个项目（EasySwapBackend）的源码，但是阅读速度很慢，在阅读是发现很多代码不好理解。不同写代码的人在做什么。现在要你为我给这个项目代码（EasySwapBackend）添加注释，不用为其他模块添加注释。添加注释要注意一下几点：
1. 为了区分源代码中的注释，你添加的“行注释”或“块注释”的开头要标记“【AI】”，比如：

	// 【AI】注册 v1 路由（在 NewRouter 里调用）。
	// 【AI】结构：/api/v1 下按业务分组注册接口，每个 handler 都通过 v1.XxxHandler(svcCtx) 生成。
	// 【AI】注意：router.go 里注释写“register for parameter checkers”但这里实际是注册路由，注释不准确。
	func loadV1(r *gin.Engine, svcCtx *svc.ServerCtx) {
		...
	}
	
	/** 【AI】
	* xxxxxxxxxxxxxxxxxxxxxxx
	* yyyyyyyyyyyyyyyyyyyyyyyyy
	*/
	
2. 每个go文件要有整个文件的块注释，说明这个文件写了哪些业务（就像需求一样），还有作者当时的想法（代码实现思路）。
3. 每个go方法要有注释，说明方法作用，以及作者编写代码的想法逻辑。
4. 你认为我可能不懂的代码，也要添加注释，给我讲讲。
5. 如果发现写的不好的地方，也要告诉我，避免我将来开发项目时模仿。如果有错误，也要直接指出来。

https://vscode.marketplace.browsertotal.com/items?itemName=ikaros.glm-for-vscode-copilot


Index Price：数学运算结果（采集多家交易所的数据）

Mark Price：基于 Index Price 做了一点点微调，让价格曲线看起来更“平滑”了。
Mark Price 作用：（1）显示用户浮动的盈亏；（2）判断是否请算用户（强制平仓）。
 但是：如果用户主动平仓  或  被强制平仓，使用的价格不是Mark Price，而是  Market Price


25.73元

---------- 怎么算出来 newReducedCredit ？
// 第一步：算新 credit（旧锚 + 资金费补偿 + 本次成交）
int256 credit = paper_old × rate + reducedCredit_old + creditChange;

// 第二步：算新 paper
int128 newPaper = paper_old + paperChange;

// 第三步：反推新锚
int128 newReducedCredit = credit - newPaper × rate;
----------



2*5e6 + -120000e6 + 60000e6
= 60010 -120000
= −59990e6 = credit

−59990e6 - 1*5e6

-------------------------
traderAddr在每个市场的资产价值：
(int256 paperAmount, int256 creditAmount) = Perpetual.balanceOf(traderAddr)


敞口（exposure）：paperAmount.decimalMul(price).abs()

仓位价值（净值）： paperAmount.decimalMul(price) + creditAmount;

账户净值（netValue）：仓位价值 + 主资产余额 + 次级资产余额


