# 八股储备（PyTorch基础）

**Q：`torch.tensor` 和 `torch.Tensor` 的区别？**
A：`torch.tensor()` 是工厂函数，根据输入推断数据类型；`torch.Tensor()` 是类构造函数，默认生成 float32 空张量。**开发中统一用 `torch.tensor()`**。

**Q：张量运算 `x * y` 和 `x @ y` 的区别？**
A：`*` 是**按元素（element-wise）**逐个相乘（如 [1,2]*[3,4]=[3,8]）；`@`（或 `torch.matmul`）是**矩阵乘法**（行乘列求和）。

**Q：遇到报错 `expected scalar type Float but found Long` 怎么办？**
A：说明喂给模型的是整型（Long），但模型需要浮点型（Float）。用 `x = x.float()` 或 `x = x.to(torch.float32)` 转换即可。

**Q：`x += y` 和 `x = x + y` 的内存区别？**
A：`x += y` 是**原地修改（in-place）**，不创建新对象，`id(x)` 不变，省内存；`x = x + y` 是**新建对象并赋值**，`id(x)` 改变。显存吃紧时用前者。
