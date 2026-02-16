# Указатели на фунции

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



