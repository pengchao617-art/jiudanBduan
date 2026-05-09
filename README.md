[index.html](https://github.com/user-attachments/files/27546148/index.html)
<!DOCTYPE html>
<html lang="zh-CN">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>途家商户端 · 5 Tab 完整原型</title>
<style>
:root{
  --bg:#FAFAF7;--bg-card:#FFFFFF;--bg-soft:#F1EFE8;
  --bg-info:#E6F1FB;--bg-warn:#FAEEDA;--bg-danger:#FCEBEB;--bg-ok:#EAF3DE;
  --text:#1F1F1E;--text-2:#5F5E5A;--text-3:#888780;
  --text-info:#0C447C;--text-warn:#854F0B;--text-danger:#A32D2D;--text-ok:#3B6D11;
  --border:rgba(0,0,0,.12);--border-2:rgba(0,0,0,.18);
}
*{box-sizing:border-box}
body{margin:0;padding:32px 24px;font-family:-apple-system,BlinkMacSystemFont,"PingFang SC","Microsoft YaHei",sans-serif;background:var(--bg);color:var(--text);line-height:1.6;font-size:14px}
.wrap{max-width:1080px;margin:0 auto}
h1{font-size:22px;font-weight:500;margin:0 0 6px}
.sub{color:var(--text-2);font-size:13px;margin-bottom:24px}
.seg-chip{padding:6px 14px;background:var(--bg-card);border:0.5px solid var(--border);border-radius:999px;font-size:13px;color:var(--text-2);cursor:pointer;font-family:inherit}
.seg-chip:hover{border-color:var(--border-2)}
.seg-chip.active{background:var(--text);color:#fff;border-color:var(--text)}
.layout{display:flex;gap:24px;align-items:flex-start;flex-wrap:wrap;margin-top:18px}
.phone-frame{width:340px;height:700px;background:var(--bg-soft);border:0.5px solid var(--border-2);border-radius:28px;padding:8px;flex-shrink:0}
.phone-screen{display:flex;flex-direction:column;height:100%;background:var(--bg-soft);border-radius:22px;overflow:hidden}
.status-bar{flex-shrink:0;height:24px;padding:0 18px;display:flex;align-items:center;justify-content:space-between;font-size:11px;color:var(--text-2)}
.phone-content{flex:1;overflow-y:auto;padding:14px 12px}
.bottom-nav{flex-shrink:0;height:54px;display:flex;border-top:0.5px solid var(--border);background:var(--bg-card)}
.nav-item{flex:1;display:flex;flex-direction:column;align-items:center;justify-content:center;font-size:11px;color:var(--text-3);gap:3px;cursor:pointer;background:none;border:none;font-family:inherit;padding:0}
.nav-item.active{color:var(--text)}
.nav-icon{width:18px;height:18px;border-radius:4px;background:var(--bg-soft)}
.nav-item.active .nav-icon{background:var(--text)}
.ph-card{background:var(--bg-card);border:0.5px solid var(--border);border-radius:8px;padding:12px;margin-bottom:10px}
.ph-title{font-size:12px;font-weight:500;margin:0 0 8px;color:var(--text-2)}
.ph-row{display:flex;justify-content:space-between;align-items:center;padding:11px 0;font-size:12px;border-top:0.5px solid var(--border)}
.list-card{background:var(--bg-card);border:0.5px solid var(--border);border-radius:8px;padding:10px;margin-bottom:8px;display:flex;gap:10px;align-items:center}
.thumb{width:48px;height:48px;border-radius:6px;background:var(--bg-soft);flex-shrink:0;display:flex;align-items:center;justify-content:center;color:var(--text-3);font-size:11px}
.badge{display:inline-block;padding:1px 6px;border-radius:4px;font-size:10px;font-weight:500;line-height:1.4}
.b-ok{background:var(--bg-ok);color:var(--text-ok)}
.b-warn{background:var(--bg-warn);color:var(--text-warn)}
.b-danger{background:var(--bg-danger);color:var(--text-danger)}
.b-info{background:var(--bg-info);color:var(--text-info)}
.b-mute{background:var(--bg-soft);color:var(--text-3)}
.chamber-tab{flex:1;text-align:center;padding:8px 0;font-size:12px;color:var(--text-2);cursor:pointer;border-bottom:2px solid transparent;background:none;border-left:none;border-right:none;border-top:none;font-family:inherit}
.chamber-tab.active{color:var(--text);border-bottom-color:var(--text);font-weight:500}
.notes{flex:1;min-width:280px;font-size:13px;line-height:1.75}
.note-block{margin-bottom:14px;padding-left:12px;border-left:2px solid var(--border)}
.note-label{font-weight:500;font-size:13px;margin-bottom:3px}
.note-text{color:var(--text-2);font-size:12px;line-height:1.65}
.avatar-circle{width:48px;height:48px;border-radius:50%;background:var(--bg-info);color:var(--text-info);display:flex;align-items:center;justify-content:center;font-weight:500;font-size:18px;flex-shrink:0}
</style>
</head>
<body>
<div class="wrap">
<h1>途家商户端 · 5 Tab 完整原型</h1>
<div class="sub">点击顶部分层 chip + 底部导航，切换 4 类商户 × 5 个 Tab = 20 个屏</div>
<div id="seg-tabs" style="display:flex;gap:8px;flex-wrap:wrap">
  <button class="seg-chip active" data-seg="single">单房房东</button>
  <button class="seg-chip" data-seg="multi">多房房东</button>
  <button class="seg-chip" data-seg="managed">托管子账号</button>
  <button class="seg-chip" data-seg="chain">连锁店长</button>
</div>
<div class="layout">
  <div class="phone-frame">
    <div class="phone-screen">
      <div class="status-bar"><span>9:41</span><span id="ph-tabname">工作台</span><span>5G</span></div>
      <div id="phone-content" class="phone-content"></div>
      <div class="bottom-nav">
        <button class="nav-item active" data-tab="workbench"><div class="nav-icon"></div><span>工作台</span></button>
        <button class="nav-item" data-tab="listing"><div class="nav-icon"></div><span>房源</span></button>
        <button class="nav-item" data-tab="order"><div class="nav-icon"></div><span>订单</span></button>
        <button class="nav-item" data-tab="message"><div class="nav-icon"></div><span>消息</span></button>
        <button class="nav-item" data-tab="me"><div class="nav-icon"></div><span>我的</span></button>
      </div>
    </div>
  </div>
  <div id="seg-notes" class="notes"></div>
</div>
</div>

<script>
const VIEWS = {
  single:{
    workbench:{type:'wb',greeting:'鲁迪，新手主线 3 / 5',chip:'单房 · 新手',primary:{type:'onboarding',progress:60,nextStep:'设置首晚价格',reward:'完成可解锁首单立减权益'},todo:[{u:1,t:'设置首晚价格 — 阻塞房源对外可见'},{u:0,t:'完善房间照片，建议至少 5 张'},{u:0,t:'确认收款账户'}],modules:[{n:'我的房源',c:'1 间在管'},{n:'客户消息',c:'0 条未读'}],hint:'高级模块在首单成交后逐步解锁'},
    listing:{type:'listing',title:'我的房源（1）',items:[{name:'瀚海蓝湾 105',sub:'整套 · 1 室',badge:'待完善',badgeType:'warn',meta:'价格未设 · 照片仅 2 张'}],footer:'+ 添加更多房源（完成新手主线后开放）',hint:'点击进入「房源生命周期视图」：基础信息 / 价格 / 数据 / 评价 一屏管理'},
    order:{type:'order',title:'我的订单',empty:'等待第一位客人入住',emptyHint:'首单到来时 App 会强提醒并附沟通话术',hint:'订单详情可一键直达：客人 IM、清洁工单、对账'},
    message:{type:'message',default:1,chambers:[{key:'cust',name:'客户消息',count:0,empty:'还没有客人消息'},{key:'noti',name:'平台通知',count:1,items:[{ic:'通',title:'新手任务提醒',preview:'完成首晚价格设置即可解锁首单立减权益',time:'今天'}]},{key:'todo',name:'系统待办',count:3,items:[{ic:'急',title:'设置首晚价格',preview:'阻塞房源对外可见',time:'今天',urgent:true},{ic:'·',title:'完善房间照片',preview:'建议至少 5 张',time:'今天'},{ic:'·',title:'确认收款账户',preview:'首单到账前必须',time:'今天'}]}],hint:'消息中心三舱合一，IM / 通知 / 待办 不再散在各处'},
    me:{type:'me',avatar:'鲁',name:'鲁迪',chip:'单房 · 新手',sub:'手机 138****0000',groups:[[{n:'我的房源',c:'1 间'},{n:'我的订单',c:'0 单'},{n:'我的钱包',c:'未绑定收款',warn:true}],[{n:'帮助中心',c:''},{n:'设置',c:''}]],hint:'收款设置 / 经营报表 / 子账号 等模块隐藏，避免新手负担'}
  },
  multi:{
    workbench:{type:'wb',greeting:'鲁迪，今日 8 间在管',chip:'多房 · 在管 8 间',primary:{type:'metrics',items:[{l:'今日入住率',v:'75%',t:'+5%'},{l:'待处理订单',v:'3',danger:true},{l:'待回复消息',v:'5'},{l:'7 日空房',v:'2 间'}]},todo:[{u:1,t:'3 笔订单待确认（点击直达订单 Tab）'},{u:0,t:'瀚海蓝湾 105 — 智能定价建议涨 12%'},{u:0,t:'5 位客人 30 分钟未回复'}],modules:[{n:'智能定价',c:'今日 2 条建议'},{n:'经营报表',c:'本月 GMV ¥48k'},{n:'房态日历',c:'未来 30 日'},{n:'客户消息',c:'5 条未读'}],hint:'工作台默认呈现经营仪表盘 + 待办流'},
    listing:{type:'listing',title:'房源管理（8）',filters:['全部 8','在售 6','暂停 1','异常 1'],items:[{name:'瀚海蓝湾 105',sub:'整套 · 2 室',badge:'在售',badgeType:'ok',meta:'本月入住率 82% · ¥468 / 晚'},{name:'海岸花园 203',sub:'整套 · 1 室',badge:'空 7 日',badgeType:'warn',meta:'建议调价 -8% · 智能定价已提示'},{name:'西湖印象 12',sub:'整套 · 3 室',badge:'异常',badgeType:'danger',meta:'门锁离线 3 小时 · 需联系工程'}],hint:'点击进入「生命周期视图」= 上房 + 定价 + 数据 + 评价 一屏整合，避免跨模块跳转'},
    order:{type:'order',title:'订单',filters:['待确认 3','进行中 5','已完成'],items:[{tag:'急',tagType:'danger',title:'李** · 入住 5/10',sub:'瀚海蓝湾 105 · 2 晚 · ¥936',meta:'30 分钟内不确认将自动取消',btn:'立即确认'},{tag:'新',tagType:'info',title:'王** · 入住 5/12',sub:'海岸花园 203 · 3 晚 · ¥1,254',meta:'5 分钟前下单',btn:'确认'},{tag:'新',tagType:'info',title:'陈** · 入住 5/15',sub:'西湖印象 12 · 4 晚 · ¥2,400',meta:'17 分钟前下单',btn:'确认'}],hint:'订单详情可一键打开客人 IM、跳转对应房源、生成清洁工单'},
    message:{type:'message',default:0,chambers:[{key:'cust',name:'客户消息',count:5,items:[{ic:'李',title:'李女士',preview:'请问可以提前 1 小时入住吗？',time:'15 分钟前',unread:true},{ic:'王',title:'王先生',preview:'好的，谢谢！',time:'1 小时前'},{ic:'陈',title:'陈先生',preview:'有停车位吗',time:'2 小时前',unread:true}]},{key:'noti',name:'平台通知',count:3,items:[{ic:'通',title:'平台新规上线',preview:'5/15 起，差评申诉流程优化',time:'今天'},{ic:'通',title:'劳动节运营建议',preview:'建议价格上调 15-20%',time:'昨天'}]},{key:'todo',name:'系统待办',count:8,items:[{ic:'急',title:'3 笔订单待确认',preview:'最早 5 分钟前',time:'今天',urgent:true},{ic:'·',title:'瀚海蓝湾 105 — 调价建议',preview:'+12%',time:'今天'}]}],hint:'IM 与系统通知合并入口但分舱内化，未读小红点逻辑统一'},
    me:{type:'me',avatar:'鲁',name:'鲁迪',chip:'多房 · 在管 8 间',sub:'手机 138****0000',groups:[[{n:'我的房源',c:'8 间'},{n:'经营报表',c:'本月 ¥48k'},{n:'我的钱包',c:'已绑定'},{n:'收款设置',c:''}],[{n:'升级为托管',c:'解锁子账号',hl:true},{n:'帮助中心',c:''},{n:'设置',c:''}]],hint:'子账号管理入口对多房房东仅作引导展示，启用需走人工申请'}
  },
  managed:{
    workbench:{type:'wb',greeting:'客服小李，授权 28 间',chip:'客服 · 子账号',primary:{type:'role',role:'客服角色',scope:'28 间房 · 3 个房东',manager:'主账号：链家托管 · 权限由 PC 端配置'},todo:[{u:1,t:'8 条客人消息待回复（仅授权范围）'},{u:0,t:'2 笔订单待客服确认'},{u:0,t:'操作日志：本周 16 次操作可查阅'}],modules:[{n:'客户消息',c:'8 条未读'},{n:'订单管理',c:'授权 28 间'},{n:'操作日志',c:'可查阅本人记录'}],hint:'经营报表 / 子账号管理 / 收款 等模块对客服角色完全不可见'},
    listing:{type:'listing',title:'授权房源（28）',filters:['全部 28','房东 A 12','房东 B 10','房东 C 6'],items:[{name:'瀚海蓝湾 105',sub:'房东：张** · 整套 · 2 室',badge:'只读',badgeType:'mute',meta:'客服角色仅可查看 / 不可编辑'},{name:'瀚海蓝湾 108',sub:'房东：张** · 整套 · 1 室',badge:'只读',badgeType:'mute',meta:'本月入住率 78%'},{name:'城市花园 305',sub:'房东：李** · 整套 · 3 室',badge:'只读',badgeType:'mute',meta:'本月入住率 65%'}],hint:'每张卡显示房东归属。客服编辑房源信息需联系运营角色'},
    order:{type:'order',title:'订单（授权 28 间）',filters:['待确认 2','待回复 8','已处理'],items:[{tag:'急',tagType:'danger',title:'刘** · 入住 5/10',sub:'瀚海蓝湾 105 · 房东：张**',meta:'客户咨询特殊需求 · 30 分钟未回复',btn:'确认 + 回复'},{tag:'·',tagType:'mute',title:'赵** · 入住 5/11',sub:'瀚海蓝湾 108 · 房东：张**',meta:'已自动确认',btn:'查看'}],hint:'授权范围外订单完全不展示（含汇总数据）。订单确认后系统自动落操作日志'},
    message:{type:'message',default:0,chambers:[{key:'cust',name:'客户消息',count:8,items:[{ic:'刘',title:'刘女士 · 瀚海 105',preview:'能不能加一张床？',time:'15 分钟前',unread:true},{ic:'赵',title:'赵先生 · 城市 305',preview:'位置怎么走',time:'30 分钟前',unread:true},{ic:'孙',title:'孙女士 · 瀚海 108',preview:'好的谢谢',time:'1 小时前'}]},{key:'noti',name:'内部通知',count:2,items:[{ic:'主',title:'主账号通知',preview:'本周客服话术规范更新，请查看',time:'今天'}]},{key:'todo',name:'系统待办',count:8,items:[{ic:'急',title:'8 条客人消息待回复',preview:'最早 30 分钟前',time:'今天',urgent:true}]}],hint:'客服仅看授权房源的客人消息；超出授权的客人完全不可见'},
    me:{type:'me',avatar:'李',name:'客服小李',chip:'客服 · 子账号',sub:'主账号：链家托管',groups:[[{n:'我的资料',c:''},{n:'切换账号',c:'多账号支持'},{n:'操作日志',c:'本周 16 次'}],[{n:'帮助中心',c:''},{n:'设置',c:''}]],hint:'我的钱包 / 收款设置 / 子账号管理 等模块对客服完全不可见，由 RBAC 拦截器在 API 层过滤'}
  },
  chain:{
    workbench:{type:'wb',greeting:'外滩店 · 店长视角',chip:'店长 · 上海外滩店',primary:{type:'switcher',current:'上海外滩店（24 间）',peers:'全部 8 个门店',alerts:1},todo:[{u:1,t:'外滩店 9 月入住率低于品牌均值 8%'},{u:0,t:'总部已下发 3 条调价指令，待执行'},{u:0,t:'连锁标准 SOP 月度核查'}],modules:[{n:'本店报表',c:'本月 GMV ¥186k'},{n:'跨店对比',c:'8 店矩阵'},{n:'批量操作',c:'推荐 PC 端'},{n:'API 配置',c:'PMS 已对接'}],hint:'总部矩阵看板放在 PC 端，App 不冗余复制'},
    listing:{type:'listing',title:'外滩店房源（24）',storeBar:'当前门店：上海外滩店',filters:['全部 24','3 楼 8','4 楼 8','5 楼 8'],items:[{name:'301 · 海景大床',sub:'25㎡ · 海景房',badge:'在住',badgeType:'info',meta:'本月入住率 88% · ¥780 / 晚'},{name:'302 · 海景双床',sub:'28㎡ · 海景房',badge:'空 2 日',badgeType:'warn',meta:'品牌建议价 ¥820'},{name:'305 · 行政套房',sub:'45㎡ · 套房',badge:'在住',badgeType:'ok',meta:'本月入住率 92%'}],hint:'切换门店后房源列表随上下文过滤；跨店批量操作请用 PC 端'},
    order:{type:'order',title:'外滩店订单（本月 78）',storeBar:'当前门店：上海外滩店',filters:['待确认 5','进行中 12','已完成'],items:[{tag:'指',tagType:'info',title:'总部下发：5/1 调价指令',sub:'外滩店全部房源 · +15%',meta:'劳动节统一调价，请确认',btn:'批量执行'},{tag:'急',tagType:'danger',title:'周** · 入住 5/10',sub:'302 房 · 2 晚',meta:'VIP 会员 · 总部要求 30 分内确认',btn:'立即确认'}],hint:'总部下发指令以特殊样式区分，与普通订单不混用'},
    message:{type:'message',default:1,chambers:[{key:'cust',name:'客户消息',count:6,items:[{ic:'周',title:'周先生 · 302 房',preview:'希望升级海景房',time:'10 分钟前',unread:true},{ic:'吴',title:'吴女士 · 305 房',preview:'已收到房卡，谢谢',time:'1 小时前'}]},{key:'noti',name:'品牌 / 总部',count:4,items:[{ic:'部',title:'总部 · 5/1 调价指令',preview:'外滩店执行 +15%',time:'今天',urgent:true},{ic:'部',title:'品牌 · 月度 SOP 核查',preview:'5 月 15 日完成',time:'今天'}]},{key:'todo',name:'系统待办',count:5,items:[{ic:'急',title:'外滩店入住率低于品牌均值',preview:'9 月数据',time:'今天',urgent:true}]}],hint:'通知舱中"总部 / 品牌"消息单独区分，便于店长优先响应连锁指令'},
    me:{type:'me',avatar:'店',name:'外滩店 · 店长',chip:'店长 · 单门店权限',sub:'品牌：链家精品 · 主账号：总部',groups:[[{n:'当前门店信息',c:'上海外滩店'},{n:'切换门店',c:'8 店可选'},{n:'本店报表',c:'PC 端深度分析'}],[{n:'我的资料',c:''},{n:'帮助中心',c:''},{n:'设置',c:''}]],hint:'子账号管理 / API 配置 / 跨店聚合 集中在 PC 端，App 端不冗余'}
  }
};

const NOTES={workbench:{single:[{l:'任务驱动 · 不堆指标',t:'首屏只露 3 件事：主线进度 + 待办 + 常用入口'},{l:'减法原则',t:'数据看板、智能定价、经营报表 在工作台不出现'},{l:'解锁机制',t:'由平台层「商户档案 + 生命周期」服务输出当前应露出的模块清单'}],multi:[{l:'经营仪表盘锚定',t:'4 个数据卡片是首屏锚点'},{l:'待办流去重',t:'同一信号在仪表盘和待办流中只表达一次'},{l:'模块入口前置',t:'智能定价 / 经营报表 / 房态 直接挂在工作台二级'}],managed:[{l:'角色识别置顶',t:'让子账号始终知道自己的边界'},{l:'数据脱敏',t:'不在授权范围内的数据完全不展示，包括汇总指标'},{l:'缺席模块',t:'经营报表、子账号管理对客服不可见'}],chain:[{l:'门店切换器置顶',t:'切换门店后所有内容都按门店上下文过滤'},{l:'异常预警强提示',t:'跨店指标低于品牌均值时首屏 danger 卡片'},{l:'总部 vs 店长分工',t:'店长视角只看本店；矩阵看板放 PC'}]},listing:{single:[{l:'一房一卡 · 强引导',t:'未完善状态用 warn 徽章 + 缺失项明示'},{l:'入口克制',t:'只能添加 1 间，主线完成后才开放第二间'},{l:'生命周期视图',t:'详情页一屏看全：基础信息 / 价格 / 数据 / 评价'}],multi:[{l:'状态徽章统一',t:'在售 / 暂停 / 异常 / 空 N 日 用一致颜色语义'},{l:'筛选 chip 必备',t:'8 间以上必有筛选'},{l:'整合避免跳转',t:'房源 = 上房 + 定价 + 数据 + 评价 的统一容器'}],managed:[{l:'房东归属显式',t:'每张卡明示「房东：X」便于客服心智'},{l:'编辑权限隔离',t:'客服只读；用「只读」徽章而非完全隐藏'},{l:'按房东筛选',t:'筛选 chip 直接按房东分组'}],chain:[{l:'门店上下文常驻',t:'顶部 storeBar 提示当前门店'},{l:'楼层筛选',t:'连锁场景按物理结构筛选比按状态高频'},{l:'品牌建议价显式',t:'连锁价格由总部指导，建议价在房源卡显示'}]},order:{single:[{l:'空态强引导',t:'0 单时不展示空表格而是引导文案 + 等待感设计'},{l:'首单仪式感',t:'首单到来触发全屏强提醒 + 沟通话术'},{l:'订单详情聚合',t:'打开订单 = 客人 IM / 房源 / 清洁工单 三处入口'}],multi:[{l:'紧急订单置顶',t:'30 分钟自动取消的订单用 danger tag + 倒计时'},{l:'快捷动作内嵌',t:'卡片直接「立即确认」按钮，不需进详情'},{l:'状态 chip 同步工作台',t:'工作台"待处理 3"点击直达"待确认 3"'}],managed:[{l:'授权强约束',t:'授权外订单完全不出现，包括统计数字'},{l:'客服动作受限',t:'确认 + 回复 OK，改价 / 退订 不可'},{l:'操作落日志',t:'每次确认订单自动落 audit_log'}],chain:[{l:'总部指令优先级',t:'总部下发的批量指令用特殊 tag「指」+ 蓝色'},{l:'VIP / 品牌客标注',t:'品牌客户优先级高 · 显式标注'},{l:'跨店操作回 PC',t:'跨店批量操作 App 引导回 PC'}]},message:{single:[{l:'三舱合一',t:'IM / 通知 / 待办 在同一个 Tab 内分舱'},{l:'引导期默认舱',t:'单房新手默认打开「平台通知」'},{l:'红点统一',t:'消息 Tab 红点 = 三舱未读总和'}],multi:[{l:'客人消息默认',t:'多房日常 IM > 通知 > 待办，默认打开 IM'},{l:'消息预览裁剪',t:'30 字以内多行截断'},{l:'未读分舱统计',t:'每舱独立未读，便于商户判断优先级'}],managed:[{l:'授权过滤',t:'IM 仅显示授权房源的客人 · 越权完全不可见'},{l:'内部通知舱',t:'托管场景下「通知」改为「内部通知」'},{l:'操作日志关联',t:'部分待办点击直接打开操作日志页'}],chain:[{l:'总部 / 品牌单独标',t:'通知舱总部消息用 ic「部」+ 加粗'},{l:'门店上下文过滤',t:'切换门店后客人消息列表跟着过滤'},{l:'指令型消息',t:'总部调价 / SOP 检查 附带快捷执行按钮'}]},me:{single:[{l:'功能克制',t:'只露房源 / 订单 / 钱包；高级功能完全不出现'},{l:'钱包未绑定提醒',t:'未绑定收款用 warn 色'},{l:'退路简单',t:'帮助中心 + 设置即可'}],multi:[{l:'升级提示',t:'多房房东天然有"扩张"诉求，「升级为托管」长期引导'},{l:'收款设置独立',t:'多房收款复杂，作为一级菜单'},{l:'子账号引导态',t:'子账号入口可见但需人工申请'}],managed:[{l:'多账号支持',t:'子账号常需在多个主账号间切换'},{l:'操作日志高频',t:'操作日志在客服自查时高频使用'},{l:'功能彻底缺席',t:'钱包 / 收款 / 子账号管理 完全不出现，不灰显'}],chain:[{l:'门店信息常驻',t:'店长每天关心本门店运营状态'},{l:'切换门店入口冗余',t:'me 页也提供切换入口便于任何位置切换'},{l:'高级功能去 PC',t:'子账号、API、跨店聚合 集中在 PC'}]}};

let curSeg='single',curTab='workbench',curChamber=null;
function tagBadge(text,type){return `<span class="badge b-${type}">${text}</span>`;}
function renderWB(v){
  let topHTML='';
  if(v.primary.type==='onboarding'){
    topHTML=`<div class="ph-card" style="background:var(--bg-info);border-color:rgba(12,68,124,.2)"><div style="display:flex;justify-content:space-between;font-size:11px;color:var(--text-info);margin-bottom:6px"><span>新手主线</span><span>${v.primary.progress}%</span></div><div style="height:4px;background:rgba(0,0,0,0.06);border-radius:2px;overflow:hidden;margin-bottom:10px"><div style="height:100%;width:${v.primary.progress}%;background:var(--text-info)"></div></div><div style="font-size:13px;font-weight:500;color:var(--text-info);margin-bottom:3px">下一步：${v.primary.nextStep}</div><div style="font-size:11px;color:var(--text-info)">${v.primary.reward}</div></div>`;
  } else if(v.primary.type==='metrics'){
    topHTML=`<div class="ph-card"><div class="ph-title">今日经营</div><div style="display:grid;grid-template-columns:1fr 1fr;gap:8px">${v.primary.items.map(m=>`<div style="background:var(--bg-soft);border-radius:8px;padding:10px"><div style="font-size:11px;color:var(--text-2);margin-bottom:2px">${m.l}</div><div style="font-size:18px;font-weight:500;${m.danger?'color:var(--text-danger);':''}">${m.v}${m.t?` <span style="font-size:11px;color:var(--text-2);font-weight:400">${m.t}</span>`:''}</div></div>`).join('')}</div></div>`;
  } else if(v.primary.type==='role'){
    topHTML=`<div class="ph-card" style="background:var(--bg-warn);border-color:rgba(133,79,11,.2)"><div style="font-size:11px;color:var(--text-warn);margin-bottom:6px">当前角色</div><div style="font-size:14px;font-weight:500;color:var(--text-warn);margin-bottom:4px">${v.primary.role} · ${v.primary.scope}</div><div style="font-size:11px;color:var(--text-warn);line-height:1.5">${v.primary.manager}</div></div>`;
  } else if(v.primary.type==='switcher'){
    topHTML=`<div class="ph-card" style="display:flex;justify-content:space-between;align-items:center"><div><div style="font-size:11px;color:var(--text-2);margin-bottom:2px">门店切换</div><div style="font-size:13px;font-weight:500">${v.primary.current}</div></div><div style="font-size:11px;color:var(--text-info)">${v.primary.peers} ↓</div></div>${v.primary.alerts?`<div class="ph-card" style="background:var(--bg-danger);border-color:rgba(163,45,45,.2);padding:10px 12px"><div style="font-size:12px;color:var(--text-danger);font-weight:500">${v.primary.alerts} 个门店指标异常，需关注</div></div>`:''}`;
  }
  const greeting=`<div style="margin-bottom:12px"><div style="font-size:16px;font-weight:500;line-height:1.3">${v.greeting}</div><div style="display:inline-block;margin-top:6px;padding:2px 8px;background:var(--bg-card);border:0.5px solid var(--border);border-radius:999px;font-size:11px;color:var(--text-2)">${v.chip}</div></div>`;
  const todo=`<div class="ph-card"><div class="ph-title">今日待办</div>${v.todo.map((t,i)=>`<div style="display:flex;gap:10px;align-items:flex-start;padding:8px 0;${i>0?'border-top:0.5px solid var(--border);':''}font-size:12px;line-height:1.5"><div style="width:6px;height:6px;border-radius:50%;flex-shrink:0;margin-top:7px;background:${t.u?'var(--text-danger)':'var(--text-3)'}"></div><div style="flex:1">${t.t}</div></div>`).join('')}</div>`;
  const mods=`<div class="ph-card"><div class="ph-title">常用模块</div>${v.modules.map((m,i)=>`<div class="ph-row" style="${i===0?'border-top:none;padding-top:0':''}"><span style="font-weight:500">${m.n}</span><span style="color:var(--text-2);font-size:11px">${m.c} ›</span></div>`).join('')}</div>`;
  const hint=`<div style="font-size:11px;color:var(--text-3);padding:8px 4px;line-height:1.6">${v.hint}</div>`;
  return greeting+topHTML+todo+mods+hint;
}
function renderListing(v){
  const head=`<div style="margin-bottom:12px"><div style="font-size:16px;font-weight:500">${v.title}</div></div>`;
  const storeBar=v.storeBar?`<div class="ph-card" style="padding:8px 12px;display:flex;justify-content:space-between;align-items:center;font-size:12px;margin-bottom:10px"><span style="color:var(--text-2)">${v.storeBar}</span><span style="color:var(--text-info)">切换 ›</span></div>`:'';
  const filters=v.filters?`<div style="display:flex;gap:8px;overflow-x:auto;margin-bottom:10px;padding-bottom:2px">${v.filters.map((f,i)=>`<span class="badge ${i===0?'b-info':'b-mute'}" style="white-space:nowrap;padding:4px 10px;font-size:11px">${f}</span>`).join('')}</div>`:'';
  const items=v.items.map(it=>`<div class="list-card"><div class="thumb">房</div><div style="flex:1;min-width:0"><div style="display:flex;justify-content:space-between;align-items:center;gap:6px;margin-bottom:3px"><div style="font-size:13px;font-weight:500;overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${it.name}</div>${tagBadge(it.badge,it.badgeType)}</div><div style="font-size:11px;color:var(--text-2);margin-bottom:3px">${it.sub}</div><div style="font-size:11px;color:var(--text-3)">${it.meta}</div></div></div>`).join('');
  const footer=v.footer?`<div style="text-align:center;padding:10px 0;font-size:12px;color:var(--text-3)">${v.footer}</div>`:'';
  const hint=`<div style="font-size:11px;color:var(--text-3);padding:8px 4px;line-height:1.6">${v.hint}</div>`;
  return head+storeBar+filters+items+footer+hint;
}
function renderOrder(v){
  const head=`<div style="margin-bottom:12px"><div style="font-size:16px;font-weight:500">${v.title}</div></div>`;
  const storeBar=v.storeBar?`<div class="ph-card" style="padding:8px 12px;display:flex;justify-content:space-between;align-items:center;font-size:12px;margin-bottom:10px"><span style="color:var(--text-2)">${v.storeBar}</span><span style="color:var(--text-info)">切换 ›</span></div>`:'';
  const filters=v.filters?`<div style="display:flex;gap:8px;overflow-x:auto;margin-bottom:10px;padding-bottom:2px">${v.filters.map((f,i)=>`<span class="badge ${i===0?'b-info':'b-mute'}" style="white-space:nowrap;padding:4px 10px;font-size:11px">${f}</span>`).join('')}</div>`:'';
  if(v.empty){
    return head+`<div class="ph-card" style="padding:30px 16px;text-align:center"><div style="font-size:14px;font-weight:500;margin-bottom:6px">${v.empty}</div><div style="font-size:11px;color:var(--text-2);line-height:1.6">${v.emptyHint}</div></div>`+`<div style="font-size:11px;color:var(--text-3);padding:8px 4px;line-height:1.6">${v.hint}</div>`;
  }
  const items=v.items.map(it=>`<div class="ph-card"><div style="display:flex;align-items:center;gap:8px;margin-bottom:6px">${tagBadge(it.tag,it.tagType)}<div style="font-size:13px;font-weight:500;flex:1">${it.title}</div></div><div style="font-size:11px;color:var(--text-2);margin-bottom:6px">${it.sub}</div><div style="display:flex;justify-content:space-between;align-items:center"><div style="font-size:11px;color:${it.tagType==='danger'?'var(--text-danger)':'var(--text-3)'}">${it.meta}</div><button style="padding:5px 12px;border:0.5px solid var(--border-2);border-radius:6px;background:var(--bg-card);font-size:11px;font-family:inherit;cursor:pointer">${it.btn}</button></div></div>`).join('');
  const hint=`<div style="font-size:11px;color:var(--text-3);padding:8px 4px;line-height:1.6">${v.hint}</div>`;
  return head+storeBar+filters+items+hint;
}
function renderMessage(v){
  if(curChamber===null) curChamber=v.default;
  const tabs=`<div class="ph-card" style="padding:0;display:flex;margin-bottom:10px">${v.chambers.map((c,i)=>`<button class="chamber-tab ${i===curChamber?'active':''}" data-ch="${i}">${c.name}${c.count?` <span style="font-size:10px;color:var(--text-2)">(${c.count})</span>`:''}</button>`).join('')}</div>`;
  const ch=v.chambers[curChamber];
  let content='';
  if(ch.empty){
    content=`<div class="ph-card" style="padding:30px 16px;text-align:center"><div style="font-size:13px;color:var(--text-2)">${ch.empty}</div></div>`;
  } else {
    content=`<div class="ph-card" style="padding:0">${ch.items.map((it,i)=>`<div style="display:flex;gap:10px;padding:12px;${i>0?'border-top:0.5px solid var(--border);':''}"><div class="avatar-circle" style="width:36px;height:36px;font-size:13px;${it.urgent?'background:var(--bg-danger);color:var(--text-danger);':''}">${it.ic}</div><div style="flex:1;min-width:0"><div style="display:flex;justify-content:space-between;align-items:center;margin-bottom:2px"><div style="font-size:12px;font-weight:500">${it.title}${it.unread?'<span style="display:inline-block;width:6px;height:6px;border-radius:50%;background:var(--text-danger);margin-left:6px;vertical-align:middle"></span>':''}</div><div style="font-size:10px;color:var(--text-3)">${it.time}</div></div><div style="font-size:11px;color:var(--text-2);overflow:hidden;text-overflow:ellipsis;white-space:nowrap">${it.preview}</div></div></div>`).join('')}</div>`;
  }
  const hint=`<div style="font-size:11px;color:var(--text-3);padding:8px 4px;line-height:1.6">${v.hint}</div>`;
  return `<div style="margin-bottom:12px"><div style="font-size:16px;font-weight:500">消息</div></div>`+tabs+content+hint;
}
function renderMe(v){
  const head=`<div class="ph-card" style="display:flex;align-items:center;gap:12px;padding:14px"><div class="avatar-circle">${v.avatar}</div><div style="flex:1"><div style="font-size:15px;font-weight:500">${v.name}</div><div style="font-size:11px;color:var(--text-2);margin-top:2px">${v.sub}</div><div style="display:inline-block;margin-top:4px;padding:2px 8px;background:var(--bg-soft);border-radius:999px;font-size:10px;color:var(--text-2)">${v.chip}</div></div></div>`;
  const groups=v.groups.map(g=>`<div class="ph-card" style="padding:0 12px">${g.map((it,i)=>`<div class="ph-row" style="${i===0?'border-top:none;':''}"><span style="font-weight:500;${it.hl?'color:var(--text-info);':''}">${it.n}</span><span style="color:${it.warn?'var(--text-warn)':'var(--text-2)'};font-size:11px">${it.c} ›</span></div>`).join('')}</div>`).join('');
  const hint=`<div style="font-size:11px;color:var(--text-3);padding:8px 4px;line-height:1.6">${v.hint}</div>`;
  return head+groups+hint;
}
function renderNotes(){
  const tn={workbench:'工作台',listing:'房源',order:'订单',message:'消息',me:'我的'};
  const sn={single:'单房房东',multi:'多房房东',managed:'托管子账号（客服）',chain:'连锁店长'};
  const list=NOTES[curTab][curSeg];
  return `<div style="font-size:14px;font-weight:500;margin-bottom:14px">${sn[curSeg]} · ${tn[curTab]} Tab 设计要点</div>`+list.map(n=>`<div class="note-block"><div class="note-label">${n.l}</div><div class="note-text">${n.t}</div></div>`).join('');
}
function render(){
  const v=VIEWS[curSeg][curTab];
  const tn={workbench:'工作台',listing:'房源',order:'订单',message:'消息',me:'我的'};
  document.getElementById('ph-tabname').textContent=tn[curTab];
  let html='';
  if(v.type==='wb') html=renderWB(v);
  else if(v.type==='listing') html=renderListing(v);
  else if(v.type==='order') html=renderOrder(v);
  else if(v.type==='message') html=renderMessage(v);
  else if(v.type==='me') html=renderMe(v);
  document.getElementById('phone-content').innerHTML=html;
  document.getElementById('seg-notes').innerHTML=renderNotes();
  if(curTab==='message'){
    document.querySelectorAll('.chamber-tab').forEach(b=>b.addEventListener('click',()=>{curChamber=parseInt(b.dataset.ch);render();}));
  }
}
document.querySelectorAll('.seg-chip').forEach(b=>{b.addEventListener('click',()=>{document.querySelectorAll('.seg-chip').forEach(x=>x.classList.remove('active'));b.classList.add('active');curSeg=b.dataset.seg;curChamber=null;render();});});
document.querySelectorAll('.nav-item').forEach(b=>{b.addEventListener('click',()=>{document.querySelectorAll('.nav-item').forEach(x=>x.classList.remove('active'));b.classList.add('active');curTab=b.dataset.tab;curChamber=null;render();});});
render();
</script>
</body>
</html>
