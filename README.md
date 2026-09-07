# bandwagonhost los angeles vps：洛杉矶多机房选型与CN2 GIA套餐全价位对比

如果你正在搜 "bandwagonhost los angeles vps"，大概率不是第一次接触搬瓦工，而是想搞清楚一件事：洛杉矶到底有几个机房，哪个机房线路对国内访问最快，以及哪个套餐在 2026 年还值得买。这篇文章围绕这几个问题展开，所有价格、套餐、机房线路均来自 BandwagonHost 官网当前公开页面，不掺旧数据。

## 洛杉矶机房为什么是搬瓦工的主场

BandwagonHost（搬瓦工）在洛杉矶运营着多个数据中心，是整个产品线里机房密度最高的城市。根据官网当前的 order/get-data 接口和各套餐可选位置，洛杉矶目前至少包含以下几个公开机房：

- **USCA_2** — Coresite LA2，定位为基础线路，提供 ANY2IX、Cloudflare、Google 以及 ChinaNet/China Unicom/China Mobile 的普通 peering，不走 CN2 GIA。
- **USCA_5** — Coresite LA2，SLA 专属机房，AMD EPYC + NVMe，提供 CN2 GIA/CTGNet、CMIN2、China Unicom Premium 三网优质线路，是唯一带 99.99% SLA 的机房。
- **USCA_6** — Digital Realty LAX10，CN2 GIA-E 线路，提供 CN2 GIA、CMIN2、China Unicom Premium。
- **USCA_9** — Coresite LA2，AMD EPYC + NVMe RAID-10，同样提供 CN2 GIA、CMIN2、China Unicom Premium，并直接 peering Apple、Google、Facebook、Tencent/ACE 等。

简单说，洛杉矶的机房分两类：一类是 USCA_2 这种走普通国际线路的"基础款"，价格便宜但晚高峰容易拥堵；另一类是 USCA_5 / USCA_6 / USCA_9 这种走 CN2 GIA / CMIN2 / China Unicom Premium 的"中国优化款"，对国内三网访问质量明显更好。

如果你买 VPS 的核心目的是给国内用户访问，那么真正值得纠结的是 USCA_5、USCA_6、USCA_9 三个 CN2 GIA 机房之间的差异，而不是"要不要选洛杉矶"。

## 三种 CN2 GIA 机房，到底差在哪

USCA_6 和 USCA_9 在线路层面非常接近，都是 CN2 GIA + CMIN2 + China Unicom Premium 的组合，区别主要在硬件和定位上。USCA_9 是较新的 AMD EPYC + NVMe RAID-10 节点，磁盘 I/O 表现更好，适合跑数据库或对存储延迟敏感的应用；USCA_6 是更早的 CN2 GIA-E 经典机房，社区里"老用户"持有量大。

USCA_5 则是另一个层级。它单独绑定 99.99% SLA，硬件是 AMD EPYC + NVMe，网络架构做了双冗余边缘路由器、双路电源、双 NIC 双光纤路径，并直接 peering Apple、Google、Facebook、Bytedance。SLA 的核心意义在于：如果 VPS 在一个月内不可达时间累计超过 4.32 分钟，可以申请服务时长补偿，补偿按阶梯计算，最高可抵扣一个月服务时长。普通 99.9% SLA 允许每月 43.2 分钟宕机，差距是十倍。

需要留意的是，SLA 有明确排除条款：DDoS 攻击导致的 nullrouting、用户自身配置问题、计划维护（提前 24 小时通知）、上游网络故障等都不计入补偿。换句话说，99.99% 是"合同承诺"，不是"绝对不宕机"。如果你的业务可能招攻击，需要在前面加一层 Cloudflare 或专门的清洗服务。

## 洛杉矶四档套餐：Basic / E-Commerce / E-Commerce SLA / Ultra

搬瓦工在洛杉矶提供的套餐按"线路等级"分四档，从低到高分别是 Basic VPS、E-Commerce VPS、E-Commerce SLA VPS、Ultra VPS。Ultra 在洛杉矶没有节点（只有香港、东京、大阪、新加坡），所以洛杉矶实际可选的是前三档。

- **Basic VPS**：走普通国际线路，USCA_2 机房，1Gbps 端口，Intel Xeon CPU，RAID-10 SSD，价格最低，适合不依赖国内访问的场景。
- **E-Commerce VPS**：CN2 GIA + CMIN2 + China Unicom Premium，2.5–10Gbps 端口，可在 USCA_6 / USCA_9 等 15+ 机房间免费迁移，是大多数国内用户的首选。
- **E-Commerce SLA VPS**：仅 USCA_5，AMD EPYC + NVMe，绑定 99.99% SLA，每两周可免费换一次 IP，适合对稳定性有合同级要求的业务。

