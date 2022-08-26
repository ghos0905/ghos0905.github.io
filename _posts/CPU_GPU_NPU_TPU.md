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

<hr>

CPU 는 Centralized Processing Unit 의 축약어입니다. 현대의 Processing chip들은 모두 폰노이만이 맨하탄 프로젝트 당시 논문에서 제안했던 전자계산기 기본 구조를 따라 발전해 왔습니다.

### 폰 노이만 아키텍쳐 (von Neumann architecture)

von Neumann architecture 출처: <a href="https://en.wikipedia.org/wiki/Von_Neumann_architecture">Wikipedia</a>
현재의 CPU 기본 구조는 폰노이만 구조에 기반하여 발전하였습니다. 폰노이만 아키텍쳐는 유연한 계산 능력이라는 장점이 뚜렷한 구조입니다. 순차적인 계산을 통해 이전 계산 결과와 다음 계산 결과의 유기적인 연계가 가능한 구조이기도 합니다. CPU는 폰노이만 아키텍쳐에서 Control, Cache 등의 메모리 영역이 고도화된 구조를 지향합니다. 여러 Level 의 캐시를 대량 집적하여 다양한 형태의 복잡한 프로그램을 효율적으로 실행하는 데에 그 목적이 있다고 할 수 있습니다. 하지만 직렬(순차) 실행으로 인한 문제점을 현대의 모든 CPU가 동일하게 가지고 있기도 합니다.

<hr>

바로 “von Neumann Bottleneck” 이라는 것인데, 모든 계산의 결과가 ALU (Arithmetic Logic Unit) 연산을 거쳐 반드시 메모리 어딘가에 저장이 되어야 한다는 것입니다. ALU 연산의 결과가 메모리 또는 칩 내부의 캐시에 저장되어야 하기 때문에 항상 한번에 하나의 트랜잭션만을 순차적으로 처리하게 됩니다.

<hr>

클럭을 높여서 처리 속도가 빨라지더라도 높아진 클럭 만큼의 계산만 더 할 수 있습니다. 클럭의 개선이 발열 등의 문제로 인해 한계에 다다른 이후 CPU의 발전은 multi-core, hyper-threading 과 같이 동시에 구동할 수 있는 코어의 개수를 늘리는 방향으로 이루어지고 있습니다.
