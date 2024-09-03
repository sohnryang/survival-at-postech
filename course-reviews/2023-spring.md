# 2023 Spring

## CSED232 객체지향프로그래밍

[[GitHub]](https://github.com/sohnryang/csed232)

- C++에 입문하는 과목이다.
- C++ 과목임을 감안하여도 사용할 수 있는 C++ 표준 버전이 높은 편이다. Visual Studio 기본 설정에서 쓸 수 있는 문법은 모두 사용할 수 있기 때문에, 적어도 C++14는 사용할 수 있다. 또한 Qt 과제는 C++17도 사용할 수 있었다.
- 데이터구조 과목과 마찬가지로 CMake를 셋업했고 GoogleTest를 통한 단위 테스트를 작성했다.
- 수업과 과제는 Visual Studio를 사용한다고 가정하고 진행되지만, Visual Studio 프로젝트 파일 외에 Makefile 제출도 받기 때문에 macOS/Linux를 사용하여도 과제를 할 수 있었다.
- 마지막 과제는 Qt로 GUI 프로그래밍을 하는 전통이 있다.

## CSED273 디지털시스템설계

[[GitHub]](https://github.com/sohnryang/csed273) [[Final Project]](https://github.com/sohnryang/csed273-final-project)

- 디지털 논리회로의 이론과 실제 구현을 배우는 과목이다.
- Verilog를 사용해 실습을 진행하는데, Vivado 환경에서 코딩해야 하기 때문에 Apple Silicon Mac 사용자는 VM이 필수이다.
- 쓸만한 윈도우 VM을 사용하기 위해서는 보통 Windows on ARM을 설치하고, Vivado와 같은 x86-64 프로그램은 에뮬레이션을 통해 구동하게 된다. 2023년 기준으로 동시성 관련 버그가 x86 emulation에 존재하는지 그냥 실행하면 simulation이 정상적으로 동작하지 않았다. 이를 해결하기 위해서는 Vivado에 포함된 exe 파일에 대해 일일이 에뮬레이션 설정을 바꾸어 단일코어만 사용하도록 바꿔야 했다.
  - `C:\Xilinx\Vivado\[비바도 버전]\bin\unwrapped\win64.o`에 있는 `exe` 파일들에 대해서 [속성] ➡️ [호환성] ➡️ [에뮬레이션 설정 변경]으로 간 뒤 [고급 설정 사용]을 켜고 멀티코어 설정에서 [단일코어 작업 강제]으로 바꾸면 된다.
- 또한 Apple Silicon Mac에서 Windows on ARM VM을 사용하는 경우에는 실습에 사용하는 보드를 연결하기 위해 따로 드라이버를 설치해 주어야 한다. [FTDI 공식 드라이버](https://ftdichip.com/wp-content/uploads/2022/02/CDM-v2.12.36.4-for-ARM64-Signed-Distributable.zip)를 사용하자.
- 매 실습마다 작성하는 보고서는 LaTeX으로 썼는데, Vivado에서 회로도를 PDF로 저장하는 기능이 있어서 요긴하게 써먹었다. PDF로 저장하면 벡터 이미지 형태로 회로도가 나오기 때문에 확대해도 깨지지 않는다.
- 학기말에 파이널 프로젝트를 팀으로 하게 되고, FPGA에서 구동되는 회로를 처음부터 설계하는 것이 목표이다. 우리 팀의 경우에는 당시 내가 [유튜브에서 재밌게 보았던](https://www.youtube.com/watch?v=D_DdyxvSdpA) 요트 다이스 게임을 구현하였다.
  - 원래 목표는 dot matrix 디스플레이에 주사위를 그리는 것이었는데, 부품 수급 이슈로 온보드 LED에 2진수로 표시하는 것으로 만족해야 했다.


## CSED331 알고리즘

[[GitHub]](https://github.com/sohnryang/csed331)

- 알고리즘은 교수님마다 수업 방식이 다른데, 2023 봄학기의 경우에는 코딩 과제와 증명 과제 두 가지 모두 나왔다.
- 코딩 과제는 online judge 사이트에 올라온 문제를 해결하는 것이었다. 사용할 수 있는 언어는 C/C++, Python, Java 정도였다.
- 코딩 과제로 나온 토픽은 다음과 같다. 가끔은 백준에서 비슷한 문제를 확인할 수도 있었다.

| ASSN | 키워드                                                       | 참고 문제                                                    |
| ---- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 1    | 정렬 알고리즘의 응용                                         |                                                              |
| 2    | 분할 정복, linear-time selection, 평면 위에서 가장 가까운 점 | [BOJ#2261](https://www.acmicpc.net/problem/2261), [BOJ#1933](https://www.acmicpc.net/problem/1933) |
| 3    | 그래프 탐색 (BFS, DFS), 단절선                               | [BOJ#11266](https://www.acmicpc.net/problem/11266)           |
| 4    | 위상 정렬, 최단 경로 알고리즘                                | [BOJ#1649](https://www.acmicpc.net/problem/1649)             |
| 5    | 그리디 알고리즘, minimum spanning tree                       | [BOJ#6549](https://www.acmicpc.net/problem/6549)             |
| 6    | Dynamic programming, 행렬 곱셈을 사용한 동적 계획법의 최적화, parametric search |                                                              |

## MATH203 응용선형대수

- 기초적인 선형대수를 배우는 과목이다. 연립방정식부터 시작해서 벡터 공간, 행렬식, 다양한 decomposition 등의 주제를 다룬다.
- 2023 봄학기에는 과제가 없는 대신 매주 퀴즈가 있었다.

## MATH210 응용복소함수론

[[GitHub]](https://github.com/sohnryang/math210)

- Analytical function에서 시작헤 Cauchy-Goursat theorem, Maximum modulus principle, Laurent series, 다양한 적분 테크닉 등을 배워 본다.
- 맨 마지막에는 conformal mapping에 대해 배우는데, 미분방정식에 대해 배웠다면 이게 어떻게 쓸모있는지를 알 수 있지 않았을까 하는 아쉬움이 있다.
- 매주 숙제가 나오는 과목이고, 나는 LaTeX으로 작성해서 제출했다.
- 숙제는 개인적인 생각으로는 책에 있는 내용을 적당히 적용만 하면 바로 풀리는 문제가 대부분이었지만, 채점이 상당히 깐깐해서 statement를 적을 때 놓치고 있는 부분이 없는지 많이 생각해 보아야 했다.

## MATH311 해석학1

[[GitHub]](https://github.com/sohnryang/math311)

- 2023 봄학기에 가장 열심히 들었던 과목이다. 시험 때도 다른 과목은 제물로 바치다시피 해서 하루전에 공부하고 해석1만 열심히 봤던걸로 기억한다. (~~교수님 눈 감으세요...~~)
- 실수의 성질부터 기본적인 topology, 수열, continuity, 미분, 적분을 배운다.
  - Baby rudin 기준 chapter 1-6이다.
- 매주 숙제가 나오는 과목이고, 나는 LaTeX으로 작성해서 제출했다.
- 숙제는 내 머리로는 상당히 어려웠고, 숙제하다가 새벽 4시쯤 자는 일이 꽤 많았다.
- 수업에 사용한 교재가 꽤나 유명한 baby rudin임에도 불구하고, 인터넷에서 찾을 수 있는 솔루션에 틀리거나 증명을 불충분하게 하고 넘어가는 내용이 있는 경우가 자주 있었다.
  - 보통 숙제하다 막히는 이유는 무언가 아이디어는 있는데 그걸 만족할만한 수준으로 증명을 못했기 때문이었기 때문에, 몰라서 솔루션을 본다고 해도 도움이 되지 않았다..
  - 잘 풀리지 않는 문제는 일단 혼자 이것저것 시도를 하면서 시간을 쓰고 :arrow_right: 인터넷에서 찾을수 있는 솔루션에서 아이디어를 모은 다음 :arrow_right: 쓸 만한 아이디어를 모아서 만족할만한 증명을 만드는 과정으로 해결했다.