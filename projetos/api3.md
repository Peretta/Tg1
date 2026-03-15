
## ✅ Projeto – *OAK-RH*
**Semestre:** Terceiro Semestre – 2024-2  
**Empresa Parceira:** Youtan - Empresa de software | Professor Responsável: *Massanori*  

---

### 📌 Problema

O departamento de Recursos Humanos da Youtan relatou dificuldades para coletar e organizar os feedbacks referentes à cultura da empresa e aos projetos internos. Além disso, o controle sobre a alocação de equipes acontece de maneira manual, o que aumenta a chance de erros e falhas de comunicação. Esse cenário gera perda de informações relevantes, dificulta a análise de clima organizacional e compromete a distribuição correta de profissionais entre os projetos.

---

### ✅ Solução Desenvolvida
A solução proposta consiste em um sistema web moderno e centralizado para gestão de feedbacks, pesquisas de clima e organização de equipes, desenvolvido especialmente para atender às necessidades do RH da Youtan. A plataforma “OAKRH” reúne em um único ambiente o cadastro de usuários com diferentes níveis de acesso, a criação de formulários personalizados e o gerenciamento de equipes. O sistema permite coletar, armazenar e visualizar respostas de avaliações técnicas, comportamentais e de satisfação, oferecendo dashboards completos para análise de desempenho individual e coletivo. Além disso, possibilita comparar avaliações ao longo do tempo, aplicar filtros estratégicos e exportar relatórios em PDF. Dessa forma, a solução elimina processos manuais, reduz erros de comunicação e oferece uma visão estruturada que fortalece a cultura organizacional e melhora a tomada de decisão do RH.

---

### 🔗 Link do Repositório Git
- GitHub: [Acessar](https://github.com/Phoenix-Team-Fatec/OAK-RH)

---

### 🧰 Tecnologias Utilizadas

| **Tecnologia** | **Funcionalidade**                                                                                                                               |
| :------------- | :----------------------------------------------------------------------------------------------------------------------------------------------- |
| **React**      | Biblioteca JavaScript utilizada para o desenvolvimento do frontend da aplicação, permitindo a criação de interfaces dinâmicas e componentizadas. |
| **Node.js**    | Ambiente de execução JavaScript multiplataforma, utilizado para rodar o código no servidor.                                                      |
| **JavaScript** | Linguagem de programação utilizada no desenvolvimento do projeto, responsável pela lógica de interação e integração entre os componentes.        |
| **TypeScript** | Superset do JavaScript que adiciona tipagem estática e recursos de orientação a objetos, aumentando a robustez e a manutenção do código.         |
| **PostgreSQL** | Banco de dados relacional, utilizado para armazenamento de dados do sistema                                                                      |
| **Firebase**   | Serviço em nuvem com banco de dados não relacional (NoSQL), utilizado para o armazenamento e autenticação de usuários (e-mails e senhas).        |
| **Git**        | Sistema de controle de versão distribuído, utilizado para o gerenciamento do código-fonte e colaboração em equipe.                               |

---

### 👨‍💻 Contribuições Pessoais

Atuei como **Desenvolvedor (Dev Team)**, contribuindo diretamente tanto no back-end quanto no front-end. Minhas principais entregas incluem:

- **Criação do modelo, controller, service e rotas de Equipes**, permitindo cadastrar, listar, editar e excluir equipes dentro da plataforma.
- Implementação de componentes do front-end, como **listar usuários pertencentes a uma equipe**, pop-ups de edição, pop-up de membros e telas do portal do usuário.
- Estruturação completa de **logout e Protected Routes**, garantindo segurança de acesso e bloqueio de páginas para usuários não autenticados.
- Implementação da **integração dos formulários no front-end**, conectando as rotas às interfaces e garantindo fluxo entre categorias, formulários e respostas.
- Configuração do back-end para **criação, edição e gerenciamento de categorias**, incluindo ajustes em CategoryModel, CategoryController e CategoryService.
- Desenvolvimento dos **dashboards de gráficos de usuários, equipes e formulários**, permitindo visualização clara e analítica para o RH.
- Refatoração da estrutura de pastas do projeto, correções de merge, resolução de conflitos e ajustes gerais no código.
- Implementação inicial do **servidor React**, configuração do `.gitignore`, remoção do `node_modules` do repositório e padronização da base do projeto.
- Participação ativa na construção das telas iniciais, fluxo do portal do usuário e no desenvolvimento contínuo da interface.

---
Alguns commits: 
- Gráficos de usuários e equipes implementados  
- Gráficos dos formulários concluídos  
- Telas iniciais do portal do usuário desenvolvidas  
- Integração da tela de formulários com o front-end  
- Atualização dos models e controller de categorias  
- Rotas, controllers e services de categorias criados  
- Criar e excluir equipes implementado  
- Pop-up de membros e lista de usuários da equipe  
- Logout e Protected Route implementados  
- EquipeModel, EquipeController e rotas principais entregues  
- Classe líder criada  
- Servidor React criado e estrutura inicial montada  
- Projeto inicial criado e configurado  

---

<details>
  <summary><strong>Detalhes Técnicos</strong></summary>

```javascript
import { Request, Response } from "express";
import { 
    createEquipeService, 
    getAllEquipesService, 
    getEquipeByIdService, 
    updateEquipeService, 
    deleteEquipeService 
} from "../services/equipeService";

// Função para criar equipe
export const createEquipe = async (req: Request, res: Response) => {
    const { nome } = req.body;  
    try {
        const newEquipe = await createEquipeService(nome);
        res.status(201).json(newEquipe);
    } catch (error) {
        res.status(500).json({ message: "Erro ao criar equipe" });
    }
}

// Função para listar todas as equipes
export const getAllEquipes = async (req: Request, res: Response) => {
    try {
        const allEquipes = await getAllEquipesService();
        res.status(200).json(allEquipes);
    } catch (error) {
        res.status(500).json({ message: "Erro ao buscar equipes" });
    }
}

// Função para listar equipe por ID
export const getEquipeById = async (req: Request, res: Response) => {
    const { id } = req.params;
    try {
        const equipe = await getEquipeByIdService(parseInt(id));
        res.status(200).json(equipe);
    } catch (error) {
        res.status(404).json({ message: "Equipe não encontrada" });
    }
}

// Função para atualizar equipe por ID
export const updateEquipe = async (req: Request, res: Response) => {
    const { id } = req.params;
    const { nome } = req.body;
    try {
        const updatedEquipe = await updateEquipeService(parseInt(id), nome);
        res.status(200).json(updatedEquipe);
    } catch (error) {
        res.status(500).json({ message: "Erro ao atualizar equipe" });
    }
}

// Função para excluir equipe por ID
export const deleteEquipe = async (req: Request, res: Response) => {
    const { id } = req.params;
    try {
        await deleteEquipeService(parseInt(id));
        res.status(200).json({ message: "Equipe excluída com sucesso" });
    } catch (error) {
        res.status(500).json({ message: "Erro ao excluir equipe" });
    }
}
```
</details>

---

[[Voltar]](../README.md)
