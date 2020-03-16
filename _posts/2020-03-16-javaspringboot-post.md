---
layout: post
title: Java Spring Boot 시작하기
---

## 그레이들 프로젝트를 스프링 부트 프로젝트로 변경

대부분 스프링 이니셜라이저(https://start.spring.io/)를 통해서 진행하지만 스프링 부트를 처음 사용하여 build.gradle의 코드가 무슨 역할을 하는지 이니셜라이저 외에 추가로 의존성 추가가 필요하면 어떻게 해야 할지 모르는 상태로 개발하여 이니셜라이저를 사용하지 않음

<pre>
<code>
ext{
        springBootVersion = '2.1.7.RELEASE'
    }
</pre>
</code>

build.gradle에서 사용하는 전역변수를 설정하겠다는 의미로 여기서는 springBootVersion 전역변수를 생성하고 그 값을 '2.1.7RELEASE'로 하겠다는 의미

<pre>
<code>
apply plugin: 'java'
apply plugin: 'eclipse'
apply plugin: 'org.springframework.boot'
apply plugin: 'io.spring.dependency-management'
</pre>
</code>

io.spring.dependency-management 플러그인은 스프링 부트의 의존성들을 관리해 주는 플러그인이라 꼭 추가해야함

나머지 플러그인은 자바와 스프링부트를 사용하기 위해 추가하는 플러그인

<pre>
<code>
repositories{
        mavenCentral()
        jcenter()
    }
    dependencies {
        classpath("org.springframework.boot:spring-boot-gradle-plugin:${springBootVersion}")
    }
</pre>
</code>

repositories는 각종 의존성들을 어떤 원격 저장소에서 받을지를 정함
dependencies는 프로젝트 개발에 필요한 의존성들을 선업하는 곳