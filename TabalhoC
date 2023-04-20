#include <stdio.h>
#include <stdlib.h>
#include <string.h>

#define MAX_ALUNOS 50

typedef struct {
  int matricula;
  float notas[3];
  int faltas;
} Aluno;

int numAlunos = 0;
Aluno alunos[MAX_ALUNOS];

void imprimir_menu() {
  printf("MENU: \n");
  printf("1 - Cadastrar aluno \n");
  printf("2 - Alterar dados de um aluno \n");
  printf("3 - Listar alunos cadastrados \n");
  printf("4 - Listar alunos aprovados \n");
  printf("5 - Listar alunos reprovados por média \n");
  printf("6 - Listar alunos reprovados por faltas \n");
  printf("0 - Sair \n");
}

int buscarAluno(int matricula) {
  for (int i = 0; i < numAlunos; i++) {
    if (alunos[i].matricula == matricula) {
      return i;
    }
  }
  return -1; // aluno não encontrado
}

void cadastrarAluno() {
  if (numAlunos >= MAX_ALUNOS) {
    printf("Erro: número máximo de alunos atingido. \n");
    return;
  }

  Aluno novoAluno;
  printf("Digite a matrícula do aluno: ");
  scanf("%d", &novoAluno.matricula);

  if (buscarAluno(novoAluno.matricula) != -1) {
    printf("Erro: matrícula já cadastrada. \n");
    return;
  }

  printf("Digite as três notas do aluno \n");
  printf("Nota 1: ");
  scanf("%f", &novoAluno.notas[0]);
  printf("Nota 2: ");
  scanf("%f", &novoAluno.notas[1]);
  printf("Nota 3: ");
  scanf("%f", &novoAluno.notas[2]);

  printf("Digite a quantidade de faltas do aluno: ");
  scanf("%d", &novoAluno.faltas);

  alunos[numAlunos] = novoAluno;
  numAlunos++;

  printf("Aluno cadastrado com sucesso. \n");
}

void alterarAluno() {
  if (numAlunos == 0) {
    printf("Erro: nenhum aluno cadastrado. \n");
    return;
  }

  int matricula;
  printf("Digite a matrícula do aluno a ser alterado: ");
  scanf("%d", &matricula);

  int posicao = buscarAluno(matricula);
  if (posicao == -1) {
    printf("Erro: aluno não encontrado. \n");
    return;
  }

  printf("Digite as três novas notas do aluno \n");
  printf("Nota 1: ");
  scanf("%f", &alunos[posicao].notas[0]);
  printf("Nota 2: ");
  scanf("%f", &alunos[posicao].notas[1]);
  printf("Nota 3: ");
  scanf("%f", &alunos[posicao].notas[2]);

  printf("Digite a nova quantidade de faltas do aluno: ");
  scanf("%d", &alunos[posicao].faltas);

  printf("Dados do aluno alterados com sucesso. \n");
}

void listarAlunos() {
  if (numAlunos == 0) {
    printf("Nenhum aluno cadastrado. \n");
    return;
  }

  printf("Alunos cadastrados: \n");
  printf("Matrícula  |  Nota 1  |  Nota 2  |  Nota 3  |  Faltas \n");
  for (int i = 0; i < numAlunos; i++) {
    printf("%-11d|  %-8.2f|  %-8.2f|  %-8.2f|  %-6d \n", alunos[i].matricula,
           alunos[i].notas[0], alunos[i].notas[1], alunos[i].notas[2],
           alunos[i].faltas);
  }
}

void listarAlunosAprovados() {
  if (numAlunos == 0) {
    printf("Nenhum aluno cadastrado. \n");
    return;
  }

  printf("Alunos aprovados: \n");
  for (int i = 0; i < numAlunos; i++) {
    float media =
        (alunos[i].notas[0] + alunos[i].notas[1] + alunos[i].notas[2]) / 3;
    if (media >= 7 && alunos[i].faltas <= 15) {
      printf("Matrícula: %d, Nota média: %.2f, Faltas: %d \n",
             alunos[i].matricula, media, alunos[i].faltas);
    }
  }
}

void listarAlunosReprovadosMedia() {
  if (numAlunos == 0) {
    printf("Nenhum aluno cadastrado. \n");
    return;
  }
  printf("Alunos reprovados por média: \n");
  for (int i = 0; i < numAlunos; i++) {
    float media =
        (alunos[i].notas[0] + alunos[i].notas[1] + alunos[i].notas[2]) / 3;
    if (media < 6) {
      printf("Matrícula: %d, Nota média: %.2f \n", alunos[i].matricula, media);
    }
  }
}

void listarAlunosReprovadosFalta() {
  if (numAlunos == 0) {
    printf("Nenhum aluno cadastrado. \n");
    return;
  }
  printf("Alunos reprovados por faltas: \n");
  for (int i = 0; i < numAlunos; i++) {
    if (alunos[i].faltas > 27) {
      printf("Matrícula: %d, Faltas: %d \n", alunos[i].matricula,
             alunos[i].faltas);
    }
  }
}

int main() {
  int opcao;

  do {
    imprimir_menu();
    printf("Digite uma opção: ");
    scanf("%d", &opcao);

    switch (opcao) {
    case 1:
      cadastrarAluno();
      break;
    case 2:
      alterarAluno();
      break;
    case 3:
      listarAlunos();
      break;
    case 4:
      listarAlunosAprovados();
      break;
    case 5:
      listarAlunosReprovadosMedia();
      break;
    case 6:
      listarAlunosReprovadosFalta();
      break;
    case 0:
      printf("Saindo do programa... \n");
      break;
    default:
      printf("Opção inválida. \n");
      break;
    }
  } while (opcao != 0);

  return 0;
}
