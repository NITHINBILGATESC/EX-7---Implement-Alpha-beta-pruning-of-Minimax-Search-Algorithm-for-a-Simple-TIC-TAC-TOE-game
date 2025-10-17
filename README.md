<h1>ExpNo 7 : Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game</h1> 
<h3>Name: Nithin Bilgates C    </h3>
<h3>Register Number: 2305001022          </h3>
<H3>Aim:</H3>
<p>
Implement Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game
</p>
<h1>GOALS of Alpha-Beta Pruning in MiniMax Search Algorithm</h1>

<h3>Improve the decision-making efficiency of the computer player by reducing the number of evaluated nodes in the game tree.</h3>
<h3>Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning and the Minimax algorithm with Python Code.</h3>
<h1>IMPLEMENTATION</h1>

The project involves developing a Tic-Tac-Toe game implementation incorporating the Alpha-Beta pruning with the Minimax algorithm. Using this algorithm, the computer player analyzes the game state, evaluates possible moves, and selects the optimal action based on the anticipated outcomes.

<h1>The Minimax algorithm</h1>

recursively evaluates all possible moves and their potential outcomes, creating a game tree.

<h1>Alpha-Beta pruning</h1>

Alpha–Beta (𝛼−𝛽) algorithm is actually an improved minimax using a heuristic. It stops evaluating a move when it makes sure that it’s worse than a previously examined move. Such moves need not to be evaluated further.

When added to a simple minimax algorithm, it gives the same output but cuts off certain branches that can’t possibly affect the final decision — dramatically improving the performance

## PROGRAM
```python
import math

def show(b): [print(" | ".join(r)) or print("-"*5) for r in b]
def win(b):
    for i in range(3):
        if b[i][0]==b[i][1]==b[i][2]!=" ": return b[i][0]
        if b[0][i]==b[1][i]==b[2][i]!=" ": return b[0][i]
    if b[0][0]==b[1][1]==b[2][2]!=" ": return b[0][0]
    if b[0][2]==b[1][1]==b[2][0]!=" ": return b[0][2]

def full(b): return all(c!=" " for r in b for c in r)

def ab(b,a,beta,maxp):
    w=win(b)
    if w=="O": return 1
    if w=="X": return -1
    if full(b): return 0
    best=-math.inf if maxp else math.inf
    for i in range(3):
        for j in range(3):
            if b[i][j]==" ":
                b[i][j]="O" if maxp else "X"
                val=ab(b,a,beta,not maxp)
                b[i][j]=" "
                if maxp:
                    best=max(best,val); a=max(a,best)
                else:
                    best=min(best,val); beta=min(beta,best)
                if beta<=a: return best
    return best

def best(b):
    sc=-math.inf; mv=None
    for i in range(3):
        for j in range(3):
            if b[i][j]==" ":
                b[i][j]="O"
                s=ab(b,-math.inf,math.inf,False)
                b[i][j]=" "
                if s>sc: sc=s; mv=(i,j)
    return mv

b=[[" "]*3 for _ in range(3)]
print("You=X | AI=O")
while True:
    show(b)
    w=win(b)
    if w or full(b): print("Result:",w if w else "Draw!"); break
    try:
        r,c=map(int,input("Enter row col (0-2): ").split())
        if b[r][c]!=" ": print("Invalid!"); continue
        b[r][c]="X"
    except: print("Bad input!"); continue
    if not win(b):
        m=best(b)
        if m: b[m[0]][m[1]]="O"

```
<hr>
<h2>Sample Input and Output:</h2>

![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8d5e329a-9aff-41a6-bcf0-46efa10e1b92)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/438b242d-54ba-443e-b040-a936e6ae3b55)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/99a33390-fa11-4ade-a19f-e93bcd7aaec9)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/440797bd-53cb-49c1-b18d-89776864c3e7)
![image](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/81575a16-26b2-46f1-a8ac-27c9ed0a0fe5)

## RESULT
We have successfully implemented Alpha-beta pruning of Minimax Search Algorithm for a Simple TIC-TAC-TOE game.
