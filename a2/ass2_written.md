# Assignment #2 written part

We assume $\log$ is $\ln$ here.

\(a)

Because $\boldsymbol{y}$ is a one-hot vector with $y_o=1$ and otherwise $0$,
$$
LHS = - y_o\log(\hat{y_o}) = RHS
$$

(b)
$$
\begin{aligned}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{v_c}} 
&= \frac{\partial}{\partial \boldsymbol{v_c}}(-\log\frac{e^{\boldsymbol{u^T_ov_c}}}{\sum_{w}e^{\boldsymbol{u^T_w v_c}}}) \\
&= \frac{\partial}{\partial\boldsymbol{v_c}}(-\boldsymbol{u^T_ov_c}+\log(\sum_{w}e^{\boldsymbol{u^T_w v_c}})) \\
&= -\boldsymbol{u_o}+\sum_{w}\boldsymbol{u_{w}}\frac{e^{\boldsymbol{u^T_w v_c}}}{\sum_{w}e^{\boldsymbol{u^T_w v_c}}} \\
&= -\boldsymbol{u_o}+\sum_{w}\boldsymbol{u_{w}}P(O=w|C=c) \\
&= -\boldsymbol{Uy}+\boldsymbol{U\hat{y}} \\
\end{aligned}
$$


(c)
$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{u_w}} 
&= \frac{\partial}{\partial \boldsymbol{u_w}}(-\log\frac{e^{\boldsymbol{u^T_ov_c}}}{\sum_{w}e^{\boldsymbol{u^T_w v_c}}}) \\
&= \frac{\partial}{\partial\boldsymbol{u_w}}(-\boldsymbol{u^T_ov_c}+\log(\sum_{w}e^{\boldsymbol{u^T_w v_c}})) \\
&= -\frac{\partial}{\partial\boldsymbol{u_w}}\boldsymbol{u^T_ov_c}+\frac{\partial}{\partial\boldsymbol{u_\omega}}\log(\sum_{w}e^{\boldsymbol{u^T_w v_c}})\\
\end{align*}
$$
When $w = o$: 
$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial\boldsymbol{u_o}} 
&= -\frac{\partial}{\partial\boldsymbol{u_o}}\boldsymbol{u^T_ov_c}+\frac{\partial}{\partial\boldsymbol{u_o}}\log(\sum_{w}e^{\boldsymbol{u^T_w v_c}}) \\
&= -\boldsymbol{v_c}+\frac{\boldsymbol{v_c}e^{\boldsymbol{u^T_o v_c}}}{\sum_{w}e^{\boldsymbol{u^T_w v_c}}} \\
&= -\boldsymbol{v_c}+\boldsymbol{v_c}P(O=o|C=c) \\
&= -\boldsymbol{v_c}+\boldsymbol{v_c}\hat{y_o} \\
\end{align*}
$$
When $w \ne o$: 
$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{u_w}} 
&= -\frac{\partial}{\partial\boldsymbol{u_w}}\boldsymbol{u^T_ov_c}+\frac{\partial}{\partial\boldsymbol{u_w}}\log(\sum_{w}e^{\boldsymbol{u^T_w v_c}}) \\
&= \frac{\boldsymbol{v_c}e^{\boldsymbol{u^T_w v_c}}}{\sum_{w}e^{\boldsymbol{u^T_w v_c}}} \\
&= \boldsymbol{v_c}P(O=w|C=c) \\
&= \boldsymbol{v_c}\hat{y_w} \\
\end{align*}
$$
In summary, 
$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{U}} 
&= \boldsymbol{v_c}(\boldsymbol{\hat{y} - y})^T \\
\end{align*}
$$
(d)
$$
\begin{align*}
\frac{\partial\sigma(x)}{\partial x}
&= \frac{e^x(e^x+1)-e^{2x}}{(e^x+1)^{2}} \\
&= \frac{e^x}{(e^x+1)^{2}} \\
&= \sigma(x)(1-\sigma(x)) \\
\end{align*}
$$
(e)
$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{v_c}} 
&= \frac{\partial}{\partial\boldsymbol{v_c}}(-\log(\sigma(\boldsymbol{u^T_o v_c}))-\sum_k\log(\sigma(-\boldsymbol{u^T_k v_c})) \\
&= -\frac{\partial}{\partial\boldsymbol{v_c}}\log(\sigma(\boldsymbol{u^T_o v_c}))-\sum_k\frac{\partial}{\partial\boldsymbol{v_c}}\log(\sigma(-\boldsymbol{u^T_k v_c})) \\
&= -\frac{1}{\sigma(\boldsymbol{u^T_o v_c})}\frac{\partial\sigma(\boldsymbol{u^T_o v_c})}{\partial\boldsymbol{v_c}}-\sum_k(\frac{1}{\sigma(-\boldsymbol{u^T_k v_c})}\frac{\partial\sigma(\boldsymbol{-u^T_k v_c})}{\partial\boldsymbol{v_c}}) \\
&= (\sigma(\boldsymbol{u^T_o v_c})-1)\boldsymbol{u_o}-\sum_k((\sigma(-\boldsymbol{u^T_k v_c})-1)\boldsymbol{u_k}) \\
\end{align*}
$$

$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{u_o}} 
&= \frac{\partial}{\partial\boldsymbol{u_k}}(-\log(\sigma(\boldsymbol{u^T_o v_c}))-\sum_k\log(\sigma(-\boldsymbol{u^T_k v_c})) \\
&= -\frac{\partial}{\partial\boldsymbol{u_o}}\log(\sigma(\boldsymbol{u^T_o v_c}))-\sum_k\frac{\partial}{\partial\boldsymbol{u_o}}\log(\sigma(-\boldsymbol{u^T_k v_c})) \\
&= -\frac{1}{\sigma(\boldsymbol{u^T_o v_c})}\frac{\partial\sigma(\boldsymbol{u^T_o v_c})}{\partial\boldsymbol{u_o}} \\
&= (\sigma(\boldsymbol{u^T_o v_c})-1)\boldsymbol{v_c} \\
\end{align*}
$$

$$
\begin{align*}
\frac{\partial \boldsymbol{J}}{\partial \boldsymbol{u_k}} 
&= \frac{\partial}{\partial\boldsymbol{u_k}}(-\log(\sigma(\boldsymbol{u^T_o v_c}))-\sum_k\log(\sigma(-\boldsymbol{u^T_k v_c})) \\
&= -\frac{\partial}{\partial\boldsymbol{u_k}}\log(\sigma(-\boldsymbol{u^T_k v_c})) \\
&= -\frac{1}{\sigma(-\boldsymbol{u^T_k v_c})}\frac{\partial\sigma(-\boldsymbol{u^T_k v_c})}{\partial\boldsymbol{u_k}} \\
&= (1-\sigma(-\boldsymbol{u^T_k v_c}))\boldsymbol{v_c} \\
\end{align*}
$$

(f)
$$
\frac{\partial \boldsymbol{J}_{\text{skip-gram}}(\boldsymbol{v_c},w_{t-m},...,w_{t+m} ,\boldsymbol{U})}{\partial \boldsymbol{U}}=\sum_{\substack{-m \le j\le m\\ j\ne0}}\frac{\partial \boldsymbol{J}(\boldsymbol{v_c},w_{t+j},\boldsymbol{U})}{\partial \boldsymbol{U}}
$$

$$
\frac{\partial \boldsymbol{J}_{\text{skip-gram}}(\boldsymbol{v_c},w_{t-m},...,w_{t+m} ,\boldsymbol{U})}{\partial \boldsymbol{v_c}}=\sum_{\substack{-m \le j\le m\\ j\ne0}}\frac{\partial \boldsymbol{J}(\boldsymbol{v_c},w_{t+j},\boldsymbol{U})}{\partial \boldsymbol{v_c}}
$$

$$
\frac{\partial \boldsymbol{J}_{\text{skip-gram}}(\boldsymbol{v_w},w_{t-m},...,w_{t+m} ,\boldsymbol{U})}{\partial \boldsymbol{v_c}}=\sum_{\substack{-m \le j\le m\\ j\ne0}}\frac{\partial \boldsymbol{J}(\boldsymbol{v_c},w_{t+j},\boldsymbol{U})}{\partial \boldsymbol{v_w}}
$$

