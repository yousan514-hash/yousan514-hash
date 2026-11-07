# Fujita

**シミュレーションで先に試して、ロボット × AI を現場に届けるエンジニア**を目指しています。

- 仕事: 製造業で、シミュレーション（NVIDIA Isaac Sim・Omniverse）と画像検査（OpenCV）の開発
- 個人: ROS 2、双腕ロボット、画像計測、ロボット × ブロックチェーン
- 考え方: AI やロボットが働き、記録され、支払われる世界で、「何を良い仕事とするか」を決めて価値を加える

![双腕の外観検査セルを RViz で動かしているところ](https://raw.githubusercontent.com/yousan514-hash/ros2-learning/main/docs/dual_arm_rviz.png)

## 作ったもの

| リポジトリ | 中身 | 確かめたこと |
|---|---|---|
| [双腕の外観検査セル](https://github.com/yousan514-hash/ros2-learning/tree/main/src/dual_arm_inspection) | 自作の 6 軸 × 2 の腕で、左手が部品を持ち、右手の手首カメラで面ごとに撮る。良品だけで学ぶ 3 段判定（OK／NG／保留）。ROS 2・RViz | 逆運動学は動きの目標 65 点すべてで上下限の中／腕どうしは最短 5.2 cm／疑似画像 200 枚で見逃し 2%・過検出 0% |
| [稼働台帳 robot_ledger](https://github.com/yousan514-hash/ros2-learning/tree/main/src/robot_ledger) | ロボットの稼働を Ed25519 の署名とハッシュの鎖で記録し、使用範囲の中の仕事だけを数えて請求額を出す | 改ざん・別の鍵で作った偽の台帳を見抜くテスト 12 件 |
| [ledger-verify-skill](https://github.com/yousan514-hash/ledger-verify-skill) | 署名つき稼働台帳を公開鍵だけで確かめる AI エージェントのスキル（Agent Skills の形。Claude Code・OpenClaw 共通） | ハッシュの鎖・Ed25519・使用範囲書の指紋・受け取りの署名・請求件数を確かめ、壊れた行を返す。pytest 28 件 |
| [count-and-measure](https://github.com/yousan514-hash/count-and-measure) | 写真から物を数えて、大きさを mm で測る（OpenCV・ArUco・射影変換） | 悪い撮影条件 40 通りで検証し、直せない条件は撮り方のルールにした。Windows と Linux で自動テスト |
| [ros2-learning](https://github.com/yousan514-hash/ros2-learning) | ROS 2 を Windows ネイティブ（Jazzy・pixi）と WSL2（Ubuntu 22.04 ＋ Humble）の両方で | 詰まったこと（古いランタイム・アプリ制御・WSL）を原因から解決した記録 |

## 取り組み中

- 双腕の検査セルを Isaac Sim に載せて、合成画像（Replicator）と疑似画像の当たり外れを比べる
- MoveIt 2 でアームの経路を計画し、シミュレーションと実機の差を詰める
- OSS への参加（OpenMind / OM1-sim に修正の PR を提出）

## 使っている技術

Python ・ ROS 2（Jazzy / Humble）・ NVIDIA Isaac Sim / Omniverse ・ OpenCV ・ Linux（Ubuntu / WSL2）・ pixi ・ Git / GitHub Actions
