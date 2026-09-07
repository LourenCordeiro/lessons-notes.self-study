# Prova técnica vaga de Estágio (27/08/26)

## Questão 1

```
def reverse_words(s: str) -> str:
    return ".".join(s.split()[::-1])

frase = input()
print(reverse_words(frase))
```

## Questão 2

```
def idade_em_dias(s: str) -> int:
    anos, meses, dias = s.split("/")
    return int(anos) * 365 + int(meses) * 30 + int(dias)

entrada = input()
print(idade_em_dias(entrada))
```

## Questão 3

```
def maior_retangulo(a: int, b: int, c: int, d: int) -> int:
    nums = sorted([a, b, c, d])
    return nums[0] * nums[3]

a, b, c, d = map(int, input().split())
print(maior_retangulo(a, b, c, d))
```

## Questão 4

```
def resolver(m: int, numeros: list[int]) -> list[str]:
    resultado = []
    for num in numeros:
        s = str(num)
        if m == 2:
            novo = "".join(d for d in s if int(d) % 2 != 0)
        else:
            digitos = list(s)
            for i in range(0, len(digitos) - 1, 2):
                digitos[i], digitos[i + 1] = digitos[i + 1], digitos[i]
            novo = "".join(digitos)
        resultado.append(novo)
    return resultado

entrada = input().split(",")
m = int(entrada[0])
numeros = [int(x) for x in entrada[1:]]
print(",".join(resolver(m, numeros)))
```

## Questão 5

```
def josephus(n: int, k: int) -> int:
    resultado = 0
    for i in range(2, n + 1):
        resultado = (resultado + k) % i
    return resultado + 1

n, k = map(int, input().split(","))
print(josephus(n, k))
```

## Questão 6

```
def ordem_segura(salas: list[int]) -> str:
    total = sum(salas)
    maximo = max(salas)
    idx_max = salas.index(maximo)

    if 2 * maximo > total:
        return "impossible"

    ordem = [idx_max + 1]
    for i in range(len(salas)):
        if i != idx_max:
            ordem.append(i + 1)

    return " ".join(map(str, ordem))

n = int(input())
salas = list(map(int, input().split()))
print(ordem_segura(salas))
```

## Questão 7

```
def buscar_aluno(entrada: list[str]) -> str:
    posicao = int(entrada[-1])
    alunos = entrada[:-1]
    return alunos[posicao]

dados = input().split(",")
print(buscar_aluno(dados))
```

## Questão 8

```
def anagrama_valido(word: str, anagrama: str) -> bool:
    if len(anagrama) != len(word):
        return False
    if anagrama == word:
        return False
    if sorted(anagrama) != sorted(word):
        return False
    return True

word = input()
anagrama = input()
print(anagrama_valido(word, anagrama))
```

## Questão 9 

```
class No:
    def __init__(self, valor: int):
        self.valor = valor
        self.esquerda = None
        self.direita = None

def construir_arvore(valores: list[str]) -> No | None:
    if not valores:
        return None

    raiz = No(int(valores[0]))
    fila = [raiz]
    i = 1

    while i < len(valores):
        atual = fila.pop(0)
        if i < len(valores):
            atual.esquerda = No(int(valores[i]))
            fila.append(atual.esquerda)
            i += 1
        if i < len(valores):
            atual.direita = No(int(valores[i]))
            fila.append(atual.direita)
            i += 1

    return raiz

def pre_ordem(no: No | None) -> list[int]:
    if no is None:
        return []
    return [no.valor] + pre_ordem(no.esquerda) + pre_ordem(no.direita)

valores = input().split()
raiz = construir_arvore(valores)
print(" ".join(map(str, pre_ordem(raiz))))
```

## Questão 10

```
def hex_para_porcentagem(codigo: str) -> str:
    r = int(codigo[1:3], 16)
    g = int(codigo[3:5], 16)
    b = int(codigo[5:7], 16)

    pct_r = r * 100 // 255
    pct_g = g * 100 // 255
    pct_b = b * 100 // 255

    return f"{pct_r}% {pct_g}% {pct_b}%"

codigo = input()
print(hex_para_porcentagem(codigo))
```
