# 函数
- ***torch.gather(input, dim, index)***
  - out[i][j][k] = input[index[i][j][k]][j][k]  # if dim == 0
  - out[i][j][k] = input[i][index[i][j][k]][k]  # if dim == 1
  - out[i][j][k] = input[i][j][index[i][j][k]]  # if dim == 2
  ```python
  t = torch.tensor([[1, 2], [3, 4]])  
      torch.gather(t, 1, torch.tensor([[0, 0], [1, 0]]))  
      tensor([  
        [ 1,  1],  
        [ 4,  3]  
      ])
  ```
  - dim指示被替换的维度，output被替换维度下标填入*t的数值*，剩余的维度下标填入t的下标的下标
- ***torch.chunk(input, chunks, dim=0)***
  - 按照chunks分块
- ***torch.split(tensor, split_size_or_sections, dim=0)***
  - 按照size分块或者按照list分块
  - ```python
    tensor([[0, 1],
        [2, 3],
        [4, 5],
        [6, 7],
        [8, 9]])
    torch.split(a, 2)
      (tensor([[0, 1],
         [2, 3]]),
       tensor([[4, 5],
         [6, 7]]),
       tensor([[8, 9]]))
    torch.split(a, [1, 4])
      (tensor([[0, 1]]),
       tensor([[2, 3],
             [4, 5],
             [6, 7],
             [8, 9]]))
   ```
