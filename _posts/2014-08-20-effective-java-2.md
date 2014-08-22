---
layout: post

title: "Effective Java 모든 객체에 공통적인 메소드"
subtitle: "ITEM 8~9"
cover_image: apple2-cover.jpg

excerpt: "Effective Java 모든 객체에 공통적인 메소드"

author:
  name: 신문규
  github: skylershin
  bio: Developer
  image: 신문규.jpg
---


## 모든 객체에 공통적인 메소드!
- Object 클래스는 상속을 목적으로 설계되었다. 이 클래스에는 (equals, hashcode, toString, clone, finalize) 와 같은 메소드들이 Object의 모든 서브 클래스에서 오버라이드하도록 설계되었다.
이 장에서는 final이 아닌 Object의 메소드들을 언제 어떻게 오버라이드 하는지 알려준다.

### Item 8. equals 메소드를 오버라이딩 할 때는 보편적 계약을 따르자.
- equals 메소드는 오버라이딩을 하는 과정에서 문제가 발생할 수 있다. 이런 부분을 가장 쉽게 피하는 방법은 상속받은 그대로 사용하는 것이다. 다음 조건 중 어느 하나라도 만족하면 그렇게 하는 것이 좋다.
  - 클래스의 각 인스턴스가 본래부터 유일한 경우
  - 두 인스턴스가 논리적으로 같은지 검사하지 않아도 되는 클래스의 경우
  - 수퍼 클래스에서 equals 메소드를 이미 오버라이딩 했고, 그 메소드를 그대로 사용해도 좋은 경우
  - private이나 package-private(접근 지시자를 지정하지 않은 경우) 클래스라서 이 클래스의 equals 메소드가 절대 호출되지 않아야 할 경우

**그렇다면 Object.equals를 언제 오버라이드 해야 좋을까?**
- 인스턴스가 갖는 값을 비교하여 논리적으로 같은지 판단할 필요가 있는 클래스로써, 자신의 수퍼클래스에서
equals 메소드를 오버라이드 하지 않았을 경우
- equals 메소드를 오버라이드 할 때는 이 메소드의 보편적 계약을 따라야 한다. equals 메소드는 equivalence relation 을 구현하며 그것은

  - **Reflexive** : null이 아닌 모든 참조 값 x에 대해, x.equals(x)는 반드시 true를 반환해야 한다.
  - **Symmetric** : null이 아닌 모든 참조 값 x와 y에 대해, y.equals(x)가 true를 반환한다면 x.equals(y)도 반드 시 true를 반환해야 한다.
  - **Transitive**: null이 아닌 모든 참조 값 x와 y에 대해, x.equals(y)가 true를 반환하고 y.equals(z)가 true를 반환한다면 x.equals(z)도 true를 반환해야 한다.
  - **Consistent**: null이 아닌 모든 참조 값 x와 y에 대해, equals 메소드에서 객체 비교 시 사용하는 정보가 변경되지 않는다면, x.equals(y)를 여러 번 호출하더라도 일관성 있게 true 또는 false를 반환해야 한다.! • null 아닌 모든 참조 값 x에 대해, x.equals(null)은 반드시 false를 반환해야 한다.



### Item 9. equals 메소드를 오버라이드 할 때는 hashCode 메소드도 항상 같이 오버라이드 하자.!
- hashCode 메소드를 제대로 오버라이드 하지 않아 코드 결함이 생기는 경우가 흔하다. 그렇게 하지 않으면 HashMap과 HashSet 등 모든 해시 기반의 컬렉션들과 우리 클래스를 같이 사용할 때 우리 클래스가 올바르게 동작하지 않을 것이다.

자바 API문서의 주요 사항은 다음과 같다.

- 애플리케이션이 실행 중에 같은 객체에 대해 한 번 이상 호출되더라도 hashCode 메소드는 같은 정수를 일관 성 있게 반환해야 한다.
- equals(Object) 메소드 호출결과 두 객체가 동일하다면, 두 객체 각각에 대해 hashCode 메소드를 호출 했을 때 같은 정수 값이 나와야 한다. (주요 위배사항)
- equals(Object) 메소드 호출결과 두 객체가 다르다고 해서 두 객체 각각에 대해 hashCode 메소드를 호출 했 !을 때 반드시 다른 정수 값이 나올 필요는 없다.

좋은 해시 메소드는 동일하지 않은 객체들에 대해 서로 다른 해시코드를 만든다. 이상적으로는 동일하지 않은 인 스턴스들에 대해 모든 가능한 해시 값을 고르게 분산시켜주어야 한다.
