# 2024 Spring

## CSED311 컴퓨터구조

[[GitHub]](https://github.com/sohnryang/csed311)

- 컴퓨터 아키텍쳐에 대해 배우는 과목이다. CPU의 설계, memory hiearachy, 병렬성, GPGPU, Domain Specific Accelerator, 스토리지 디바이스 등에 대해 배운다.
- 강의 중에 좋은 질문을 하면 크레딧을 준다! 이게 없었으면 수업에 집중을 못했을 것 같다.
- 프로그래밍 과제는 5-stage in-order RISC-V core를 베릴로그로 구현하는 것이다.
  - Single cycle에서 시작해서 파이프라인을 추가하고 L1캐시를 붙이기까지 매우 재밌는 경험이었다.
  - 이번 학기부터 Vivado 대신 verilator를 사용하는 것으로 바뀌어서 가상머신 없이 시뮬레이션을 실행할 수 있다는 점도 좋았다.
- 프로그래밍 과제는 2인1팀으로 진행하게 되는데, OS 때와 마찬가지로 훌륭한 팀원 [@Aplace0927](https://github.com/Aplace0927) 덕분에 수월하게 과제를 수행할 수 있었다.
- 베릴로그가 다른 일반적인 프로그래밍 언어와는 상당히 다른 동작을 보이는데, 나의 경우에는 reactive programming과 비슷한 방식으로 동작한다고 생각하면 이해하기 편했다.
  - Reactive programming을 그렇다고 굳이 정식으로 공부할 필요는 없고, vue.js와 같은 프론트엔드 프레임워크를 생각하면 편할 듯 하다.


## CSED321 프로그래밍언어

[[GitHub]](https://github.com/sohnryang/csed321)

- 프로그래밍 언어 이론에 대해 배우는 과목이다. Untyped/simply typed lambda calculus, mutable reference, environment semantics, exceptions, subtyping, recursive types, polymorphism을 다뤘다.
- 어떻게 보면 이 과목이 대학교에 온 이유이기도 하기 때문에, 개인적으로 가장 재밌게 들었던 과목이었다.
- 프로그래밍 과제는 OCaml을 사용하고, 다음과 같은 과제가 나왔다.

| 과제 | 내용                                                 |
| ---- | ---------------------------------------------------- |
| 1    | 기본적인 함수형 프로그래밍                           |
| 2    | 기본적인 함수형 프로그래밍 (Tail recursion, modules) |
| 3    | 기본적인 함수형 프로그래밍 (modules)                 |
| 4    | Untyped lambda calculus 인터프리터                   |
| 5    | Simply typed lambda calculus 타입체커                |
| 6    | Call-by-need에 기반한 environment semantics          |
| 9    | FeatherWeight Java 인터프리터, 타입체커              |
| 7    | SML subset을 machine code로 컴파일하기               |

- 마지막으로 나온 프로그래밍 과제는 다 구현만 했다면 A0는 기본적으로 나온다는 소문이 있을 만큼 어려운 난이도를 자랑한다.
  - 내 구현에서는 SSA-like 형태인 IR로 일단 lowering한 다음, 이 IR에서 나온 레지스터를 함수 스택 공간에 매핑시키는 방법으로 구현하였다.
  - SSA-like IR인 이유는 PHI node를 사용하지 않고, heap memory를 사용하는 동작의 경우에는 스택에 push/pop을 수행하면서 레지스터 하나의 값을 계속 변경하기 때문이다. 여담으로, 우리가 구현해야 하는 SML subset은 control flow의 분기가 함수의 맨 처음에서만 일어나기 때문에 PHI node는 어차피 필요하지 않았다.
  - 시간이 좀 더 있었다면 IR 설계를 조금 더 꼼꼼하게 하고, 스택에 모든 변수를 저장하는 대신 register allocation을 했을 것 같다.
  - 마지막 과제를 모두 구현하려는 계획이 있다면, 우선 calling convention부터 고민하고 시작하는 것이 좋을 것이다.
- 프로그래밍 과제에서 사용하는 OCaml 버전이 4.05로 상당히 낮다.
  - 단순히 버전만 낮은 것이라면 크게 문제가 되지 않겠지만, 안타깝게도 language server를 포함한 대부분의 OCaml 개발 도구는 최소 4.06 버전을 요구하기 때문에 4.05 버전에서는 개발이 상당히 힘들어진다. 부수적으로 Apple Silicon Mac에서는 OCaml 4.05를 AArch64 `opam`으로 설치할 수 없기 때문에, 마지막 과제를 제외하고는 OCaml 4.14에서 API 버전에 주의하면서 코딩하였다.
  - 마지막 과제에서는 `typing` 모듈이 소스 코드 대신 `.cmo` binary blob으로 제공되는데, `.cmo` binary blob은 호환성이 보장되지 않기 때문에 OCaml 4.14에서 컴파일할 수 없다. 해결하는 데에는 여러 방법이 있겠지만, 나는 x86 `opam`을 설치해서 4.05 버전의 switch를 만든 다음 빌드할 때만 이 4.05 버전의 switch를 사용하였다. 개발할 때는 `typing.cmo` 파일을 지우고 `typing.ml` 파일에 언제나 `NotImplemented` 예외만 발생시키는 코드만 넣어 두어 타입체킹은 통과한 상태로 두었다가, 빌드할 때 지웠던 `typing.cmo` 파일을 `git restore`하고 4.05 버전 switch를 사용해 컴파일하도록 [간단한 스크립트](https://github.com/sohnryang/csed321/blob/main/hw7/build.sh)를 작성하였다.
- OCaml REPL은 언어 기본 REPL 치고도 상당히 불친절하기 때문에, 가능하다면 `utop`을 사용하자.

## CSED353 네트워크

[[GitHub]](https://github.com/sohnryang/csed353)

- 컴퓨터 네트워크에 대해서 배우는 과목이다. Application layer부터 시작해서 link layer까지 top-down 방식으로 네트워크의 구성 요소를 다룬다.
- 프로그래밍 과제는 Stanford CS144의 Sponge를 사용하는데, minimal working TCP stack을 구현하는 좋은 경험을 할 수 있다.
  - 특히 프로젝트를 CMake로 셋업해 두었고, C++17과 AddressSanitizer를 사용하여 편안하게 개발할 수 있다는 점이 매력적이었다.
  - 특이하게도 가장 어려운 과제는 마지막이 아니라 중간에 있다. TCP connection을 구현하는 것이었는데, 다 구현했고 테스트도 모두 통과하는 상황에서 벤치마크를 돌린다는 점에 꽂혀서 안해도 되는 성능이 나왔는데도 밤새 FlameGraph를 보면서 최적화를 했다.
  - 마지막 과제에서는 완성된 TCP stack을 사용해서 다른 사람의 구현과 파일을 주고받는 것이었다. [나름 대용량인 영상 파일](https://www.youtube.com/watch?v=dQw4w9WgXcQ)로 테스트해 봤을 때 1.5 MiB/s 이라는 준수한 속도가 나왔다.

- 오픈북 오픈 인터넷이라는 시험 포맷을 사용하는데, 암기를 싫어하는 나에게는 개인적으로 매우 마음에 들었다. 중간고사 때에는 live coding 문제도 나와서 first blood를 따는 소소한 즐거움도 챙길 수 있었다.

## CSED451 컴퓨터그래픽스

[[GitHub]](https://github.com/sohnryang/csed451) [[Term Project]](https://github.com/sohnryang/csed451-term-project)

- 컴퓨터 그래픽스에 대해 배우는 과목이다. 2D 그래픽, transformation, hierarchial modeling, view matrix, rasterization, shader, texture, rendering, curve를 다룬다.
- 프로그래밍 과제는 유사 [길건너 친구들](https://www.crossyroad.com/) 게임을 OpenGL을 사용해 단계적으로 구현하는 것이었다.
  - 2D에서 시작해 hierarchial modeling, 3D rendering, shader, texture mapping을 적용하게 된다.
  - 최근 게임 개발에서 많이 사용되는 [ECS 구조](https://en.wikipedia.org/wiki/Entity_component_system)를 사용해 설계하였는데, 지금 돌아보면 굳이 그래야 했을까 하는 생각이 들긴 한다.
  - 나는 Apple Silicon Mac을 사용하고, 팀원은 Windows 환경이었기 때문에 CMake를 사용해 cross compile이 되는 환경을 만들어 사용하였다. 이 환경에서 개발은 매끄럽게 잘 되었지만 제출은 Visual Studio 프로젝트 파일 형식이어야 했기 때문에 과제 듀 30분 전에 헐레벌떡 프로젝트를 만들어서 내는 경험을 할 수 있었다.
- 학기말에는 term project를 해야 한다. 원래 3인1팀으로 해야 하지만 팀원을 못구해서 2인1팀으로 했고, Vulkan compute shader를 사용해 GPU accelerated ray tracer를 만들었다.
  - Vulkan을 겁 없이 고른 이유는 단순히 Apple Silicon Mac과 Windows 모두에서 돌아가는 그래픽스 스택이 그것밖에 없어서 였는데, 초심자에게 Vulkan은 너무 가혹했다. 차라리 WebGPU 쓸걸...
  - 그냥 ray tracer를 짜면 novelty가 없기 때문에, 포탈을 시뮬레이션할 수 있도록 구현하였다.
  - 텀프는 미리미리 해두자. 그렇지 않으면 최종발표 [전날](https://github.com/sohnryang/csed451-term-project/commit/90fd76d0907d90d67b0fd7ecccf0e878be47bde6) [밤에](https://github.com/sohnryang/csed451-term-project/commit/61de2ff99f604a43ba9ada311336637935de0466) [밤샘을](https://github.com/sohnryang/csed451-term-project/commit/722a596a64cc9e4459ccfcc95a6f70b30e10c994) [달리게](https://github.com/sohnryang/csed451-term-project/commit/63fb299810add10d5283cca9fee420cc1b02bd84) 될 것이다.
- 프로그래밍 과제와 텀프 모두 훌륭한 팀원 [@m4080m](https://github.com/m4080m) 덕분에 수월하게 수행할 수 있었다.