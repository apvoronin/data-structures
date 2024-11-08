# 1. Стек

### Определение

**Стек** — абстрактный тип данных[^1], представляющий собой список элементов, организованных по принципу LIFO (Last In, First Out), что означает, что элемент, добавленный последним, будет извлечен первым.

**Вершиной стека** называется элемент, находящийся на самом верхнем уровне стека, к которому осуществляется доступ для операций добавления и удаления.

------

### Основные операции стека


1. **Push** — добавление элемента на вершину стека.
2. **Pop** — удаление элемента с вершины стека.
3. **Top** — просмотр элемента на вершине стека.
4. **isEmpty** — проверка на наличие элементов в стеке.

Оценка по временной сложности: все основные операции стека работают за O(1), так как они обращаются только к вершине стека.

Оценка по памяти: O(n), где n - количество элементов в стеке.

------

### Реализация стека

Стек может быть реализован на основе **массива** или **связного списка**.

- **Массив**:

  - Используется статический или динамический массив.

  - **Преимущества**: быстрая индексация и простая реализация.

  - **Недостатки**: если массив статический, то есть риск переполнения при большом числе элементов. При динамическом массиве потребуется дополнительное время при расширении.

    

- **Связный список**:

  - Каждый элемент стека представлен узлом связного списка. Вершина стека — это первый элемент списка.  
    
  - **Преимущества**: стек может расти динамически без затрат времени на расширение.  
    
  - **Недостатки**: требует дополнительной памяти для хранения указателей, что может привести к фрагментации памяти при частых вставках и удалениях.

------

### Ограничения стека:

**Ограниченный доступ к элементам**: можно работать только с вершиной стека. Для доступа к элементам из середины или конца нужно удалить все элементы выше, что может быть неэффективно для задач, где требуется доступ к произвольным элементам.

#### Ограничения при реализации на массиве

1. **Фиксированный размер** (в статическом массиве): размер задается при создании стека, и если стек переполняется, его нельзя расширить.
2. **Перевыделение памяти при расширении** (в динамическом массиве): при достижении максимального размера массива выделяется новый массив большего размера, что может замедлить операции при большом количестве данных.

#### Ограничения при реализации на связном списке

1. **Память на указатели**: каждый элемент требует дополнительной памяти для хранения указателя, что увеличивает общие затраты на память.
2. **Фрагментация памяти**: частое динамическое выделение памяти может привести к фрагментации, особенно при большом числе операций.

  



# 2. Очередь

### Определение

**Очередь** — это абстрактный тип данных[^1], работающий по принципу FIFO (First In, First Out), что означает, что первый добавленный элемент удаляется первым. Элементы добавляются в конец очереди и удаляются из начала.

------

### Основные операции очереди

- **enqueue**: добавление элемента в конец очереди.
- **dequeue**: удаление элемента из начала очереди.
- **peek**: просмотр элемента в начале очереди без его удаления.
- **isEmpty**: проверка на наличие элементов в очереди.

Оценка по временной сложности: все операции работают за O(1).

Оценка по памяти: O(n).

------

### Реализация очереди

- **Массив**:
  
  Используется циклическая очередь для предотвращения перерасхода памяти.
  
  Для реализации циклической очереди в операциях enqueue и dequeue берется остаток от деления индексов хвоста/головы очереди на количество элементов:
  
  tail = (tail + 1) % n  и   head = (head + 1) % n.
  
  **Преимущества:**
  
  - проста в разработке,
  - по сравнению с реализацией на списке есть незначительная экономия памяти.
  
  **Недостатки:**
  
  - количество элементов в очереди ограничено размером массива
  
  - при переполнении очереди требуется перевыделение памяти и копирование всех элементов в новый массив, что увеличивает временную сложность до O(n).
  
    
  
- **Связный список**:
  
  Используется односвязный список, в котором есть поле, хранящее значение элемента, и указатель на следующий элемент.
  
  **Преимущества:**
  
  - каждая операция выполняется за время O(1).
  
  **Недостатки:**
  
  - память фрагментируется гораздо сильнее и последовательная итерация по такой очереди может быть ощутимо медленнее, нежели итерация по очереди реализованной на массиве.

------

### Ограничения очереди

- **Ограниченный доступ к элементам**: Нет возможности получить доступ к элементу по индексу.
#### Ограничения при реализации на массиве

1. **Фиксированный размер** (в статическом массиве): размер задается при создании очереди, и если очередь переполняется, его нельзя расширить.
2. **Перевыделение памяти при расширении** (в динамическом массиве): при достижении максимального размера массива выделяется новый массив большего размера, что может замедлить операции при большом количестве данных.

#### Ограничения при реализации на связном списке

1. **Память на указатели**: каждый элемент требует дополнительной памяти для хранения указателя, что увеличивает общие затраты на память.
2. **Фрагментация памяти**: частое динамическое выделение памяти может привести к фрагментации, особенно при большом числе операций.

  


# 3. Односвязный список

### Определение

**Односвязный список** — это абстрактный тип данных[^1], состоящий из узлов, связанных между собой последовательно посредством указателей. Каждый узел списка имеет указатель на следующий элемент. Указатель последнего элемента списка является нулевым указателем. Первый узел списка называется «головным», а последний - «хвостовым».

----

### Операции над односвязным списком

- **Добавление узла**:
  
  - **В начало**: O(1) — обновление указателя на голову.
  - **В конец**: O(n) — проход до последнего узла.
  - **В произвольное место**: O(n) — проход до нужной позиции.
