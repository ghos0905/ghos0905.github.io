---
layout: post
title:  CPU, GPU, NPU, and TPU
date: 2022-08-26 22:09:00
description: For understanding concept of representative processing units.
tags: process unit
categories: computer architecture
---

## CPU 계산 구조

AI 시대인 요즘의 키워드를 기준으로 하여 CPU GPU TPU NPU 네 가지 유형을 이야기하고 있지만, 이들 중에서 CPU와 나머지 GPU, TPU, NPU 칩은 구조나 목적상으로 큰 차이점이 있습니다.

<br>

CPU 는 Centralized Processing Unit 의 축약어입니다. 현대의 Processing chip들은 모두 폰노이만이 맨하탄 프로젝트 당시 논문에서 제안했던 전자계산기 기본 구조를 따라 발전해 왔습니다.

### 폰 노이만 아키텍쳐 (von Neumann architecture)

von Neumann architecture 출처: <a href="https://en.wikipedia.org/wiki/Von_Neumann_architecture">Wikipedia</a>
현재의 CPU 기본 구조는 폰노이만 구조에 기반하여 발전하였습니다. 폰노이만 아키텍쳐는 유연한 계산 능력이라는 장점이 뚜렷한 구조입니다. 순차적인 계산을 통해 이전 계산 결과와 다음 계산 결과의 유기적인 연계가 가능한 구조이기도 합니다. CPU는 폰노이만 아키텍쳐에서 Control, Cache 등의 메모리 영역이 고도화된 구조를 지향합니다. 여러 Level 의 캐시를 대량 집적하여 다양한 형태의 복잡한 프로그램을 효율적으로 실행하는 데에 그 목적이 있다고 할 수 있습니다. 하지만 직렬(순차) 실행으로 인한 문제점을 현대의 모든 CPU가 동일하게 가지고 있기도 합니다.

<br>

바로 “von Neumann Bottleneck” 이라는 것인데, 모든 계산의 결과가 ALU (Arithmetic Logic Unit) 연산을 거쳐 반드시 메모리 어딘가에 저장이 되어야 한다는 것입니다. ALU 연산의 결과가 메모리 또는 칩 내부의 캐시에 저장되어야 하기 때문에 항상 한번에 하나의 트랜잭션만을 순차적으로 처리하게 됩니다.

<br>

클럭을 높여서 처리 속도가 빨라지더라도 높아진 클럭 만큼의 계산만 더 할 수 있습니다. 클럭의 개선이 발열 등의 문제로 인해 한계에 다다른 이후 CPU의 발전은 multi-core, hyper-threading 과 같이 동시에 구동할 수 있는 코어의 개수를 늘리는 방향으로 이루어지고 있습니다.

### CPU 에서 연산이 어떻게 이루어지는지 살펴봅시다

위에서 CPU 연산의 강점과 약점에 대해 이야기 했습니다. 간단히 CPU 에서 연산이 이루어지는 예제를 살펴보면 내용을 이해하는데 도움이 될 것입니다.

<br>

모든 CPU 는 기계어를 실행합니다. 그리고 CPU 종류마다 실행할 수 있는 기계어의 종류는 다를 수 있습니다. 그래서 CPU를 비롯한 마이크로 프로세서는 자기가 실행할 수 있는 기계어의 모음을 가지고 있습니다. 이런 기계어의 모음을 ISA 라고 부르며, 이는 Instruction Set Architecture 의 축약어입니다.

<br>

예를 들어 CPU 에서 “1 + 2 = 3” 연산이 어떻게 수행되는지 살펴봅시다. 다음의 세 개의 명령어 세트만 가지고 있는 단순한 마이크로 프로세서가 있다고 가정해 보겠습니다. 그리고 이 마이크로 프로세서에는 3 개의 레지스터가 있으며, 각각 reg1, reg2, reg3 로 지정하여 프로그램할 수 있다고 가정해 보겠습니다. 실제로 이런 프로세서가 있다면 별로 쓸모는 없겠지만, 개념을 이해하기 위해 단순한 구조로 가정해 보는 것입니다.

<br>

|명령어|설명|
|---|---|
|LDR|CPU 내부의 레지스터로 데이터 가져오기|
|STR|	CPU 내부의 레지스터에서 메모리로 데이터 내보내기|
|ADD|	두 개의 레지스터의 데이터 값을 더하여 결과를 다른 레지스터에 저장하기|
|Instrunction Set|

위와 같은 ISA 를 가진 프로세서가 있다고 할 때, 아래와 같은 기계어 프로그램을 통해 계산을 수행할 수 있습니다.

<br>

₩₩₩
LDR reg1, #1; // reg1 레지스터에 상수 1 로드 
LDR reg2, #2; // reg2 레지스터에 상수 2 로드
ADD reg1, reg2, reg3; // reg1 값과 reg2 값을 더해 reg3 에 저장
STR reg3, [0x00040222h]; // reg3 의 값을 0x00040222 메모리로 내보냄
₩₩₩
