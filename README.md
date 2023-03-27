# Tabuleiro Othello

## _Campeonato de Inteligências Artificiais - UFRJ_

O código a seguir foi elaborado por [victorlcampos](https://github.com/victorlcampos/TabuleiroOthello) e [rodrigomorgado](https://github.com/rodrigomorgado), originalmente em Python 2.x. Eu o modifiquei para Python 3.x e adicionei novas funções, além de uma nova aparência.

## Descrição

Todas as informações a seguir estão em conformidade com as [Regras Oficiais do Jogo](https://www.worldothello.org/about/about-othello/othello-rules/portugues-brasil).

O Othello é um jogo de dois jogadores, em que cada um possui uma cor (normalmente preto e branco). O objetivo do jogo é terminar com mais peças da sua cor no tabuleiro do que as peças da cor de seu oponente.

O jogo acontece em um tabuleiro 8x8 com uma área 2x2 no meio preenchida com peças de cores alternadas. Os jogadores se revezam colocando as peças de suas respectivas cores. Se a colocação de uma peça cria uma linha de peças consecutivas do adversário delimitada por peças da sua cor, no início e no final da linha, todas as peças na linha “viram” para se tornar da sua cor. Observe que essa "linha" pode ser feita na vertical, horizontal ou diagonal.

Para que um movimento seja válido, ele deve criar uma das linhas acima mencionadas. Se não houver movimentos válidos, você deve passar sua vez para o seu oponente. O jogo termina quando ambos os jogadores não podem se mover, e o jogador com mais peças de sua cor no tabuleiro vence.

## Representação do tabuleiro

O tabuleiro é representado como uma matriz, que inclui cada placa do tabuleiro, bem como a borda externa. Um tabuleiro inicial contém quatro peças no centro:

```
? ? ? ? ? ? ? ? ? ?
? . . . . . . . . ?
? . . . . . . . . ?
? . . . . . . . . ?
? . . . ● ○ . . . ?
? . . . ○ ● . . . ?
? . . . . . . . . ?
? . . . . . . . . ?
? . . . . . . . . ?
? ? ? ? ? ? ? ? ? ?
```

A borda externa é marcada pelo símbolo "**?**", e as placas vazias são "**.**", o preto é "○" e o branco é "●". As peças pretas e brancas representam os dois jogadores.

```
EMPTY, BLACK, WHITE, OUTER = '.', '○', '●', '?'
```

**OBS.: Dependendo do contraste do shell, o símbolo "●" pode ser confundido com o preto. Uma maneira de evitar confusões, é lembrar que a bolinha vazada é sempre a preta e a preenchida é sempre a branca.**

## Instruções

Para jogar, execute o programa em um interpretador Python 3.x. Serão apresentados os agentes disponíveis para jogar. Escolha primeiro o jogador para ser a peça preta e, em seguida, o jogador para a peça branca.

Ao iniciar o jogo, um tabuleiro 8x8 será exibido na tela, com um quadrado de 2x2 de peças alternadas no centro. Um placar na parte superior do tabuleiro indicará a pontuação de cada jogador e de quem é a vez de jogar. Após cada jogada, o tempo que levou para a jogada será exibido na parte inferior do tabuleiro. Vale lembrar que o tempo máximo permitido para uma jogada é de `10 segundos`.

Por padrão o jogo possui 3 agentes:

- **coner_player** - Uma estratégia que prioriza os cantos do tabuleiro.
- **human_player** - Jogador humano.
- **random_player** - Uma estratégia que sempre escolhe um movimento aleatório válido.

## Criação do Agente

Caso queira criar um novo agente, basta criar um arquivo na pasta **"controllers/models/players/"** com nome do arquivo possuindo o sufixo `_player`, ou seja, `nome_do_agente_player.py`. O conteúdo do arquivo deve ser obrigatóriamente um classe que tenha a função `play`, a qual receberá o tabuleiro atual como parâmetro.

```python
class ExemploPlayer:
    def __init__(self, color):
        self.color = color
    def play(self, board):
        return minimax_funcao()
```

## Objetivo

O objetivo deste desafio é criar um agente que possa escolher os melhores movimentos durante o jogo. Para isso, você deve implementar obrigatoriamente o algoritmo **Minimax** na função `play`, que será responsável por iniciar a lógica da sua Inteligência Artifial e retornar o melhor movimento a ser feito.

A classe `Board` (tabuleiro) possui algumas funções úteis que irão ajudá-lo na elaboração das heurísticas:

- **play(move, color)** - Retorna o tabuleiro atualizado com o movimento e peça passada.
- **get_square_color(l, c)** - Retorna o símbolo na coordenada passada, ou seja, '.', '○', '●', '?'.
- **get_clone()** - Retorna uma cópia do tabuleiro.
- **valid_moves(color)** - Retorna uma lista de todos os movimentos válidos para o jogador.
- **score()** - Retorna uma lista com a quantidade de peças de cada cor: [branco, preto].
- **\_opponent(color)** - Retorna o oponente da peça passada.
