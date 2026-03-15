## ✅ Projeto – *Scrum Tutor* 
**Semestre:** Primeiro Semestre – 2023-1  
**Empresa Parceira:** Fatec – Professor Responsável: *Egideo*  

---

### 📌 Problema
As equipes da empresa possuem dificuldades no processo de organização do trabalho, principalmente na definição de prioridades, prazos e responsabilidades. A falta de conhecimento sobre papéis e funções dentro de uma metodologia ágil gera retrabalho, comunicação ineficiente e baixa previsibilidade das entregas. Sem um método estruturado, os projetos acabam atrasando e o fluxo de desenvolvimento se torna pouco transparente para gestores e colaboradores.

---

### ✅ Solução Desenvolvida
A solução desenvolvida consiste em um sistema web projetado para auxiliar equipes no entendimento e na aplicação correta da metodologia Scrum, oferecendo uma experiência clara, didática e prática. O website reúne em páginas distintas todos os elementos essenciais do framework — eventos, papéis, artefatos, apêndices e bibliografia — permitindo que qualquer equipe compreenda rapidamente suas responsabilidades, fluxos e prioridades. Além disso, a plataforma disponibiliza uma área completa de avaliação de equipes, baseada no método PACER, onde líderes podem avaliar proatividade, autonomia, colaboração e entregas, recebendo os resultados diretamente por e-mail

---

### 🔗 Link do Repositório Git
- GitHub: [Acessar](https://github.com/Phoenix-Team-Fatec/ScrumTutor)

---


### 🧰 Tecnologias Utilizadas
| **Tecnologia** | **Funcionalidade**                                                                  |
| -------------- | ----------------------------------------------------------------------------------- |
| **HTML**       | Define a estrutura e o conteúdo das páginas web.                                    |
| **CSS**        | Responsável pela estilização e layout das páginas.                                  |
| **Flask**      | Framework web em Python utilizado para criar e gerenciar o servidor da aplicação.   |
| **Python**     | Linguagem de programação utilizada no desenvolvimento do backend com Flask.         |
| **AWS**        | Plataforma de nuvem utilizada para hospedagem e deploy da aplicação web.            |
| **Figma**      | Ferramenta de prototipação para o design da interface e fluxo de navegação do site. |
| **Git**        | Sistema de controle de versão utilizado para gerenciar e versionar o código-fonte.  |

---

### 👨‍💻 Contribuições Pessoais

Atuei como **Product Owner (PO)** e também contribuí no **desenvolvimento** da solução.

- Fui responsável por **entender e refinar os requisitos com o cliente** (professor e orientador), em especial a dúvida sobre a avaliação solicitada: se seria apenas baseada no modelo **PACER** ou se incluiria também **avaliações ao final de cada texto explicativo**.  
- Conduzi o alinhamento com o cliente, definindo que seriam implementadas **as duas abordagens**:  
  - a **avaliação PACER** para medir o desempenho da equipe;  
  - e **perguntas ao final dos artigos** para reforçar o entendimento do conteúdo teórico.  
- Participei da **definição das páginas e estrutura de navegação** (menu, página de boas-vindas, páginas de bibliografia, eventos, papéis, artefatos etc.), garantindo coerência entre o conteúdo e a jornada do usuário.  
- Atuei na implementação e ajustes de **front-end (HTML5 + CSS3 + Bootstrap)**, incluindo melhorias de design, centralização de cards, atualização de layout e remoção/reorganização de páginas desnecessárias.  
- Contribuí diretamente na **implementação do formulário PACER**, bem como no seu funcionamento dentro da aplicação (envio dos dados para o back-end e processamento).  
- Implementei, em conjunto com o time, a **funcionalidade de envio de e-mail** usando Flask-Mail, configurando o servidor SMTP e a lógica de envio da avaliação para o e-mail da equipe.  
- Fui responsável por grande parte da **organização do repositório no GitHub**:  
  - atualização contínua do **README.md** (MVP, backlog, tecnologias, links, vídeo de apresentação, LinkedIn, prioridades);  
  - criação e manutenção do **backlog do produto** e documentação das **Sprints**;  
  - limpeza de arquivos obsoletos e **organização de pastas**.  

---

Alguns dos commits no projeto:

- **Base do HTML e início do Flask**  
  - *“Base do HTML (temporário)”*   
  - *“SPRINT 2 - Início do Flask”*  
- **Backlog, MVP e organização do README**  
  - *“ADD BACKLOG README.md”*  
  - *“Criacao MVP, VP e OBJ README.md”*
  - *“Sprints, Time e Tecnologias README.md”*
- **Design e conteúdo**  
  - *“Boas-Vindas”*
  - *“Bibliografia UPDATE”*
  - *“Correção do Design”*
  - *“Centralizando carda”*
- **Funcionalidade PACER e e-mail**  
  - *“Implementação do funcionamento do form da PACER”*
  - *“Implementação do EMAIL”*
  - *“Conteudo do email”*
  - *“Correção do bug”*
- **Organização do repositório**  
  - *“ORGANIZAÇÃO DAS PASTAS DO GIT”* 
  - Diversos *“Update README.md”*, incluindo backlog, prioridades e links.

---

<details>
  <summary><strong>Detalhes Técnicos (código – envio de e-mail PACER)</strong></summary>

```python
from flask import Flask, render_template, request, redirect
from flask_mail import Mail, Message

app = Flask(__name__)
app.secret_key = "phoenix"

# Configuração de e-mail
app.config["MAIL_SERVER"] = "smtp.googlemail.com"
app.config["MAIL_PORT"] = 587
app.config["MAIL_USE_TLS"] = True
app.config["MAIL_USERNAME"] = "phoenix.team.sjc@gmail.com"
app.config["MAIL_PASSWORD"] = "<senha_de_app>" 

mail = Mail(app)

class Avaliacao:
    def __init__(self, papel, proatividade, autonomia, colaboracao, entrega):
        self.papel = papel
        self.proatividade = proatividade
        self.autonomia = autonomia
        self.colaboracao = colaboracao
        self.entrega = entrega

notas = []

@app.route("/criar", methods=["POST"])
def criar():
    papel        = request.form.getlist("papel")
    proatividade = request.form.getlist("proatividade")
    autonomia    = request.form.getlist("autonomia")
    colaboracao  = request.form.getlist("colaboracao")
    entrega      = request.form.getlist("entrega")

    for i in range(len(papel)):
        avaliado = Avaliacao(
            papel[i],
            proatividade[i],
            autonomia[i],
            colaboracao[i],
            entrega[i],
        )
        notas.append(avaliado)

    # Envio de e-mail com o resultado da avaliação PACER
    msg = Message(
        subject="Avaliação PACER - Scrum Tutor",
        sender="noreply@app.com",
        recipients=["phoenix.team.sjc@gmail.com"],
    )
    # Template HTML com o resumo das avaliações
    msg.html = render_template("pacer.html", notas=notas)
    mail.send(msg)

    return redirect("/Pacer")
```
</details>

---

[[Voltar]](../README.md)