# Clinic-Project

Este projeto é um sistema simples de clínica médica em Java que usa SQLite para gerenciar médicos, pacientes e agendamentos.

## 1. Pré-requisitos e como rodar

### Pré-requisitos
- Java JDK instalado (versão 8 ou superior)
- Arquivo `clinica.db` presente na pasta do projeto
- Biblioteca JDBC do SQLite: `sqlite-jdbc-3.36.0.3.jar`

### Como rodar
No Windows, a partir da pasta raiz `clinicaMedica`:

```bash
javac -cp .;sqlite-jdbc-3.36.0.3.jar Main.java
java -cp .;sqlite-jdbc-3.36.0.3.jar Main
```

Se você usar uma IDE, adicione `sqlite-jdbc-3.36.0.3.jar` ao classpath e execute a classe `Main`.

## 2. Organização do projeto

### Pastas e arquivos
- `controladores/`
  - `Agenda.java`
  - `Clientes.java`
  - `Staff.java`
  - Contém a lógica do sistema e a coordenação entre interface e banco de dados.

- `output/`
  - `MenuPrincipal.java`
  - `MenuMedico.java`
  - `MenuCliente.java`
  - `MenuAgendamento.java`
  - Contém os menus de console e a entrada do usuário.

- `Sql/`
  - `SqlAgendamento.java`
  - `SqlCliente.java`
  - `SqlMedico.java`
  - Contém o acesso direto ao banco de dados SQLite.

- Arquivos na raiz
  - `Main.java` — ponto de entrada do programa
  - `clinica.db` — banco de dados SQLite
  - `sqlite-jdbc-3.36.0.3.jar` — driver JDBC do SQLite

### Padrão de organização
O projeto usa um estilo parecido com MVC:
- `output/` como View (interface do usuário)
- `controladores/` como Controller (regras de negócio)
- `Sql/` como Model (acesso aos dados)

Não é um MVC estrito, mas há separação clara entre interface, lógica e banco de dados.

## 3. Funções implementadas

### O que o sistema faz
- Cadastrar, alterar, remover e buscar médicos
- Cadastrar, alterar, remover e buscar pacientes
- Agendar consultas
- Alterar agendamentos
- Cancelar consultas
- Marcar consulta como realizada
- Buscar consultas por médico ou paciente
- Gerar relatório básico de consulta realizada

### Classes principais
- `Main.java`: inicia o menu principal
- `MenuPrincipal.java`: exibe menu inicial e navega entre opções
- `MenuMedico.java`: menu de médicos
- `MenuCliente.java`: menu de pacientes
- `MenuAgendamento.java`: menu de agendamentos
- `Staff.java`: controla operações de médico
- `Clientes.java`: controla operações de paciente
- `Agenda.java`: controla operações de agendamento
- `SqlMedico.java`, `SqlCliente.java`, `SqlAgendamento.java`: executam as consultas no banco

## 4. Segurança e boas práticas

### Medidas adotadas
- Uso de `PreparedStatement` para construir consultas SQL, reduzindo risco de injeção SQL básica.
- Verificação de existência de médico e paciente antes de agendar ou alterar dados.
- Tratamento de exceções de entrada em menus para evitar que o programa quebre com valores inválidos.


## 5. Biblioteca utilizada
- `sqlite-jdbc-3.36.0.3.jar`
  - Driver JDBC para conectar ao banco SQLite.
  - Usado em `Sql/SqlAgendamento.java`, `Sql/SqlCliente.java` e `Sql/SqlMedico.java`.
