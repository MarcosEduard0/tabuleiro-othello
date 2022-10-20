# Tabuleiro Othello

## _Campeonato UFRJ_

Código elaborado por [victorlcampos](https://github.com/victorlcampos/TabuleiroOthello) e [rodrigomorgado](https://github.com/rodrigomorgado). O código foi feito em Python 2.x e modificado por mim, para Python 3.x. Além disso, foram adicionadas novas funções e um novo visual.

## Descrição

Othello é um jogo de dois jogadores com cada jogador tendo uma cor (normalmente preto e branco), e o objetivo do jogo é terminar com mais peças da sua cor no tabuleiro do que as peças da cor de seus oponentes.

O jogo acontece em uma tabuleiro de 8x8 com uma área 2x2 no meio preenchido com peças de cores alternadas. Os jogadores se revezam colocando as peças de suas respectivas cores. Se a colocação da peça cria uma linha contínua de peças com sua cor no início e no final da linha, todos os peças na linha “viram” para se tornar sua cor.

Para que um movimento seja válido, ele deve criar uma das linhas acima mencionadas. Se não houver movimentos válidos, você deve passar sua vez para o seu oponente. O jogo termina quando ambos os jogadores não podem se mover, e o jogador com mais peças de sua cor no tabuleiro vence.

## Instruções

Instruções para jogar Othello, execute em qualquer interpretador Python 3.x. Aparecerá os agentes disponiveis para jogar. Escolha primeiro jogador da peça branca e em seguida o jogador da peça preta.

Você será presenteado com uma tabuleiro de 8x8 na tela com um quadrado de 2x2 de peças alternados no meio, conforme descrito acima. Haverá um placar na parte superior do tabuleiro para acompanhar sua pontuação (quantas peças de cada cor) e indicar de quem é a vez. Além disso, ao fim de cada jogada será apresentado na parte inferior do tabuleiro um cronometro indicando quanto tempo levou a jogada.

Por padrão o jogo possui 3 agentes:

- **coner_player** - prioriza os cantos do tabuleiro.
- **human_player** - jogador humano.
- **random_player** - escolhas aleatórias de movimentos.

## Criação de Agentes

A criação de novos agentes devem ser feitas na pasta **"controllers/models/players/"** e o nome do arquivo deve possuir o prefixo `_player`, ou seja, `exemplo_player.py`. O conteúdo do arquivo deve obrigatóriamente um classe, contendo a função `play` que receberá o tabuleiro atual.

```python
class ExemploPlayer:
    def __init__(self, color):
        self.color = color
    def play(self, board):
        return minimax_funcao()
```

## Objetivo

Você deve criar um agente capaz de descidir os melhores movimentos a serem realizados para ganhar do seu oponente. A função `play` é responsavel por iniciar sua I.A e retornar o melhor movimento a ser feito. Para isso, em cada turno será receberá o tabuleiro (board) atual. Você também deverá implementar o algoritmo **Minimax** que será as resposável por decidir qual melhor movimento a ser realizado.

A classe board possui funções que retornam informações do tabuleiro:

- **play(movimento, peça)** - retorna o tabuleiro com o movimento e paça passada.
- **get_square_color(linha, coluna)** - retorna qual a cor da peça na coordenada passada.
- **get_clone()** - retorna uma copia do tabuleiro.
- **valid_moves(peça)** - retorna os movimentos possiveis da peça.
- **score()** - retorna uma tupla com a quantidade de peças de cada cor [branco, preta].
- **\_opponent(peça)** - retorna o oponente da peça passada.

## License

**Free Software, Hell Yeah!**
