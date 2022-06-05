---
title: space-based detection
banner: "https://ae01.alicdn.com/kf/H84799946d2d0483fae7f64508be400a7f.jpg"
banner_y: 0.556
banner_lock: true
---

21-cm global signal detection 已经取得一些结果，比如对再电离发生的红移区间的限制 ([[When did Reionization happen]]) ，再比如 EDGES3 对 CD 的超出标准模型的观测 () 。
不过在地面上 探测21厘米信号收到地球大气电离层的干扰，越到低频越显著， 
EGDES3 的 87MHz 的结果也有人怀疑是 大气电离层的问题 ()
到空间去探测 21-cm signal 是近年来比较热门的想法。

这里整理了 21-cm signal space-based detection 的进展。 

## take home messages 
- EGDES3 此前（2018年）报道探测到 87MHz 处的21厘米吸收峰，比standard model 预言的要深很多、宽很多。这可能是因为背景辐射有未知的加热机制，也可以是因为IGM 气体有其它的冷却机制，甚至气体可能通过和暗物质相互作用而“过度”冷却。
- 这一结果掀起了理论解释的热潮。
- 但这个观测结果本身是需要进一步交叉验证的。 SARAS3 在2021年给出了相反的结果，认为 EGDES3 测到的是假信号。
- 如果是假信号，可能来自前景去除的问题，可能是一些系统误差。其中有人分析 地球大气的电离层可能对实验结果造成了干扰。到太空去“重复”EDGES的实验，就有很大潜力判断 EDGES3 和 SARAS3 哪个正确。
	- 电离层的影响 与频率的-2次方成正比，所以越到低频影响越大。再电离阶段影响小一些，但是上空间也有助于避免人类射电活动的干扰 RFI。
	- （也有人认为 ground plane也会提供假信号 [A Ground Plane Artifact that Induces an Absorption Profile in Averaged Spectra from Global 21 cm Measurements, with Possible Application to EDGES](https://www.colorado.edu/project/dark-ages-polarimeter-pathfinder/2019/04/03/ground-plane-artifact-induces-absorption-profile-averaged-spectra-global-21-cm)
- DAPPER 就打算先在 cosmic dawn 验证 EGDES3 的结果，再进一步通过对 dark ages的测量，来区分不同的 暗物质冷却模型，为下一步的研究提供方向，限制人们对暗物质的理解。

我调查了目前最新的两个项目， [[DAPPER]] 和 [[DSL]] ，两者区别很大。
[[DAPPER]] 感觉就是瞄准了 21cm global signal，特别是 EDGES3的观测结果引来的争议。
而 [[DSL]] 则主要是想开创 1-30MHz 窗口，想做的事情非常多， global  signal  只是其中一个小目标。
（轨道设计、能源、重量（？）上我会参考 DSL , 而仪器 （antenna）主要参考 DAPPER。

- 我们做 CubeSat主要要考虑一下问题：
	- 天线构型和大小。
		- 总体来说是 length ~ lambda/2 , （2m for z=20, ） 比较好，色散可以忽略。
		- DAPPER是直接用了4根天线，同时把偏振也测了（为什么？），看起来没有ground plane。
		- DSL 分两个频段，因为它本身就是干涉阵，*在低频段为了有效积累积分时间，就多个卫星一起测了*，用的是 triple-disk 构型。高频段（30MHz+）只用一颗卫星，用的是 cone-disk 构型(d~40cm,h~30cm) 。（不同构型的区别？beam pattern 不同？如何选择？）用到了ground plane。 
		- ground plane 会改变 beam pattern，可以指向特定天区。高银纬的前景小。（这个好处是否足够有吸引力？——分析见下
			- 如果要做 ground plane，可以将太阳能翻版和 ground plane结合？
	- 轨道和时间分布
		- 轨道可以低一点，DAPPER是50-120km，DSL是300km，
		- 观测需要月球挡住地球（最好也能挡住太阳），有效观测时间在30%左右。想必是越低越好（
	- 观测时间
		- 拿前景dominate system thermal noise，再假设 bandwidth，可以估算积分时间。（天到年量级比较正常。（例子见下
	- **频率覆盖**：
		- 需要综合考虑科学价值、卫星尺寸、积分时间需求。
	- 重量、功耗
	- 数传：
		- 如果参考DSL ，
- 可以拓展到 array 上，但干涉阵更复杂，DSL已有讨论。


### 权衡天区定位的重要性

以 $z=20$ 为例，$\nu=67.62\rm{~MHz}$,
高银纬 $T_{\rm{sky}} \sim 180\left(\frac{\nu}{180 \mathrm{MHz}}\right)^{-2.6} \mathrm{~K} \simeq 2295 \rm{~K}$,  (fomula from Furlanetto 2006 )
全天平均 $T_{\rm{sky}} \sim 2300\left(\frac{\nu}{75 \mathrm{MHz}}\right)^{-2.5} \mathrm{~K} \simeq 2980 \rm{~K}$,  (fomula from Shi 2022)

$\Delta T^{N}= \frac{T_{\mathrm{sys}}}{\sqrt{\Delta \nu t_{\mathrm{int}}}}$ ,
假设 bandwidth $\Delta \nu = 1\rm{MHz}$,  $T_{\rm{sky}}$  dominate $T_{\rm{sys}}$ .
要求 sensitivity  $\Delta T = 10 \rm{~mK}$,
高银纬 $t_{\mathrm{int}} \simeq 5.267\times 10^{4} \rm{~s} \simeq 14.6 \rm{~hr}$,
全天平均 $t_{\mathrm{int}} \simeq 8.88\times 10^{4} \rm{~s} \simeq 24.7 \rm{~hr}$ .  多了约 70%. **感觉不是很重要……**
如果我们专注于这个目标，运行一年的话，其实有效时间可以到达100天，sensitivity能做到 1mK.

#### bandwidth choice:
假设 bandwidth $\Delta \nu = 1\rm{MHz}$, 
> “For the Dark Ages measurement, **as only auto-correlation is needed**, the required spectral resolution is 1 MHz.” (Boonstra et al., 2016, p. 6)

#### sensitivity choice:
要求 sensitivity  $\Delta T = 10 \rm{~mK}$, 实际有望再降低一个数量级。
> “For the Dark Ages science case, the goal is to reach 5 mK error on the brightness temperature estimate at 20 MHz,” (Boonstra et al., 2016, p. 6)
> “within eight months of mission duration: this would allow a detection of the dark age signal at SNR=10.” (Boonstra et al., 2016, p. 6)



## global signal 的科学意义

- search for divergences from the standard model that will indicate new physics such as **heating or cooling produced by dark matter**.


## problem of ground-based observations 

-   ionosphere refraction and absorption -> go to space.

 study the chromatic ionospheric effects on global 21-cm observations. https://arxiv.org/abs/2011.10517

-   radio frequency interference (RFI) -> the Moon can shield  the RFI from Earth.

## signal antenna

[DAPPER website](https://www.colorado.edu/project/dark-ages-polarimeter-pathfinder/)


## interforemeter

- [DSL]

## chanllege

main challenge : the removal of bright foregrounds.

### DAPPER resolve 

 (1) a **polarimeter** to measure both intrinsically polarized emission and polarization induced by the anisotropic foregrounds and large antenna beam to aid in the separation of the foregrounds from the *isotropic, unpolarized global signal*, 
  
  (2) a **pattern recognition** analysis pipeline based on well-characterized *training sets* of *foregrounds* from sky observations, *instrument systematics* from simulations and laboratory measurements, and *signals* from theoretical predictions.
