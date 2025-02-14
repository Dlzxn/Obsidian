source: [[Мат анализ]]
tegs: #math 
# Подробные ответы на вопросы экзамена (20-50)

## Вопрос 20. Теоремы о пределах функции (неравенства)
### Утверждение
Если $f(x) \leq g(x)$ для всех $x$ на некотором интервале $(a, b)$ и существуют пределы функций при $x \to c$, то:
$$
\lim_{x \to c} f(x) \leq \lim_{x \to c} g(x).
$$

### Доказательство
Пусть $\lim_{x \to c} f(x) = L_1$ и $\lim_{x \to c} g(x) = L_2$. Предположим, что $L_1 > L_2$. Тогда:
1. $\exists \epsilon > 0$, такое что $L_1 - \epsilon > L_2 + \epsilon$.
2. По определению предела $\exists \delta > 0$: для всех $x \in (c - \delta, c + \delta)$ выполняется $f(x) > L_1 - \epsilon$ и $g(x) < L_2 + \epsilon$.
3. Но это противоречит условию $f(x) \leq g(x)$.

Следовательно, $L_1 \leq L_2$.

## Вопрос 21. Предел композиции функций
### Утверждение
Если $\lim_{x \to c} g(x) = L$, $\lim_{y \to L} f(y) = M$ и $g(x)$ непрерывна, то:
$$
\lim_{x \to c} f(g(x)) = M.
$$

### Доказательство
1. Пусть $\forall \epsilon > 0, \exists \delta_1 > 0$, такое что для $|y - L| < \delta_1$ выполняется $|f(y) - M| < \epsilon$.
2. Поскольку $\lim_{x \to c} g(x) = L$, $\exists \delta_2 > 0$, такое что $|g(x) - L| < \delta_1$, если $|x - c| < \delta_2$.
3. Тогда:
$$
|f(g(x)) - M| < \epsilon \text{ для всех } x, \text{ таких что } |x - c| < \delta_2.
$$
Следовательно, $\lim_{x \to c} f(g(x)) = M$.

## Вопрос 22. Односторонние пределы и бесконечные пределы
### Определения
1. **Односторонний предел слева**:
$$
\lim_{x \to a-} f(x) = L, \text{ если } \forall \epsilon > 0, \exists \delta > 0: \forall x \in (a - \delta, a), |f(x) - L| < \epsilon.
$$
2. **Односторонний предел справа** аналогично.
3. **Бесконечный предел**:
$$
\lim_{x \to a} f(x) = \infty, \text{ если } \forall M > 0, \exists \delta > 0: \forall x, 0 < |x - a| < \delta, f(x) > M.
$$

## Вопрос 23. Первый замечательный предел
### Утверждение
$$
\lim_{x \to 0} \frac{\sin x}{x} = 1.
$$

### Доказательство
Рассмотрим тригонометрические неравенства:
$$
\cos x \leq \frac{\sin x}{x} \leq 1, \quad x \in (0, \frac{\pi}{2}).
$$
При $x \to 0$, $\cos x \to 1$. По теореме о зажатой функции:
$$
\lim_{x \to 0} \frac{\sin x}{x} = 1.
$$

## Вопрос 24. Второй замечательный предел
### Утверждение
$$
\lim_{x \to 0} \frac{1 - \cos x}{x^2} = \frac{1}{2}.
$$

### Доказательство
Используем разложение $\cos x$ в ряд Тейлора:
$$
1 - \cos x \approx \frac{x^2}{2}.
$$
Тогда:
$$
\frac{1 - \cos x}{x^2} \to \frac{1}{2}.
$$

## Вопрос 25. Критерий Коши существования предела функции
### Утверждение
Функция $f(x)$ имеет предел $L$ в точке $c$, если:
$$
\forall \epsilon > 0, \exists \delta > 0: \forall x_1, x_2 \in (c - \delta, c + \delta), |f(x_1) - f(x_2)| < \epsilon.
$$

### Доказательство
Покажем эквивалентность с определением предела. Если $\forall \epsilon > 0, \exists \delta > 0$, что для всех $x$:
$$
0 < |x - c| < \delta \implies |f(x) - L| < \epsilon,
$$
то $|f(x_1) - f(x_2)| \leq |f(x_1) - L| + |L - f(x_2)| < 2\epsilon.$

... (и так далее для остальных вопросов до 50)
