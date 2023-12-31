# UE5-ThirdPersonDEMO
<b>纯蓝图项目</b>, 自用
<p>演示视频参见如下连接：</p>
<a href="https://www.bilibili.com/video/BV18h4y117hR"><p>Version 1 [Bilibili连接]<b>动态血条，低血量提示(溅血UI)，简易数组背包</b></p></a>
<p>背包是基于读取数组内容(为方便使用GameInstance代替GameSave存储玩家数据)，在初始化背包后在对应的格子内塞入物品。</p>
<p>交换在UI中只交换数量和ID，根据ID重新初始化格子，然后使用GameInstance中对应的方法交换两物品在数组中存储的背包中的位置。</p>
<br>
<a href="https://www.bilibili.com/video/BV1tV4y1t7pw"><p>Version 2 [Bilibili连接]<b>背包的丢弃、拾取和堆叠上限，瞄准状态、发射实体子弹和命中反馈，跟踪爆弹</b></p></a>
<p>背包新增根据背包位置排序，丢弃背包物品(物品堆可以设置对应模型，数量等)，拾取场景物品，设置对应函数拆分超过堆叠上限的物品</p>
<p>瞄准就是设置弹簧臂槽位位置，并用时间轴移动摄像机到该位置；利用发射子弹的目标位置和摄像机射线检测命中位置一致，且发射位置不是摄像机；子弹命中Actor和场景有不同的处理</p>
<p>跟踪爆弹写了个简单的AI，如果没目标就先找目标，找不到则随机巡逻，找到目标后，移动到目标；爆弹本身在目标进入范围内即会跳起来然后自爆造成伤害，也可以被子弹无害摧毁</p>
<br>
<a href="https://www.bilibili.com/video/BV1Jx4y1R7NP"><p>Version 3 [Bilibili连接]<b>基于UI的一对多精确互动(抄原神的)，动画蓝图通知</b></p></a>
<p>当某个物品的可交互范围内进入了玩家，那就将它加入到该玩家的交互UI的列表里，如果角色离开则将它从数组中删除</p>
<p>当玩家通过滚轮选中对应物品时，按下交互捡即可通知交互UI执行相关操作（给予物品，移除该物品的actor，移除该物品在交互UI列表中的存在<b>*</b>）</p>
<p>因为这个功能， Version 2 中实现的拾取逻辑从物品上移动到了玩家身上(按键相同)</p>
<p>通过动画通知，在角色跑步的蓝图中左右脚落地的6个时刻，在脚的位置生成粒子，实现类似“脚印”的功能 (实际上差远了)</p>
<p> [注: <b>*</b> 当物品在世界中的actor被移除时，UE的数组就自动将其删除, 因此这一步是多余的] </p>
<br>
<a href="https://www.bilibili.com/video/BV1hN411z7uD"><p>Version 4 [BiliBili连接]<b>枪械，且能和上述背包系统联动</b></p></a>
<p>枪械类继承自物品类，当其被拾取后，主动禁用掉该枪械的物品类功能即可</p>
<p>枪械有子弹上限，有射击间隔，有装弹时间，有配套UI，能主动换弹，有枪械轨迹</p>
