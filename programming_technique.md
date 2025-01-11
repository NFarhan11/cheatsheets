# Programing Technique

A collection of random programming techniques that I found.

## To Toggle

- `not` keyword to toggle boolean.

```python
index_open = False
if key_pressed:
    index_open = not index_open # True
```

## Circular Indexing

- reset index when reaching boundary.
- good for navigation feature or 2D animation.

```python
arr = [0, 1, 2, 3]
current_index = current_index % len(arr) # 0,1,2,3,0,1,2,3,...
```

> _4 % 4 = 0_  
> _5 % 4 = 1_  
> _Thus, out of bound number is reset to 0_

## Vertical Scrolling

- push visible items up when index exceed visible items

```python
v_offset = 0 if index < visible else - item_height
y = main_rect.y + index * item_height + v_offset
```

> _y is a coordinate, where it control current_item y-position._

## Easy Padding

- automate padding for inner rect

```python
padding = p
inner_width = outer_width - padding * 2
inner_height = outer_height - padding * 2

inner_x = outer_x + padding
inner_y = outer_y + padding
```
