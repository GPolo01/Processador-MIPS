# Processador MIPS - Logisim
> Trabalho da Disciplina de Projetos Digitais e Microprocessadores

## 🎯 Objetivo
[cite_start]Este projeto consiste no desenvolvimento e simulação de um microprocessador de 32 bits, inspirado na arquitetura MIPS, utilizando o software **Logisim 3.8**[cite: 5]. O processador foi projetado para executar um conjunto de 15 instruções fundamentais, incluindo operações aritméticas, lógicas e de controle de fluxo.

## ⚙️ Arquitetura e Formato de Instrução

[cite_start]O processador opera com instruções de **32 bits** divididas no seguinte formato unificado[cite: 18]:

| Campo | Opcode | a (Reg 1) | b (Reg 2) | c (Reg Dest) | Imed |
| :--- | :---: | :---: | :---: | :---: | :---: |
| **Bits** | 4 | 4 | 4 | 4 | 16 |

### Sinais de Controle
[cite_start]Para gerenciar o fluxo de dados, foram implementados 7 sinais de controle[cite: 20]:

| Sinal | W (Write) | Halt | Imed | Jump | Branch | Print | Funct |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **Bits** | 1 | 1 | 1 | 1 | 1 | 1 | 3 |

* [cite_start]**Funct:** Utilizado pela ULA para selecionar a operação específica (ex: Soma, Subtração, XOR)[cite: 21].
* [cite_start]**Halt:** Para a execução do processador impedindo a leitura de novas instruções[cite: 14].
* [cite_start]**Print (Show):** Controla o display para exibir o valor de um registrador específico[cite: 16].

## 🛠️ Componentes Desenvolvidos

[cite_start]Além dos componentes nativos do Logisim (como ROM, Multiplicador e MUX), foram criados módulos personalizados para este processador[cite: 7, 8]:

* **Unidade de Controle:** Decodifica o Opcode e gera os sinais de controle.
* **ULA (Unidade Lógica e Aritmética):** Suporta soma, subtração, complemento e operações lógicas.
* **Banco de Registradores:** Gerencia leitura e escrita com sinal de clock e reset.
* **Detector de Zero e Extensão de Sinal:** Auxiliares para operações de Branch e imediatos.
* [cite_start]**PC (Program Counter) com Jump/Branch:** Lógica de desvio condicional e incondicional[cite: 12, 13].

## 💻 Instruções Implementadas

[cite_start]Foram implementadas **15 instruções** na Memória de Controle.

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

## 🚀 Exemplo de Execução
O projeto inclui um algoritmo de **Progressão Aritmética (Soma de PA)** escrito em Assembly e convertido para binário para validação do processador. [cite_start]O algoritmo realiza o loop de soma `(a + i*d)` e exibe o resultado no display ao final [cite: 24-52].

## 📦 Como Executar
1. [cite_start]Instale o [Logisim 3.8](http://www.cburch.com/logisim/)[cite: 5].
2. Clone este repositório.
3. Abra o arquivo principal `.circ` no Logisim.
4. Carregue a imagem da memória (se necessário) e ative o Clock.
5. [cite_start]Utilize o botão **Reiniciar** para garantir que o estado inicial dos registradores esteja correto.

---
**Autor:** Gabriel Henrique Polo
