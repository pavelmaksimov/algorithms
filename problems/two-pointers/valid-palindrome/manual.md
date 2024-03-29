# [Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)
## Задача
Фраза является **палиндромом**, если после преобразования всех прописных букв в строчные и удаления всех не алфавитно-цифровых символов она читается одинаково вперед и назад. Буквенно-цифровые символы включают буквы и цифры.

Задана строка `s`, верните `true`_, является ли она **палиндромом** или_ `false` _иным_ образом.
```
Пример 1:
Ввод: s = "Человек, план, канал: Панама"
Вывод:true 
Пояснение: "amanaplanacanalpanama" - это палиндром.

Пример 2:
Ввод: s = "участвовать в гонках на автомобиле"
Вывод:false 
Пояснение: "raceacar" не является палиндромом.

Пример 3:
Ввод: s = " "
Вывод:true 
Пояснение: s является пустой строкой "" после удаления не буквенно-цифровых символов.
Поскольку пустая строка читается одинаково вперед и назад, это палиндром.
```
## Идея
Указатели поставить на начало и конец. Пропуская не алфавитно-цифровые символы, сравнивать значения под указателями.
## Нюансы
## Решение
```python
class Solution:
    def isPalindrome(self, s: str) -> bool:
        l, r = 0, len(s) - 1

        while l <= r:
            if not s[l].isalnum():
                l += 1
                continue
            if not s[r].isalnum():
                r -= 1
                continue
            
            if s[l].lower() != s[r].lower():
                return False
            
            l += 1
            r -= 1
        
        return True
```
Оценка по памяти `O(1)`

Оценка по времени `O(n)`
