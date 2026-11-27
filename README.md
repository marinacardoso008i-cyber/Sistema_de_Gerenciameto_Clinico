# Sistema de Gerenciamento de Senhas de Atendimento Clínico

## Sobre o projeto

Este projeto foi desenvolvido em linguagem C para simular um sistema de gerenciamento de senhas de atendimento em uma clínica.

O sistema permite cadastrar pacientes, identificar automaticamente a categoria de atendimento, gerar uma senha sequencial e organizar a fila de acordo com as regras definidas para a atividade.

As regras de prioridade deste sistema são didáticas e foram definidas especificamente para o projeto.

## Objetivo

O objetivo é desenvolver uma aplicação funcional em C utilizando funções, estruturas de decisão, repetição, estruturas de armazenamento, validação de dados e um menu interativo.

## Funcionalidades

- Cadastro de pacientes;
- Registro dos dados do paciente;
- Classificação automática;
- Geração de senha sequencial;
- Organização da fila;
- Consulta da próxima senha;
- Chamada de pacientes;
- Registro de atendimento;
- Painel de chamadas;
- Quantidade de pacientes aguardando por categoria;
- Listagem dos pacientes cadastrados;
- Validação de informações digitadas.

## Categorias

### Urgente

A categoria urgente é utilizada para pacientes com idade superior a 80 anos.

As senhas possuem o formato:

```text
U001
U002
U003
```

### Preferencial

A categoria preferencial é utilizada para pacientes que se enquadram em uma das condições abaixo:

- Idade igual ou superior a 50 anos;
- Gestante;
- Lactante;
- Pessoa com espectro autista;
- Pessoa com mobilidade reduzida;
- Pessoa acompanhada de criança de colo;
- Pessoa com obesidade;
- Pessoa com deficiência;
- Doador de sangue;
- Outra condição de prioridade informada no cadastro.

As senhas possuem o formato:

```text
P001
P002
P003
```

### Normal

A categoria normal é utilizada quando o paciente não possui nenhuma das condições de prioridade cadastradas.

As senhas possuem o formato:

```text
N001
N002
N003
```

## Ordem de atendimento

A fila segue a seguinte prioridade:

```text
Urgente
    ↓
Preferencial
    ↓
Normal
```

Dentro de cada categoria, o sistema respeita a ordem de emissão das senhas, seguindo o conceito FIFO (First In, First Out).

Exemplo:

```text
P001
P002
P003
```

A ordem de chamada será:

```text
P001 → P002 → P003
```

Uma senha que já foi chamada não retorna para a fila.

## Menu do sistema

O sistema possui as seguintes opções:

```text
1 - Cadastrar paciente
2 - Consultar proxima senha
3 - Chamar paciente
4 - Mostrar painel
5 - Listar pacientes
0 - Sair
```

## Funções implementadas

### `classificarPaciente()`

Verifica as condições do paciente, define sua categoria e gera a senha.

### `cadastrarPaciente()`

Recebe os dados do paciente e realiza as validações necessárias.

### `encontrarProximaSenha()`

Procura a próxima senha de acordo com a prioridade e a ordem de cadastro.

### `consultarProximaSenha()`

Apresenta a próxima senha que será chamada.

### `chamarPaciente()`

Realiza a chamada do paciente e registra que ele foi atendido.

### `mostrarPainel()`

Exibe as informações da fila, a próxima senha e a quantidade de pacientes aguardando em cada categoria.

### `listarPacientes()`

Apresenta os pacientes cadastrados, suas senhas, categorias e situação do atendimento.

### `menu()`

Controla o menu principal e direciona cada opção para sua respectiva função.

## Estrutura de armazenamento

O sistema utiliza uma `struct` chamada `Paciente` para armazenar as informações de cada pessoa.

Também é utilizado um vetor com capacidade para até 100 pacientes:

```c
Paciente pacientes[MAX_PACIENTES];
```

## Compilação

O programa pode ser compilado utilizando o GCC.

No terminal:

```bash
gcc main.c -o sistema_clinica
```

## Execução

No Windows:

```bash
sistema_clinica.exe
```

No Linux:

```bash
./sistema_clinica
```

O programa também pode ser executado em ambientes online que possuam suporte à linguagem C, como o GDB Online.

## Exemplo de geração de senha

Ao cadastrar uma pessoa de 55 anos:

```text
Paciente cadastrado com sucesso!
Categoria: Preferencial
Senha: P001
```

Ao cadastrar uma pessoa de 85 anos:

```text
Paciente cadastrado com sucesso!
Categoria: Urgente
Senha: U001
```

Ao cadastrar uma pessoa de 30 anos sem nenhuma condição de prioridade:

```text
Paciente cadastrado com sucesso!
Categoria: Normal
Senha: N001
```

## Exemplo de chamada

Considerando que as senhas estejam aguardando:

```text
N001 - Normal
P001 - Preferencial
U001 - Urgente
```

A ordem de chamada será:

```text
U001
P001
N001
```

Isso ocorre porque a categoria urgente possui prioridade sobre a preferencial, e a preferencial possui prioridade sobre a normal.

## Tecnologias utilizadas

- Linguagem C;
- GCC;
- GDB Online;
- GitHub.

## Autora

Marina Alves

Aluna de Análise e Desenvolvimento de Sistemas - 2° Semestre - UDF
