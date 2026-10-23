# amador-canonical-operator

`amador-canonical-operator` es una librería académica y científica en Python puro, sin dependencias externas, desarrollada para la representación y evolución de sistemas cuántico-disipativos, variedades de Kähler y problemas combinatorios complejos bajo un marco port-Hamiltoniano, variacional y geométrico.

La biblioteca implementa el Operador Canónico de Amador, la Transformada de Amador PS-KL, y una arquitectura modular de cinco capas inspirada en la formulación del manuscrito "Formulación del Operador Canónico de Amador y Colapso de Dimensionalidad en Variedades de Kähler y Sistemas Cuántico-Disipativos".

Declaración de intención académica y autoría:

"Esta librería constituye una contribución académica y científica abierta formulada por el investigador independiente Francisco Amador Barrios Espinoza (Venezuela, 2026) para la resolución de problemas de alta complejidad computacional. Mediante el Operador Canónico de Amador, la Transformada de Amador y la relajación holomorfa en variedades de Kähler bajo régimen de isentropía computacional (ΔS = 0), este motor permite colapsar la complejidad algorítmica de búsqueda exponencial O(2^n) a trayectorias geodésicas deterministas en tiempo polinómico O(n)."

## Ecuación central

La ecuación interna del motor es:

\[
\mathcal{F}_{\text{int}}[\rho(t), u(t)] = [J(\rho) - R(\rho)]\nabla_{\rho} H(\rho) + \sum_k \gamma_k \mathcal{D}_k(\rho) + G(u)
\]

y el cierre cinemático del operador maestro está dado por:

\[
\Pi_{T^*\mathcal{M}\to\mathcal{M}} \circ \mathcal{P}_{T\mathcal{M}}
\]

proyectando sobre el espacio tangente hermítico de traza nula, preservando la condición de densidad positiva y trazada unitaria.

## Autor

Francisco Amador Barrios Espinoza  
Investigador Independiente (Venezuela, 2026)

## Instalación

```bash
pip install amador-canonical-operator
```

## Uso rápido

```python
from amador_operator import ComplexMatrix, CanonicalAmadorOperator

rho0 = ComplexMatrix([
    [1.0+0.0j, 0.0+0.0j],
    [0.0+0.0j, 0.0+0.0j],
])

op = CanonicalAmadorOperator(dim=2, theta=0.75)

def u_func(t):
    return [0.1 + 0.0j, -0.05 + 0.0j]

rho_t, history = op.integrate(rho0, u_func, (0.0, 1.0), 0.01)
print(rho_t)
print(history[-1]["energy"])
```

## Publicación en PyPI

```bash
python -m pip install --upgrade build twine
python -m unittest discover -s tests
python -m build
python -m twine upload dist/*
```

## Estructura principal

- `amador_operator.linalg`: álgebra lineal compleja, pseudoinversa, eliminación de Gauss-Jordan, producto tensorial, cálculo de gradientes.
- `amador_operator.core_dynamics`: port-Hamiltonian, disipación Lindblad y control port.
- `amador_operator.variational`: levantamiento de Hilbert-Amador y proyector PS-KL.
- `amador_operator.channels`: canales Toeplitz, Bott-Chern, Dirac y renormalizador gauge.
- `amador_operator.canonical`: operador maestro y solucionador de complejidad polinómica.

## Licencia

MIT License.
