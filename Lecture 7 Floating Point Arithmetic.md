2024.10.16

# Lecture 7 Floating Point Arithmetic

## Something Surprising

```python
x = 1e-16  # this is x = 10^(-16)
print(1 + x == 1)
```

True

```python
a = 1e16
b = -1e16
c = 1.0

print((a + b) + c)
```

1.0

```python
print(a + (b + c))
```

0.0

## Convert (x)_10 to (x)_2

### Converting the Integer Part

| calculation       | quotient | remainder |
| ----------------- | -------- | --------- |
| $11 \div 2$      | $5$     | $1$ (LSB)      |
| $5 \div 2$       | $2$     | $1$       |
| $2 \div 2$       | $1$     | $0$       |
| $1 \div 2$       | $0$ (stop)     | $1$ (MSB)       |

- We read the remainders from **<u>bottom to top</u>**: $1$ (MSB), $0$, $1$, $1$ (LSB):


$$(11)_{10} = (1011)_2$$

### Converting the Decimal Part

| calculation         | result         | integer part | fractional part |
| ------------------- | -------------- | ------------ | ------------------------- |
| $0.625 \times 2$    | $1.25$        | $1$          | $0.25$                   |
| $0.25 \times 2$     | $0.50$        | $0$          | $0.50$                   |
| $0.5 \times 2$      | $1.0$         | $1$          | $0.0$                    |

Thus, 0.625 in binary, when we read the integer parts from **<u>top to bottom</u>**:
$$(0.625)_{10} = (0.101)_{2}$$

## IEEE-754

