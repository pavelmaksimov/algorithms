```python
class Solution:
    def fib(self, n: int) -> int:
        p1 = 0
        p2 = 1
        count = 0
        
        while count < n:
            p1, p2 = p2, p1 + p2
            count += 1

        return p1 + p2

Input n = 2
Output 3
Expected 1

Тут счетчик неправильно выставил, он должен быть 2

Но тогда при n=0 ответ неверный

Лучше использовать стек, это уменьшает рик ошибиться где-то

Не хотел писать условия if когда n=0 и n=1, из-за этого
Много ошибок с тем, что следующее число возвращал в последовательности Фибоначчи
В ообщем запутался в том, как цикл остановить 
во время при этом не писать условия на случаи f(n=0) и f(n=1)

Для гибкости не хватило понимание, что не обязательно останавливаться 
в тот момент, когда счетчик циклов дошел до N
Можно еще один раз итерацию сделать, тогда первая переменная будет нужным значением.
```