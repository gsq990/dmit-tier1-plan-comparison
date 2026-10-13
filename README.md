# DMIT 36.9：$36.9/年买到的是什么配置，香港、洛杉矶、东京三地入门款怎么选，优惠码能不能叠

搜「DMIT 36.9」的人，多半是在某个补货帖里看到一句话——DMIT 年付 $36.9 起。这句话不算错，但它省掉了三个决定你要不要下单的信息：这是哪条线路、哪个机房的机器、流量跑完之后会发生什么。

$36.9 这个数字背后对应的是 DMIT 的 T1.WEE 机型，走 Tier 1 国际线路，1 核 1GB 内存。它不是 CN2 GIA，也不是 Eyeball，这一点很多转发帖不会写清楚。下面把这条线拆开讲。

## DMIT 36.9 到底是哪一款

DMIT 把产品按网络分成三条线：Premium（Pro）、Eyeball（EB）、Tier 1（T1）。$36.9/年 只出现在最便宜的 Tier 1 线上，机型叫 WEE，也就是各产品线的入门款。

核心配置摆在这里：

- 1 核 vCPU / 1GB 内存 / 20GB SSD
- 每月 1000GB 流量，端口 4Gbps
- 1 个 IPv4 + 1 个 IPv6 /64
- 流量用完后不关机，降速继续跑

真正值得说一句的是最后一条。多数便宜 VPS 超量后直接断流或按 GB 计费，DMIT 的做法是让你继续用，只是带宽被人为压下来——洛杉矶 WEE 压到 100Mbps，香港 WEE 压到 50Mbps。对于挂个监控、跑个跳板、做海外镜像下载这类场景，限速后的带宽其实还够用，等于把「超量」变成了「限速月付」。

顺带算一笔账：$36.90 一年，摊到每月大约 $3.1。这个价格在洛杉矶、香港、东京三个机房都能买到，差别只在机房和线路细节。

## 香港、洛杉矶、东京：三个 $36.9 差在哪

同样是 $36.9/年、同样是 1 核 1GB/20GB SSD/1000GB 流量，三个机房的 WEE 并不是一模一样的东西。差别集中在超量后的限速值和测试 IP 上。