- **Удаление узла**:
  - **Из начала**: O(1) — обновление указателя на голову.
  - **Из конца**: O(n) — проход до предпоследнего узла.
  - **Из произвольного места**: O(n) — поиск узла перед удаляемым.
- **Поиск узла**:

  - O(n) — последовательный проход от головы до конца.

----

### Вставка узла

Чтобы вставить узел в односвязный список после данного узла необходимо обновить указатели:

- Установить указатель `next` нового узла на следующий узел.

- Установить указатель `next` предыдущего узла на новый узел.

  ```c++
   void insert(Node* new_node, Node* prev_node){
     new_node->next = prev_node->next;
     prev_node->next = new_node;
   }
  ```

----

### Удаление узла

Чтобы удалить узел из односвязного списка после данного узла необходимо:

- Сохранить указатель на удаляемый узел

- Обновить указатель данного узла `next`, чтобы он указывал на узел, следующий за удаляемым. Это исключит удаляемый узел из цепочки.

- Освободить память, занятую удаляемым узлом, по сохраненному указателю.

  ```c++
   void removeAfter(Node* prev_node){
     if (prev_node->next != nullptr) {
         Node* tmp = prev_node->next;
         prev_node->next = prev_node->next->next;
         delete tmp;
     }
   }
  ```

### Ограничения односвязного списка

- **Однонаправленность**: Доступ только в одном направлении, усложняет операции с предыдущими узлами.
- **Дополнительная память**: Каждый узел требует дополнительной памяти для хранения указателя.
- **Ограниченный доступ к элементам**: Невозможность быстрого доступа к элементам по индексу.
- **Низкая скорость поиска**: O(n) для поиска, так как нужно пройти весь список.

------

### Преимущества и недостатки односвязного списка

**Преимущества**:

- Отсутствие фиксированной длины.
- Простота добавления и удаления узлов, особенно в начале списка.

**Недостатки**:

- Невозможность быстрого доступа к элементам и необходимость проходить весь список.
- Сложность работы с предыдущими узлами.
  
  



# 4. Двусвязный список

### Определение

Двусвязный список — это абстрактный тип данных[^1], состоящий из узлов, связанных между собой посредством указателей. Каждый узел списка имеет указатель на следующий и предыдущий элемент. Указатель последнего узла является нулевым указателем. Первый узел списка называется «головным», а последний - «хвостовым».

------

### Операции двусвязного списка

- **Добавление узла**:

  - **В начало**: O(1)

  - **В конец**: O(1) при наличии указателя на последний узел, O(n) в противном случае
  - **В произвольное место**: O(n)

-  **Удаление узла**:
   - **С начала**: O(1)
   - **С конца**: O(1) при наличии указателя на последний узел, O(n) в противном случае
   - **С произвольной позиции**: O(n)
- **Поиск узла**:
  - O(n) — последовательный проход от головы до конца.

----

### Вставка узла

Чтобы вставить узел в двусвязный список после данного узла необходимо обновить указатели:

- Установить указатель `next` нового узла на следующий узел, а указатель `prev` на предыдущий узел.

- Установить указатель `next` предыдущего узла на новый узел.

- Установить указатель `prev` следующего узла на новый узел

  ```c++
   void insert(Node* new_node, Node* prev_node){
     new_node->next = prev_node->next;
     new_node->prev=prev_node;
     prev_node->next=new_node;
     new_node->next->prev=new_node;
   }
  ```

----

### Удаление узла

Чтобы удалить узел из двусвязного списка после данного узла необходимо:

- Сохранить указатель на удаляемый узел

- Обновить указатель данного узла `next`, чтобы он указывал на узел, следующий за удаляемым. Обновить указатель `prev` у узла, следующего за удаляемым, на узел предыдущий удаляемому. Это исключит удаляемый узел из цепочки.

- Освободить память, занятую удаляемым узлом, по сохраненному указателю.

  ```c++
   void removeAfter(Node* prev_node){
     if (prev_node->next != nullptr) {
         Node* tmp = prev_node->next;
         prev_node->next = prev_node->next->next;
         prev_node->next->prev=prev_node
         delete tmp;
     }
   }
  ```



----

### Ограничения

- **Дополнительная память**: Каждый узел требует дополнительной памяти для хранения указателей.
- **Ограниченный доступ к элементам**: Невозможность быстрого доступа к элементам по индексу.
- **Низкая скорость поиска**: O(n) для поиска, так как нужно пройти весь список.
- **Увеличенная вычислительная нагрузка**: Необходимость обновления нескольких указателей при добавлении и удалении узлов.
  
----

### Преимущества и недостатки двусвязного списка

**Преимущества**:

- Двунаправленность: каждый узел содержит указатели как на следующий, так и на предыдущий узел, что позволяет легко перемещаться вперед и назад.
- Отсутствие фиксированной длины.
- Простота добавления и удаления узлов, особенно в начале списка.
- Подходит для реализации сложных структур данных: для стека, очереди, деревьев.

**Недостатки**:

- Невозможность быстрого доступа к элементам и необходимость проходить весь список.
- Каждый узел хранит два указателя, что увеличивает потребление памяти по сравнению с односвязным списком.
- Реализация двусвязного списка сложнее, чем односвязный список, из-за необходимости управления двумя указателями.
- Поскольку узлы выделяются динамически, это может привести к фрагментации памяти, что ухудшает производительность.




[^1]: **Абстрактный тип данных**— это математическая модель, где тип данных определяется поведением с точки зрения *пользователя* данных, а именно в терминах возможных значений, возможных операций над данными этого типа и поведения этих операций.
