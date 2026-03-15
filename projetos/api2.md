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
