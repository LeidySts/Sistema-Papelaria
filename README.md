# Sistema-Papelaria
Criando um sistema de papelaria on line.
#include <stdio.h>
#include <string.h>

char nome[120][50]; /*declaramos uma MATRIZ DE STRING , onde 120 é a quantidade de nomes que podemos inserir no sistema e 50 é a quantidade máxima de letras que o nome deve ter*/
int cpf[120];
int opcao; /*declaramos as matrizes e vetores como variáveis globais para que sejam acessíveis por todas as funções que a gente venha a criar no programa*/
char sexo[120][11];
char telefone[120][17];
char rg[120][17];
int idade[120];

void cadastro();
void pesquisa(); /*criamos o protótipo da função pesquisa*/


int main() {

cadastro(); /*estamos chamando a função cadastro*/
pesquisa();

return 0;
} // Fim da função principal

void cadastro() {
static int dados; /*A variável dados é do tipo static (estática) porque ela precisa receber e manter os seus valores durante a execução do programa*/
do {
   printf("\n Informe o NOME: ");
   fgets(nome[dados],50,stdin);

   printf(" Digite o CPF sem o ponto(.) ou /: ");
   scanf("%d",&cpf[dados]);
   getchar();

   printf(" Informe o SEXO: ");
   fgets(sexo[dados],11,stdin);

   printf(" Informe o TELEFONE: ");
   fgets(telefone[dados],17,stdin);


   printf(" Informe o RG: ");
   fgets(rg[dados],17,stdin);

   printf(" Informe a IDADE: ");
   scanf("%d", &idade[dados]);
   getchar();

   printf("\n Digite 1 para continuar ou outro valor pra sair: ");
   scanf("%d",&opcao);
   getchar(); /*para limpar o buffer. Sem essa função o programa ia ignorar a próxima leitura de dados que é o nome porque a função fgets() lê o  "ENTER" que a gente deu após digitar o CPF e passa para próxima instrução que neste caso é o E-mail do usuário*/
 dados=dados+1; /*com esse comando de incremento, quando dados igual a 1 ele vai guardar nome,e-mail e CPF de alguém. Se o usuário continuar, dados vai ser igual a 2 e a variável dados vai guardar nome,e-mail e CPF de outra pessoa e assim vai indo, até o usuário sair */
  }while(opcao==1); /* se opcao==1, continue executando*/


}// Fim da função cadastro


void pesquisa() {

int cpfPesquisa;
int i;

do {

   printf("\n\t ------Menu Pesquisar ------");
   printf("\n\n Digite 1 para pesquisar: ");
   scanf("%d",&opcao);

   switch(opcao){

        case 1:
        printf("\n Informe o cpf : ");
        scanf("%d",&cpfPesquisa);

         for(i=0;i<120;i++) {
              if(cpf[i]==cpfPesquisa){
                  printf("\n Nome: %s",nome[i]);
                  printf(" Cpf: %d \n",cpf[i]);
                  printf(" Sexo:%s \n",sexo[i]);
                  printf(" Telefone:%s \n",telefone[i]);
                  printf(" Rg:%s \n",rg[i]);
                  printf(" Idade:%d \n",idade[i]);
   }//Fim do comando if
}//Fim do comando for
        break;
       
        default: /*Se o Usuário não digitar as opções 1 ou 2, a mensagem de erro vai ser mostrada*/
        printf("\n Error, tente novamente! \n");
        break;

    }//Fim do switch
    printf("\n DIGITE 1 para continuar buscando um usuário ou outro numero para finalizar \n");
    scanf("%d",&opcao);

  }while(opcao==1 );//Fim do comando do-while

}//Fim da função void pesquisa()

