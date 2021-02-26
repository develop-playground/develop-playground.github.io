---
title: "[Spring] Building a RESTful Web Service"
categories: Spring
toc : true
toc_sticky: true
date: 2021-01-19
last_ modified_at : 2021-02-26
---

Spring을 이용하여 간단하게 RESTful Web Service을 구축해보자.

### 무엇을 개발할 것인가

사용자가 http://localhost:8080/greeting 을 요청하게 되면 다음에 표시된 JSON 형태로 응답한다.

```json
{"id" : 1, "content" : "Hello, World!"}
```

`name` 을 http 요청시 매개변수로 사용하면 사용자 지정 인사말을 사용할 수 있다.

`http://localhost:8080/greeting?name=Jang`

```json
{"id" : 1, "content" : "Hello, Jang!"}
```

### 필요한 것

- 약 15분의 시간
- 본인이 개발시 사용하는 IDE
- JDK 1.8 이상
- Gradle 4 이상 또는 Maven 3.2 이상

### 이 가이드를 완료하는 방법

시간이 없을시에는 제공되는 `github`에서 소스코드를 clone 받아서 실행만 해보고, 시간적 여유가 있다면 직접 따라하면서 하나하나 차근차근 학습하는 것이 좋다.

```bash
git clone https://github.com/spring-guides/gs-rest-service.git
```

### Starting with Spring Initialize

저자는 `IntelliJ IDEA`를 사용중이며 IntelliJ에서 제공하는 `Spring Initializr`를 이용한다.

`New Project`를 클릭한 뒤 'Spring Initializr'를 선택한다.

사용할 'jdk'를 선택한 뒤 Next.

`Aritifact`를 restservice로 입력하고, Type을 Maven, Gradle 중 사용할 것을 체크한다.

(저자는 최근 Gradle 학습중으로 Gradle 체크)

구현할 언어, packaging, Java version을 선택해주고 Next.

이 프로젝트는 굉장히 간단한 것이라서 `Dependencies`는 [Web] - [Spring Web]만 선택해준다.

프로젝트가 생성되면 다음과 같은 `build.gradle` 파일을 확인 할 수있다.

```bash
plugins {
    id 'org.springframework.boot' version '2.4.2'
    id 'io.spring.dependency-management' version '1.0.11.RELEASE'
    id 'java'
}

group = 'com.example'
version = '0.0.1-SNAPSHOT'
sourceCompatibility = '1.8'

repositories {
    mavenCentral()
}

dependencies {
    implementation 'org.springframework.boot:spring-boot-starter-web'
    testImplementation 'org.springframework.boot:spring-boot-starter-test'
}

test {
    useJUnitPlatform()
}
```

`maven`으로 선택했다면 다음과 같은 `pom.xml`을 확인할 수 있다.

```xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
	xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 https://maven.apache.org/xsd/maven-4.0.0.xsd">
	<modelVersion>4.0.0</modelVersion>
	<parent>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-parent</artifactId>
		<version>2.3.2.RELEASE</version>
		<relativePath/> <!-- lookup parent from repository -->
	</parent>
	<groupId>com.example</groupId>
	<artifactId>rest-service</artifactId>
	<version>0.0.1-SNAPSHOT</version>
	<name>rest-service</name>
	<description>Demo project for Spring Boot</description>

	<properties>
		<java.version>1.8</java.version>
	</properties>

	<dependencies>
		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-web</artifactId>
		</dependency>

		<dependency>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-starter-test</artifactId>
			<scope>test</scope>
			<exclusions>
				<exclusion>
					<groupId>org.junit.vintage</groupId>
					<artifactId>junit-vintage-engine</artifactId>
				</exclusion>
			</exclusions>
		</dependency>
	</dependencies>

	<build>
		<plugins>
			<plugin>
				<groupId>org.springframework.boot</groupId>
				<artifactId>spring-boot-maven-plugin</artifactId>
			</plugin>
		</plugins>
	</build>

</project>
```

### Create a Resource Representation Class

이제 프로젝트 설정을 끝냈으니 웹 서비스를 만들 준비가 끝났다.

이 가이드에서는 매개 변수를 사용한 `GET` 요청을 처리한다.

`/greeting` 이라는 `GET` 요청을 보내서 `200 Ok`로 정상적인 응답을 보인다면 다음과 같은 JSON 형태의 응답이 출력될 것이다.

```json
{
	"id" : 1,
	"content" : "Hello, World!"
}
```

우선 응답에 사용될 `/src/main/java/com/example/restservice/Greeting.java` 클래스를 생성한다.

```java
package com.example.restservice;

public class Greeting {

	private final long id;
	private final String content;

	public Greeting(long id, String content) {
		this.id = id;
		this.content = content;
	}

	public long getId() {
		return id;
	}

	public String getContent() {
		return content;
	}
}
```

### Create Resource Controller

`RESTful` 웹 서비스를 구축하는 Spring에서는 `HTTP` 요청은 컨트롤러를 이용해 처리된다.

우리는 이 요청을 `@RestController` 어노테이션으로 식별한다.

`GET` 요청에 대한 응답을 위해 `@GetMapping` 을 이용해서 `/greeting` 요청에 대한 반환할 인스턴스에 대한 처리를 한다..

```java
package com.example.restservice;

import java.util.concurrent.atomic.AtomicLong;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GreetingController {

	private static final String template = "Hello, %s!";
	private final AtomicLong counter = new AtomicLong();

	@GetMapping("/greeting")
	public Greeting greeting(@RequestParam(value = "name", defaultValue = "World") String name) {
		return new Greeting(counter.incrementAndGet(), String.format(template, name));
	}
}
```

`/greeting` 이라는 `GET` 요청이 들어오면 매개변수가 있으면 입력된 매개변수의 name 값, 없다면 'World"를 Greeting 클래스의 content로 설정하여 인스턴스를 생성한다.

### Test the Service

이제 웹 브라우저 창을 열고 `http://localhost:8080/greeting` 을 입력해보자.

다음과 같이 정상적인 응답을 확인할 것이다.

이번엔 `http://localhost:8080/greeting?name=Byeongsoon` 을 입력해보자.

다음과 같이 World가 아닌 입력한 나의 이름이 나올 것이다.

### Summary

축하합니다. 아주 간단하지만 방금 `Spring`으로 `RESTful` 웹 서비스를 개발했습니다.
