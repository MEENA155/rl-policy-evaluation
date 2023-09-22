# POLICY EVALUATION

## AIM
To develop a Python program to evaluate the given policy.

## PROBLEM STATEMENT
The bandit slippery walk problem is a reinforcement learning problem in which an agent must learn to navigate a 7-state environment in order to reach a goal state. The environment is slippery, so the agent has a chance of moving in the opposite direction of the action it takes.
### States:
The environment has 7 states:

1. Two Terminal States: G: The goal state & H: A hole state. 
2. Five Transition states / Non-terminal States including S: The starting state.

### Actions:
The agent can take two actions:

R: Move right. 
L: Move left.
### Transition Probabilities:
The transition probabilities for each action are as follows:

50% chance that the agent moves in the intended direction. 33.33% chance that the agent stays in its current state. 16.66% chance that the agent moves in the opposite direction. For example, if the agent is in state S and takes the "R" action, then there is a 50% chance that it will move to state 4, a 33.33% chance that it will stay in state S, and a 16.66% chance that it will move to state 2.
### Rewards:

The agent receives a reward of +1 for reaching the goal state (G). The agent receives a reward of 0 for all other states.
### Graphical Representation:
![268425166-53ee31d4-511d-4241-807e-a5f5d6b16fc2](https://github.com/MEENA155/rl-policy-evaluation/assets/94677128/419ae4d1-767e-498f-ac81-322cb2ed286c)

## POLICY EVALUATION FUNCTION

![268425175-91f3edf0-94b0-4c81-b7dd-61c28497472f](https://github.com/MEENA155/rl-policy-evaluation/assets/94677128/3ba4d2e7-6796-4d9a-8837-d50cf047f85e)
## Program:
```
Register Number: 212221240028
Name:   Meena S
def policy_evaluation(pi, P, gamma=1.0, theta=1e-10):
    prev_V = np.zeros(len(P), dtype=np.float64)
    # Write your code here to evaluate the given policy
    while True:
      V = np.zeros(len(P))
      for s in range(len(P)):
        for prob, next_state, reward, done in P[s][pi(s)]:
          V[s] += prob * (reward + gamma *  prev_V[next_state] * (not done))
      if np.max(np.abs(prev_V - V)) < theta:
        break
      prev_V = V.copy()
    return V

## Code to evaluate the first policy
V1 = policy_evaluation(pi_1, P)
print_state_value_function(V1, P, n_cols=7, prec=5)

## Code to evaluate the second policy
V2 = policy_evaluation(pi_2, P)
print_state_value_function(V2, P, n_cols=7, prec=5)

## Comparing policies based on state value function
### The state value function of the second policy V2 is greater than that of the first policy V1, so we conclude that the second policy is the best policy.

V1
print_state_value_function(V1, P, n_cols=7, prec=5)
V2
print_state_value_function(V2, P, n_cols=7, prec=5)
V1>=V2
if(np.sum(V1>=V2)==7):
  print("The first policy is the better policy")
elif(np.sum(V2>=V1)==7):
  print("The second policy is the better policy")
else:
  print("Both policies have their merits.")
```

## OUTPUT:
![268425327-c2308b42-eaeb-4b64-a126-758538b69335](https://github.com/MEENA155/rl-policy-evaluation/assets/94677128/f70b8df6-e172-4d86-84d3-be7b8e7fdd8c)
![268425327-c2308b42-eaeb-4b64-a126-758538b69335](https://github.com/MEENA155/rl-policy-evaluation/assets/94677128/0b6ef704-fd30-4c16-8937-0036122af969)
![268425327-c2308b42-eaeb-4b64-a126-758538b69335](https://github.com/MEENA155/rl-policy-evaluation/assets/94677128/629d8c4e-0014-4a19-91b8-b5824e54edc4)
![268425327-c2308b42-eaeb-4b64-a126-758538b69335](https://github.com/MEENA155/rl-policy-evaluation/assets/94677128/3b1b164c-8c34-45f7-9dca-d8b479c37a51)


## RESULT:

Thus, a Python program is developed to evaluate the given policy.
