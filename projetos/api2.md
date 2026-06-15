## ✅ Projeto – *DataEase*
**Semestre:** Segundo Semestre – 2024-1  
**Empresa Parceira:** Fatec – Professor Responsável: *Bertotti*  

---

### 📌 Problema

Os usuários da empresa enfrentam dificuldades para acessar e interpretar informações armazenadas no banco de dados, pois grande parte deles não possui conhecimento adequado em SQL. Como resultado, dependem constantemente do setor técnico para extrair relatórios e consultas simples, tornando o processo lento e burocrático. Essa limitação prejudica a tomada de decisões e impede que usuários tenham autonomia para explorar os dados que já estão disponíveis.

---

### ✅ Solução Desenvolvida
A solução criada consiste em um aplicativo Desktop chamado DataEase, projetado para permitir que usuários sem conhecimento técnico em SQL consultem bancos de dados de forma simples e intuitiva. O sistema oferece uma interface simples, composta por um campo de entrada para linguagem natural, um botão de envio e uma área destinada à visualização dos resultados retornados. Sua principal funcionalidade é a tradução automática de linguagem natural em comandos SQL, executando as consultas diretamente no banco escolhido pelo usuário retornando os dados desejados, ou seja você pergunta e ele responde - o sql é feito por baixo dos panos. Além disso, o DataEase possibilita o cadastro de usuários, a configuração de múltiplos bancos de dados e a troca do modelo de linguagem utilizado. Com isso, elimina a dependência do setor técnico, acelera o acesso à informação e garante autonomia aos usuários na exploração dos dados corporativos.

---

### 🔗 Link do Repositório Git
- GitHub: [Acessar](https://github.com/Phoenix-Team-Fatec/DataEase)

---

### 🧰 Tecnologias Utilizadas

#### Tecnologias Utilizadas
| **Tecnologia**  | **Funcionalidade**                                                                                                   |
| --------------- | -------------------------------------------------------------------------------------------------------------------- |
| **Java**       | Linguagem responsável pelo desenvolvimento de todo o sistema, desde a interface a conexão com o modelo de linguagem. |
| **MySQL**       | Armazenamento de informações do usuário                                                                              |
| **LangChain4j** | Biblioteca do java utilizada para conexão dos modelos.                                                               |
| **LM Studio**   | Ferramenta utilizada para execução dos modelos.                                                                      |
| **Git**         | Sistema de controle de versão utilizado para gerenciar e versionar o código-fonte.                                   |

### 👨‍💻 Contribuições Pessoais

Atuei como **Desenvolvedor (Dev Team)** no projeto. Minhas principais contribuições foram:

- **Implementação do módulo de comunicação com o modelo de linguagem**, utilizando *LangChain4j* e *LM Studio*, incluindo a criação da função para estabelecer conexão com o servidor LLM (`ligar servidor LM`).
- Desenvolvimento de **funcionalidades-chave do CRUD de usuários**, incluindo otimizações no método `cadastrarUser`, implementação do método `getNameDB` e criação do `getIdUsuario`.
- Criação e gerenciamento do **banco de dados MySQL**, com tabelas para usuários e conexões, além de consultas e selects de validação.
- Desenvolvimento das **interações entre a interface e o back-end**, incluindo atualizações na tela de chat para a Sprint 3, ajustes visuais e funcionamento da área de entrada de comandos.
- Implementação da **conexão em tempo real com o banco**, permitindo que o texto gerado pelo modelo fosse executado diretamente no banco pelo usuário.
- Comentários, limpeza e organização do código durante as Sprints, garantindo clareza e documentação interna adequada.
- Participação no versionamento Git, com commits contínuos envolvendo criação de funcionalidades, correções e refinamento do fluxo interno da aplicação.

---

### Hard skills:

| **Tecnologia** | **O que consigo fazer** |
|---|---|
| **Java** | Implementar métodos de cadastro (`cadastrarUser`), buscar IDs/nomes de banco (`getIdUsuario`, `getNameDB`) e integrar a tela de chat ao back-end. |
| **MySQL** | Criar schema, tabelas de usuários/conexões e consultas de validação usadas pelo CRUD. |
| **LangChain4j** | Montar a ponte entre a aplicação Java e o modelo de linguagem para gerar SQL a partir de texto. |
| **LM Studio** | Configurar e validar a função de conexão com o servidor LLM local (`ligar servidor LM`). |
| **Hugging Face** | Explorar e testar modelos de linguagem compatíveis com o fluxo de tradução NL → SQL. |

### Soft Skills:

**Cenário — entregando o coração do DataEase**

Na Sprint 3, o time precisava que o usuário digitasse uma pergunta em linguagem natural e recebesse o resultado da consulta na hora — mas a integração com o modelo ainda não estava estável. Assumi a tarefa de **conectar o LM Studio via LangChain4j**, testando localmente até a função `ligar servidor LM` funcionar de ponta a ponta.

Enquanto isso, participei das **dailies e alinhamentos de backlog**, avisando cedo quando a conexão com o banco ou o CRUD de usuários bloqueava outras entregas. Com **proatividade**, fui além do mínimo: otimizei o `cadastrarUser` em duas etapas, comentei o código para facilitar revisão e modelei o MySQL para suportar múltiplos bancos por usuário. Quando a tela de chat precisou de ajustes visuais e funcionais, trabalhei de forma **autônoma** na integração front-back, garantindo que o texto gerado pelo modelo fosse executado diretamente no banco escolhido — cumprindo a promessa do produto: *perguntar e receber a resposta, sem saber SQL*.


Alguns dos commits no desenvolvimento:

- *Função ligar servidor LM funciona*  
-*Finalização das modificações da tela Chat para Sprint 3*  
- *Método getNameDB feito*  
- *Código comentado e adição do método getIdUsario*
- *Otimização do método cadastrarUser (1/2)*  
- *Otimização do método cadastrarUser (2/2)*  
- *Atualização telaChat*  
- *Criação de banco de dados e select*  
- *Conexão realizada, dados sendo enviados*  

---

<details>
  <summary><strong>Detalhes Técnicos (exemplo de código utilizado no projeto)</strong></summary>

```java
package org.example;

import dev.langchain4j.model.chat.ChatLanguageModel;
import dev.langchain4j.model.localai.LocalAiChatModel;

public class Main {
    public static void main(String[] args) {

        ChatLanguageModel model = LocalAiChatModel.builder()
                .baseUrl("http://localhost:1234/v1/")
                .modelName("nsql")
                .temperature(0.9)
                .build();

        String answer = model.generate("Create a table");
        System.out.println(answer);
    }
}
```
</details>

---

[[Voltar]](../README.md)
