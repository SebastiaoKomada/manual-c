## Exercícios sobre Linguagem C - Parte 1

### 1. Estrutura do Programa em C

**Questão 1:** O que acontece se o `return 0;` for omitido da função `main()`?

**Solução:** Em C moderno (padrões C99 e posteriores), omitir `return 0;` de `main()` ainda retorna 0 implicitamente. Porém, é boa prática manter a declaração explícita.

**Questão 2:** Identifique e corrija os erros no código abaixo:
```c
#include <stdio.h>
int main() {
    printf("Bem vindo")
    return 0
}
```

**Solução:**
- Faltou ponto e vírgula após `printf` e `return`.
```c
#include <stdio.h>
int main() {
    printf("Bem vindo");
    return 0;
}
```

### 2. Tipos de Dados e Variáveis

**Questão 3:** Qual é a saída do código abaixo?
```c
int a = 5;
int b = 2;
float resultado = a / b;
printf("%f", resultado);
```

**Solução:** `2.000000`. Como ambos os operandos são inteiros, a divisão ocorre entre inteiros (5/2 = 2), e depois é convertido para float.

**Questão 4:** Corrija o código acima para que a saída seja `2.500000`.

**Solução:**
```c
float resultado = (float)a / b;
```

### 3. Entrada/Saída de Dados

**Questão 5:** Qual é o problema do seguinte código?
```c
char letra;
printf("Digite uma letra: ");
scanf("%c", &letra);
printf("Letra digitada: %c", letra);
```

**Solução:** Pode ocorrer de `letra` capturar um `
` do buffer anterior. Solução: adicionar um espaço antes de `%c`:
```c
scanf(" %c", &letra);
```

### 4. Controle de Fluxo

**Questão 6:** Reescreva usando operador ternário:
```c
if (idade >= 18) printf("Maior de idade");
else printf("Menor de idade");
```

**Solução:**
```c
printf("%s", idade >= 18 ? "Maior de idade" : "Menor de idade");
```

### 5. Laços de Repetição

**Questão 7:** Escreva um programa que imprime os números de 10 até 1 usando um `while`.

**Solução:**
```c
int i = 10;
while (i >= 1) {
    printf("%d\n", i);
    i--;
}
```

### 6. Funções

**Questão 8:** Implemente uma função que receba dois inteiros e retorne o maior deles.

**Solução:**
```c
int maior(int a, int b) {
    return (a > b) ? a : b;
}
```

### 7. Arrays

**Questão 9:** Escreva um programa que leia 5 números inteiros para um array e calcule a média deles.

**Solução:**
```c
int numeros[5];
int soma = 0;
for (int i = 0; i < 5; i++) {
    printf("Digite o %dº numero: ", i+1);
    scanf("%d", &numeros[i]);
    soma += numeros[i];
}
printf("Media: %.2f\n", soma / 5.0);
```

### 8. Ponteiros

**Questão 10:** Explique a diferença entre `int a = 10;` e `int *p = &a;`.

**Solução:**
- `a` é uma variável que armazena o valor 10.
- `p` é um ponteiro que armazena o endereço de `a`, ou seja, aponta para a memória onde `a` está armazenado.

### 9. Alocação Dinâmica

**Questão 11:** Complete:

Alocação de um array de 10 inteiros usando `malloc`:
```c
int *vetor = (int*) _________;
```

**Solução:**
```c
int *vetor = (int*) malloc(10 * sizeof(int));
```

### 10. Arquivos

**Questão 12:** Qual a diferença entre abrir um arquivo com `"w"` e `"a"`?

**Solução:**
- `"w"`: abre o arquivo para escrita, apagando o conteúdo anterior se existir.
- `"a"`: abre para escrita *no final* do arquivo, preservando o conteúdo anterior.

**Questão 13:** Como se escreve uma linha com nome e idade em um arquivo?

**Solução:**
```c
FILE *f = fopen("dados.txt", "w");
if (f != NULL) {
    fprintf(f, "Nome: %s, Idade: %d\n", "Joana", 22);
    fclose(f);
}
```
