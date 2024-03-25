# 函数
- *torch.gather(input, dim, index)*
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
