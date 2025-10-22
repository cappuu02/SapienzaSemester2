# Introduction
**_Managing resources in contemporary cloud systems is increasingly challenging due to_**:
- **Dynamic and unpredictable workloads**
- **Multi-tenant infrastructures** with competing demands
- **Energy efficiency** and **cost optimization** requirements

**Limitations of Traditional Approaches**
- Conventional methods rely on **threshold-based** or **heuristic rules**, which:
- struggle to adapt to rapid workload variations,
- often result in **over-provisioning** (wasted resources) or **under-provisioning** (performance degradation).

**_Emerging Need_**
Modern cloud environments require a **self-adaptive, data-driven strategy** capable of continuously learning and optimizing resource allocation decisions.

# Reinforcement Learning

```ad-success
title: Solution
==Reinforcement Learning (RL)== provides a framework for **learning optimal resource management policies** through real-time data and accumulated experience, enabling systems to autonomously adapt to changing conditions.

```

Why Reinforcement learning?

```ad-abstract
title: Definition
**_Reinforcement Learning (RL)_** is a framework for learning by interaction: the agent learns the best actions through trial, feedback, and adaptation.

```

Key reasons why RL fits cloud resource management:
- **Sequential decision-making:**  
    RL optimizes a _sequence_ of actions whose effects may unfold over time — for example, a scaling action taken now influences future system performance and cost.
- **Experience-based learning:**  
    The RL agent learns directly from **real operational data**, without requiring an explicit or perfect model of the cloud environment.
- **Self-adaptive behavior:**  
    RL continuously **adjusts to workload variations, system failures, and changing conditions**, ensuring robust performance in dynamic contexts.
- **Goal-oriented control:**  
    System objectives are encoded in a **reward function**, enabling the agent to balance goals such as minimizing cost, maximizing performance, and maintaining Service Level Objectives (SLOs).

```ad-example
title: Tic-Tac-toe Example
**Goal:**  
Determine the **best move (optimal action)** at each turn.

**Key Concepts:**

- **State (s):** the current configuration of the game board.
    
- **Action (a):** placing a symbol (X or O) in a chosen cell.
    
- **Reward (r):** the immediate outcome of an action
    
    - `+1` → win
        
    - `0` → draw
        
    - `–1` → loss
        
- **Total reward (G):** cumulative sum of rewards until the end of the game.
    
- **Policy (π):** a rule that defines which action to take in each state.
    

Each move influences future outcomes — making this a **sequential decision-making problem**, similar to how **cloud resource management** decisions affect future performance and cost.
```

## Policy Evaluation

```ad-abstract
title: Policy Evaluation
A policy defines how the agent acts in every state. We can measure how good a policy is using the value function:
$v_{\pi}(s) = \text{Expected total reward from state s following policy} \hspace{0.1cm} \pi$
- High value $\to$ good position for the agent
- A low $\to$ risky or losing position
  

$$v_{\pi}(s) = E_{\pi}[G_t \mid S_t = s]$$

```

The immediate reward of intermediate actions is 0 
![[M101.png]]

```ad-example
![[M102.png]]
Suppose the agent follows a **policy** that, in **state A**, always chooses **action a = (0,2)** — for instance, placing its symbol in the middle cell.

After this move, the game can evolve into:

- **State B** with probability **0.5**,
    
- **State C** with probability **0.5**, depending on the opponent’s counter-move.
    

The **value of state A**, denoted $V(A)$, represents the **expected return** (average reward) starting from A and following the current policy:

$$V(A) = 0.5 \times (-1) + 0.5 \times V(C)$$

Given that:

$$V(C) = 1$$

we get:

$$V(A) = 0$$

If the agent adopted **a different policy**, the value of $V(A)$ would change:

- choosing **(0,1)** → $$V(A) = 0.5$$
    
- choosing **(2,2)** → $$V(A) = -0.5$$
    

```

```ad-question
**Question:**  
What value $V(s)$ would correspond to a state from which the agent can **always win** (i.e., win with probability $1$)?

```

