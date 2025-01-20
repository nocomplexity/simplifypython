# Common mistakes

## Never change a list while iterating over it.

Can can search why your function does not work for too long. In the example below the list is modified while iterating over it. This can lead to skipping elements! Random behaviour.

```python
def delete_old_rows(rss_json_list):    
    print(f'Total number of items in RSS JSON before clean up: {len(rss_json_list)}')
    counter = 0
    for i,item in enumerate(rss_json_list):
        if is_older_than_40_days(item['date']):            
            print(f'Item to delete {i} - Date: {item['date']}')
            rss_json_list.remove(item)
            counter += 1
        else:
            print(f'\nKeeping Item {i} - Date: {item['date']}\n')
    print(f'Total number of items removed (older than 40 days - or date in RSS field says so...): {counter}')
    print(f'Total number of items in RSS JSON archive now: {len(rss_json_list)}')
    return rss_json_list
```


## Avoid range command

While the range function is generally useful for creating sequences of numbers for `for`` loops, there might be cases where avoiding its use could be more appropriate.


```python
# multiply 2 to all elements of arr
arr = [10, 20, 30]

# bad practice
for i in range(len(arr)):
    print(2*arr[i])  # 20, 40, 60

# good practices
for i in arr:
    print(2*i)  # 20, 40, 60

# print in reverse order
for i in reversed(arr):
    print(2*i)  # 60, 40, 20
```

    20
    40
    60
    20
    40
    60
    60
    40
    20


