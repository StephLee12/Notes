- [Details of Final Report](#details-of-final-report)
  - [Envs](#envs)
    - [Cartpole-v0](#cartpole-v0)
    - [LunarLander-v2](#lunarlander-v2)
  - [PPO](#ppo)
  - [DQN(Deep Q-Learning)](#dqndeep-q-learning)
  - [DDQN(Dueling Deep Q-Learning)](#ddqndueling-deep-q-learning)

# Details of Final Report

## Envs

### Cartpole-v0

👉 小车需要左右移动来保持杆子竖直

👉 游戏继续进行的两个条件

- 杆子倾斜的角度$\,\theta\,$不能大于15度
- 小车移动的位置保持在一定范围(中间到两边各2.4单位长度)

👉 与环境交互返回的变量

- action: shape——2 0 or 1 代表左移右移
- observation(state):shape——4 依次为小车在轨道的位置、杆子与竖直方向的夹角、小车速度、角度变化率
- reward:只要采取一个action，会获得+1的reward，当一个回合的奖励达到200时，游戏结束，即游戏的最大步长为200个时间步
- done:判断一个回合是否结束

### LunarLander-v2

👉 agent平稳落地

👉 与环境交互返回的变量

- action: shape——4
  - 0——do nothing
  - 1——左引擎发动
  - 2——主引擎发动
  - 3——右引擎发动
- observation:shape——8 前两个元素为agent的坐标
- reward:
  - 根据落地平稳程度和燃料使用多少打分
  - 一个回合内agent平稳降落到地面的reward大概在100-140之间
  - 如果回合结束时agent坠毁,reward倒扣100
  - 如果回合结束agent到达旗子处，reward附加100
  - 游戏结束的reward为200

## PPO

## DQN(Deep Q-Learning)

## DDQN(Dueling Deep Q-Learning)