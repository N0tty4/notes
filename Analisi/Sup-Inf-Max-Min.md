# maggiore
## maggiorante
Dato un insieme $A \subseteq \mathbb{R}, M \in \mathbb{R}$ è un maggiorante di A se $\forall a \in A, M\geq a$
## limitato superiormente
se $\exists M \in \mathbb{R} : \forall a \in A, M \geq a$, allora è limitato superiormente 
## massimo
Dato un insieme $A \subset \mathbb{R}$ il massimo si definisce come $\exists M \in A : \forall a \in A, M \geq A$ 

# Minore
## minorante
Dato un insieme $A \subseteq \mathbb{R}, m \in \mathbb{R}$ si definisce un minorante se $\forall a \in A, M \leq a$
## limitato inferiormente
se $\exists m \in \mathbb{R} : \forall a \in A, m \leq a$, allora l'insieme è limitato inferiormente.
## minimo
$M$ si definisce minimo di $A$ se $\exists m \in A : \forall a \in A, m \leq a$

# Limitato
Dato un insieme $A \subseteq \mathbb{R}$, tale insieme si definisce limitato se $\exists m, M \in \mathbb{R} : \forall a \in A, m \leq a \leq M$.
# Assioma di completezza
- Se $A$ è limitato superiormente allora l'insieme dei minoranti ha un elemento minimo chiamato __sup(A)__ (estremo superiore)
- Se A è limitato inferiormente allora l'insieme dei minoranti ha un elemento massimo chiamato __inf(A)__ (estremo inferiore)
## Proprietà del sup
$$
\sup(A) = +\infty \iff \forall M \in \mathbb{R}, \exists a \in A : M \leq a
$$
$$
\sup(A) = l \in \mathbb{R} \iff 
\left\{ 
    \begin{array}{l}
        \forall a \in A, a \leq l &\\
        \forall \epsilon > 0, \exists a \in A : l - \epsilon < a
    \end{array} 
\right.
$$

## Proprietà dell'inf
$$
\inf(A) = -\infty \iff \forall M \in \mathbb{R}, \exists a \in A : M < a
$$
$$
\inf(A) = l \in \mathbb{R} \iff
\left\{ 
    \begin{array}{l}
        \forall a \in A, a \geq l &\\
        \forall \epsilon > 0, \exists a \in A : l + \epsilon > a
    \end{array} 
\right.

$$
Quando si tratta $\inf(A)$ o il $\sup(A)$  ci si riferisce l'immagine di una funzione, non il suo dominio.

