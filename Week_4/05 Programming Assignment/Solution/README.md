# Решение задачи «Перебор перестановок»

Основная идея — использовать алгоритм prev_permutation для итеративного построения предыдущей перестановки по заданной. Его удобно обернуть в цикл do while.

Кроме того, для инициализации первой перестановки используем алгоритмы iota (заполняющий диапазон числами от 1 до n) и reverse.

```c++
#include <iostream>
#include <vector>
#include <algorithm>
#include <numeric>

using namespace std;

int main() {
  int range_length;
  cin >> range_length;
  vector<int> permutation(range_length);
  
  // iota             -> http://ru.cppreference.com/w/cpp/algorithm/iota
  // Заполняет диапазон последовательно возрастающими значениями
  // Обратные итераторы позволяют заполнить его, двигаясь от конца к началу
  iota(permutation.rbegin(), permutation.rend(), 1); 
  
  // prev_permutation ->
  //     http://ru.cppreference.com/w/cpp/algorithm/prev_permutation
  // Преобразует диапазон в предыдущую (лексикографически) перестановку,
  // если она существует, и возвращает true,
  // иначе (если не существует) - в последнюю (наибольшую) и возвращает false
  do {
    for (int num : permutation) {
      cout << num << ' ';
    }
    cout << endl;
  } while (prev_permutation(permutation.begin(), permutation.end()));

  return 0;
}

```