### Policy Evaluation: Bellman Equation
The value function v(s) must satisfy a consistency relationship because the value of state s is related to the value of the neighboring states s', i.e. the states that can be reached after an action 
- $v(s) = \sum_{s'}p(s' \mid s, a) [r + v(s')] = \sum_{s'} p(s' \mid s, a) r + \sum_{s'} p (s' |s,a) v(s')$
- Let $p(s'|s,a)$ be the probability that due to the action taken in $s$, the next state is $s'$ (consider only non-terminal states) 
- Since the actions are fixed (given), this defines a ==Markov Reward Process== (MRP)

![[M103.png]]

```ad-example
![[M104.png]]

```

### Optimal Policy
```ad-abstract
title: Optimal Policy
best sequence of actions that maximizes the expected total reward. 

```

A key result is that the optimal sequence of actions can be obtained through a greedy evaluation: at each step, the agent selects the action that leads to the next state with the highest expected value, according to the current estimate of the value function. 
It is useful to use a graph where actions and terminal states have different symbols.

![[M105.png]]

The maximum value that a state can have, $v_*(s)$, i.e. the maximum expected reward $G$ the agent can obtain by being in that state, obeys the following consistency rule:
$$v(s) = maxa(\sum_{s'}p(s' \mid s,a)r + \sum_{s'}p(s' \mid s,a)v_*(s'))$$
$p(s’|s,a)$ is the probability that the next state is $s’$, given the current state is s and the action taken is $a$. 

![[M107.png]]

How to beat the worst enemy? ==Minimax Algorithm==
What if the adversary always responds with its best possible move? 
The value of the next state should be lowest possible (ideally -1)

![[M108.png]]

## The action-value function $Q(S,A)$

```ad-abstract
title: The Action-Value Function $Q(S,A)$
Un modo alternativo per valutare una **policy** è tramite la **funzione di valore stato-azione**, indicata con $Q(s, a)$.

La funzione
$$Q_\pi(s, a)$$

rappresenta il **ritorno totale atteso** (expected total return) partendo dallo **stato sss**, eseguendo l’**azione aaa** e seguendo poi la **policy $\pi$** per tutte le azioni successive.

In altre parole, $Q_\pi(s, a)$ è la ricompensa media attesa risultante da:

1. trovarsi nello **stato $s$**,
    
2. eseguire una **specifica azione $a$** (che può anche non appartenere alla policy $\pi$),
    
3. e successivamente **seguire la policy $\pi$** per tutte le mosse future.

```

![[M109.png]]

```ad-abstract
title: Q Value Computation
Given a policy and a model, $Q(s,a)$ can be computed following similar algorithms to those used to evaluate $v(s)$
Similarly, $Q_*(s,a)$ can be computed in the same way as $v_*(s)$.

```

```ad-abstract
title: Agent-ENV Interface
Agente e ambiente interagiscono lungo una **sequenza di passi discreti nel tempo**, $t = 0, 1, 2, 3, \dots$
Ad ogni **passo temporale $t$**, l’agente riceve una **rappresentazione dello stato dell’ambiente**, $S_t$​, e in base a questo sceglie un’**azione $A_t$​**.
Un passo temporale dopo, come conseguenza (almeno parziale) della sua azione, l’agente riceve una **ricompensa numerica $R_{t+1}$​** e si trova in un **nuovo stato $S_{t+1}$​**.

>Questa interazione **sequenziale** costituisce la base del modello di **reinforcement learning**.

```

## Markov Decision Process

```ad-abstract
title: MDP (Markov Decision Process)
Un **MDP** è una tupla $(S, A, P, R, \gamma)$, dove:

- **$S$**: Insieme finito di stati
- **$A$**: Insieme finito di azioni
- **$P$**: Funzione di transizione di probabilità $p(s, s', a) = \Pr(S_{t+1} = s' \mid A_t = a, S_t = s)$
- **$R$**: Funzione di reward $r(s, s', a)$: reward ricevuto quando ci si sposta da $s$ a $s'$ a causa dell'azione $a$
- **$\gamma$**: Fattore di sconto $\gamma \in (0,1)$

Caratteristiche principali
- In generale, non esiste uno stato finale e il sistema viene eseguito "per sempre".
- Per questo motivo, la somma dei reward viene scontata tramite il fattore $\gamma$.

Definizione del ritorno ($G_t$)
Il ritorno totale atteso a partire dal tempo $t$ è definito come:
$$G_t \doteq R_{t+1} + \gamma R_{t+2} + \gamma^2 R_{t+3} + \cdots$$
Questa equazione può essere espressa in forma ricorsiva come:
$$G_t = R_{t+1} + \gamma G_{t+1}$$

```

Una **politica ottima** π* è definita come quella politica per cui:
$$V_{\pi^*}(s) \geq V_{\pi}(s), \quad \forall s \in S, \ \forall \pi$$
For finite MDP there is always at least a deterministic optimal policy. 
- Per MDP finiti **esiste sempre almeno una politica ottima deterministica**
- Questo significa che per ogni stato esiste un'azione ottima univoca da scegliere
- La funzione valore $V^{\pi^*}(s)$ rappresenta il massimo ritorno atteso ottenibile partendo dallo stato $s$

**_MONTECARLO PREDICTION_**
In Monte Carlo (MC), the value of a state $V(s)$ is estimated as the average (over many episodes) of all observed returns following visits to $s$ (a state is at most visited once per episode) 
$Q$: In TTT, what does the value represent? 

![[M110.png]]

**_Temporal Difference (TD) Prediction_**
![[M111.png]]


```ad-abstract
title: Q-Learning
Il **Q-Learning** è considerato una delle scoperte più importanti nel Reinforcement Learning.

**_Concetti Fondamentali_**
- Se **$Q^*$** è nota, allora la migliore azione nello stato $s$ è:
  $$\text{argmax}_a Q^*(s,a)$$
- Il Q-Learning stima **$Q^*$** direttamente dagli episodi e fornisce la politica ottima basata su $Q^*$

**_Politiche nel Q-Learning_**

1. Politica Target (Target Policy)
	- **Politica ottima** che vogliamo apprendere
	- **Politica greedy**: seleziona sempre l'azione con il valore Q più alto
	  $$\pi(s) = \text{argmax}_a Q(s,a)$$

2. Politica Comportamentale (Behavior Policy)
	- Politica **seguita durante l'apprendimento**
	- A volte sceglie azioni diverse dalla politica target
	- Utilizzata per **esplorare** altre azioni
	- Tipicamente implementata come **politica $\epsilon$-greedy**:
	  - Con probabilità $\epsilon$: sceglie un'azione casuale (esplorazione)
	  - Con probabilità $1-\epsilon$: sceglie l'azione migliore (sfruttamento)

**_Caratteristiche_**
- **Algoritmo off-policy**: apprende la politica ottima mentre segue una politica diversa
- **Esplorazione vs Sfruttamento**: bilanciato tramite il parametro $\epsilon$


```

![[M112.png]]

**_Algorithm_**
![[M113.png]]
- **_Exploitation_**: select an action according to $Q*$.
- **_Exploration_**: select a random action.
- The tradeoff between exploration and exploitation is regulated by $\epsilon$ Q-Learning is a tabular method 
- For convergence to the optimal policy, every state–action pair must be visited infinitely often, ensuring proper learning of all Q-values. 
- The best policy is deterministic, it’s just a lookup table

```ad-example
![[M113.png]]

```

## From games to cloud control
The same RL principles apply to resource management: 
**_State_**: resource usage (CPU, memory), request rate, SLOs 
**_Actions_**: adjust resource limits or number of replicas 
**_Reward_**: combination of performance, cost, and energy efficiency 
The definition of f the reward function is critical as it should reflect the need to maximize performance and SLO satisfaction, while minimizing energy and cost

```ad-example
In molti sistemi, l'autoscaling è basato su soglie predefinite (ad esempio, scale-out se CPU > 70%).

Tuttavia, le soglie statiche sono spesso subottimali.

Un autoscaler basato su Reinforcement Learning:
- Lo **stato** codifica l'utilizzo corrente, la latenza e l'andamento del carico di lavoro.
- Le **azioni** disponibili sono:
  - Scalabilità verticale → regolare i limiti di CPU/memoria
  - Scalabilità orizzontale → aggiungere/rimuovere container
- La **ricompensa** penalizza le violazioni degli SLO (Service Level Objectives) e l'uso eccessivo di risorse.
- L'agente impara dinamicamente le soglie migliori per bilanciare prestazioni e costi.
  
![[M115.png]]

```

## Single Agent RL
![[M116.png]]

### Single RL design
- **Stati**:
  - Rapporto di Preservazione degli SLO ($SP$)
  - Utilizzo delle Risorse ($RU(CPU, mem)$)
  - Variazioni del Tasso di Arrivo ($AC$)
  - Limiti delle Risorse ($RLT(CPU, mem)$)
  - Concorrenza Orizzontale ($NC$)

- **Azioni**:
  - **Scalabilità verticale**: ± dimensione del passo dei limiti di risorse ($a_v = \Delta RLT \, CPU, mem$)
  - **Scalabilità orizzontale**: ± dimensione del passo del numero di container di funzione ($a_h = \Delta NC$)

- Reward Function
$$R_t = \alpha \cdot RU_t + \beta \cdot SP_t + penalty$$
	- $\alpha \cdot RU_t$ = resource utilization
	- $\beta \cdot SP_t$ = SLO Presentation
	- $penalty$ = Penalize illegal or undesired actions
		- Frequent dangling decisions
		- Scale in/up/down when $NC_t = 0$

### Reward Function Sensitivity Study (Single-agent RL)
![[M117.png]]

>**_Optimal policy_**: as few SLO violations as possible while keeping the resource utilization as high as possible 

## Multi-Tenant RL Pipeline in Openwhisk
![[M118.png]]
## Performance under multi-tenancy
![[M119.png]]
## RL for Autoscaling
Un agente modifica le soglie che l'auto-scaler utilizza per effettuare lo scale-out (aumento) o lo scale-in (riduzione) della memoria e della CPU.

Ad esempio, se $u > \theta_u$ (o $r > \theta_r$) lo scaler aggiunge CPU avviando una nuova replica (scalabilità orizzontale) o aumenta la memoria attualmente allocata.

Le soglie rappresentano lo stato dell'agente e le azioni consistono nell'aumentare o diminuire il valore corrente di un quanto ($\delta_u$, $\delta_r$), oppure lasciarlo invariato.

![[M120.png]]
The reward function is critical as it determines the goal of the agent. By focusing on cost, the reward is interpreted as a penalty, and the agent will try to minimize the penalty

![[M121.png]]

```ad-example
title: Example of Esperimental Results
![[M122.png]]

```

## Q-Learning and DQL
Se lo spazio degli stati non è grande, l'implementazione del Q-learning è quasi immediata, poiché è possibile utilizzare una matrice per rappresentare $Q[s,a]$.

Tuttavia, i metodi tradizionali di RL hanno difficoltà con stati ad alta dimensionalità.

L'approccio più semplice è il **DQN** (Deep Q-Network), che estende il Q-learning utilizzando una rete neurale profonda per approssimare la funzione Q:  
$Q(s, a; \theta)$  
dove $\theta$ rappresenta i parametri della rete.

Un'altra strategia è approssimare direttamente la politica ottima. In questo caso, la rete neurale fornisce le **probabilità** della migliore azione da eseguire in uno stato.

Inoltre, il numero di stati può essere elevato e non è necessario visitarli tutti: il valore degli stati non visitati può essere appreso **generalizzando** i valori di altri stati.

![[M123.png]]