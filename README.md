## Bayesian linear regression using conjugate Gaussian prior

1. Data is considered to be generated from a true function with added noise. We assume the true function is a linear combination of the weights and inputs. Hence, Bayesian *Linear* Regression. W and $\epsilon$ are the weight and noise distributions respectively. Both are assumed to be Gaussian as it is a conjugate prior for Gaussian likelihood $P(Y|W)$. The equation can then be written as:  
> $$Y = \phi(X) \cdot W + \epsilon <br>
> $$W \sim \mathcal{N} ( \overline{w} ,\Sigma_w)$$ <br> 
> $$\epsilon \sim \mathcal{N}(\overline{\epsilon}, \Sigma_\epsilon )$$

2.  Fact: For joint normality, we have if X and Y are normally distributed and independent the (X,Y) must also have a multivariate normal distribution. 
> $$\begin{pmatrix}W \\ \epsilon \end{pmatrix} \sim\mathcal{N}\left( \begin{pmatrix}\overline{w}\\\overline{\epsilon}  \end{pmatrix},\begin{pmatrix} \Sigma_W & 0 \\ 0& \Sigma_\epsilon\end{pmatrix}\right)$$

3. We can write the joint distribution $Y$ as a linear combination of $W,\epsilon$ using the following relation:
> $$\begin{bmatrix}W \\Y\end{bmatrix} = A\begin{bmatrix}W \\ \epsilon\end{bmatrix}=\begin{bmatrix}I & 0 \\ \phi(X) & I\end{bmatrix}\begin{bmatrix}W \\ \epsilon\end{bmatrix}$$

4. Fact: Every linear combination of components of a multivariate normal distribution is also normally distributed. Assuming, $\overline{\epsilon}=0$,  we have: 
> $$\begin{pmatrix}W \\ Y\end{pmatrix} \sim\mathcal{N}\left( \begin{pmatrix}\overline{w} \\\phi\overline{w}  \end{pmatrix},\begin{pmatrix} \Sigma_W & \Sigma_W\phi^T \\ \phi\Sigma_W & \phi\Sigma_W\phi^T + \Sigma_\epsilon end{pmatrix}\right)$$ <br>
$$\mu_{\text{post}} = \overline{w}+ \Sigma_{\text{W}} \phi^T (\phi \Sigma_{\text{W}} \phi^T + \Sigma_\epsilon)^{-1} (Y - \phi \overline{w})$$ <br>
$$\Sigma_{\text{post}} = \Sigma_{\text{W}} - \Sigma_{\text{W}} \phi^T (\phi \Sigma_{\text{W}} \phi^T + \Sigma_\epsilon)^{-1} \phi \Sigma_{\text{W}}$$ <br> 
where $\mu_{\text{post}}$ and $\Sigma_{\text{post}}$ are the parameters of the posterior distribution $P(W|Y)$.

5. This result agrees with the regularized closed form MAP estimate of weights as setting a prior $P(W)$, acts as regularization: 
> $W_{\text{MAP}}= (\phi^T\phi + \lambda I)^{-1}\phi^TY$ <br>
  $\lambda= {\sigma_{\epsilon}}/{\sigma_{W}}$

6. Predictive distribution $P(\hat{Y}|W)$ can  be given by: 
>  $\mu_{\text{pred}}= \phi\mu_{\text{post}}$ <br>
>  $\Sigma_{\text{pred}}= \phi\Sigma_{\text{post}}\phi^T$
