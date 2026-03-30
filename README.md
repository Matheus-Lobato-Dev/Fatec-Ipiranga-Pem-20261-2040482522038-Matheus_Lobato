#include <stdio.h>
#include <stdbool.h>

// constante para representar espaço vazio
const char vazio = ' ';

// matriz do tabuleiro
char tabuleiro[3][3];

// função para inicializar o tabuleiro
void inicializarTabuleiro() {
    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {
            tabuleiro[i][j] = vazio;
        }
    }
}

// função para mostrar o tabuleiro
void mostrarTabuleiro() {

    printf("\n");

    for(int i = 0; i < 3; i++) {

        printf(" %c | %c | %c ", tabuleiro[i][0], tabuleiro[i][1], tabuleiro[i][2]);

        if(i < 2) {
            printf("\n-+-+-\n");
        }
    }

    printf("\n\n");
}

// função para verificar vitória
bool verificarVitoria(char jogador) {

    // verificar linhas
    for(int i = 0; i < 3; i++) {
        if(tabuleiro[i][0] == jogador &&
           tabuleiro[i][1] == jogador &&
           tabuleiro[i][2] == jogador) {
            return true;
        }
    }

    // verificar colunas
    for(int i = 0; i < 3; i++) {
        if(tabuleiro[0][i] == jogador &&
           tabuleiro[1][i] == jogador &&
           tabuleiro[2][i] == jogador) {
            return true;
        }
    }

    // diagonal principal
    if(tabuleiro[0][0] == jogador &&
       tabuleiro[1][1] == jogador &&
       tabuleiro[2][2] == jogador) {
        return true;
    }

    // diagonal secundária
    if(tabuleiro[0][2] == jogador &&
       tabuleiro[1][1] == jogador &&
       tabuleiro[2][0] == jogador) {
        return true;
    }

    return false;
}

// verificar se ainda existem espaços vazios
bool existeEspaco() {

    for(int i = 0; i < 3; i++) {
        for(int j = 0; j < 3; j++) {

            if(tabuleiro[i][j] == vazio) {
                return true;
            }

        }
    }

    return false;
}

int main() {

    int linha, coluna;

    char jogador_atual = 'X';

    bool vencedor = false;

    inicializarTabuleiro();

    // laço principal do jogo
    while(existeEspaco() && !vencedor) {

        mostrarTabuleiro();

        printf("Jogador %c\n", jogador_atual);
        printf("Digite linha (0-2): ");
        scanf("%d", &linha);

        printf("Digite coluna (0-2): ");
        scanf("%d", &coluna);

        // validação da jogada
        if(tabuleiro[linha][coluna] != vazio) {
            printf("Posicao ocupada! Tente novamente.\n");
            continue;
        }

        // inserir símbolo no tabuleiro
        tabuleiro[linha][coluna] = jogador_atual;

        // verificar vitória
        if(verificarVitoria(jogador_atual)) {
            vencedor = true;
        } else {

            // alternar jogador
            if(jogador_atual == 'X') {
                jogador_atual = 'O';
            } else {
                jogador_atual = 'X';
            }

        }
    }

    // mostrar tabuleiro final
    mostrarTabuleiro();

    // verificar resultado final
    if(vencedor) {
        printf("O jogador %c venceu!\n", jogador_atual);
    } else {
        printf("O jogo terminou em empate.\n");
    }

    return 0;
}