| 机房 | 机型 | 配置 | 流量 / 端口 | 超量后 | 价格 | 下单 |
| --- | --- | --- | --- | --- | --- | --- |
| 洛杉矶 | LAX.AS3.T1.WEE | 1 核 / 1GB / 20GB SSD | 1000GB / 4Gbps | 100Mbps 不限流 | $36.90/年 | [ 洛杉矶 T1.WEE 年付入口](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=tier-1&aff=12046) |
| 香港 | HKG.AS3.T1.WEE | 1 核 / 1GB / 20GB SSD | 1000GB / 4Gbps | 50Mbps 不限流 | $36.90/年 | [ 香港 T1.WEE 年付入口](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| 东京 | TYO.AS3.T1.WEE | 1 核 / 1GB / 20GB SSD | 1000GB / 4Gbps | 降速不限流 | $36.90/年 | [ 查看东京 T1 系列库存](https://www.dmit.io/aff.php?aff=12046) |

三台机器的 CPU 平台都是 AMD EPYC 7003 系列（DMIT 内部代号 AS3）。AS3 相对后来的 AN5 平台便宜一些，代价是 DMIT 官方在价目页上明确提示：AS3 仍在持续建设和优化阶段，磁盘性能与 SLA 可能低于成熟平台。这句话的意思很直白——别拿它跑对稳定性要求很高的生产业务。

选哪个机房，取决于你的用途：

- 大陆用户做中转或需要相对低的延迟，香港机房物理距离最近，但要注意 T1 这条线本身没有大陆优化。
- 面向欧美用户的服务、下载量大、想跑备份或镜像，洛杉矶更合适，国际带宽资源也更充足。
- 面向日本本地业务或者需要日本 IP，才选东京。

如果买这台机器是为了给国内用户提供访问，那 $36.9 的 T1 很可能不是你要的东西，往下看。

## Tier 1 这条线的真实水平

DMIT 自己对 Tier 1 的描述是纯国际路由，不针对中国大陆做优化。翻译成人话：电信、联通、移动的去回程路径不保证走 CN2 GIA 或 CMIN2，晚高峰的绕路和丢包是可能出现的，具体表现取决于你所在地区和运营商。

这条线的强项不在延迟，在价格和带宽配额。4Gbps 的端口配上 1000GB 月流量，加上超量后不限流，适合下面这些用法：

- 国际业务落地、面向海外用户的小型站点
- 备份、离线下载、镜像同步
- 监控探针、跑脚本的长期在线小机器
- 学 Linux、练 Docker、搭开发测试环境

不适合的用法同样明确：给国内用户做访问入口、对延迟敏感的业务、指望它稳定解锁特定流媒体。DMIT 官方也写明不保证分配的 IP 能解锁 Netflix、ChatGPT 或游戏等特定服务。

需要国内线路质量的话，DMIT 的另外两条线是 Premium（洛杉矶走 CN2 GIA，三网回程 AS4809）和 Eyeball（洛杉矶走 CMIN2），入门价分别是 $10.90/月 起。

## DMIT 全套餐对比

### Tier 1 国际线路全家桶

Tier 1 是 DMIT 价格最低的一条线，除 WEE 为年付特价外，其余机型按月计费。洛杉矶与香港的配置阶梯基本一致。

| 机型 | CPU / 内存 / 硬盘 | 流量 / 端口 | 超量后 | 价格 | 下单 |
| --- | --- | --- | --- | --- | --- |
| LAX.AS3.T1.WEE | 1 核 / 1GB / 20GB | 1TB / 4Gbps | 100Mbps 不限 | $36.90/年 | [ 洛杉矶 T1.WEE 购买](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=tier-1&aff=12046) |
| LAX.AS3.T1.TINY | 1 核 / 1GB / 20GB | 2TB / 4Gbps | 200Mbps 不限 | $6.90/月 | [ 洛杉矶 T1 全线购买](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=tier-1&aff=12046) |
| LAX.AS3.T1.STARTER | 2 核 / 2GB / 40GB | 4TB / 10Gbps | 200Mbps 不限 | $12.90/月 | [ 洛杉矶 T1 全线购买](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=tier-1&aff=12046) |
| LAX.AS3.T1.MINI | 2 核 / 4GB / 80GB | 8TB / 10Gbps | 200Mbps 不限 | $21.90/月 | [ 洛杉矶 T1 全线购买](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=tier-1&aff=12046) |
| LAX.AS3.T1.MICRO | 4 核 / 4GB / 120GB | 16TB / 10Gbps | 500Mbps 不限 | $32.90/月 | [ 洛杉矶 T1 全线购买](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.WEE | 1 核 / 1GB / 20GB | 1TB / 4Gbps | 50Mbps 不限 | $36.90/年 | [ 香港 T1.WEE 购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.TINY | 1 核 / 1GB / 20GB | 2TB / 4Gbps | 100Mbps 不限 | $6.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.STARTER | 1 核 / 2GB / 40GB | 4TB / 10Gbps | 100Mbps 不限 | $12.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.MINI | 2 核 / 2GB / 60GB | 8TB / 10Gbps | 100Mbps 不限 | $21.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.MICRO | 4 核 / 4GB / 80GB | 16TB / 10Gbps | 200Mbps 不限 | $32.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.MEDIUM | 4 核 / 8GB / 160GB | 32TB / 10Gbps | 200Mbps 不限 | $49.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.LARGE | 8 核 / 16GB / 320GB | 64TB / 10Gbps | 500Mbps 不限 | $99.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| HKG.AS3.T1.GIANT | 8 核 / 24GB / 640GB | 128TB / 10Gbps | 1Gbps 不限 | $199.90/月 | [ 香港 T1 全线购买](https://www.dmit.io/cart.php?region=hong-kong&generation=as3&network=tier-1&aff=12046) |
| TYO.AS3.T1.WEE | 1 核 / 1GB / 20GB | 1TB / 4Gbps | 降速不限流 | $36.90/年 | [ 查看东京 T1 系列](https://www.dmit.io/aff.php?aff=12046) |
| TYO.AS3.T1 系列 | 1 核 1GB 起至 8 核 24GB | 2TB–128TB | 降速不限流 | $6.90/月起 | [ 查看东京 T1 系列](https://www.dmit.io/aff.php?aff=12046) |

香港 T1 的部分机型还提供年付价格，例如 TINY 约 $53.83/年、STARTER 约 $108.36/年、MINI 约 $183.96/年，年付比月付划算，但周期也长。这些价格是第三方站点按官方页面整理的，最终以结算页显示为准。

### 洛杉矶 Premium 与 Eyeball

这两条线面向中国大陆访问质量，价格比 Tier 1 高一个档次，也不存在 $36.9 的年付特价。下表为洛杉矶 AS3 平台的两条线。

| 机型 | CPU / 内存 / 硬盘 | 流量 / 端口 | 超量后 | 价格 | 下单 |
| --- | --- | --- | --- | --- | --- |
| LAX.AS3.Pro.TINY（CN2 GIA） | 1 核 / 2GB / 20GB | 1TB / 1Gbps | 4Mbps 不限 | $10.90/月 | [ 洛杉矶 Premium 全线](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.Pocket | 2 核 / 2GB / 40GB | 1.5TB / 4Gbps | 4Mbps 不限 | $16.90/月 | [ 洛杉矶 Premium 全线](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.STARTER | 2 核 / 2GB / 80GB | 3TB / 10Gbps | 4Mbps 不限 | $34.90/月 | [ 洛杉矶 Premium 全线](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.MINI | 4 核 / 4GB / 80GB | 5TB / 10Gbps | 8Mbps 不限 | $62.90/月 | [ 洛杉矶 Premium 全线](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.MICRO | 4 核 / 4GB / 160GB | 7TB / 10Gbps | 8Mbps 不限 | $87.90/月 | [ 洛杉矶 Premium 全线](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.Pro.MEDIUM | 6 核 / 8GB / 160GB | 14TB / 10Gbps | 10Mbps 不限 | $199.90/月 | [ 洛杉矶 Premium 全线](https://www.dmit.io/cart.php?region=los-angeles&generation=as3&network=premium&aff=12046) |
| LAX.AS3.EB.TINY（CMIN2） | 1 核 / 2GB / 20GB | 1.5TB / 2Gbps | 4Mbps 不限 | $10.90/月 | [ 洛杉矶 Eyeball 全线](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.Pocket | 2 核 / 2GB / 40GB | 3TB / 4Gbps | 4Mbps 不限 | $16.90/月 | [ 洛杉矶 Eyeball 全线](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.STARTER | 2 核 / 2GB / 80GB | 5TB / 10Gbps | 4Mbps 不限 | $34.90/月 | [ 洛杉矶 Eyeball 全线](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.MINI | 4 核 / 4GB / 80GB | 10TB / 10Gbps | 8Mbps 不限 | $62.90/月 | [ 洛杉矶 Eyeball 全线](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.MICRO | 4 核 / 4GB / 160GB | 14TB / 10Gbps | 8Mbps 不限 | $87.90/月 | [ 洛杉矶 Eyeball 全线](https://www.dmit.io/aff.php?aff=12046) |
| LAX.AS3.EB.MEDIUM | 6 核 / 8GB / 160GB | 30TB / 10Gbps | 10Mbps 不限 | $199.90/月 | [ 洛杉矶 Eyeball 全线](https://www.dmit.io/aff.php?aff=12046) |

香港 Premium 线目前常规产品已升级到 AN5 平台（AMD EPYC 9005 系列），月付 $39.90 起；香港 Eyeball 仍在 Beta 阶段，官方明确不建议用于稳定性要求高的生产环境。

Eyeball 和 Premium 的超量后限速值看起来很低（4–10Mbps），这是这两条线的定位决定的——它们卖的是线路质量而非流量，超量后能继续跑但不适合大流量业务。

> 库存提醒：DMIT 的补货是分批次放量的，热门低价机型（尤其 WEE）经常在几小时内售罄。表里的价格和配置来自官方价目页与近期补货资料，能否下单、实际账单金额以结算页面为准。

## 优惠码：$36.9 基本吃不到

这是搜「DMIT 36.9」时最容易被误导的一点。$36.9 已经是年付特价，而 DMIT 现行的 Tier 1 优惠码大多明确把 WEE 排除在外。

根据近期的第三方整理，目前流传的优惠码大致是这些：

| 优惠码 | 适用范围 | 折扣 |
| --- | --- | --- |
| 2025-XMAS-LAX-T1-10-OFF-RECURRING | 洛杉矶 T1 全部套餐，不含 WEE | 10% 折扣 + 5% 返现 |
| 2025-XMAS-LAX-PRO-EB-ANNUALLY-STARTER-AND-HIGHER-15OFF-RECURRING | 洛杉矶 Pro/EB 年付 STARTER 及以上 | 15% 折扣 + 10% 返现 |
| 2025-XMAS-LAX-PRO-EB-10-OFF-RECURRING | 洛杉矶 Pro/EB 常规套餐 | 10% + 5% 返现 |
| LAX-EB-LAUNCH-NON-MONTHLY-RECURRING-20OFF | 洛杉矶 EB TINY 及以上，非月付 | 8 折循环 |
| 202510_HKG_TYO_PRO_20OFF_RECURRING | 香港/东京 Pro，季付及以上 | 8 折循环 |
| 202510_HKG_TYO_T1_30OFF_RECURRING | 香港/东京 T1，季付及以上，不含 WEE | 7 折循环 |
| 2025-TYO-T1-HI-GSL-NON-MONTHLY-30OFF | 东京 T1 TINY 及以上，季付及以上 | 7 折 |
| 2025-TYO-T1-HI-GSL-MONTHLY-10OFF | 东京 T1 月付 | 9 折 |
| Lite-Annually-Recur-30OFF | Standard 网络系列年付 | 7 折循环 |
| Lite-Semi-Annually-Recur-20OFF | Standard 网络系列半年付 | 8 折循环 |

结论是：想用 $36.9 拿 WEE，就别指望再叠折扣；如果把目标换成 TINY 及以上机型（月付 $6.90 起）并走季付或年付，优惠码才有发挥空间，香港和东京的 T1 甚至有 7 折循环码。

这些码的时效性和适用范围由 DMIT 随时调整，下单时在结算页填进优惠码框点验证，能减就减，减不了说明已经失效。这也是唯一可靠的确认方式。

## 谁该买 $36.9，谁该加钱往上走

从价格梯度看，判断标准其实很清楚：

**适合买 WEE $36.9 年付的**：预算压到最低、需要一台长期在线的海外小机器、主要面向国际访问、能接受晚高峰线路波动。年付 $36.9 的性价比摆在那儿，试错成本也低。

**应该考虑 T1.TINY 或更高配置的**：月付 $6.90 就能拿到 2TB 流量，$12.90 上到 2 核 2GB/4TB。如果你需要更多流量或者更高的超量后限速（200Mbps 对比 WEE 的 100Mbps），多花的钱比想象中少，而且月付可以随时停。

**应该直接看 Premium 或 Eyeball 的**：主要用户在国内、在意延迟和晚高峰质量、用它承载正经业务。这种情况下 $36.9 的 T1 再便宜也不解决问题，洛杉矶 Pro.TINY 的 CN2 GIA 是 $10.90/月，预算差距不小，但线路是两回事。

**别买的**：指望它稳定解锁特定流媒体服务、或者拿 AS3 平台跑对 SLA 有硬要求的生产系统。官方已经提前说明 AS3 仍在优化阶段，这不属于意外。

## 购买前该确认的几件事

- 支付方式支持支付宝、微信支付、PayPal 和信用卡，国内用户付款没有障碍。
- 下单前用官方 Looking Glass 从自己的网络测一遍去回程。DMIT 提供按线路区分的测试入口，比看别人的测速图靠谱。
- 年付虽然单价最低，但一旦线路不适合你，退款政策未必对得上你的预期，不确定就先月付一两个月。
- AS3 与 AN5 是两个硬件平台，同价位下 AN5（EPYC 9005 + DDR5）配置更高，但价格也更高；不要只看核心数。

## 常见问题

**$36.9 是月付还是年付？**
年付。这是 WEE 机型的年付特价，折算下来月均约 $3.1。同机型一般没有更便宜的月付方案。

**$36.9 的机器走 CN2 GIA 吗？**
不走。$36.9 的 WEE 属于 Tier 1 国际线路，不含中国大陆优化。CN2 GIA 是洛杉矶 Premium 线的配置，入门 $10.90/月。

**流量用完了会停机吗？**
不会。Tier 1 线超量后降速继续使用，洛杉矶 WEE 降至 100Mbps，香港 WEE 降至 50Mbps，不限流量。

**可以随时升级配置吗？**
DMIT 支持在控制面板内升级配置，具体可升级项和差价以面板显示为准。

**$36.9 能叠加优惠码吗？**
现行的 T1 系列优惠码基本都标注了「不含 WEE」，实际能叠的机会很小。结算页验证一下最快。

看完这些如果已经想清楚用途，直接从对应机房的入口进就行。不确定要哪条线，先拿 Tier 1 的最低配摸底，是最省钱的做法。
