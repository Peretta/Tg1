## ✅ Projeto – *Lumen*
**Semestre:** Quarto Semestre – 2025-1  
**Empresa Parceira:** FAPG - FUNDAÇÃO DE APOIO À PESQUISA DE PÓS-GRADUANDOS | Professor Responsável: *Juliana*  


---

### 📌 Problema

A FAPG não possui uma forma estruturada de acompanhar o andamento dos projetos em execução, o que dificulta a visualização de prazos, tarefas e responsáveis. A ausência de um acompanhamento centralizado faz com que relatórios sejam feitos manualmente e muitas vezes de forma tardia. Essa falta de transparência afeta a tomada de decisão, impede a análise de desempenho e compromete a eficiência da gestão dos projetos desenvolvidos pela instituição.

---

### ✅ Solução Desenvolvida

A solução proposta consiste em uma plataforma web centralizada para gestão completa dos projetos da FAPG, oferecendo uma visão integrada de prazos, tarefas, responsáveis e áreas de atuação. O sistema permite login seguro, garantindo proteção aos dados sensíveis da instituição. Entre as principais funcionalidades, destacam-se o cadastro, edição e listagem de projetos, além do registro de etapas, tarefas e subtarefas, sua atribuição a membros específicos e acompanhamento de status. A plataforma também possibilita a organização por áreas de atuação e a recuperação de projetos excluídos. Essa abordagem elimina planilhas manuais, aumenta a transparência, acelera a tomada de decisão e fortalece o controle sobre o andamento das iniciativas da FAPG.

---

### 🔗 Link do Repositório Git
- GitHub: [Acessar](https://github.com/Phoenix-Team-Fatec/API-4)

---

##### [Repositório](https://github.com/Phoenix-Team-Fatec/API-4)

| **Tecnologia** | **Funcionalidade**                                                                                                                               |
| :------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| **React**      | Biblioteca JavaScript utilizada para o desenvolvimento do frontend da aplicação, permitindo a criação de interfaces dinâmicas e componentizadas. |
| **Node.js**    | Ambiente de execução JavaScript multiplataforma, utilizado para rodar o código no servidor.                                                      |
| **JavaScript** | Linguagem de programação utilizada no desenvolvimento do projeto, responsável pela lógica de interação e integração entre os componentes.        |
| **TypeScript** | Superset do JavaScript que adiciona tipagem estática e recursos de orientação a objetos, aumentando a robustez e a manutenção do código.         |
| **PostgreSQL** | Banco de dados relacional, utilizado para armazenamento de dados do sistema                                                                      |
| **Firebase**   | Serviço em nuvem com banco de dados não relacional (NoSQL), utilizado para o armazenamento e autenticação de usuários (e-mails e senhas).        |
| **Ollama**     | Ferramente utilizada para executar e gerenciar modelos                                                                                           |
| **Git**        | Sistema de controle de versão distribuído, utilizado para o gerenciamento do código-fonte e colaboração em equipe.                               |

---

### 👨‍💻 Contribuições Pessoais
Atuei como Desenvolvedor no time. Trabalhei diretamente na implementação de funcionalidades essenciais relacionadas ao ciclo de vida dos projetos, especialmente nos módulos de etapas, tarefas e projetos excluídos. Desenvolvi o CRUD completo de Etapas, incluindo a relação entre etapas e usuários, garantindo que a atribuição e acompanhamento ocorressem de forma consistente no banco de dados. Implementei a integração da tela “Minhas Tarefas”, permitindo que cada membro visualizasse suas atividades pendentes de maneira centralizada.

Também implementei o Soft Delete, a funcionalidade de restauração de projetos, e o processo automático de remoção definitiva após 30 dias, garantindo conformidade, rastreabilidade e organização. Modelei e ajustei migrations ao longo do projeto, além de estruturar rotas do back-end e integrações necessárias com o React. Contribuí ainda para melhorias de interface e experiência do usuário, incluindo pop-ups e ajustes de layout.

Apliquei uma IA capaz de chamar funções do beckend, como por exemplo "concluir tarefas"

### Hard skills:

 - React, 
 - Node.js, 
 - TypeScript, 
 - PostgreSQL, 
 - Integração com IA (Ollama) para chamada de funções e 
 - Migrations

### Soft Skills:

- Colaboração: conversas em relação ao backlog e as atividades da sprint
- Proatividade: execução de tarefas do backlog como DevTeam
- Autonomia: manutenção do repositório e README
- Visão de Produto.


Alguns commits

- CRUD Etapa e relação com usuário 
- Atualização de migrations 
- Soft Delete de projetos e etapas 
- Integração da tela “Minhas Tarefas” 
- Exclusão de etapa/tarefa com vínculos
- Regra de exclusão definitiva após 30 dias
- Restauração de projetos e ajuste de rotas
- IA para concluir tarefas e melhorar ações de etapa

<details>
  <summary><strong>Detalhes (opcional – códigos, diagramas, prints)</strong></summary>

```python

// services/OllamaService.ts
import axios from 'axios';

class OllamaService {
 static async processMessage(message: string) {
 const prompt = `
SISTEMA: Você é um assistente especialista em tarefas. 
Siga estas regras:
1. Analise a mensagem e responda APENAS com JSON
2. Ações válidas: complete_task, uncomplete_task, complete_etapa, list_overdue
3. IDs são sempre números inteiros
4. Ignore texto irrelevante
Exemplos:

Usuário: "Finalize a tarefa 12"
Resposta: {"action": "complete_task", "taskId": 12}
Usuário: "Desmarque a tarefa 5"
Resposta: {"action": "uncomplete_task", "taskId": 5}
Usuário: "Conclua todas da etapa 3"
Resposta: {"action": "complete_etapa", "etapaId": 3}
Usuário: "Tarefas atrasadas?"
Resposta: {"action": "list_overdue"}

Mensagem atual: "${message}"
Resposta (APENAS JSON):`;
  
  try {
    console.log('Enviando prompt para Ollama:', prompt); // Log do prompt enviado
    
    const response = await axios.post('http://localhost:11434/api/generate', {
      model: 'gemma:2b',
      prompt: prompt,
      format: 'json',
      stream: false
    });

    console.log('Resposta bruta do Ollama:', response.data.response); // Log da resposta
    
    const parsedResponse = JSON.parse(response.data.response);
    console.log('Resposta parseada:', parsedResponse);
    
    return parsedResponse;
  } catch (error) {
    console.error('Erro detalhado no OllamaService:', {
      errorMessage: error.message,
      responseData: error.response?.data
    });
    throw error; // Propague o erro para o controller
  }
}
}

export default OllamaService;

```
</details>

---

[[Voltar]](../README.md)
