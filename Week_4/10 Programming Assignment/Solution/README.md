# Решение задачи «Группировка строк по префиксу»

### Часть 1. Группировка по первому символу
```c++
#include <algorithm>
#include <utility>
#include <string>


template <typename RandomIt>
pair<RandomIt, RandomIt> FindStartsWith(
    RandomIt range_begin, RandomIt range_end, char prefix) {
      
  // Все строки, начинающиеся с '<prefix>', больше или равны строке "<prefix>"
  auto left = lower_bound(range_begin, range_end, string(1, prefix));
  
  // Составим следующий в алфавите символ.
  // Не страшно, если prefix = 'z':
  // в этом случае мы получим следующий за 'z' символ в таблице символов
  char next_prefix = static_cast<char>(prefix + 1);
  
  // Строка "<next_prefix>" в рамках буквенных строк
  // является точной верхней гранью
  // множества строк, начнающихся с '<prefix>'
  auto right = lower_bound(range_begin, range_end, string(1, next_prefix));
  
  return {left, right};
}

```

### Часть 2. Группировка по префиксу

```c++
#include <algorithm>
#include <utility>
#include <string>


template <typename RandomIt>
pair<RandomIt, RandomIt> FindStartsWith(
	RandomIt range_begin, RandomIt range_end, string prefix) {
	
  // Все строки, начинающиеся с prefix, больше или равны строке "<prefix>"
  auto left = lower_bound(range_begin, range_end, prefix);
  
  // Составим строку, которая в рамках буквенных строк является
  // точной верхней гранью множества строк, начинающихся с prefix
  string upper_bound = prefix;
  ++upper_bound[upper_bound.size() - 1];
  
  // Первое встреченное слово, не меньшее upper_bound,
  // обязательно является концом полуинтервала
  auto right = lower_bound(range_begin, range_end, upper_bound);
  
  return {left, right};
}

```
