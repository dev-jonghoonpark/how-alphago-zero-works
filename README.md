# How AlphaGo Zero Works

**기보 없이, 탐색을 선생 삼아.** AlphaGo Zero는 사람 기보를 한 장도 보지 않고 무작위 가중치에서 시작해, 자기대국과 탐색만으로 사흘 만에 이세돌을 이긴 AlphaGo를 100:0으로 이겼습니다. Silver 외 「Mastering the Game of Go without Human Knowledge」(Nature 550, 2017)를 따라가며, 선생이 없는데 무엇을 정답 삼아 배웠는지를 브라우저에서 직접 실험해 보는 인터랙티브 교육 자료입니다.

🔗 **[데모 바로가기](https://dev-jonghoonpark.github.io/how-alphago-zero-works/)**

이 자료의 축은 **라벨의 출처가 사람에서 탐색으로 바뀌었다**는 것입니다. 학습 식은 지도학습과 거의 같고, 정답만 "사람이 둔 수"에서 "자기 신경망으로 MCTS를 돌려 얻은 방문 분포 π"로 바뀌었습니다.

## 다루는 내용

1. **무엇이 달라졌나** · AlphaGo(2016)와 나란히 놓기: 기보, 손으로 만든 특징, 별도 정책망, 롤아웃이 빠졌다
2. **입력: 17장의 평면** · 7×7 판에 직접 두며 X·Y·C 평면이 채워지는 과정 보기, 패가 과거 평면을 요구하는 이유
3. **신경망: 몸통 하나, 머리 둘** · ResNet 20/40블록 구성과 가중치 수, sep/dual × conv/res 비교(각 약 600 Elo)
4. **탐색: 롤아웃 없는 MCTS와 PUCT** · 사전확률 P를 탐색이 π로 고쳐 쓰는 과정, c_puct·온도 τ·루트 디리클레 잡음
5. **학습: 탐색이 선생이다** · (s, π, z) 표본과 손실 (z − v)² − πᵀ log p + c‖θ‖², 정책 반복
6. **미니 AlphaZero** · 브라우저에서 무작위 가중치부터 실제로 학습하는 틱택토 AlphaZero(양머리 신경망 + PUCT MCTS + 자기대국), 학습한 신경망의 p·π·v 들여다보기
7. **파이프라인** · 최적화·평가(55% 관문)·자기대국, 온도 일정, 기권, 대칭, 병렬 탐색
8. **결과** · 3일 만에 AlphaGo Lee 100:0, 40일 만에 AlphaGo Master 89:11, Elo 5,185, 지도학습과의 비교
9. **무엇을 배웠고 무엇을 받았나** · 정석의 발견과 폐기, 늦게 배운 축, 주어진 도메인 지식 목록
10. **그 뒤** · AlphaZero, MuZero, 추론 모델과의 연결
11. 정리와 퀴즈 8문항

## 참고

- Silver et al. (2017), *Mastering the game of Go without human knowledge*, Nature 550 — [nature.com](https://www.nature.com/articles/nature24270)
- Silver et al. (2016), *Mastering the game of Go with deep neural networks and tree search*, Nature 529
- Silver et al. (2018), *A general reinforcement learning algorithm that masters chess, shogi, and Go through self-play* — [arXiv:1712.01815](https://arxiv.org/abs/1712.01815)
- Schrittwieser et al. (2020), *Mastering Atari, Go, chess and shogi by planning with a learned model* — [arXiv:1911.08265](https://arxiv.org/abs/1911.08265)

앞선 편: [How AlphaGo Works](https://github.com/dev-jonghoonpark/how-alphago-works)

[how-ai-works](https://github.com/dev-jonghoonpark/how-ai-works) 시리즈의 일부입니다.
