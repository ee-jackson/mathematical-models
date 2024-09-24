# Constructing a simple model
eleanorjackson
2024-09-24

### Flow diagram of the model

``` mermaid
flowchart LR
  A(Seed) -- survive --> B(Seedling)
  B -- survive --> C(Adult)
  C -- reproduce --> A
  B -. mortality -.-> DEAD2:::hidden
  A -. mortality -.-> DEAD1:::hidden
  C -. mortality -.-> DEAD3:::hidden
  
  classDef hidden display: none;
```

### Specifying the model

$$
n_s(t) = n_a(t) - M_s(t)
$$

$$
n_j(t) = n_a(t) - M_j(t)
$$

$$
n_a(t) = n_s(t) - M_a(t)
$$

Number of seeds at time $t$ equals the number of adults minus the
mortality of seeds.

Number of juveniles at time $t$ equals the number of seeds minus the
mortality of juveniles.

Number of adults at time $t$ equals the number of juveniles minus the
mortality of adults.

I think we want a discrete time model rather than continuous time -
continuous time might allow continuous production of seeds, while this
only happens annually. So a sensible time step might be 1 year?

A *recursion equation* describes the value of a variable in the next
time step. e.g.

$$
n(t + 1) = n(t) + \text{increase} - \text{decrease}
$$

In continuous time models you use *differential equations,* which
specify the rate of change of the variables over time. e.g.

$$
\frac{\text{d}(n(t))}{\text{d}t} = \text{rate of increase} - \text{rate of decrease}
$$ You can also have something called a *difference equation,* which
might describe the change in a variable within a time step. e.g.

$$
\Delta n = \text{increase} - \text{decrease}
$$

Constraints of this model might be that,

- the number of seeds and is always larger than the number of juveniles
  and the number of juveniles is always larger than the number of adults
- none of the parameters can be less than one

https://kevintshoemaker.github.io/NRES-470/LECTURE7.html

https://kevintshoemaker.github.io/NRES-470/LAB4.html

http://ecovirtual.ib.usp.br/doku.php?id=en:ecovirt:roteiro:pop_str:pstr_mtr

## Transition matrix

When a matrix is used to represent a stage-structured population
(i.e. seed, seedling, adult), it is often called a ’Lefkovitch” (or
stage-based) matrix.
