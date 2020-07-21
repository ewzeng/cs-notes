today: monte carlo integration

high-dim integration: need lots of samples, higher error (curse of dimensionality)

mc integration: take random samples; error independent of dim. simple, efficient, unbiased.

- $F_N = \frac{1}{N}\sum_{i = 1}^N \frac{f(X_i)}{p(X_i)}$, $p(x) > 0$ if $f(x) > 0$

importance sampling: sample where it is important (e.g. sample integrand where its big). pick $p$ to achieve (ideal is when $f/p$ is constant)

- for example, when computing radiance, incoming radiance is zero for most directions. leads to noise of $p$ is uniform. soln: integrate only over the area of the light