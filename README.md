# Sistema de Jogo de Xadrez

Jogo de xadrez completo em Java, jogável via terminal, implementando as regras oficiais do jogo — incluindo movimentos especiais como roque, en passant e promoção de peão, além de detecção de xeque e xeque-mate.

## 📋 Sobre o projeto

O projeto é dividido em duas camadas bem definidas: um **framework genérico de jogos de tabuleiro** (`boardgame`), reutilizável para qualquer jogo baseado em grade (tabuleiro, peças, posições), e a **implementação específica das regras de xadrez** (`chess`), construída sobre esse framework. Essa separação é o principal destaque arquitetural do projeto.

## ✨ Funcionalidades

- Tabuleiro 8x8 com posicionamento inicial padrão de todas as peças.
- Movimentação de todas as 6 peças do xadrez (**Peão, Torre, Cavalo, Bispo, Rainha, Rei**), cada uma com sua lógica de movimento própria.
- **Movimentos especiais completos:**
  - **Roque** (curto e longo).
  - **En passant**.
  - **Promoção de peão**, com escolha da peça (Bispo, Cavalo, Torre ou Rainha).
- **Detecção de xeque e xeque-mate**, impedindo inclusive que o jogador faça uma jogada que o coloque em xeque.
- Interface via terminal com **cores ANSI**, destacando peças de cada cor e as casas para onde uma peça pode se mover.
- Histórico de peças capturadas, exibido separadamente por cor.

## 🛠️ Tecnologias utilizadas

- **Java**
- Programação Orientada a Objetos (herança, polimorfismo, abstração)
- Tratamento de exceções customizadas (`BoardException`, `ChessException`)

## 🏗️ Arquitetura

```
sistema-jogo-de-xadrez/
└── src/
    ├── boardgame/                    # Framework genérico de jogo de tabuleiro
    │   ├── Board.java                 # Tabuleiro genérico (linhas, colunas, peças)
    │   ├── Piece.java                  # Classe abstrata de peça genérica
    │   ├── Position.java                # Posição (linha, coluna) no tabuleiro
    │   └── exceptions/BoardException.java
    ├── chess/                         # Regras específicas do xadrez
    │   ├── ChessMatch.java              # Estado da partida e regras do jogo
    │   ├── ChessPiece.java               # Peça de xadrez (especialização de Piece)
    │   ├── ChessPosition.java             # Posição em notação de xadrez (ex: "e4")
    │   ├── Color.java                      # Cor da peça (branco/preto)
    │   ├── exceptions/ChessException.java
    │   └── pieces/                          # Implementação de cada peça
    │       ├── King.java, Queen.java, Rook.java
    │       ├── Bishop.java, Knight.java, Pawn.java
    └── application/
        ├── Main.java                  # Loop principal do jogo
        └── UI.java                     # Interface via terminal (impressão do tabuleiro, cores, leitura de jogadas)
```

A classe `ChessPiece` estende `Piece` (do framework genérico), e cada peça específica (`King`, `Queen`, etc.) estende `ChessPiece`, implementando seu próprio método `possibleMoves()` — um exemplo direto de **polimorfismo** aplicado a um problema real.

## ▶️ Como executar

### Pré-requisitos
- JDK instalado

### Passos

1. Clone o repositório:
   ```bash
   git clone https://github.com/rui-fernando/sistema-jogo-de-xadrez.git
   cd sistema-jogo-de-xadrez
   ```
2. Compile o projeto:
   ```bash
   javac -d bin src/boardgame/*.java src/boardgame/exceptions/*.java src/chess/*.java src/chess/exceptions/*.java src/chess/pieces/*.java src/application/*.java
   ```
3. Execute:
   ```bash
   java -cp bin application.Main
   ```
4. Digite a posição de origem e destino de cada jogada (ex: `e2` e `e4`) para mover as peças. O terminal exibe o tabuleiro colorido a cada jogada, com destaque para os movimentos possíveis da peça selecionada.

## 🎓 Créditos

Este projeto foi desenvolvido como parte de um curso na Udemy sobre lógica de programação e orientação a objetos em Java, utilizando a implementação de um jogo de xadrez como estudo de caso para os conceitos ensinados.

## 👤 Autor

Desenvolvido por [Rui Fernando](https://github.com/rui-fernando), estudante de Ciência da Computação na Universidade Estadual da Paraíba (UEPB).
