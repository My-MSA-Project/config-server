# ⚙️ Spring Cloud Config Server

[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.x-6DB33F?style=for-the-badge&logo=spring-boot)](https://spring.io/projects/spring-boot)
[![Java](https://img.shields.io/badge/Java-17-B07219?style=for-the-badge&logo=openjdk)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
[![Gradle](https://img.shields.io/badge/Gradle-8.x-02303A?style=for-the-badge&logo=gradle)](https://gradle.org/)

---

## 📖 개요

이 프로젝트는 **Spring Cloud Config**를 사용하여 구현한 중앙 집중식 구성 서버입니다.  
분산 시스템 환경에서 여러 마이크로서비스의 외부 설정을 효율적으로 관리하는 핵심 역할을 수행합니다.

## ✨ 주요 기능

- **중앙 집중식 설정 관리**: 모든 마이크로서비스의 설정을 단일 위치에서 관리합니다.
- **다양한 백엔드 지원**: Git 또는 로컬 파일 시스템(`native`)을 사용하여 설정 정보를 관리할 수 있습니다.
- **보안**: Spring Security를 통해 설정 정보에 대한 접근을 안전하게 제어합니다.

## 🛠️ 기술 스택

- **Java**: `17`
- **Spring Boot**: `3.x`
- **Spring Cloud Config**: `Server`
- **Build Tool**: `Gradle`

## 🚀 시작하기

### ✅ 요구사항

- Java `17` 이상
- Gradle `8.x` 이상

### 📦 빌드

아래 명령어를 사용하여 프로젝트를 빌드합니다.

```bash
./gradlew build
```

### ▶️ 실행

빌드가 완료되면, 아래 명령어를 통해 애플리케이션을 실행할 수 있습니다.

```bash
java -jar build/libs/config-server-0.0.1-SNAPSHOT.jar
```

> 💡 서버는 기본적으로 **8888 포트**에서 실행됩니다.

## ⚙️ 구성

- 이 서버는 `native` 프로필을 사용하여 로컬 파일 시스템의 설정 파일을 서비스하도록 구성되어 있습니다.
- 설정 파일은 `src/main/resources/config` 디렉토리 내에 위치해야 합니다.
  - 예: `order-service.yml`, `user-service-dev.yml`
- 서버의 기본 설정은 `src/main/resources/application.yaml` 파일에 정의되어 있습니다.

### 🔗 설정 파일 접근 규칙

클라이언트 애플리케이션은 아래와 같은 URL 형식으로 설정 정보를 요청할 수 있습니다.

> ```
> /{application}/{profile}
> /{application}-{profile}.yml
> /{application}-{profile}.properties
> ```

**예시:**
`order-service` 애플리케이션의 `development` 프로필 설정 정보를 가져오려면 아래 URL로 요청합니다.

> ```http
> http://localhost:8888/order-service/development
> ```

## 🔒 보안

- Spring Security가 적용되어 있어 설정 정보에 접근하기 위해 사용자 인증이 필요합니다.
- 기본 인증 정보는 `application.yaml` 파일에 정의되어 있습니다.
  - **Username**: `user`
  - **Password**: `application.yaml` 파일에서 확인해주세요.