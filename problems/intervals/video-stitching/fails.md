```python
class Solution:
    def videoStitching(self, clips: List[List[int]], time: int) -> int:
        clips.sort(key=lambda x: x[0])
        counter = 1
        last = clips[0]

        if last[0] > 0:
            return -1

        for i in range(1, len(clips)):
            if last[1] >= time:
                return counter

            current = clips[i]
            
            if current[0] > last[1]:
                # Если начало текущего больше конца последнего, они не пересекаются, значит невозможно соединить полное видео.
                return -1
            elif current[1] <= last[1]:
                # Если конец текущего меньше последнего, такой нам не интересен.
                pass
            elif current[0] <= last[0]:
                # Конец текущего длинее последнего.
                # Если начало текущего меньше или равно началу последнго и конец текущего длиннее последнего, значит последний выкидывается, его можно заменить.
                # Меньше не может быть, потому что они отсортированы по началам.
                end = max(current[0], last[0])
                last = current
                last[1] = end
            else:
                # Конец текущего длинее последнего.
                # Если начало текущего больше начала последнего интервала и конец текущего длиннее последнего, увеличить счетчик и заменить последний.
                counter += 1
                end = max(current[0], last[0])
                last = current
                last[1] = end

        return counter

Input clips = [[0,1],[1,2]]
time = 5
Output 2
Expected -1

После выходна из цикла не добавил проверку

if last[1] < time:
    return -1

Input clips = [[8,10],[17,39],[18,19],[8,16],[13,35],[33,39],[11,19],[18,35]]
time = 20
Output 2
Expected -1

Не добавил проверку, что начало первого интервало равняется 0, иначе это не полное видео.


if last[0] > 0:
    return -1

Еще надо было обрезать лишние концы начал роликов
```