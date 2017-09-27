selenium testng reportng autotest framework with maven

* 日志：集成HTML格式及原生文本日志；
* 断言，testng断言api重新封装，加入断言失败截图和日志记录信息；
* 报告，集成reportng的汇总报告和realtime-report的实时报告查看；
* 数据管理，文本、xls、csv读写，stringutils封装，jdbc api封装；
* autoit应用程序支持，用于处理异常组件的识别和测试；
* webdriver api健壮性封装，BOT-Style；
* 支持chromedriver、iedirverserver、geckdriver、MicrosoftWebDriver；
* 提倡使用maven调度，示例如下：

```xml
<plugins>
	<plugin>
		<groupId>org.apache.maven.plugins</groupId>
		<artifactId>maven-surefire-plugin</artifactId>
		<version>2.20.1</version>
		<configuration>
			<suiteXmlFiles>
				<file>task/testng.xml</file>
			</suiteXmlFiles>
			<properties>
				<property>
					<name>usedefaultlisteners</name>
					<value>false</value>
				</property>
				<property>
					<name>listener</name>
					<value>com.fudax.report.HTMLReporter,
						org.testng.reporters.FailedReporter,com.fudax.report.realtime.listener.RealTimeTestResultListener</value>
				</property>
			</properties>
			<reportsDirectory>${basedir}/report</reportsDirectory>
			<systemProperties>
				<property>
					<name>realtimeReportDir</name>
					<value>${basedir}/report/realtime</value>
				</property>
			</systemProperties>
		</configuration>
		<dependencies>
			<dependency>
				<groupId>org.apache.maven.surefire</groupId>
				<artifactId>surefire-testng</artifactId>
				<version>2.20.1</version>
			</dependency>
		</dependencies>
	</plugin>
	[...]
</plugins>
```
