# 企业应用开发

- 1511483 禚晨晨

- 1511433 李沛昂

- 1511455 王信

- 1511473 张爽

## 需求分析

#### 项目背景

现有一家电子产品(光电码盘)生产商业务量上升, 引发如下问题:

1. 从接受订单到投入生产流程长, 过程中的消息传递困难

2. 基础记录(纸质账本\证明)统计成本高, 但希望能够积累数据, 便于对日后的市场趋势进行预测

3. 接受订单\生产\采购\仓库管理等各项业务流程不够规范统一

4. 对仓库等重要设施监管困难

5. 重要原料的采购不够及时, 或采购过多导致资金流短缺, 或采购过少影响生产

由此引发我们要开发的生产管理系统的系统目标, 我们期望达到这些功能:

#### 系统目标

1. 实现`订单 - 生产计划 - 仓库 - 采购`之间的信息的快速共享. 消除订单在生产计划处的信息积压, 将仓库数据实时共享给生产计划和采购, 缩短缺货响应时间, 减少安全库存的占压资金

2. 仓库\生产等信息的快速统计. 公司在做决策时, 能针对公司目前的物料\产品占用资金的情况快速方便地看到数据, 了解各种物料\产品的成本

3. 规范化公司生产流程. 包括开发部门在内的材料领用, 订单\生产\仓库各方面都有规范的操作记录, 加速从订单到生产的流程, 预防监守自盗现象的发生

#### 主要生产流程

