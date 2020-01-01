---
layout: post
title: Spring Log4j 로그레벨 설정 
comments: true 
categories : [Web-Back/Spring]
tags: [Spring, Log4j]
---

# Log4j로그 레벨 설정 

## Log4j 구성요소

요소 | 설명
---|-----
Logger | 출력할 메세지를 Appender에 전달한다.
Appender | 전달된 로그를 어디에 출력할 지 결정한다. (콘솔 출력, 파일 기록, DB 저장 등)
Layout | 로그를 어떤 형식으로 출력할 지 결정한다.


## Log4j 레벨

순서대로 높은 레벨을 가지며, 출력 레벨 설정이 따라 설정 레벨 이상의 로그가 출력된다.

로그레벨 | 설명
-----|------
 FATAL | 아주 심각한 에러가 발생한 상태를 나타낸다.
 ERROR | 어떠한 요청을 처리하는 중 문제가 발생한 상태를 나타낸다.
 WARN | 프로그램의 실행에는 문제가 없지만, 향후 시스템 에러의 원인이 될 수 있는 경고성 메시지를 나타낸다.
 INFO | 어떠한 상태변경과 같은 정보성 메시지를 나타낸다.
 DEBUG | 개발시 디버그 용도로 사용하는 메시지를 나타낸다.
 TRACE | 디버그 레벨이 너무 광범위한 것을 해결하기 위해서 좀 더 상세한 이벤트를 나타낸다.

 ```xml
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE log4j:configuration PUBLIC "-//APACHE//DTD LOG4J 1.2//EN" "log4j.dtd">
<log4j:configuration xmlns:log4j="http://jakarta.apache.org/log4j/">

	<!-- Appenders -->
	<appender name="console" class="org.apache.log4j.ConsoleAppender">
		<param name="Target" value="System.out" />
		<layout class="org.apache.log4j.PatternLayout">
			<param name="ConversionPattern" value="%-5p: %c - %m%n" />
		</layout>
	</appender>
	
	<!-- 특정 패키지 출력 설정 -->
	<!-- Application Loggers -->
	<logger name="com.dw.example">
		<level value="info" />
	</logger>
	
	<!-- 3rdparty Loggers -->
	<logger name="org.springframework.core">
		<level value="info" />
	</logger>
	
	<logger name="org.springframework.beans">
		<level value="info" />
	</logger>
	
	<logger name="org.springframework.context">
		<level value="info" />
	</logger>

	<logger name="org.springframework.web">
		<level value="info" />
	</logger>

	<!-- 기본 출력 설정 -->
	<!-- Root Logger -->
	<root>
		<priority value="warn" />
		<appender-ref ref="console" />
	</root>
	
</log4j:configuration>

```
