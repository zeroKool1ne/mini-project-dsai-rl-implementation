# Presentation: Reinforcement Learning — Grid World
**10 Minutes | DNL**

---

## 1. Problem Introduction — 2 Minutes

**What did I choose?**
> Grid World — an agent navigates through a 10x10 maze from start to goal, without hitting walls.

**What to say, what to show:**
- "I chose Grid World because it's the most intuitive problem — you can directly see what the agent is doing."
- "The maze is a 10x10 matrix. Zeros are free cells, ones are walls."
- "The agent starts top-left, the goal is bottom-right."
- Show notebook: **Cell 1** (Maze array)

**Why is this interesting for RL?**
> "The agent has no map — it doesn't know where the goal is. It has to find out through trial & error."

---

## 2. Algorithm Explanation — 3 Minutes

**Which algorithm?**
> Q-Learning

**How it works — simple explanation:**
> "Imagine learning a new video game. At first you press random buttons. Over time you notice: if I go left here, I get closer to the goal. You store that experience."

**That's exactly Q-Learning:**
- The agent stores a value for every state and action in the **Q-table**
- Good actions → higher value
- Bad actions → lower value
- Over time the table learns the best path

**Key Parameters:**
| Parameter | What it does |
|---|---|
| `alpha = 0.1` | How fast it learns |
| `gamma = 0.9` | Future rewards count almost as much as immediate ones |
| `epsilon = 0.5 → 0.01` | Starts with lots of exploration, becomes more targeted over time |

**Rewards:**
- Goal reached: **+50**
- Hit a wall: **-10**
- Each step: **-1** (so it looks for the shortest path)

---

## 3. Implementation Demo — 3 Minutes

**What to show, what to say:**

1. Open notebook, show **Cell 2** (Parameters)
   > "Here I set all parameters. The Q-table has shape 10x10x4 — for every cell, each of the 4 directions."

2. Show **Cell 3** (choose_action)
   > "ε-greedy: with probability epsilon it picks randomly, otherwise it uses the best known action."

3. **Cell 4** — run the training
   > "5000 episodes. The formula updates the Q-table after every action."

4. **Cell 6** — show maze plot
   > "This is the learned path — the agent figured out on its own how to get through."

5. **Cell 7** — show rewards plot
   > "Here you can see how the rewards increase over time — the agent is getting better."

---

## 4. Results and Analysis — 2 Minutes

**How well did it work?**
> "After training, the agent reliably finds a path through the maze. The learning curve shows a clear upward trend."

**Challenges:**
> "Epsilon decay was tricky — too fast and the agent explores too little and gets stuck in bad solutions. Too slow and it doesn't converge."

**What would I do differently?**
> "I would train more episodes and compare different epsilon decay rates. Or make the maze bigger."

---

## 5. Resources & Key Insights — 1 Minute

**Resources:**
- GeeksForGeeks — What is Reinforcement Learning
- OpenAI Gym Documentation

**Key Insight:**
> "The most interesting part was the Exploration-Exploitation dilemma. Too much exploration = the agent doesn't learn. Too little = it never finds the best path. That applies to real life too, by the way."

---

## Q&A — Likely Questions & Answers

**"Why Q-Learning and not SARSA?"**
> "Q-Learning is off-policy — it learns the optimal policy regardless of what the agent is currently doing. Simpler to implement as a starting point."

**"What's the difference to Deep Learning?"**
> "With Q-Learning we store a table — works well for small state spaces. With Deep Q-Learning a neural network replaces the table — needed when the state space is huge, e.g. Atari games."

**"Why epsilon at 0.5 in the beginning?"**
> "At the start the agent knows nothing — it should explore a lot. Over time epsilon drops to 0.01, so it mainly uses what it has learned."

**"Could the agent fail?"**
> "Yes — if epsilon decays too fast or rewards are set incorrectly, it won't converge. That's also a common problem in real RL projects."
