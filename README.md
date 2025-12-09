# Processador MIPS - Logisim
> Trabalho da Disciplina de Projetos Digitais e Microprocessadores

## Objetivo
Este projeto consiste no desenvolvimento e simulação de um microprocessador de 32 bits, inspirado na arquitetura MIPS, utilizando o software **Logisim 3.8**. O processador foi projetado para executar um conjunto de 15 instruções fundamentais, incluindo operações aritméticas, lógicas e de controle de fluxo.

## Arquitetura e Formato de Instrução

O processador opera com instruções de **32 bits** divididas no seguinte formato unificado:

| Campo | Opcode | a (Reg 1) | b (Reg 2) | c (Reg Dest) | Imed |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Bits** | 4 | 4 | 4 | 4 | 16 |

### Sinais de Controle
Para gerenciar o fluxo de dados, foram implementados 7 sinais de controle:

| Sinal | W (Write) | Halt | Imed | Jump | Branch | Print | Funct |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Bits** | 1 | 1 | 1 | 1 | 1 | 1 | 3 |

* **Funct:** Utilizado pela ULA para selecionar a operação específica (ex: Soma, Subtração, XOR).
* **Halt:** Para a execução do processador impedindo a leitura de novas instruções.
* **Print (Show):** Controla o display para exibir o valor de um registrador específico.

## Componentes Desenvolvidos

Além dos componentes nativos do Logisim (como ROM, Multiplicador e MUX), foram criados módulos personalizados para este processador:

* **Unidade de Controle:** Decodifica o Opcode e gera os sinais de controle.
* **ULA (Unidade Lógica e Aritmética):** Suporta soma, subtração, complemento e operações lógicas.
* **Banco de Registradores:** Gerencia leitura e escrita com sinal de clock e reset.
* **Detector de Zero e Extensão de Sinal:** Auxiliares para operações de Branch e imediatos.
* **PC (Program Counter) com Jump/Branch:** Lógica de desvio condicional e incondicional.

## Instruções Implementadas

Foram implementadas **15 instruções** na Memória de Controle.

### Aritméticas (5 instruções)
* `add`, `sub`, `mult` (operações entre registradores)
* `addi`, `subi` (operações com imediato)

### Lógicas e Shift (4 instruções)
* `and`, `or`, `xor` (Bitwise)
* `sll` (Shift Left Logical)

### Controle de Fluxo e Sistema (6 instruções)
* `jump` (Desvio incondicional)
* `branch` (Desvio condicional se igual)
* `li` (Load Immediate)
* `show` (Exibe valor no display - Instrução personalizada)
* `nop` (No Operation)
* `halt` (Para o processador)

## Exemplo de Execução
O projeto inclui um algoritmo de **Progressão Aritmética (Soma de PA)** escrito em Assembly e convertido para binário para validação do processador. O algoritmo realiza o loop de soma `(a + i*d)` e exibe o resultado no display ao final.

## Como Executar
1. Instale o [Logisim 3.8](http://www.cburch.com/logisim/).
2. Clone este repositório.
3. Abra o arquivo principal `.circ` no Logisim.
4. Carregue a imagem da memória (se necessário) e ative o Clock.
5. Utilize o botão **Reiniciar** para garantir que o estado inicial dos registradores esteja correto.

---
**Autor:** Gabriel Henrique Polo
