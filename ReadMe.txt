telnet 客户端类

◆ 这是什么？
可与 PowerSehll（v5 及更高版本）一起使用的 telnet 客户端类。
它可用于自动配置设备，例如使用 telnet 配置的网络设备。

◆ 你能做什么？
・与设备的 Telnet 连接
・发送命令（包括登录/注销）
・接收命令发送结果
·切割

◆ 不能做的事
・自动设备设置ww
由于它只实现了telnet客户端功能，因此您需要自己编写自动配置所需的处理。
您可以通过继承此类来为您的设备创建自定义类，也可以按原样使用此 telnet 客户端类编写脚本。

◆ 班级成员说明
·构造函数
	Telnet客户端()
	TelnetClient（字符串，整数）
		连接到指定节点
			string : 连接目标 IP 或主机名
			int：端口号

・公开方法
	＃ 联系
	[无效] 连接（字符串，整数）
		连接到指定节点
			string : 连接目标 IP 或主机名
			int：端口号

	# 断开连接
	[无效] 断开连接()
		与已连接的节点断开连接
		（TCP级别断开连接而不是注销等处理）

	＃ 发送
	[无效] 发送（字符串，布尔）
		发送命令
			string : 要发送的命令
			bool: 是否记录发送命令
				$true：输出
				$false ：无输出（**** 已记录）

	＃ 收到
	[字符串[]]接收（字符串）
		接收（这里也实现了telnet协商）
		接收到的内容记录在日志中
			string : 监听的提示
			继续等待，直到收到此提示（超时：30 秒）

	# 更改环境设置
	[void] SetEnvironment（字符串，布尔，整数，布尔，布尔）
		改变运行环境
			string ：日志文件的完整路径（如果设置了 $null，则使用默认值）
				默认：脚本路径 telnet_YYYY-MMDD.log
			bool : 禁止日志保存
					$false : 保存日志
					$true：不保存日志（显示它们）
					默认值：$false
			int：超时（秒）
				默认值：30
			bool: 是否输出协商/提示等待状态到日志
				$true ：输出到日志
				$false : 不输出到日志
				默认值：$false
			bool: 是否将开发调试输出到日志
				$true ：输出到日志
				$false : 不输出到日志
				默认值：$false

	# 日志输出
	[字符串] 日志（字符串）
		输出日志
			string : 日志输出消息

・公共财产
	没有任何

◆ 使用方法
	请按原样使用 TelnetClient 类或创建继承它的自定义类。
	运行时，请将TelnetClient.ps1和DecisionTable.csv放在同一文件夹中。

◆ 文件
	Telnet客户端.ps1
		Telnet 客户端类主体

	决策表.csv
		运动控制决策表数据

	自述文件.txt
		这个文件

	样本1.ps1
		使用裸 Telnet Client 类时的实现示例

	样本2.ps1
		继承Telnet Client类时的实现示例

	样本2Class.ps1
		Telnet Client 类继承示例（在sample2.ps1 中使用）

	决策表.xlsx
		人类可视的运动控制决策表

	方法结构.txt
		内部调用方法的树形结构

	备忘录.txt
		Telnet协商操作备忘录
