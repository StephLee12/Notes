$$
    \begin{aligned}
        &L_1 = \{频繁1项集\}\\
        &for(k=2;L_{k-1} \neq \emptyset;k++) \text{ do begin} \\
        & \qquad C_k = apriori\_gen(L_{k-1})\\
        & \qquad \text{for all transactions } t\in D\text{ do begin}\\
        & \qquad \qquad C_t = subset(C_k,t)\\
        & \qquad \qquad \text{for all candidates }c\in C_t do\\
        & \qquad \qquad \qquad c.count++\\
        & \qquad \qquad end\\
        & \qquad end\\
        & L_k = \{c\in C_k | c.count \geq min_{sup}\}\\
        & end\\
        & fre\_set = \bigcup L_k
    \end{aligned}
$$