下面分别给出当前官网公开的全部套餐配置和价格。所有价格均为美元，币种以官网为准。

## Basic VPS 套餐（USCA_2 普通线路）

Basic 是搬瓦工最便宜的产品线，洛杉矶对应 USCA_2 机房，1Gbps 端口，Intel Xeon CPU，RAID-10 SSD，可在美国、加拿大、荷兰、纽约等基础机房间免费迁移。CPU 配额按官方 ToS：20G 套餐为 1 核的 25%，40G 为 50%，80G 为 1 核 100%，160G 及以上为 1 核 100% + 额外百分比。

| 套餐 | RAM | SSD | CPU | 月流量 | 端口 | 起步价 | 计费周期 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 20G KVM - PROMO (PID 44) | 1 GB | 20 GB | 2 vCPU | 1 TB | 1 Gbps | $49.99 | 年付 | [订购 Basic 20G](https://bwh81.net/aff.php?aff=77528&pid=44) |
| 40G KVM - PROMO (PID 45) | 2 GB | 40 GB | 3 vCPU | 2 TB | 1 Gbps | $52.99 | 半年付 | [订购 Basic 40G](https://bwh81.net/aff.php?aff=77528&pid=45) |
| 80G KVM - PROMO (PID 46) | 4 GB | 80 GB | 4 vCPU | 3 TB | 1 Gbps | $19.99 | 月付 | [订购 Basic 80G](https://bwh81.net/aff.php?aff=77528&pid=46) |
| 160G KVM - PROMO (PID 47) | 8 GB | 160 GB | 5 vCPU | 4 TB | 1 Gbps | $39.99 | 月付 | [订购 Basic 160G](https://bwh81.net/aff.php?aff=77528&pid=47) |
| 320G KVM - PROMO (PID 48) | 16 GB | 320 GB | 6 vCPU | 5 TB | 1 Gbps | $79.99 | 月付 | [订购 Basic 320G](https://bwh81.net/aff.php?aff=77528&pid=48) |
| 480G KVM - PROMO (PID 49) | 24 GB | 480 GB | 7 vCPU | 6 TB | 1 Gbps | $119.99 | 月付 | [订购 Basic 480G](https://bwh81.net/aff.php?aff=77528&pid=49) |

Basic 系列的 80G/160G/320G/480G 还提供季度、半年、年付多档，年付单价更低。如果你只是要一个洛杉矶 IP 跑点轻量服务、做跳板或测试，Basic 20G 年付 $49.99 是搬瓦工整个目录里最便宜的入口。

## E-Commerce VPS 套餐（CN2 GIA + CMIN2 + CUP）

E-Commerce 是搬瓦工的"中国优化"主力产品线，洛杉矶可选 USCA_6 和 USCA_9 两个 CN2 GIA 机房，端口从 2.5Gbps 起步，高配升到 5Gbps 和 10Gbps。所有 E-Commerce 套餐都支持在 15+ 个机房间免费迁移，包括洛杉矶 DC6/DC9、圣何塞、温哥华 CN2、纽约 CN2、阿姆斯特丹 CN2/9929、大阪 Softbank、迪拜等。

| 套餐 | RAM | SSD | CPU | 月流量 | 端口 | 起步价 | 计费周期 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| SPECIAL 20G (PID 87) | 1 GB | 20 GB | 2 vCPU | 1 TB | 2.5 Gbps | $49.99 | 季付 | [订购 E-Commerce 20G](https://bwh81.net/aff.php?aff=77528&pid=87) |
| SPECIAL 40G (PID 88) | 2 GB | 40 GB | 3 vCPU | 2 TB | 2.5 Gbps | $89.99 | 季付 | [订购 E-Commerce 40G](https://bwh81.net/aff.php?aff=77528&pid=88) |
| SPECIAL 80G (PID 89) | 4 GB | 80 GB | 4 vCPU | 3 TB | 2.5 Gbps | $56.99 | 月付 | [订购 E-Commerce 80G](https://bwh81.net/aff.php?aff=77528&pid=89) |
| SPECIAL 160G (PID 90) | 8 GB | 160 GB | 6 vCPU | 5 TB | 5 Gbps | $86.99 | 月付 | [订购 E-Commerce 160G](https://bwh81.net/aff.php?aff=77528&pid=90) |
| SPECIAL 320G (PID 91) | 16 GB | 320 GB | 8 vCPU | 8 TB | 5 Gbps | $159.99 | 月付 | [订购 E-Commerce 320G](https://bwh81.net/aff.php?aff=77528&pid=91) |
| SPECIAL 640G (PID 92) | 32 GB | 640 GB | 10 vCPU | 10 TB | 10 Gbps | $289.99 | 月付 | [订购 E-Commerce 640G](https://bwh81.net/aff.php?aff=77528&pid=92) |
| SPECIAL 1280G (PID 93) | 64 GB | 1.28 TB | 12 vCPU | 12 TB | 10 Gbps | $549.99 | 月付 | [订购 E-Commerce 1280G-12T](https://bwh81.net/aff.php?aff=77528&pid=93) |
| SPECIAL 1280G 15T | 64 GB | 1.28 TB | 12 vCPU | 15 TB | 10 Gbps | $679.00 | 月付 | [订购 E-Commerce 1280G-15T](https://bit.ly/BandWaGon) |
| SPECIAL 1280G 20T | 64 GB | 1.28 TB | 12 vCPU | 20 TB | 10 Gbps | $899.00 | 月付 | [订购 E-Commerce 1280G-20T](https://bit.ly/BandWaGon) |

E-Commerce 20G 季付 $49.99 是进入 CN2 GIA 线路最便宜的门票，年付 $169.99 折算下来约 $14.17/月，比同配置 Basic 贵一倍，但晚高峰国内访问质量差距明显。如果你不确定要不要长期用，从 20G 季付起步试一个月最稳妥。

## E-Commerce SLA VPS 套餐（USCA_5，99.99% SLA）

SLA 系列只在 USCA_5 提供，硬件统一是 AMD EPYC + NVMe RAID-10 + ECC 内存，CPU 为 AMD 专用核（非共享），网络架构做了双冗余。所有 SLA 套餐都包含每两周一次免费换 IP、IPv4 + IPv6 /64、二级私有网络接口。

| 套餐 | RAM | SSD | CPU | 月流量 | 端口 | 起步价 | 计费周期 | 购买 |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 20G SLA (PID 164) | 1 GB ECC | 20 GB NVMe | 2x AMD | 1 TB | 2.5 Gbps | $65.89 | 季付 | [订购 SLA 20G](https://bwh81.net/aff.php?aff=77528&pid=164) |
| 40G SLA (PID 165) | 2 GB ECC | 40 GB NVMe | 3x AMD | 2 TB | 2.5 Gbps | $116.99 | 季付 | [订购 SLA 40G](https://bwh81.net/aff.php?aff=77528&pid=165) |
| 80G SLA (PID 166) | 4 GB ECC | 80 GB NVMe | 4x AMD | 3 TB | 2.5 Gbps | $69.99 | 月付 | [订购 SLA 80G](https://bwh81.net/aff.php?aff=77528&pid=166) |
| 160G SLA (PID 167) | 8 GB ECC | 160 GB NVMe | 6x AMD | 5 TB | 5 Gbps | $109.99 | 月付 | [订购 SLA 160G](https://bwh81.net/aff.php?aff=77528&pid=167) |
| 320G SLA (PID 168) | 16 GB ECC | 320 GB NVMe | 8x AMD | 8 TB | 5 Gbps | $199.99 | 月付 | [订购 SLA 320G](https://bwh81.net/aff.php?aff=77528&pid=168) |
| 640G SLA (PID 169) | 32 GB ECC | 640 GB NVMe | 10x AMD | 10 TB | 10 Gbps | $369.99 | 月付 | [订购 SLA 640G](https://bwh81.net/aff.php?aff=77528&pid=169) |
| 1280G SLA 12T (PID 170) | 64 GB ECC | 1.28 TB NVMe | 12x AMD | 12 TB | 10 Gbps | $699.99 | 月付 | [订购 SLA 1280G-12T](https://bwh81.net/aff.php?aff=77528&pid=170) |
| 1280G SLA 15T (PID 171) | 64 GB ECC | 1.28 TB NVMe | 12x AMD | 15 TB | 10 Gbps | $879.99 | 月付 | [订购 SLA 1280G-15T](https://bwh81.net/aff.php?aff=77528&pid=171) |
| 1280G SLA 20T (PID 172) | 64 GB ECC | 1.28 TB NVMe | 12x AMD | 20 TB | 10 Gbps | $1,159.99 | 月付 | [订购 SLA 1280G-20T](https://bwh81.net/aff.php?aff=77528&pid=172) |

SLA 20G 季付 $65.99 比 E-Commerce 20G 季付 $49.99 贵约 32%，差价买的是 99.99% 合同承诺 + AMD EPYC 专用核 + NVMe + 双冗余网络 + 免费换 IP。对大多数个人用户，这个差价不一定值；对跑跨境电商、TikTok 直播后端、API 服务的用户，SLA 的合同补偿机制有实际意义。

## 不同需求该选哪个洛杉矶套餐

把决策简化成几个典型场景：

**只是想要一个洛杉矶 IP，国内访问质量不重要。** 选 Basic 20G 年付 $49.99，USCA_2 机房，跑个轻量站点、跳板、CI 测试机都够用。

**国内三网访问都要稳，预算敏感。** 选 E-Commerce 20G 季付 $49.99，USCA_6 或 USCA_9 都行，CN2 GIA + CMIN2 + CUP 三网优化，晚高峰比 Basic 明显稳。

**跑正经业务，需要合同级稳定性。** 选 SLA 80G 月付 $69.99，USCA_5，AMD EPYC + NVMe + 99.99% SLA，4GB 内存够跑 WordPress/WooCommerce + 缓存层。

**高流量媒体站或直播后端。** SLA 160G 月付 $109.99 起，5Gbps 端口，8TB 流量，是性价比拐点；再往上 320G/640G 价格跳得比较快，按实际流量选。

**需要在不同机房间切换找最佳线路。** 选 E-Commerce 任意套餐，支持在 15+ 机房间免费迁移；SLA 锁死 USCA_5 不能迁。

一个常被忽略的细节：E-Commerce 套餐的 CPU 在高配档会从 Intel Xeon 切到 AMD EPYC。20G–80G 仍是 Intel Xeon，160G 及以上在 USCA_9 节点是 AMD EPYC + NVMe。如果你在意磁盘 I/O，优先选 USCA_9 的高配档。

## 关于优惠码和购买流程

搬瓦工的优惠码长期在变，社区里被反复验证的两个长期码是 **BWHNCXNVXV** 和 **BWHCGLUKKB**，都是约 6.78% 的循环折扣，可在结账页面的 promo code 框输入。优惠码是否对某个套餐生效要在结账页确认，部分限量版套餐可能不参与。

购买流程很简单：点上面的套餐链接进入官方购物车 → 选择机房和计费周期 → 输入优惠码 → 注册账号或登录 → 用支付宝、PayPal、信用卡或银联支付 → 在 KiwiVM 面板里激活 VPS。新购有 30 天退款窗口，不满意可以在控制台直接申请退款。

需要说明的是，所有套餐链接都通过搬瓦工官方联盟体系跳转，点击后会进入官方购物车并自动带上追踪参数，价格和直接访问官网完全一致。

## 几个常被问到的问题

**洛杉矶和香港 CN2 GIA 怎么选？** 香港延迟更低（典型 30ms 以内 vs 洛杉矶 150ms 左右），但价格贵 3–5 倍。如果用户群在华南且预算充足，香港更好；大多数场景下洛杉矶 CN2 GIA 的性价比更高。

**USCA_6 和 USCA_9 选哪个？** 线路几乎一样，USCA_9 是较新的 AMD EPYC + NVMe 节点，磁盘性能更好；USCA_6 是经典 CN2 GIA-E 机房。新购优先 USCA_9，已有 USCA_6 用户没必要专门迁。

**SLA 的 99.99% 真的能赔吗？** 能，但有条件。需要在故障发生后 90 天内提交工单并明确说明"SLA Service Credit"，补偿是服务时长不是现金，且排除 DDoS、自身配置、计划维护等情形。把它当成"合同约束"而不是"绝对不宕机"更现实。

**能不能在套餐间升级？** 可以，在 KiwiVM 面板或联系支持升级，按比例补差价；降级需要工单，不能自助。

**E-Commerce 套餐能迁到 SLA 机房吗？** 不能。SLA 是独立产品线，只在 USCA_5；E-Commerce 可在 USCA_6/USCA_9 等机房间迁，但不能进 USCA_5。

如果你已经清楚自己的需求，直接点对应套餐的订购链接进官方购物车就行；如果还在 Basic 和 E-Commerce 之间犹豫，从 E-Commerce 20G 季付起步试一个月，体验晚高峰国内访问质量后再决定要不要升级或换机房，是成本最低的判断方式。
