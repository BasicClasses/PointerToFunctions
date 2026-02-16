# Указатели на фунции

Указатель на функцию — это переменная, которая хранит адрес функции (как указатель на данные хранит адрес переменной). 

Где используется: 
 - Callback-функции (передаём “что сделать” как параметр).
 - Выбор стратегии: сортировка по-разному, разные формулы расчёта, разные обработчики событий.
 - Таблица команд: “команда → функция” (например, интерпретатор команд).
 - В низкоуровневых API на C (например, обработчики в библиотеках).

## Синтаксис
```
ReturnType (*pointerName)(ParamTypes...);
```

```
int mul(int a, int b) { return a * b; }

int main() {
    int (*pf)(int, int) = mul; // pf хранит адрес функции mul
    int r = pf(3, 4);          // 12
}
```

## typedef / using: делаем тип читаемым
```
using Op = int(*)(int, int);   // Op — “указатель на функцию: int(int,int)”

int add(int a, int b) { return a + b; }
int sub(int a, int b) { return a - b; }

int main() {
    Op op = add;
    op = sub;
}
```

## Передача функции как параметра
```
#include <iostream>

using Op = int(*)(int, int);

int apply(int x, int y, Op op) {
    return op(x, y);
}

int add(int a, int b) { return a + b; }
int mul(int a, int b) { return a * b; }

int main() {
    std::cout << apply(2, 3, add) << "\n"; // 5
    std::cout << apply(2, 3, mul) << "\n"; // 6
}
```

## Массив/таблица функций
```
#include <iostream>

using Op = int(*)(int,int);

int add(int a,int b){ return a+b; }
int sub(int a,int b){ return a-b; }
int mul(int a,int b){ return a*b; }

int main() {
    Op ops[] = { add, sub, mul };

    int choice = 0;
    int x = 10, y = 5;

    std::cout << "0:add 1:sub 2:mul\n";
    std::cin >> choice;

    if (choice >= 0 && choice < 3)
        std::cout << opsx, y << "\n";
}
```





# Задания

## Transform: “функция как параметр”

“Мы пишем один универсальный цикл по массиву, а что делать с каждым элементом — решает функция, которую мы передали.” 
Практический аналог: 
 - преобразование данных перед выводом/сохранением 
 - нормализация значений (abs, clamp, scale)
 
Реализовать: 
```
void transform(int* a, int n, UnOp f);
```
Заготовка 
```
int square(int x) {
    // TODO
    return 0;
}

int inc(int x) {
    // TODO
    return 0;
}

int abs_val(int x) {
    // TODO
    return 0;
}

void transform(int* a, int n, UnOp f) {
    // TODO
}
```
## Калькулятор через таблицу: “dispatch/таблица действий”
Смысл 
Вместо: if op == '+' then add else if '-' then sub ... 
мы строим таблицу функций и выбираем нужную по ключу.” 

Заготовка
```
int add(int a, int b) { /* TODO */ return 0; }
int sub(int a, int b) { /* TODO */ return 0; }
int mul(int a, int b) { /* TODO */ return 0; }
int div_safe(int a, int b) { /* TODO */ return 0; }

BinOp get_op(char op) {
    // TODO: реализовать через таблицу указателей на функции
    // подсказка:
    // static BinOp ops[] = { add, sub, mul, div_safe };
    // выбрать индекс по op и вернуть ops[idx]
    return nullptr;
}

```

## count_if + copy_if: “предикаты + динамическая память”

Заготовка
```
#include "task4_filter.h"

bool is_even(int x)     { /* TODO */ return false; }
bool is_positive(int x) { /* TODO */ return false; }
bool is_neg(int x)      { /* TODO */ return false; }

int count_if(const int* a, int n, Pred pred) {
    // TODO
    return 0;
}

int* copy_if(const int* a, int n, int& out_n, Pred pred) {
    // TODO
    out_n = 0;
    return nullptr;
}
```



