---
title: 직렬화(Serialization)/역직렬화(Deserialization)
date: 2025-11-26 00:00:00
tags:
    - Codable
categories:
    - Computer Science
---

직렬화(Serialization)와 역직렬화(Deserialization)에 대해서 알아봅시다.

![serialization & deserialization](Serialization.jpg) [^1]
[^1]: [참조](https://en.wikipedia.org/wiki/Serialization)

## 직렬화(Serialization)
- 메모리에 존재하는 데이터를, 범용 포맷(JSON, XML, 바이너리 등)으로 변환하는 과정
- Encoding

### 목적
- 메모리에 있는 데이터를 전송 및 저장이 가능한 형태로 만들기 위함

### 예시
- 네트워크 전송
- 파일 저장
- 다른 시스템 및 프로그래밍 언어와 데이터 교환 
- iOS에서
    - `class`와 `struct`로 정의한 데이터 모델의 인스턴스를 JSON으로 변환하여 서버로 전송

## 역직렬화(Deserialization)
- 범용 포맷(JSON, XML, 바이너리 등)으로 작성된 데이터를, 메모리 상의 데이터 구조로 변환하는 과정
- Decoding

### 목적
- 범용 포맷의 데이터를 애플리케이션에서 사용할 수 있는 형태로 변환하기 위함

### 예시
- 네트워크로부터 데이터 수신
- 파일에서 데이터 읽기
- 다른 시스템에서 전달받은 데이터 처리
- iOS에서
    - API 호출을 통해 받은 JSON 데이터를 iOS 앱에서 정의한 데이터 모델의 인스턴스로 변환하여 앱에서 사용
