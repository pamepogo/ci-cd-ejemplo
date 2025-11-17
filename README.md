# Ejemplo de CI/CD en Python

Este repositorio demuestra un ciclo completo de Integración Continua (CI) y Despliegue Continuo (CD) para un paquete Python simple, utilizando GitHub Actions. El proyecto incluye código fuente, pruebas unitarias y la construcción de un paquete distribuible.

## ¿Qué es CI/CD?

CI/CD (Continuous Integration / Continuous Deployment) es una metodología de desarrollo de software que automatiza el proceso de integración de cambios en el código, pruebas y despliegue de aplicaciones. El objetivo es detectar errores temprano, mejorar la calidad del código y acelerar el tiempo de entrega.

### Ciclo de CI/CD explicado paso a paso

1. **Desarrollo Local**: El desarrollador escribe código y pruebas.
2. **Commit y Push**: Los cambios se suben al repositorio Git (GitHub).
3. **Integración Continua (CI)**:
   - Se activa automáticamente al push o pull request.
   - Instala dependencias.
   - Ejecuta pruebas automatizadas (unitarias, integración, etc.).
   - Si las pruebas pasan, continúa; si fallan, se detiene y notifica.
4. **Construcción del Paquete**:
   - Si CI pasa, se construye el artefacto (paquete Python en este caso).
   - Se genera un wheel (.whl) o source distribution (.tar.gz).
5. **Despliegue Continuo (CD)** (opcional):
   - Sube el paquete a un repositorio como PyPI.
   - Despliega la aplicación en un servidor o contenedor.

En este ejemplo, nos enfocamos hasta la construcción del paquete.

## Estructura del Proyecto

- `main.py`: Código fuente con funciones básicas (suma y multiplicación).
- `test_main.py`: Pruebas unitarias usando `unittest`.
- `setup.py`: Configuración para construir el paquete.
- `requirements.txt`: Dependencias necesarias para construcción.
- `.github/workflows/ci.yml`: Workflow de GitHub Actions para CI/CD.

## Ejemplo Práctico

### Código Fuente

El paquete incluye dos funciones simples:

```python
def add(a, b):
    return a + b

def multiply(a, b):
    return a * b
```

### Pruebas

Las pruebas verifican el comportamiento correcto:

```python
import unittest
from main import add, multiply

class TestMain(unittest.TestCase):
    def test_add(self):
        self.assertEqual(add(2, 3), 5)
    # Más pruebas...
```

### Ejecución Local

1. Clona el repositorio:
   ```bash
   git clone https://github.com/tuusuario/ci-cd-python-example.git
   cd ci-cd-python-example
   ```

2. Instala dependencias:
   ```bash
   pip install -r requirements.txt
   ```

3. Ejecuta pruebas:
   ```bash
   python -m unittest test_main.py
   ```

4. Construye el paquete:
   ```bash
   python setup.py sdist bdist_wheel
   ```

### Workflow de GitHub Actions

El archivo `.github/workflows/ci.yml` define el pipeline:

- **Trigger**: Push a `main` o pull requests.
- **Jobs**:
  - `test`: Instala Python, ejecuta pruebas.
  - `build`: Construye el paquete y lo sube como artefacto.

Esto asegura que cada cambio se pruebe y empaquete automáticamente.

## Beneficios de CI/CD

- Detección temprana de bugs.
- Automatización de tareas repetitivas.
- Mayor confianza en los despliegues.
- Colaboración eficiente en equipos.

Para más detalles, revisa el workflow en `.github/workflows/ci.yml`.