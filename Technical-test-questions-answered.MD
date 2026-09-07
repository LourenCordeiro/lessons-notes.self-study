# Prova técnica vaga de Estágio (28/08/26)

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