![这里写图片描述](https://img-blog.csdn.net/20180506153009405?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 系统各模块需求分析

我们将系统分为6个模块(浏览信息功能不列出):

- BOM管理: 主要负责产品配方\原料信息管理

- 订单管理: 录入订单, 将订单分解为物料单传递到生产部门和仓库

- 生产管理: 领取物料, 管理物料单

- 仓库管理: 出入库(物料\产品)信息登记, 库存信息统计, 成本统计, 材料报废

- 采购管理: 缺料浏览, 物料报价管理, 供货商管理

- 用户管理: 修改密码, 管理用户, 管理用户组

系统使用过程中, 针对不同的分工, 可以分为以下几个用户组:

- 系统管理员: 可以浏览\修改系统所有数据, 需要该用户负责人对公司完全负责

- 监察员: 可以浏览系统所有数据, 但无法修改数据

- 研发技术员: 可以进行BOM系统管理

- 销售经理: 可以向系统中提交订单

- 仓库管理员: 可以进行仓库信息和采购管理信息的修改

实际过程中系统管理员可以新建用户组, 自由分配权限, 但任何人都不应该有删除系统操作记录的权限.

##### BOM管理模块

- 添加产品类别

- 修改产品类别

- 添加新产品的配方

- 创建某种产品的衍生型号

- 修改产品配方

- 添加原料类别

- 修改原料类别

- 修改原料信息

##### 订单管理模块

- 创建订单

- 将订单分解为物料清单

- 完成订单

- 取消订单

- 延期订单

##### 生产管理模块

- 领料确认

- 对一次性发不齐物料的, 自动判断能生产完成的成品所需的物料数量, 并生成剩余部分的领料单

- 管理领料单

- 折损登记, 针对生产过程中的折损, 重新进行领料

##### 仓库管理模块

- 物料\产品出库管理

- 物料\产品入库管理(采购\生产完成\退货)

- 库存情况统计

- 标记报废材料

- 库存成本统计

##### 采购管理模块

- 快速浏览缺料

- 修改原料供应商

- 修改原料报价

##### 用户管理模块

- 修改密码

- 修改信息

- 添加用户

- 删除用户

- (系统管理员)重置某用户密码

- 修改用户组



## 设计界面

#### 登录窗口

![这里写图片描述](https://img-blog.csdn.net/20180506150724708?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 用户不存在 ->

![这里写图片描述](https://img-blog.csdn.net/20180506150734188?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 密码错误 ->

![这里写图片描述](https://img-blog.csdn.net/20180506150743375?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 正确登录 ->主窗口

#### 主窗口

![这里写图片描述](https://img-blog.csdn.net/20180506150753763?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### BOM管理

##### 产品配方管理

![这里写图片描述](https://img-blog.csdn.net/20180506150907167?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 选择产品条目

![这里写图片描述](https://img-blog.csdn.net/20180506150923236?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 新建种类 ->

![这里写图片描述](https://img-blog.csdn.net/20180506150955197?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 修改种类 ->

![这里写图片描述](https://img-blog.csdn.net/20180506151015512?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 新建产品 ->

![这里写图片描述](https://img-blog.csdn.net/20180506151025766?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 修改配方

![这里写图片描述](https://img-blog.csdn.net/20180506151038146?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 原料管理

![这里写图片描述](https://img-blog.csdn.net/20180506151108601?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 新建种类 -> 略

###### 修改种类 -> 略

###### 新建原料 ->

![这里写图片描述](https://img-blog.csdn.net/20180506151146235?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

###### 修改原料 ->

![这里写图片描述](https://img-blog.csdn.net/20180506151158687?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 订单管理

![这里写图片描述](https://img-blog.csdn.net/20180506151307318?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 生产管理

##### 物料确认

![这里写图片描述](https://img-blog.csdn.net/20180506151318307?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 领料单管理

![这里写图片描述](https://img-blog.csdn.net/20180506151329136?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 仓库管理

![这里写图片描述](https://img-blog.csdn.net/20180506151342776?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 采购辅助

##### 缺料浏览

![这里写图片描述](https://img-blog.csdn.net/20180506151355800?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 报价管理

![这里写图片描述](https://img-blog.csdn.net/20180506151406353?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 供货商管理

![这里写图片描述](https://img-blog.csdn.net/20180506151415994?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 用户管理

##### 修改密码

![这里写图片描述](https://img-blog.csdn.net/20180506151424814?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

##### 用户管理

![这里写图片描述](https://img-blog.csdn.net/20180506151432797?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

## 数据库设计

![这里写图片描述](https://img-blog.csdn.net/2018050615193467?watermark/2/text/aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2FhYWFieg==/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70)

#### 库存内容

用于存储各种原料、成品相关信息，与BOM管理、订单交付紧密关联

- Instock有外键RawMaterialId、ProductId，与RawMaterial、Product相关联

#### BOM管理

用于管理各种产品配方，详细记录了不同产品所需原料，是生产与库存之间的桥梁

- Product有外键ClassId，与ProductClass相关联

- Product对应多个ProductFormulaItem，通过后者的外键ProductId关联

- 与Product类似，RawMaterial有外键ClassId，与MaterialClass关联，同样对应多个ProductFormulaItem，通过后者外键RawMaterialId关联

#### 出入库记录

用于记录库存内容的变动情况，分为出库记录和入库记录，可详细查询物流变动

- StorageRecord与多个StorageRecordItem对应，通过后者外键StorageRecordId关联；同理，OutboundRecord也与多个OutboundRecordItem对应，通过后者外键OutboundRecordId关联

- 多个StorageRecordItem、OutboundRecordItem与RawMaterail或Product关联，根据它们是否为Product判断，即isProduct属性，随后通过外键RawMaterailId或ProductId关联

#### 供应商\报价

用于原料采购时的信息记录，详细记录了不同供应商提供的材料与标价，方便采购

- 多个MaterialSupply对应一个供应商Supplier，通过外键SupplierId关联

- 多个MaterialSupply对应一个Material，通过外键MaterialId关联

#### 用户\用户组

管理使用系统的人员权限

- 每个User对应多条出入库记录StorageRecord、OutboundRecord，通过后者的UserId关联

- 每个User都有自己所属的UserGroup，通过User的ClassId关联

#### 日志记录

记录User的操作，便于日后查找

- 每个记录Log都有其操作人User，通过外键UserId关联

#### 订单\物料单管理

记录订单详情内容，便于BOM管理分解为原料生产等

- 每个Order有多个OrderItem，通过后者OrderId外键关联；每个OrderItem
都有其所对应的产品Product，由外键ProductId关联

- 每个Order还与分解后得出的物料单MaterialList对应，通过后者的OrderId关联；每个MaterialList有多个MaterialListItem，通过后者的MaterialListId关联；每个MaterialListItem都有其对应原料RawMaterial，通过MaterialListItem的外键RawMaterialId关联

## 项目下载

- 项目github下载地址：https://github.com/minexin/blog/raw/master/ERP2.zip


