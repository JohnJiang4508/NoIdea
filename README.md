flowchart LR
    R([r(t) 参考输入]) --> E{误差计算}
    Y([y(t) 输出]) --> E
    E -->|e(t) 误差| SM[("PID型滑模面<br>s = ė + λe + μ∫e dt")]
    SM -->|s(t)| C[("总控制律<br>u = u_eq + u_sw")]
    subgraph C_detail [控制律分解]
        C1[("等效控制 u_eq<br>使 ṡ = -κs")]
        C2[("切换控制 u_sw<br>= -η·sgn(s)")]
    end
    C -->|u(t)| P[被控对象]
    P --> Y
    SM -.->|滑模面参数| C1
    SM -.->|s(t)| C2
