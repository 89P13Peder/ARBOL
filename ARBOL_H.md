
```c++
#ifndef TREE_H
#define TREE_H
```
Aquí se definen las directivas de preprocesador que evita la inclusión múltiple del mismo archivo.

```c++
#include <iostream>
```

Esta línea incluye la librería estándar de C++ iostream, que es necesaria para realizar operaciones de entrada y salida.


```c++
template <typename T>
class Node {
public:
T data;
Node* firstChild;
Node* nextSibling;

    explicit Node(T data);
};
```
Se define la clase Node, esta va a representar los nodos del árbol, esta clase tiene 3 miembros de datos:
1. `data`: contendrá los datos del nodo.
2. `firstChild`: va a apuntar al primer hijo del nodo actual.
3. `nextSibling`: va a apuntar al siguiente hermano del nodo actual.
4. La plantilla `template <typename T>`: nos permite hacer que el tipo de datos almacenados sea genérico.
5. `explicit Node(T data);`: Este es el constructor para inicializar el nodo con un valor dado, este constructor se declara como 
explícito para evitar las conversiones implícitas. 
```c++
template <typename T>
class Tree {
public:
    Node<T>* root;

    Tree();

    Node<T>* addNode(T data, Node<T>* parent = nullptr);

    void printTree(Node<T>* node, int level = 0);
};
```
Esta es la definición de la clase `Tree` o la clase que interpretará al árbol.
La clase permite recibir valores con tipo de dato genérico o el tipo de dato que llegue por parámetro.  
Esta contiene sus miembros públicos:
1. `root`: Es un puntero al nodo raíz del árbol (el primer nodo creado).
2. `Tree()`: Constructor por defecto de un árbol de la clase.
3. `addNode(T data, Node<T>* parent = nullptr)`: Este método agrega un nodo al árbol.
4. `printTree(Node<T>* node, int level = 0)`: Este método imprime todo el contenido del árbol en la consola.


```c++
#include "Tree.cpp"

#endif //TREE_H
```

