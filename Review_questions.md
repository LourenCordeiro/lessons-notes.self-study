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
Um pacote é um conjunto de código reutilizável, publicado para que outras pessoas
possam usar, como o FastAPI ou o Pandas. Um gerenciador de pacotes é a ferramenta
que busca, baixa, instala, atualiza e remove esses pacotes, cuidando também das
dependências: se o FastAPI precisa do Pydantic e do Starlette, eles são instalados junto,
nas versões compatíveis.
O pip (pip installs packages) é o gerenciador de pacotes oficial do Python. Ele baixa os
pacotes do PyPI (Python Package Index, pypi.org), o repositório público da comunidade,
com centenas de milhares de pacotes. O requirements.txt registra as versões para o
ambiente ser reproduzível. 

## O que é um ambiente virtual (venv) e por que é fundamental usá-lo? ## 
Um ambiente virtual é uma pasta isolada que contém uma cópia (ou um link) do
interpretador Python e seu próprio diretório de pacotes. Quando o ambiente está ativo,
tudo que você instala com o pip vai para essa pasta, e não para o Python do sistema. O
venv é o módulo da biblioteca padrão que cria esses ambientes. (O problema que ele resolve
Sem ambiente virtual, todos os projetos compartilham o mesmo lugar de instalação.
Imagine dois projetos na sua máquina: um novo, que precisa do pydantic 2.9, e um
legado, que só funciona com o pydantic 1.10. Só pode existir uma versão instalada por
vez, então atualizar para um projeto quebra o outro. Esse conflito é conhecido como
dependency hell).

*Por que é fundamental*
- Isolamento: cada projeto tem suas versões, sem conflito entre eles.
- Reprodutibilidade: o ambiente pode ser recriado igual na máquina de outra pessoa,
na pipeline de CI e no servidor de produção.
- Proteção do sistema: em Linux e macOS, o sistema operacional usa o próprio Python.
Instalar pacotes nele pode quebrar ferramentas do sistema, e por isso distribuições
recentes bloqueiam o pip install global (PEP 668).
- Clareza de dependências: o ambiente só tem o que o projeto realmente usa, então o
pip freeze gera uma lista limpa.

## Como a internet funciona? ## 
A internet é uma rede de redes: milhões de redes independentes (de empresas,
universidades, provedores e datacenters) interligadas, que trocam dados seguindo um
conjunto comum de protocolos, as regras que definem o formato e a ordem da
comunicação. O conjunto central é a pilha TCP/IP.
Um princípio fundamental é a comutação de pacotes: os dados não viajam como um
bloco contínuo, mas quebrados em pequenos pacotes. Cada pacote carrega o endereço
de origem e de destino e pode seguir um caminho diferente pela rede. No destino, eles são
remontados na ordem certa.
<img width="1417" height="435" alt="image" src="https://github.com/user-attachments/assets/99147e7a-55d6-4956-8df5-61c0ac6b5047" />
<img width="1331" height="582" alt="image" src="https://github.com/user-attachments/assets/c084bcb2-e694-40e9-be15-48c85551c09f" />


## O que é a arquitetura Cliente-Servidor? ## 
É um modelo de arquitetura distribuída em que as responsabilidades são divididas
entre dois papéis:
• Cliente: quem inicia a comunicação e faz pedidos. Pode ser um navegador, um app
de celular ou outro serviço.
• Servidor: quem fica esperando pedidos, processa e responde. Concentra os dados e
as regras de negócio.
A comunicação segue o padrão requisição-resposta (request-response): o cliente
sempre inicia, e o servidor sempre responde.
<img width="1412" height="470" alt="image" src="https://github.com/user-attachments/assets/484c09d3-32ab-418a-bb09-21995d8fe3db" />

## O que é I/O? ## 
I/O (Input/Output, entrada e saída) é toda operação em que um programa troca dados
com algo fora da CPU e da memória principal: disco, rede, teclado, tela, banco de
dados, filas de mensagens.
- Ler ou gravar um arquivo.
- Consultar um banco de dados.
- Chamar uma API pela rede.
- Publicar ou consumir uma mensagem numa fila.
- Ler o que o usuário digita: o input() é uma operação de I/O.

1-I/O-bound: o tempo é dominado pela espera de I/O. É o caso da grande maioria das
APIs web, que passam o tempo esperando o banco e outros serviços.
2-CPU-bound: o tempo é dominado por cálculo, como processar imagens, compactar
arquivos ou treinar modelos.

## O que é assincronidade e como ajuda no I/O? ## 
Em um modelo síncrono, cada operação precisa terminar antes que a próxima comece.
Se a operação é de I/O, a execução fica bloqueada esperando.
Em um modelo assíncrono, quando uma operação de I/O é iniciada, o programa não
espera parado: ele registra que quer ser avisado quando o resultado chegar e segue
executando outras tarefas. Isso é chamado de I/O não bloqueante.
Um conceito acadêmico importante aqui é a diferença entre concorrência e paralelismo.
Concorrência é lidar com várias tarefas ao mesmo tempo, intercalando-as; paralelismo é
executar várias tarefas literalmente ao mesmo tempo, em núcleos diferentes. O código
assíncrono é concorrente: uma única thread alterna entre muitas tarefas, aproveitando os
momentos de espera.

*EVENT LOOP*
Quem coordena tudo isso é o event loop (laço de eventos). Ele mantém uma fila de
tarefas e repete o ciclo: executa uma tarefa até ela precisar esperar I/O (o await), guarda
o ponto onde ela parou, passa para a próxima tarefa pronta e, quando o sistema
operacional avisa que um I/O terminou, coloca a tarefa correspondente de volta na fila.

<img width="1392" height="490" alt="image" src="https://github.com/user-attachments/assets/d58fb5a1-5791-4db1-9b3b-3b30e307056f" />


## O que é, de fato, uma API? ## 
API significa Application Programming Interface (Interface de Programação de Aplicações).
É um contrato que define como um componente de software pode ser usado por outro:
quais operações existem, que dados cada uma recebe, o que devolve e quais erros podem
acontecer.
O conceito acadêmico central por trás de uma API é o encapsulamento, ou ocultação de
informação (information hiding, termo de David Parnas, 1972): quem usa a API depende
apenas da interface, nunca da implementação. Isso permite trocar o banco de dados,
reescrever a lógica ou mudar de linguagem sem afetar quem consome, desde que o
contrato seja mantido.
<img width="1381" height="361" alt="image" src="https://github.com/user-attachments/assets/b68ce6c1-85d9-46d5-9ef8-09a97a248cfb" />

*Características de uma boa API*

- Contrato claro e documentado: quem consome sabe exatamente o que enviar e o
que esperar.
- Estabilidade: mudanças que quebram clientes exigem uma nova versão (por exemplo,
/v2/pedidos).
- Erros previsíveis: formatos e códigos de erro consistentes.
- Segurança: autenticação, autorização e limites de uso (rate limiting).

## O que é o padrão REST? ## 
## O que é o protocolo HTTP? ## 
## Quais são os principais Métodos (ou Verbos) HTTP? ## 
## O que são os Códigos de Status HTTP? ## 
## O que é JSON? ## 
## O que é um Framework web? ## 
