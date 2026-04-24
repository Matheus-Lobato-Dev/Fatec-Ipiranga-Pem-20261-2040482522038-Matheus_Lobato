#include <stdio.h>
#include <string.h>

#define MAX 100

struct Produto {
    int id;
    char nome[50];
};

struct Produto produtos[MAX];
int total = 0;


void cadastrar() {
    if (total >= MAX) {
        printf("Limite de produtos atingido!\n");
        return;
    }

    printf("Digite o ID do produto: ");
    scanf("%d", &produtos[total].id);

    printf("Digite o nome do produto: ");
    scanf(" %[^\n]", produtos[total].nome);

    total++;

    printf("Produto cadastrado com sucesso!\n");
}


void listar() {
    if (total == 0) {
        printf("Nenhum produto cadastrado.\n");
        return;
    }

    printf("\nLista de Produtos:\n");
    for (int i = 0; i < total; i++) {
        printf("ID: %d | Nome: %s\n", produtos[i].id, produtos[i].nome);
    }
}


void atualizar() {
    int id;
    printf("Digite o ID do produto para atualizar: ");
    scanf("%d", &id);

    for (int i = 0; i < total; i++) {
        if (produtos[i].id == id) {
            printf("Digite o novo nome: ");
            scanf(" %[^\n]", produtos[i].nome);
            printf("Produto atualizado!\n");
            return;
        }
    }

    printf("Produto nao encontrado.\n");
}


void excluir() {
    int id;
    printf("Digite o ID do produto para excluir: ");
    scanf("%d", &id);

    for (int i = 0; i < total; i++) {
        if (produtos[i].id == id) {

            for (int j = i; j < total - 1; j++) {
                produtos[j] = produtos[j + 1];
            }

            total--;
            printf("Produto excluido com sucesso!\n");
            return;
        }
    }

    printf("Produto nao encontrado.\n");
}

int main() {

    int opcao;

    do {
        printf("\n--- CRUD DE PRODUTOS ---\n");
        printf("1 - Cadastrar produto\n");
        printf("2 - Listar produtos\n");
        printf("3 - Atualizar produto\n");
        printf("4 - Excluir produto\n");
        printf("0 - Sair\n");

        printf("Escolha uma opcao: ");
        scanf("%d", &opcao);

        switch(opcao) {
            case 1:
                cadastrar();
                break;
            case 2:
                listar();
                break;
            case 3:
                atualizar();
                break;
            case 4:
                excluir();
                break;
            case 0:
                printf("Encerrando...\n");
                break;
            default:
                printf("Opcao invalida!\n");
        }

    } while(opcao != 0);

    return 0;
}
