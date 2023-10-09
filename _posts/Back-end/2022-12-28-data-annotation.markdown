---
title: '[Lombok] @Getter + @Setter = @Data ?'
layout: post
categories: backend
tags: lombok
date: 2022-12-28 00:01:20 +0900
# related_posts:
# - _posts/Algorithm/<post_name.md>

---

스프링프레임워크를 사용하는 개발자에게 롬복 라이브러리는 이제 필수입니다. 빌더 패턴을 사용하면서 빌더 메소드를 작성하지 않아도 되게 해주는 @Builder, @NoArgsConstructor, @RequiredArgsConstructor, @AllArgsConstructor 등의 생성자 어노테이션 등 롬복은 개발자들이 그동안 정성스럽게 작성해온 메소드와 기능들을 어노테이션만으로 대신하게 해주는 강력한 라이브러리입니다. 

<br/>

> Project Lombok is a java library that au>tomatically plugs into your editor and build tools, spicing up your java.
> Never write another getter or equals method again, with one annotation your class has a fully featured builder, Automate your logging variables, and much more.
> 
> 롬복은 당신의 에디터와 빌드 툴에 자동으로 연결되어 당신의 자바 기능을 향상시키는 자바 라이브러리입니다. 
> 더이상 getter, equals 메소드를 작성하지 마세요. 하나의 어노테이션만으로 당신의 클래스는 완벽한 기능을 갖춘 builder를 가지게 될 겁니다. 그 밖에 로깅 변수 등 많은 것들을 자동화하세요. 
>
> * 출처 : https://projectlombok.org/


<br/>

@Getter와 @Setter는 Lombok을 대표하는 어노테이션입니다. 이름에서도 알 수 있듯이 이 어노테이션들은 그동안 일일이 메소드로 작성해야 했던 게터와 세터를 어노테이션 하나로 해결합니다. @Data는  클래스에 @Getter와 @Setter를 한번에 적용합니다. Setter를 작성하지 않는 엔티티에는 @Data를 사용하지 않지만, 데이터를 설정할 일이 많은 DTO 계층에는 @Data를 붙임으로써 getter와 setter를 모두 작성하는 효과를 가져올 수 있습니다.


그동안 단순히 @Getter, @Setter를 모두 포함하는 어노테이션으로 @Data를 사용해왔는데, 그 내부가 궁금해 뜯어보니 이외에도 다른 어노테이션을 가지고 있음을 알 수 있었습니다. 


<br/>

**@Data가 포함하는 Lombok 어노테이션들**

- Getter
- Setter
- RequiredArgsConstructor
- ToString
- EqualsAndHashCode
- Value

<br/>

각 어노테이션들에 대해서는 자세한 사용법과 함께 다른 포스팅에서 다루기로 하고, 본 포스팅에서는 @Data가 @Getter/@Setter 이외에도 다른 어노테이션을 포함하고 있다는 사실과, 해당 어노테이션들의 간단한 기능에 대해서만 언급하겠습니다. 

<br/>



- @RequiredArgsConstructor : final이나 @NonNull인 필드값만 파라미터로 받는 생성자를 만들어주는 어노테이션

- @ToString : toString() 메소드를 작성해주는 어노테이션. 특정 필드값을 toString() 대상에서 제외시키는 exclude 사용 가능.
  
- @EqualsAndHashCode : 두 객체의 내용이 같은지 여부, 즉 동등성(equality)을 비교하는 equals와 두 객체가 같은 객체인지, 즉 동일성(identity)을 비교하는 hashCode를 자동생성해주는 어노테이션. equals와 hashCode 메소드 생성시 부모 클래스의 필드까지 고려할지 여부를 callSuper 속성을 통해 설정할 수 있음.

- @Value : 설정파일(.properties, yml)에 설정한 내용을 주입시켜주는 어노테이션. DB 연결에 필요한 정보 등 공개가 곤란한 설정 정보들을 따로 빼두고, 필요한 곳에만 주입하는 기능을 제공함. 


<br/>




---
### 참고
- https://projectlombok.org/
- https://n1tjrgns.tistory.com/164
- https://j-sik.tistory.com/m/109
