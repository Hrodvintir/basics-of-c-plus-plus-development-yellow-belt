# Решение задачи «Удаление повторов»

Внимание! Ниже опубликовано решение необязательной задачи «Удаление повторов». Настоятельно рекомендуем попытаться её решить перед тем, как читать решение.

```c++
#include <algorithm>
using namespace std;

template <typename DataType>
void RemoveDuplicates(vector<DataType>& elements) {
  sort(begin(elements), end(elements));
  elements.erase(
      unique(begin(elements), end(elements)),
      elements.end());
}

```
