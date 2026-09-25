## Para que o Python serve? ## 
Python é uma linguagem de programação de alto nível, de propósito geral, com
tipagem dinâmica e forte, criada por Guido van Rossum e lançada em 1991. Alto nível
significa que ela esconde detalhes da máquina, como gerenciamento de memória.
Propósito geral significa que não foi feita para um único domínio. Tipagem dinâmica
significa que o tipo de uma variável é definido em tempo de execução, e forte significa
que ela não converte tipos sozinha de forma implícita: "2" + 2 gera erro em vez de
adivinhar o resultado.

Sistemas que exigem desempenho máximo ou tempo de resposta previsível (jogos,
sistemas embarcados, drivers) costumam usar C, C++ ou Rust. Apps mobile nativos usam
Swift e Kotlin, e o frontend no navegador usa JavaScript/TypeScript. Muitas bibliotecas de
Python, como NumPy e PyTorch, contornam a questão do desempenho sendo escritas em
C/C++ por baixo: você escreve em Python, mas o trabalho pesado roda em código
compilado.

## O que é uma linguagem compilada? ## 
Uma linguagem é chamada de compilada quando seu código-fonte é traduzido, antes da
execução, por um programa chamado compilador, que gera um arquivo em código de
máquina (as instruções binárias que o processador entende). Esse processo é chamado
de compilação AOT (Ahead-of-Time).
Durante a compilação, o compilador passa por fases bem definidas, estudadas na
disciplina de compiladores:
- Análise léxica: quebra o texto em tokens (palavras-chave, nomes, operadores).
- Análise sintática: verifica se os tokens seguem a gramática da linguagem e monta
uma árvore (AST).
- Análise semântica: verifica o significado, por exemplo se os tipos são compatíveis.
- Otimização: reescreve o código para rodar mais rápido.
- Geração de código: produz o código de máquina para aquele processador e sistema
operacional.

## O que é uma linguagem interpretada?## 
Uma linguagem é chamada de interpretada quando seu código é executado por outro
programa, o interpretador, que lê e executa as instruções durante a execução, sem
gerar antes um executável em código de máquina.
O interpretador funciona num ciclo contínuo: lê a próxima instrução, analisa o que ela
significa e executa a ação correspondente. Por isso, o mesmo código roda em qualquer
sistema que tenha o interpretador instalado: é o interpretador que conhece a máquina,
não o seu código.
Compilado ou interpretado é uma característica da implementação, não da linguagem
em si. A maioria das linguagens modernas é híbrida:
- Java e C# compilam para bytecode, que roda numa máquina virtual (JVM, .NET) com
compilação JIT.
- JavaScript no motor V8 (Chrome e Node.js) começa interpretando e usa JIT
(Just-In-Time) para compilar para código de máquina os trechos que rodam muitas
vezes.
- TypeScript é transpilado (traduzido para outra linguagem do mesmo nível) para
JavaScript pelo tsc, etapa em que também aparecem os erros de tipo.

## Como funciona o Python por debaixo dos panos? (Analisar se é compilada/interpretada)? ## 

Uma linguagem é chamada de interpretada quando seu código é executado por outro
programa, o interpretador, que lê e executa as instruções durante a execução, sem
gerar antes um executável em código de máquina.
O interpretador funciona num ciclo contínuo: lê a próxima instrução, analisa o que ela
significa e executa a ação correspondente. Por isso, o mesmo código roda em qualquer
sistema que tenha o interpretador instalado: é o interpretador que conhece a máquina,
não o seu código.

<img width="1411" height="391" alt="image" src="https://github.com/user-attachments/assets/14b03d12-a5b6-4c2d-8ef3-ad5eb3b2ab4e" />

<img width="1377" height="503" alt="image" src="https://github.com/user-attachments/assets/3837f73b-41c2-4770-9d00-7248bbaca6b6" />

## O que é um gerenciador de pacotes (pip)? ## 
## O que é um ambiente virtual (venv) e por que é fundamental usá-lo? ## 
## Como a internet funciona? ## 
## O que é a arquitetura Cliente-Servidor? ## 
## O que é I/O? ## 
## O que é assincronidade e como ajuda no I/O? ## 
## O que é, de fato, uma API? ## 
## O que é o padrão REST? ## 
## O que é o protocolo HTTP? ## 
## Quais são os principais Métodos (ou Verbos) HTTP? ## 
## O que são os Códigos de Status HTTP? ## 
## O que é JSON? ## 
## O que é um Framework web? ## 
