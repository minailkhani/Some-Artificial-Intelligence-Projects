# 8-puzzle solver using DFS, BFS, IDS, UCS, A*
In this problem, we have a 3 x 3 square with 8 labels. The states are set from 1 to 8 and one state is empty (you can assign the number zero to it). We want to sort the states in increasing order. You are allowed to move the states vertically or horizontally to arrive in the requested order.

### example:
![image](https://user-images.githubusercontent.com/83788223/221373596-80226403-f2c3-4ec3-8891-d2d7b2fa2d4e.png)

states: a permutation from 0 to 8 

operator(Actions): moving tile 0 (blank) horizontally or vertically and only one step 

Goal state: all the tiles are in ascending order and at the end it is empty or zero 

Transition model: A permutation from 0 to 8 and an action is given and zero moves in the direction of the action.

Initial state: The board that is given at the beginning (note that half of the initial states cannot reach the goal state. The formula and the reason for this are explained in class. In this question, all the initial states are such that they reach the answer.)

Heuristic: the total distance of each tile to its original location. The distance of the tile to its original location is calculated by assuming that there is no tile in the way and we count the number of horizontal and vertical movements that bring the tile to its original location. We can use other heuristics such as the number of tiles that are not in their place. But this definition has a greater distance than the previous definition in terms of the distance (number of steps) to reach the solution, and we know that the smaller heuristic to the actual distance to the goal state, the better the algorithm works.

path cost: -1 (for each step)

## implemention:

![image](https://user-images.githubusercontent.com/83788223/221376839-12bcbc84-f4e2-4db6-a77a-ba6dfd26cc29.png)

The diffrence between DFS, BFS, IDS and A* is the Queuing function

These algorithms have a tree structure. So, we implement node, which is actually a state and holds father, child, depth, and f. (I will explain about f later). Also, to sort the states (nodes) in A* and UCS algorithm, we need to have order on them. We consider order with depth and implement it with operator overloading.

For A* and UCS, we use queue.PriorityQueue, which has a library in Python, for queue, and for IDS and BFS, which has no relation to the order defined on the node class, we use Python's own queue, and for DFS, LifoQueue (first in, first out ) We use.

### example: 
We have 3 groups of examples: easy, medium, and hard 
### comparing space complexity:
![image](https://user-images.githubusercontent.com/83788223/221377127-0ef2c273-9908-4f49-9b1c-d5a01d32899a.png)


### comparing time complexity:
![image](https://user-images.githubusercontent.com/83788223/221377230-c87b5ab2-1187-4457-9aa3-491f9a9841b3.png)


time and space complexity for each instance and each algorithm is available in the xlsx file

solution(DFS) to an example (the order of printing the steps of the solution is from the goal state to the initial state: \
![image](https://user-images.githubusercontent.com/83788223/221377847-537388c2-4de1-4a25-8402-36e11e9c66bd.png)


