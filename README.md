# SIR-model-for-novel-coronavirus-with-pytorch
A modified SIR model to predict the situation for 2019-nCoV using gradient descent with pytorch.

Data was retrieved from official report, including the number of comfirmed cases, suspected cases, dead cases, recovered cases from 1.13, 2020 to 2.13, 2020. Let $C_n$ denote the number of comfirmed cases at time $n$, $H_n$ denote the number of healed cases at time $n$ and $D_n$ denote the dead cases at time $n$, and $S_n$ is the susceptible population. In the beginning we assume $S_0 + D_0 + C_0 + H_0 = 100000$. During computing $S_n$, bias should be added to modify the assumption error. The recurrent formula can be written as:

$$
S_n = S_{n-1} - \lambda_1 C_{n-1} * S_{n-1} + \b
$$

$$
C_n = C_{n-1} + \lambda_1 C_{n-1} * S_{n-1} - \b - \lambda_2 C_{n-1} - \lambda_3 C_{n-1}
$$

$$
H_n = H_{n-1} + \lambda_2 C_{n-1}
$$

$$
D_n = D_{n-1} + \lambda_3 C_{n-1}
$$
