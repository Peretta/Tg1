## ✅ Projeto – *Gerenciamento de Regras de Negócio*
**Semestre:** Sexto Semestre – 2025-2  
**Empresa Parceira:** Dom Rock | Professor Responsável: *Professor Walmir*  

---

### 📌 Problema

Empresas enfrentam desafios significativos no gerenciamento de regras de negócio, especialmente quando estas são dinâmicas e sofrem alterações frequentes. As regras são constantemente atualizadas devido ao lançamento de novos produtos, descontinuidade de produtos, mudanças em precificação, acordos comerciais, políticas de vendas e parcerias.

Decorrente dessa atividade, a base de conhecimento de regras geralmente não está registrada e organizada de forma adequada, ocasionando inconsistência operacional, conflito entre regras aplicadas por múltiplos colaboradores, conhecimento tácito e perda de rastreabilidade de processos. 

Especificamente, no contexto de **cálculo de comissionamento mensal de funcionários**, as dificuldades incluem:
- Aplicação incorreta de percentuais de comissionamento conforme cargo e legislação trabalhista
- Gerenciamento de exceções e particularidades por cargo
- Falta de transparência nas decisões de cálculo
- Dificuldade em manter regras consistentes em diferentes cenários de venda

---

### ✅ Solução Desenvolvida

Um **sistema integrado de gerenciamento de regras de negócio e cálculo de comissionamento** composto por três camadas:

1. **Backend (Spring Boot)**: API REST para cálculo de comissões, gerenciamento de regras de negócio, armazenamento em MongoDB e importação de dados via Excel.

2. **Frontend Web (Vue.js 3)**: Aplicação SPA (Single Page Application) para criação, visualização e gerenciamento de regras de negócio com interface intuitiva e autenticação.

3. **Agente IA (LLMs)**: Sistema inteligente baseado em modelos de linguagem generativos (LLM) para:
   - Interpretação de regras de negócio em linguagem natural
   - Geração automática de código com base em requisitos
   - Indexação e recuperação de regras via RAG (Retrieval-Augmented Generation)
   - Processamento de PDFs e código-fonte para construção de base de conhecimento

---

### 🔗 Links dos Repositórios Git
- **Backend (Spring Boot)**: [Acessar](https://github.com/Phoenix-Team-Fatec/API_6_backend)
- **Frontend (Vue.js)**: [Acessar](https://github.com/Phoenix-Team-Fatec/API_6_frontend)
- **ML Agent (Python/LLM)**: [Acessar](https://github.com/Phoenix-Team-Fatec/API_6_ML)

---

### 🧰 Tecnologias Utilizadas

## 📊 Tabela Consolidada de Tecnologias e Sua Aplicação

| Tecnologia | Onde foi usada |
|---|---|
| **Java 17** | Linguagem de programação para backend |
| **Spring Boot** | Framework web para construção de API REST com features avançadas |
| **MongoDB** | Banco de dados NoSQL para armazenamento de regras, comissões e dados de funcionários |
| **Maven** | Gerenciador de dependências e build |
| **Python 3.10+** | Linguagem para desenvolvimento do agente IA |
| **LangChain** | Framework para orquestração de agentes IA e gerenciamento de prompts |
| **FastAPI** | Framework web moderno para APIs Python |
| **LanceDB** | Banco de dados vetorial para RAG (Retrieval-Augmented Generation) |
| **MLflow** | Rastreamento de experimentos e modelos de ML |
| **Ollama** | Execução local de modelos LLM |
| **LangChain Groq** | Integração com modelos Groq |
| **Google Vertex AI / Gemini** | Integração com modelos Google |
| **HuggingFace** | Acesso a modelos de IA abertos |
| **PyMUPDF** | Processamento de PDFs para indexação de regras |
| **Vue** | Biblioteca JavaScript para construção de interfaces reativas |
| **Vue Router** | Roteamento para aplicação web |
| **Pandas** | Manipulação e análise de dados |

[[Voltar]](../README.md)
