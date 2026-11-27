# 🏥 Sistema de Gerenciamento de Senhas de Atendimento Clínico

## 📌 Sobre o projeto

Este projeto foi desenvolvido em linguagem C para simular um sistema de gerenciamento de senhas de atendimento em uma clínica.

O sistema permite cadastrar pacientes, identificar automaticamente a categoria de atendimento, gerar uma senha sequencial e organizar a fila de acordo com as regras de prioridade propostas na atividade.

> **Observação:** as regras de prioridade utilizadas neste projeto são exclusivamente didáticas e foram definidas para a atividade. Elas não representam integralmente a legislação de atendimento prioritário nem uma classificação médica de risco.

---

## 🎯 Objetivo

Desenvolver uma aplicação em linguagem C capaz de:

- Cadastrar pacientes;
- Registrar informações do paciente;
- Classificar automaticamente o atendimento;
- Gerar senhas sequenciais;
- Organizar a fila por prioridade;
- Consultar a próxima senha;
- Chamar pacientes;
- Registrar pacientes como atendidos;
- Exibir um painel com as filas;
- Informar a quantidade de pacientes aguardando em cada categoria.

---

## 🏷️ Categorias de atendimento

O sistema possui três categorias:

| Código | Categoria | Regra |
|---|---|---|
| N | Normal | Pacientes sem condição de prioridade |
| P | Preferencial | Gestantes, lactantes, pessoas com necessidade especial, pessoas com obesidade, mulheres com 60 anos ou mais e homens com 65 anos ou mais |
| U | Urgente | Pacientes com idade superior a 80 anos |

A prioridade utilizada pelo sistema é:

```text
URGENTE
   ↓
PREFERENCIAL
   ↓
NORMAL
```

A numeração é independente para cada categoria.

Exemplo:

```text
N001
N002
P001
P002
U001
U002
```

---

## ⚙️ Funcionalidades

### 1. Cadastro de paciente

O sistema solicita:

- Nome;
- Gênero;
- Idade;
- Gestante;
- Lactante;
- Necessidade especial;
- Condição de obesidade.

Após o cadastro, o sistema identifica a categoria e gera a senha automaticamente.

### 2. Classificação

O paciente é classificado automaticamente de acordo com as regras da atividade.

Pacientes com idade superior a 80 anos recebem prioridade urgente.

Caso não sejam urgentes, o sistema verifica as condições preferenciais.

### 3. Gerenciamento da fila

A fila segue:

```text
Urgente → Preferencial → Normal
```

Dentro de cada categoria é respeitada a ordem de cadastro (FIFO).

### 4. Chamada

O sistema permite chamar a próxima senha disponível.

Após a chamada, o paciente é marcado como atendido e não retorna para a fila.

### 5. Painel

O painel apresenta:

- Próxima senha;
- Categoria;
- Próximas senhas;
- Quantidade de pacientes aguardando por categoria.

### 6. Listagem

Também é possível visualizar todos os pacientes cadastrados e verificar se estão aguardando ou já foram atendidos.

---

## 🧩 Funções implementadas

### `classificarPaciente()`

Identifica a categoria do paciente e gera sua senha.

### `cadastrarPaciente()`

Realiza o cadastro e valida os dados informados.

### `encontrarProximaSenha()`

Procura a próxima senha que deve ser atendida de acordo com a prioridade.

### `consultarProximaSenha()`

Mostra qual será a próxima senha chamada.

### `chamarPaciente()`

Realiza a chamada do próximo paciente e registra o atendimento.

### `mostrarPainel()`

Exibe o painel da clínica e a quantidade de pacientes aguardando.

### `listarPacientes()`

Mostra os pacientes cadastrados e seus respectivos status.

### `menu()`

Apresenta o menu principal e controla as opções escolhidas pelo usuário.

---

## 💻 Como compilar

O programa pode ser compilado utilizando o GCC.

No terminal, dentro da pasta do projeto:

```bash
gcc main.c -o sistema_clinica
```

---

## ▶️ Como executar

### Windows

```bash
sistema_clinica.exe
```

### Linux

```bash
./sistema_clinica
```

---

## 🖥️ Exemplo de utilização

Ao executar o programa, será apresentado:

```text
=====================================
 SISTEMA DE SENHAS - CLINICA
=====================================
1 - Cadastrar paciente
2 - Consultar proxima senha
3 - Chamar paciente
4 - Mostrar painel
5 - Listar pacientes
0 - Sair

Escolha uma opcao:
```

Após cadastrar um paciente:

```text
===== CADASTRO DE PACIENTE =====

Nome: Maria
Genero (M/F): F
Idade: 25
E gestante? (S/N): S
E lactante? (S/N): N
Possui necessidade especial? (S/N): N
Possui condicao de obesidade? (S/N): N

Paciente cadastrado com sucesso!
Categoria: Preferencial
Senha: P001
```

Outro paciente com mais de 80 anos:

```text
Nome: João
Genero (M/F): M
Idade: 85
E lactante? (S/N): N
Possui necessidade especial? (S/N): N
Possui condicao de obesidade? (S/N): N

Paciente cadastrado com sucesso!
Categoria: Urgente
Senha: U001
```

Nesse caso, a próxima senha será:

```text
U001
```

pois a categoria urgente possui prioridade sobre a preferencial.

---

## 📚 Conceitos utilizados

Neste projeto foram utilizados conceitos estudados em linguagem C, como:

- Variáveis;
- Tipos de dados;
- `struct`;
- Vetores;
- Funções;
- Parâmetros;
- Ponteiros;
- `if/else`;
- `switch`;
- `for`;
- `do...while`;
- `strcmp()`;
- `strcpy()`;
- `sprintf()`;
- Validação de entrada;
- Organização de filas.

---

## 👩‍💻 Autora

**Marina Alves**

Aluna de Análise e Desenvolvimento de Sistemas - 2° Semestre
