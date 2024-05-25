
```c++
#include "Tree.h"
```

```c++
template <typename T>
Node<T>::Node(T data) : data(data), firstChild(nullptr), nextSibling(nullptr) {}
```
Esta es la implementación del constructor de de la clase `Node`:
Inicializa cada miembro de datos, data con el valor que se le proporcione y `firstChild` se inicializa
como nulo al igual que `nextSibling`.
```c++
template <typename T>
Tree<T>::Tree() : root(nullptr) {}
```
Implementa el constructor de la clase `Tree`, inicializando root como nulo, lo que significa que
el árbol se inicializa vacío.
```c++
template <typename T>
Node<T>* Tree<T>::addNode(T data, Node<T>* parent) {
Node<T>* newNode = new Node<T>(data);

    if(parent) {
        if(parent->firstChild) {
            Node<T>* sibling = parent->firstChild;
            while(sibling->nextSibling) {
                sibling = sibling->nextSibling;
            }
            sibling->nextSibling = newNode;
        } else {
            parent->firstChild = newNode;
        }
    } else {
        root = newNode;
    }

    return newNode;
}
```
Implementación del método `addNode` de la clase `Tree`, esta agrega un nuevo nodo al árbol.
Si el puntero parent no es nulo, o sea un puntero válido. Si `parent` no es nulo se pasa a la siguiente 
condicional la cual verifica si ese parent tiene un hijo, si firstChild es un puntero válido no nulo significa que `parent` tiene
por lo menos un hijo.
- En `Node<T>* sibling = parent->firstChild` Se declara el nodo de ese hijo, el cual sería el hermano del nuevo nodo al que queremos añadir al árbol.
- El bucle siguiente comprueba si el hermano declarado anteriormente tiene otro hermano, si esto es verdadero se va moviendo entre todos los hermanos que sean hijos de `parent`,
esto hasta que `nextSibling` sea nulo.
- Posteriormente se asigna newNode al puntero nextSibling del último hermano. Esto agrega el nuevo nodo como hermano siguiente deespués del último hermano del nodo `parent`.

- `parent->firstChild = newNode`: En caso de que el nodo parent no tiene nungún hijo, el nodo nuevo se asigna como el primer hijo del nodo `parent`.
- Como condicional final en caso de que no haya un nodo parent o un nodo inicial(parent = nullptr), se asigna el nuevo nodo como la raiz del árbol.
- Finalmente se retorna el nuevo nodo añadido en su correspondiente posición. 

```c++
template <typename T>
void Tree<T>::printTree(Node<T>* node, int level) {
if(!node) return;

    for(int i = 0; i < level; i++) std::cout << "--";
    std::cout << node->data << '\n';

    printTree(node->firstChild, level + 1);
    printTree(node->nextSibling, level);
}
```

Implementación del método `printTree()` de la clase `Tree`.
- Este método primero confirma si el árbol está vacío, si es así no se devuelve nada.
De otro módo mediante un ciclo `for` se itera las veces que indique `level` que es el tamaño del árbol.      
- Se accede a los datos de cada nodo y se imprimen en consola.            
- Se realiza recurcividad para imprimir los datos de los hijos y los hermanos.
