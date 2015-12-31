# 分布式任务调度框架xxl-job
github地址：https://github.com/xuxueli/xxl-job

git.osc地址：http://git.oschina.net/xuxueli0323/xxl-job

博客地址(内附使用教程)：http://www.cnblogs.com/xuxueli/p/5021979.html
	
# 特点：基于quartz封装实现的的集群任务调度管理平台
	1、简单：支持通过Web页面对任务进行CRUD操作，操作简单，一分钟上手；
	2、动态：支持动态修改任务状态，动态暂停/恢复任务，即时生效；
	3、服务HA：任务信息持久化到mysql中，Job服务天然支持集群，保证服务HA；
	4、任务HA：某台Job服务挂掉，任务会平滑分配给其他的某一台存活服务，即使所有服务挂掉，重启时或补偿执行丢失任务；
	5、一个任务只会在其中一台服务器上执行；
	6、任务串行执行；
	7、支持任务执行日志；
	8、支持自定义参数；

# 新版本 V1.2.x ：架构模块化		【开发中...】
	说明：V1.2版本将系统架构按功能拆分为：
		调度模块[xxl-job-admin]：负责管理调度信息，按照调度配置发出调度请求；
		任务模块[xxl-job-client-demo]：负责接收调度请求并执行任务逻辑；任务模块可以方便的嵌入web项目，可以参考此demo；
		通讯模块[xxl-job-client]：负责调度模块和任务模块之间的信息通讯；
	优点：
		解耦：任务模块提供任务接口，调度模块维护调度信息，业务相互独立；
		高扩展性；
		稳定性；
		
	Tips：如果您追求一个简单调度服务，这里也提供了一个简洁分支[xxl-job-simple]，它针对旧版调度框架做了细微完善；
	
# 其他说明
	清楚僵尸任务：qrtz_cron_triggers、qrtz_triggers、qrtz_job_details顺序删除
	V1.2新增任务日志，记得执行“qrtz_trigger_log”生成表结构
	