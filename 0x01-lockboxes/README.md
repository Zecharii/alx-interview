# 0x01. Lockboxes
This is a project task that determines if all boxes can be opened.

## Requirements
* Allowed editors: `vi`, `vim`, `emacs`
* All your files will be interpreted/compiled on Ubuntu 20.04 LTS using Python3 (version 3.4.3)
* All your files should end with a new line
* The first line of all your files should be exactly `#!/usr/bin/python3`
* A README.md file, at the root of the folder of the project, is mandatory
* Your code should be documented
* Your code should use the PEP 8 style (version 1.7.x)
* All your files must be executable

## Description
This project involves solving the problem of determining if all the boxes can be opened. Each box is numbered sequentially from `0` to `n - 1` and may contain keys to the other boxes. The goal is to write a method `canUnlockAll(boxes)` that returns `True` if all the boxes can be opened, and `False` otherwise.

## Prototype
```
def canUnlockAll(boxes):
```
## Parameters
* `boxes`: A list of lists, where each sublist represents a box and contains keys to other boxes.

## Returns
* `True` if all boxes can be opened, else `False`.

## Assumptions
* All keys will be positive integers.
* There can be keys that do not have corresponding boxes.
* The first box boxes[0] is initially unlocked.

## Example Usage

```
#!/usr/bin/python3

canUnlockAll = __import__('0-lockboxes').canUnlockAll

boxes = [[1], [2], [3], [4], []]
print(canUnlockAll(boxes))  # True

boxes = [[1, 4, 6], [2], [0, 4, 1], [5, 6, 2], [3], [4, 1], [6]]
print(canUnlockAll(boxes))  # True

boxes = [[1, 4], [2], [0, 4, 1], [3], [], [4, 1], [5, 6]]
print(canUnlockAll(boxes))  # False
```

## Implementation

```
#!/usr/bin/python3
def canUnlockAll(boxes):
    if not boxes:
        return False

    n = len(boxes)
    opened = [False] * n
    opened[0] = True
    stack = [0]
    
    while stack:
        current_box = stack.pop()
        for key in boxes[current_box]:
            if key < n and not opened[key]:
                opened[key] = True
                stack.append(key)
    
    return all(opened)

# Test cases
if __name__ == "__main__":
    boxes = [[1], [2], [3], [4], []]
    print(canUnlockAll(boxes))  # True

    boxes = [[1, 4, 6], [2], [0, 4, 1], [5, 6, 2], [3], [4, 1], [6]]
    print(canUnlockAll(boxes))  # True

    boxes = [[1, 4], [2], [0, 4, 1], [3], [], [4, 1], [5, 6]]
    print(canUnlockAll(boxes))  # False
```

## Usage
To use this implementation, save the code in a file named `0-lockboxes.py`. Make sure to make the file executable and follow PEP 8 styling guidelines. Then, you can run the script and test the `canUnlockAll` function with different lists of boxes to determine if all boxes can be opened.

