numpy

![e1626f81aeb6f02925383ea907481e34.png](../../_resources/36c62046ea9d40a8b2132eb695edc646.png)

np.dot  向量积

np.cross  AXB 与A，B 均垂直

np.outer 外积 \[\]

subtract -

add +

*  *

dot 向量积

# Broadcasting

x = np.array(\[1,2\]) # vector

y = np.array(3) # scalar

z = x + y

print ("z:\\n", z)

\# Transposing

x = np.array(\[\[1,2,3\], \[4,5,6\]\])

print ("x:\\n", x)

print ("x.shape: ", x.shape)

y = np.transpose(x, (1,0))

# Reshaping

x = np.array(\[\[1,2,3,4,5,6\]\])

print (x)

print ("x.shape: ", x.shape)

y = np.reshape(x, (2, 3))

# Unintended reshaping

z_incorrect = np.reshape(x, (x.shape\[1\], -1))

print ("z\_incorrect:\\n", z\_incorrect)

print ("z\_incorrect.shape: ", z\_incorrect.shape)

# Intended reshaping

y = np.transpose(x, (1,0,2))

print ("y:\\n", y)

print ("y.shape: ", y.shape)

z_correct = np.reshape(y, (y.shape\[0\], -1))

print ("z\_correct:\\n", z\_correct)

print ("z\_correct.shape: ", z\_correct.shape)

# Removing dimensions

x = np.array(\[\[\[1,2,3\]\],\[\[4,5,6\]\]\])

print ("x:\\n", x)

print ("x.shape: ", x.shape)

y = np.squeeze(x, 1) # squeeze dim 1

print ("y: \\n", y)

print ("y.shape: ", y.shape)  # notice extra set of brackets are gone

# Adding dimensions

x = np.array(\[\[1,2,3\],\[4,5,6\]\])

print ("x:\\n", x)

print ("x.shape: ", x.shape)

y = np.expand_dims(x, 1) # expand dim 1

print ("y: \\n", y)

print ("y.shape: ", y.shape)   # notice extra set of brackets are added

torch

x = torch.randn(2, 3)

y = torch.randn(2, 3)

z = x + y

# Dot product

x = torch.randn(2, 3)

y = torch.randn(3, 2)

z = torch.mm(x, y)

# Transpose

x = torch.randn(2, 3)

print(f"Size: {x.shape}")

print(f"Values: \\n{x}")

y = torch.t(x)

\# Reshape

x = torch.randn(2, 3)

z = x.view(3, 2)

# Dangers of reshaping (unintended consequences)

x = torch.tensor(\[

\[\[1,1,1,1\], \[2,2,2,2\], \[3,3,3,3\]\],

\[\[10,10,10,10\], \[20,20,20,20\], \[30,30,30,30\]\]

\])

print(f"Size: {x.shape}")

print(f"x: \\n{x}\\n")

a = x.view(x.size(1), -1)

print(f"\\nSize: {a.shape}")

print(f"a: \\n{a}\\n")

b = x.transpose(0,1).contiguous()

print(f"\\nSize: {b.shape}")

print(f"b: \\n{b}\\n")

c = b.view(b.size(0), -1)

print(f"\\nSize: {c.shape}")

print(f"c: \\n{c}")

# Dimensional operations

x = torch.randn(2, 3)

print(f"Values: \\n{x}")

y = torch.sum(x, dim=0) # add each row's value for every column

print(f"Values: \\n{y}")

z = torch.sum(x, dim=1) # add each columns's value for every row

print(f"Values: \\n{z}")

# Select with dimensional indicies

x = torch.randn(2, 3)

print(f"Values: \\n{x}")

col_indices = torch.LongTensor(\[0, 2\])

print(col_indices)

chosen = torch.index\_select(x, dim=1, index=col\_indices) # values from column 0 & 2

print(f"Values: \\n{chosen}")

row_indices = torch.LongTensor(\[0, 1\])

col_indices = torch.LongTensor(\[0, 2\])

chosen = x\[row\_indices, col\_indices\] # values from (0, 0) & (2, 1)

print(f"Values: \\n{chosen}")

# Concatenation

x = torch.randn(2, 3)

print(f"Values: \\n{x}")

y = torch.cat(\[x, x\], dim=0) # stack by rows (dim=1 to stack by columns)

# Tensors with gradient bookkeeping

x = torch.rand(3, 4, requires_grad=True)

y = 3*x + 2

z = y.mean()

z.backward() # z has to be scalar

print(f"x: \\n{x}")

print(f"x.grad: \\n{x.grad}")