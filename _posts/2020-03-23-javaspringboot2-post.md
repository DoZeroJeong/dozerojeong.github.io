---
layout: post
title: Java Spring Boot JPA 사용하기
---

build.gradle에 다음과 같이 의존성들을 등록

<pre>
<code>
 compile('org.springframework.boot:spring-boot-starter-data-jpa')
 compile('com.h2database:h2')
</code>
</pre>

<pre>
<code>
 package com.spring.first.boot.domain.posts;

 import com.spring.first.boot.domain.BaseTimeEntity;
 import lombok.Builder;
 import lombok.Getter;
 import lombok.NoArgsConstructor;
 import javax.persistence.*;

 @Getter
 @NoArgsConstructor
 @Entity
 public class Posts extends BaseTimeEntity {

    @Id
    @GeneratedValue(strategy = GenerationType.IDENTITY)
    private Long id;

    @Column(length = 500, nullable = false)
    private String title;

    @Column(columnDefinition = "TEXT", nullable = false)
    private String content;

    private String author;

    @Builder
    public Posts(String title, String content, String author){
        this.title = title;
        this.content = content;
        this.author = author;
    }
 }
</code>
</pre>

@Entity는 JPA의 어노테이션이며, @Getter와 @NoArgsConstructor는 롬복의 어노테이션이다   
*어노테이션은 메소드나 변수앞에 붙은 **@** 표시를 말한다.   
롬복 어노테이션은 필수 어노테이션은 아니고 이후에 코틀린 등의 새 언어 전환으로 필요 없을 경우 쉽게 삭제할 수 있다.   
@Column은 굳이 선언하지 않더라도 해당 클래스의 필드는 모두 칼럼이 되는데 기본값 외에 추가로 변경이 필요한 옵션이 있으면 사용한다.  
@NoArgsConstructor은 기본 생성자를 자동으로 추가해준다.   
@Getter는 클래스 내 모든 필드의 Getter 메소드를 자동으로 생성한다.