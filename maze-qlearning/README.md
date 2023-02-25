# Maze solver using q-learning algorithm
In this problem, an environment is given to the program. The environment contains a series of navigable paths marked with white color. The starting point of the agent is also determined. The goal is to exit this environment, which is achieved by reaching the end point. It is also essential that the agent passes all the flags in the environment. They are marked in red in the figure below. W stands for Way, B stands for  Block, F stands for Flag, A stands for Agent, and T stands for Target. \
![image](https://user-images.githubusercontent.com/83788223/221370728-1437e601-920f-49b8-b1ed-f72c7bea7041.png)

States: each state is an object that contains:\
1)type of the state(way, flag, target, block, visited) \
2)the location of the agent\
3)number of visited flags\
4)reward for visiting that state

actions: Horizontal and vertical movement provided that it does not go outside the environment and into the blocks 

rewards:We consider a negative number (not too big) for w. (Because our goal is to find the shortest path, if the reward for w is non-negative, we will not reach the optimal solution). We consider negative infinity for b so that their selection is never a good choice. For f's, it is a positive number and is bigger than the reward for w, and after every f is visited once, its value is equal to the w that has been visited once, and after that, it is treated like a w. For t, we consider a number larger than reward for f. And also, in order to avoid going to repeated states, we attribute a smaller negative reward to the state after each visit.

Goal state: reaching t while the shortest path has been traveled so that all f's have been visited.

## implementing
algorithm:\
![image](https://user-images.githubusercontent.com/83788223/221371822-8435232d-374b-407b-8c00-3b5bb0a3a82e.png)

Due to the fact that the problem is a complex problem, we have made minor changes in the algorithm. For example, in the i-th time of execution, a maximum of i steps can be taken. As a result, we run the algorithm more times, the rewards of the initial steps are closer to the desired state, so we can have exploration for the first steps. This is extremely useful.

there are 600 episodes \
I tried the values 0.25, 0.5, 1 for lambda and alpha and figured out that 1 for alpha and 0.5 for gamma are the best values \
### q-table:
![image](https://user-images.githubusercontent.com/83788223/221372694-400b7675-f5f3-4a93-99bf-f1aa9e0c7782.png)

### q_table graph:
![image](https://user-images.githubusercontent.com/83788223/221372410-f14ae905-67ab-4e86-85e8-ce553e7210b8.png)

