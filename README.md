# 포스텍 컴공/수학에서 살아남기

포스텍 컴공/수학을 복수전공하는 학생이 전공 과목을 수강하면서 좋았던 점, 아쉬웠던 점 등 후배들에게 도움이 될 만한 내용을 적었다.

## 배경

- 컴퓨터공학, 수학을 좋아하는 학부생.
- 코딩은 초등학교 때부터 했고, assembler 등 low level과 관련된 내용을 가끔 경험하기도 했다.
- 고등학교에서 대학교 1학년 수준의 미적분학 과목을 수강하였고, 모종의 이유로 물리학에 관심을 두어 (고등학교 수준에 맞게 조정되었지만) 일반역학, 전자기학, 양자역학 등을 공부한 경험이 있다.
- 고등학교 3학년 때 (하라는 공부는 안하고) 컴파일러 최적화 쪽에 꽂혀서, 대학교에 붙으면 컴파일러 쪽을 파봐야지 라는 생각을 하게 되었다.
- Linux나 macOS 환경에서 주로 코딩을 수행한다. 23년 1학기부터 Apple Silicon Mac을 사용 중이어서, 이와 관련한 팁들도 몇가지 적을 것이다.

## Course Reviews

### 2022 Spring

#### MATH101 미적분학1

- 1차원에서의 미적분을 다루는 과목이다.
- 고등학교때 미적분학을 수강해서 쉬울 줄 알았으나, 증명의 비중이 상당해 생각보다 어려움이 있었다.
- 수업 시간과 시험에서 증명의 비중이 상당했고, 개인적으로는 매우 좋아했지만, 해석학 등에서 배우는 내용을 사용하면 증명이 간단한데, 쓸 수 있는 거라곤 epsilon-delta 논법과 트릭 몇가지 정도였던 경우가 꽤 있어서 힘들었던 경험도 있다.
- 개인적으로는 이 과목을 듣고 수학과 복수전공을 결심했다.
- 다행히도 1학년 미적분학에서 요구하는 증명은 많은 경우 복잡하지 않기 때문에, 전제에서 결론으로 이어지는 과정을 따라가면서 증명을 공부하면 도움이 될 것이다.

### 2022 Fall

#### CSED101 프로그래밍과 문제해결

[[GitHub]](https://github.com/sohnryang/csed101)

- C언어 코딩을 배우는 과목이다.
- C언어의 기초적인 문법을 이미 알고 있다면 수업을 따라가는 데에는 전혀 무리가 없을 것이다.
- 이미지 처리, 사다리 타기 게임, 플레이리스트 관리 등의 간단한 CLI 프로그램을 구현하는 과제가 나온다.
- 과제에서 사용 가능한 문법 제한이 있었기 때문에, C언어 숙련도에 따라 사용 불가능한 문법들을 생각하면서 코딩해야 하는 아이러니한 상황이 일어날 수도 있다.

#### CSED199 새내기연구참여

- 랩마다/교수님마다 내용이 다르지만, 내가 참여한 연구실의 경우 매주 공부한 내용에 대해 질문을 받으시고, 앞으로 읽어볼 논문/공부해볼 내용 등을 추천해 주시는 시간이었다.
- 처음에는 TVM과 같은 딥러닝 컴파일러에서 사용되는 auto-tuning 기법 (TASO, TenSet, Unity 등)에 대한 공부를 했지만, 머신러닝이 나오면 집중을 잘 하지 못한다는 본인의 역량 문제로 딱히 집중을 잘하진 못했다.
- 중간에 일반적인 컴파일러 쪽으로 방향을 틀었고, LLVM 튜토리얼을 돌면서 간단한 컴파일러 프론트엔드를 만드는 토이 프로젝트를 했는데 또 이쪽은 적성에 잘 맞아서 재밌게 코딩했다. 이렇게 진행한 프로젝트는 [`stapl`](https://github.com/sohnryang/stapl)에서 계속 진행 중이다.

#### CSED233 데이터구조

[[GitHub]](https://github.com/sohnryang/csed233)

- 리스트, 스택, 큐 등의 간단한 자료 구조부터, B-tree, binary search tree, AVL tree 등의 트리 종류, 그리고 그래프 알고리즘에 대해서 배우는 과목이다.
- 프로그래밍 과제를 통해 자료 구조를 C++으로 직접 구현해 본다. 구현한 코드를 검증하는 데 사용할 수 있는 테스트 케이스를 제공하는데, CMake를 써서 자동화하기 매우 좋다.
- C++으로 코딩하기 때문에, [LLVM libfuzzer](https://www.llvm.org/docs/LibFuzzer.html)를 사용해서 fuzzing을 수행하면서 버그를 탐색해 볼 수 있었다.

#### CSED490E 컴퓨터공학특강: 알고리즘 및 문제해결 실습

- 백준 문제를 풀면서 PS에 입문하는 강의이다.
- 매 수업 때마다 2~3문제 정도 숙제로 풀어야 할 백준 문제가 나온다.
- 나의 경우에는 높은 확률로 숙제에 이미 풀어본 문제가 나와서, 언어 연습도 할 겸 Rust 또는 Go로 다시 구현해보았다.

#### MATH102 미적분학2

- 다변수 미적분을 다루는 과목이다.
- 증명 난이도를 고려해서인지 1학기의 미적분학1에 비해서는 증명이 줄고 계산이 늘어난 느낌을 받았다.

### 2023 Spring

#### CSED232 객체지향프로그래밍

#### CSED273 디지털시스템설계

#### CSED331 알고리즘

#### MATH203 응용선형대수

#### MATH210 응용복소함수론

#### MATH311 해석학1

### 2023 Fall

#### CSED211 컴퓨터SW시스템개론

#### CSED312 운영체제

#### CSED341 오토마타및형식언어

#### MATH230 확률및통계

#### MATH261 이산수학

#### MATH312 해석학2

### 2024 Spring

#### CSED311 컴퓨터구조

#### CSED321 프로그래밍언어

#### CSED353 네트워크

#### CSED451 컴퓨터그래픽스
