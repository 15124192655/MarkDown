计算两个类别的均值向量：

$\boldsymbol{m_1} = \frac{1}{n_1}\sum_{i=1}^{n_1}\boldsymbol{x_i}$

$\boldsymbol{m_2} = \frac{1}{n_2}\sum_{i=n_1+1}^{n}\boldsymbol{x_i}$

其中，$n_1$和$n_2$分别是两个类别的样本数。

计算类内离散度矩阵：

$\boldsymbol{S_1} = \sum_{i=1}^{n_1}(\boldsymbol{x_i}-\boldsymbol{m_1})(\boldsymbol{x_i}-\boldsymbol{m_1})^T$

$\boldsymbol{S_2} = \sum_{i=n_1+1}^{n}(\boldsymbol{x_i}-\boldsymbol{m_2})(\boldsymbol{x_i}-\boldsymbol{m_2})^T$

$\boldsymbol{S_w} = \boldsymbol{S_1} + \boldsymbol{S_2}$

计算类间离散度矩阵：

$\boldsymbol{S_b} = (\boldsymbol{m_1}-\boldsymbol{m_2})(\boldsymbol{m_1}-\boldsymbol{m_2})^T$

计算投影向量$\boldsymbol{w}$：

$\boldsymbol{w} = \boldsymbol{S_w}^{-1}(\boldsymbol{m_1}-\boldsymbol{m_2})$

计算投影后的样本$\boldsymbol{y_i}$：

$\boldsymbol{y_i} = \boldsymbol{w}^T\boldsymbol{x_i}$

设定阈值$t$，将投影后的样本$\boldsymbol{y_i}$分为两类。

根据投影后的样本$\boldsymbol{y_i}$，我们可以计算出它们在一维空间上的均值和方差。设$y_{1i}$表示属于第一类的样本$i$在一维空间上的投影，$y_{2i}$表示属于第二类的样本$i$在一维空间上的投影，则均值和方差分别为：

$\mu_1 = \frac{1}{n_1}\sum_{i=1}^{n_1}y_{1i}$

$\mu_2 = \frac{1}{n_2}\sum_{i=n_1+1}^{n}y_{2i}$

$\sigma_1^2 = \frac{1}{n_1}\sum_{i=1}^{n_1}(y_{1i}-\mu_1)^2$

$\sigma_2^2 = \frac{1}{n_2}\sum_{i=n_1+1}^{n}(y_{2i}-\mu_2)^2$

我们可以选择一个阈值$t$，使得将样本投影到一维空间后，所有满足$y_i \geq t$的样本被判定为属于第一类，而所有满足$y_i < t$的样本被判定为属于第二类。如何选择阈值$t$可以根据实际需求进行，常见的方法有设置$t=\frac{\mu_1+\mu_2}{2}$，或者在$t$的取值范围内进行交叉验证等。