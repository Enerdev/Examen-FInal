# Sistema de Gestión Académica - Examen Final Unidad 1

## 📋 Descripción del Proyecto

Sistema de gestión de calificaciones de estudiantes que implementa operaciones CRUD con estructuras de datos avanzadas. El programa permite registrar estudiantes, calcular promedios, buscar registros de forma eficiente y ordenar datos utilizando diferentes algoritmos.

## 📁 Estructura del Proyecto

```
Final unidad 1 codigos/
├── C++/
│   ├── codigo.cpp        # Implementación en C++
│   ├── codigo            # Ejecutable compilado
│   └── .vscode/          # Configuración de VSCode
├── python/
│   ├── codigo.py         # Implementación en Python
│   └── __pycache__/      # Cache de Python
└── README.md
```

## 🔗 Recursos Adicionales

**Drive con documentación y archivos complementarios:**
[https://drive.google.com/drive/folders/17rX6YgXj4MX8R1r07TpN2zbfqfZPYlbp?usp=sharing](https://drive.google.com/drive/folders/17rX6YgXj4MX8R1r07TpN2zbfqfZPYlbp?usp=sharing)

---

## 📊 Funcionalidades Principales

✅ **Registro de Estudiantes** - Agregación de nuevos registros con validación de clave primaria  
✅ **Búsqueda O(1)** - Búsqueda ultrarrápida usando tabla hash  
✅ **Cálculo de Promedios** - Promedio de tres calificaciones  
✅ **Ordenamiento** - Múltiples algoritmos de clasificación  
✅ **Historial** - Sistema de pila para deshacer cambios  
✅ **Visualización** - Formato tabular profesional  

---

## 🔄 Diferencias: C++ vs Python

### 1. **Estructuras de Datos**

#### C++
```cpp
// Usa struct fuertemente tipado
struct Estudiante {
    string codigo;
    string nombre;
    float nota1, nota2, nota3;
    float promedio;
};

// Contenedores STL nativos
vector<Estudiante> hoja;
unordered_map<string, int> indiceHash;
stack<vector<Estudiante>> historial;
queue<string> colaAtencion;
```

#### Python
```python
# Usa diccionarios flexibles
estudiante = {
    "codigo": "...",
    "nombre": "...",
    "nota1": 0.0,
    "nota2": 0.0,
    "nota3": 0.0,
    "promedio": 0.0
}

# Contenedores built-in
hoja = []                    # Lista
indice_hash = {}             # Diccionario
historial = []               # Lista
cola_atencion = deque()      # Cola (collections)
```

**Diferencia:** C++ requiere tipado explícito; Python es dinámico y más flexible.

---

### 2. **Búsqueda en Tabla Hash**

#### C++
```cpp
auto it = indiceHash.find(codigo);
if (it != indiceHash.end()) {
    int pos = it->second;
    // O(1) - Búsqueda garantizada
}
```

#### Python
```python
if codigo in indice_hash:
    pos = indice_hash[codigo]
    # O(1) - Búsqueda garantizada
```

**Diferencia:** Sintaxis diferente pero complejidad idéntica O(1).

---

### 3. **Cálculo de Promedio**

#### C++
```cpp
inline float calcularPromedio(float n1, float n2, float n3) {
    return (n1 + n2 + n3) / 3.0f;
}
```
**Nota:** Usa `inline` para optimización en compilación.

#### Python
```python
def calcular_promedio(n1, n2, n3):
    return (n1 + n2 + n3) / 3.0
```

**Diferencia:** C++ es más rápido (compilado); Python es más legible.

---

### 4. **Historial (Stack/Pila)**

#### C++
```cpp
stack<vector<Estudiante>> historial;

void guardarHistorial() {
    historial.push(hoja);  // Copia automática
}
```

#### Python
```python
historial = []

def guardar_historial():
    historial.append(deepcopy(hoja))  # deepcopy necesario
```

**Diferencia:** Python necesita `deepcopy()` para evitar referencias mutables; C++ copia automáticamente.

---

### 5. **Ordenamiento**

#### C++
```cpp
// Usa algoritmos de la STL (generalmente optimizados)
sort(hoja.begin(), hoja.end(), [](const Estudiante &a, const Estudiante &b) {
    return a.promedio > b.promedio;
});
```

#### Python
```python
def quicksort(lista):
    if len(lista) <= 1:
        return lista
    pivote = lista[-1]
    mayores = [x for x in lista[:-1] if x["promedio"] >= pivote["promedio"]]
    menores = [x for x in lista[:-1] if x["promedio"] < pivote["promedio"]]
    return quicksort(mayores) + [pivote] + quicksort(menores)

def merge_sort(lista):
    # Implementación manual
    ...
```

**Diferencia:** Python implementa manualmente (quicksort, merge sort); C++ usa la STL optimizada.

---

### 6. **Validación de Entrada**

#### C++
```cpp
if (indiceHash.find(e.codigo) != indiceHash.end()) {
    cout << "[ERROR] El codigo ingresado ya se encuentra registrado.\n";
    return;
}
```

#### Python
```python
if codigo in indice_hash:
    print("[ERROR] Llave primaria duplicada. El codigo ya existe.")
    return

try:
    nota1 = float(input("Nota 1 (0-20): "))
except ValueError:
    print("[ERROR] Valores numericos incorrectos en calificaciones.")
    return
```

**Diferencia:** Python incluye manejo de excepciones `try-except`; C++ confía en la entrada.

---

## 📈 Comparativa de Rendimiento

| Operación | C++ | Python |
|-----------|-----|--------|
| Búsqueda Hash | ⚡ O(1) muy rápido | ⚡ O(1) rápido |
| Ordenamiento | ⚡⚡ Compilado, optimizado | ⚡ Interpretado |
| Uso de Memoria | 💾 Menor | 💾 Mayor |
| Tiempo de Compilación | ⏱️ Necesario | ⏱️ Ninguno |
| Legibilidad | 📖 Intermedia | 📖 Alta |

---

## 🚀 Cómo Ejecutar

### C++
```bash
cd C++
g++ -O2 -std=c++17 codigo.cpp -o codigo
./codigo
```

### Python
```bash
cd python
python3 codigo.py
```

---

## 📚 Conceptos Aplicados

- **Tablas Hash** - Búsqueda O(1)
- **Vectores Dinámicos** - Gestión de colecciones
- **Stack (Pila)** - Historial de cambios
- **Queue (Cola)** - Atención de solicitudes
- **Algoritmos de Ordenamiento** - QuickSort, MergeSort
- **Abstracción de Datos** - Struct vs Diccionario
- **Tratamiento de Errores** - Validación de entrada

---

## 👤 Autor
Emerson

**Año:** 2026 - Algoritmos y Estructura de Datos - Unidad 1 Examen Final
