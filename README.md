# Multiple server with infinite capacity - (M/M/c):(oo/FIFO)
## Aim :
To find (a) average number of materials in the system (b) average number of materials in the conveyor (c) waiting time of each material in the system (d) waiting time of each material in the conveyor, if the arrival  of materials follow poisson process with the mean interval time 10 seconds, serivice time of two lathe machine follow exponential distribution with mean serice time 1 second and average service time of robot is 7seconds.

## Software required :
Visual components and Python

## Theory:
Queuing are the most frequently encountered problems in everyday life. For example, queue at a cafeteria, library, bank, etc. Common to all of these cases are the arrivals of objects requiring service and the attendant delays when the service mechanism is busy. Waiting lines cannot be eliminated completely, but suitable techniques can be used to reduce the waiting time of an object in the system. A long waiting line may result in loss of customers to an organization. Waiting time can be reduced by providing additional service facilities, but it may result in an increase in the idle time of the service mechanism.

![image](https://user-images.githubusercontent.com/103921593/203238035-1c8109bc-cbf2-4c77-baea-c5b682a752ef.png)

## Procedure :

![image](https://user-images.githubusercontent.com/103921593/203238265-176740b0-eae2-4772-90be-5449869ac9b0.png)




## Experiment:


## Program
```
import math

# Input from user
inter_arrival_time = float(input("Enter mean inter-arrival time (seconds): "))
service_time = float(input("Enter mean service time per server (seconds): "))
c = int(input("Enter number of servers: "))

# Arrival and service rates
lam = 1 / inter_arrival_time
mu = 1 / service_time

# Traffic intensity
rho = lam / (c * mu)

if rho >= 1:
    print("\nSystem is unstable (ρ >= 1)")
else:
    # Calculate P0
    summation = 0
    for n in range(c):
        summation += ((lam / mu) ** n) / math.factorial(n)

    last_term = (((lam / mu) ** c) / math.factorial(c)) * (1 / (1 - rho))

    P0 = 1 / (summation + last_term)

    # Calculate Lq
    Lq = (
        (((lam / mu) ** c) * rho)
        / (math.factorial(c) * ((1 - rho) ** 2))
    ) * P0

    # Calculate Ls
    Ls = Lq + (lam / mu)

    # Calculate waiting times
    Wq = Lq / lam
    Ws = Ls / lam

    # Output
    print("\n----- Results -----")
    print(f"Traffic Intensity (ρ) = {rho:.4f}")
    print(f"Average number in queue (Lq) = {Lq:.6f}")
    print(f"Average number in system (Ls) = {Ls:.6f}")
    print(f"Average waiting time in queue (Wq) = {Wq:.6f} seconds")
    print(f"Average waiting time in system (Ws) = {Ws:.6f} seconds")
```

## Output :
<img width="1245" height="555" alt="image" src="https://github.com/user-attachments/assets/6290954f-0fde-45a1-b81f-38a8c1a92903" />


## Result : 

