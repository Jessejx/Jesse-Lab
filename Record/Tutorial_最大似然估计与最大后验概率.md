# Frequentist vs. Bayesian Approaches in Machine Learning
本节，我将简单介绍Bayesian派与频率派的区别与联系，希望你喜欢

## Frequentist

Maximum Likelihood Estimation MLE

$$
\begin{align*}
\hat{\theta} &=\underset{\theta}{\arg \max } \mathrm{P}(X \mid \theta) \\
    &=\underset{\theta}{\arg \max } \prod_{i=0}^n \mathrm{P}\left(x_i \mid \theta\right) \\
    &=\underset{\theta}{\arg \max } \sum_{i=0}^n \log \mathrm{P}\left(x_i \mid \theta\right)
\end{align*}
$$

极大似然估计，估计似然函数。给定 $\theta$，找到使 $\theta$ 最大的值， （对应神经网络CNN、参数是 $\theta$，输出是 $x$，不断的给CNN输入数据），通过统计的方法找到 $\theta$是多少，这也是最大似然的思想. PS：似乎我们从最大似然的思想，我们可以窥探出为什么深度学习与频率派一同兴起。通过调整模型的函数 $\theta$，从而找出模型的预测 $x$与 gt最相近的数值，这不正是我们DL中supervised的学习模式吗？ e.g. Regression。

## Bayesian 
Maximum Posterior Probability

$$
\begin{align*}
\hat{\theta}&=\underset{\theta}{\arg \max } \mathrm{P}(\theta \mid X) \\
            &=\underset{\theta}{\arg \max } \frac{\mathrm{P}(X \mid \theta) \mathrm{P}(\theta)}{\mathrm{P}(X)} \\
            &=\underset{\theta}{\arg \max } \mathrm{P}(X \mid \theta) \mathrm{P}(\theta) \\
            &=\underset{\theta}{\arg \max } \log \mathrm{P}(X \mid \theta)+\log \mathrm{P}(\theta) \\
            &=\underset{\theta}{\arg \max } \sum_{i=0}^n \log \mathrm{P}\left(x_i \mid \theta\right)+\log \mathrm{P}(\theta)
\end{align*}
$$

另一个门派，贝叶斯门派的思想是已知观察值 $X$,那么我们思考的是已知样本 $X$值（PS：注意，贝叶斯中的 $X$是样本，与频率派的 $X$不相同），也就是说，我看到了结果，我要推出原因（什么样的 $\theta$可以得到这个 $X$样本）  

公式中 $\sum_{i=0}^n \log \mathrm{P}\left(x_i \mid \theta\right)$为似然项, $\log \mathrm{P}(\theta)$为先验项，似然项可以和最大似然估计简单等价（并不等价），先验项可以理解为我们所得到的先验知识（比如投硬币的正反面几率为百分之五十）。同时，如果样本数量较少，受先验项的影响较大；如果样本数较大，受先验项的影响较小。




