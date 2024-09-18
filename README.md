# Permutation-Disturbance

Rahul likes to create disturbance in numbers. In other words, he does not like when numbers are in their right positions.
He has a permutation P of size N. In one operation, he can swap any two adjacent elements.
His goal is to alter the permutation in such a way that Pi ≠ i satisfies for all 1 ≤ i ≤ N.
Help Chef find the minimum number of operations required to reach his goal.
Note that a permutation of size N is a sequence of integers consisting of all integers from 1 to N exactly once.

def min_operations_to_disturb(n, P):
    swaps = 0
    i = 0
    while i < n:
        if P[i] == i + 1:
            if i + 1 < n and P[i + 1] == i + 2:
                swaps += 1
                i += 2  
            else:
                swaps += 1
                i += 1  
        else:
            i += 1
    
    return swaps

import sys
input = sys.stdin.read
data = input().split()

t = int(data[0])
index = 1
results = []

for _ in range(t):
    n = int(data[index])
    P = list(map(int, data[index + 1: index + 1 + n]))
    index += n + 1
    
    results.append(str(min_operations_to_disturb(n, P)))

sys.stdout.write("\n".join(results) + "\n")
