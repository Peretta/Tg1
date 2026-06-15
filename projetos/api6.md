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

1. **Backend (Spring Boot)**: API REST para cálculo e auditoria de comissões, gerenciamento de regras de negócio, armazenamento em MongoDB e importação de dados via Excel.

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

### Hard skills:

| **Tecnologia** | **O que consigo fazer** |
|---|---|
| **Spring Boot** | Desenvolver motor de comissionamento com auditoria etapa a etapa, CRUD de usuários/lojas/marcas e APIs REST. |
| **Python (LangChain/FastAPI)** | Montar agente IA que interpreta regras, gera código e consulta base indexada via RAG. |
| **HuggingFace** | Acessar e testar modelos abertos compatíveis com o pipeline de geração e recuperação de regras. |
| **Vue.js 3** | Criar interfaces para listagem, criação e edição de regras de negócio com fluxo autenticado. |
| **Pandas** | Importar e validar dados de funcionários e vendas a partir de planilhas Excel. |
| **MongoDB** | Armazenar regras dinâmicas, resultados de comissão e trilhas de auditoria por funcionário. |

### Soft Skills:

**Cenário — quando a regra de comissão mudou na véspera do fechamento**

A Dom Rock precisava calcular comissionamento mensal com dezenas de exceções — férias, licença, bônus por faixa, override de marca — e ainda rastrear *por que* cada valor foi calculado. Na sprint do **motor de comissionamento**, implementei a função `calcular_comissionamento` com **auditoria** etapa a etapa, para que o RH pudesse explicar qualquer valor ao funcionário.

Quando o cliente pediu suporte a novas regras temporárias (overrides de percentual por mês), **negociei** com o PO o escopo mínimo viável para não atrasar o fechamento: overrides via dicionário, sem refatorar todo o engine. Revisei PRs de colegas (`feature/commission-engine`, `feature/rules-listing`) aplicando **gestão de qualidade** — garantindo testes de unidade e interfaces consistentes entre service e implementação. Com **proatividade**, documentei o tutorial de importação de dados e corrigi duplicidade de funcionários na base. O resultado foi um sistema em que regras deixam de ser conhecimento tácito e passam a ser rastreáveis, auditáveis e editáveis pela equipe de negócio.

### Commits e Participações Relevantes

- Merge pull request #15 from Phoenix-Team-Fatec/fix/docs-dom-rock
- Merge pull request #14 from Phoenix-Team-Fatec/feature/mvc-lojas
- Funcionários sem repetição
- CRUD de usuário, 
- Alteração no comando que exibe versões
- Interfaces e implementações em services
- Merge branch 'develop' into refactor/servico-interface-impl
- Merge pull request #4 from Phoenix-Team-Fatec/feature/rules-listing
- Tutorial importar dados
- Devcontainer alterado
- Merge pull request #3 from Phoenix-Team-Fatec/feature/commission-engine
- Testes de unidade
- marcas, lojas efuncionarios
- auditoria

<details>

  
```

def calcular_comissionamento(
    funcionarios: list[Funcionario],
    vendas: list[Venda],
    tabela_comissao: list[ComissionamentoBase],
    intercorrencias: list[Intercorrencia],
    ano: int,
    mes: int,
    overrides: Optional[dict] = None,
    auditoria: bool = True,
) -> list[ResultadoComissionamentoDetalhado]:
    """
    Calcula o comissionamento de todos os funcionários para o mês/ano
    informado, aplicando todas as regras gerais e intercorrências.

    overrides: dict opcional para regras temporárias do mês (ex: % especial
               por marca/cargo, bônus de período, etc.)
    auditoria: se True, coleta etapas para rastreamento; se False, apenas calcula
    """
    if overrides is None:
        overrides = {}

    total_dias = dias_no_mes(ano, mes)
    data_competencia = date(ano, mes, 1)

    # --- Indexar tabela de comissão ---
    indice_comissao: dict[tuple[int, int], float] = {
        (c.cod_marca, c.cod_cargo): c.perc_comissao for c in tabela_comissao
    }

    # Aplicar overrides de % de comissão para o mês
    for (cod_marca, cod_cargo), perc in overrides.get("perc_override", {}).items():
        indice_comissao[(cod_marca, cod_cargo)] = perc

    # --- Consolidar vendas por matrícula e por loja ---
    vendas_por_matricula: dict[str, float] = {}
    vendas_por_loja: dict[str, float] = {}

    for v in vendas:
        vendas_por_matricula[v.matricula] = (
            vendas_por_matricula.get(v.matricula, 0.0) + v.vlr_venda
        )
        vendas_por_loja[v.cod_loja] = vendas_por_loja.get(v.cod_loja, 0.0) + v.vlr_venda

    print_debug("")
    print_debug("========== VENDAS CONSOLIDADAS ==========")
    print_debug(f"Vendas por matrícula: {vendas_por_matricula}")
    print_debug(f"Vendas por loja: {vendas_por_loja}")

    # --- Indexar intercorrências por matrícula ---
    intercorr_por_matricula: dict[str, list[Intercorrencia]] = {}
    for ic in intercorrencias:
        intercorr_por_matricula.setdefault(ic.matricula, []).append(ic)

    resultados: list[ResultadoComissionamentoDetalhado] = []

    for func in funcionarios:
        # NOVO: Criar coletor para este funcionário
        coletor = ColetoraEtapas() if auditoria else None
        
        print_debug("")
        print_debug("==========================================")
        print_debug(f"INICIANDO CÁLCULO DA MATRÍCULA: {func.matricula}")
        print_debug(f"Funcionário: cargo={func.cod_cargo} - {func.descr_cargo}")
        print_debug(f"Loja: {func.cod_loja} - {func.descr_loja}")
        print_debug(f"Marca: {func.cod_marca} - {func.descr_marca}")
        print_debug(f"Admissão: {func.data_admissao}")
        print_debug(f"Demissão: {func.data_demissao}")
        # Verificar se funcionário estava ativo no mês
        admitido_no_mes = (
            func.data_admissao.year == ano and func.data_admissao.month == mes
        )
        demitido_no_mes = (
            func.data_demissao is not None
            and func.data_demissao.year == ano
            and func.data_demissao.month == mes
        )

        # Ignorar funcionários demitidos antes do mês de competência
        if func.data_demissao is not None and func.data_demissao < data_competencia:
            print_debug("Funcionário ignorado: demitido antes do mês de competência.")
            continue

        # Ignorar admitidos após o mês de competência
        if func.data_admissao > date(ano, mes, total_dias):
            print_debug("Funcionário ignorado: admitido após o mês de competência.")
            continue

        eh_gerente = func.cod_cargo == COD_CARGO_GERENTE

        # --- Base de vendas ---
        if eh_gerente:
            base_vendas = vendas_por_loja.get(func.cod_loja, 0.0)
            print_debug("Funcionário é gerente.")
            print_debug(
                f"Base de vendas usada: total da loja {func.cod_loja} = R$ {base_vendas:,.2f}"
            )
        else:
            base_vendas = vendas_por_matricula.get(func.matricula, 0.0)
            print_debug("Funcionário não é gerente.")
            print_debug(
                f"Base de vendas usada: vendas da matrícula {func.matricula} = R$ {base_vendas:,.2f}"
            )
        
        # ETAPA 1: Registrar base de vendas
        if coletor:
            coletor.registrar(
                secao="Base de Vendas",
                descricao=f"Buscar base de vendas para matrícula {func.matricula}",
                entrada={
                    "matricula": func.matricula,
                    "eh_gerente": eh_gerente,
                    "cod_cargo": func.cod_cargo
                },
                saida={"base_vendas": base_vendas},
                logica="Se gerente: utiliza total da loja; se vendedor: utiliza vendas pessoais",
                condicao="Gerente" if eh_gerente else "Vendedor"
            )

        # Bônus sobre base de vendas (ex: bônus por tempo de casa adicionado à base)
        bonus_base_venda = sum(
            ic.valor
            for ic in intercorr_por_matricula.get(func.matricula, [])
            if ic.tipo == "bonus_venda"
        )

        if bonus_base_venda:
            print_debug(
                f"Bônus adicionado à base de vendas: R$ {bonus_base_venda:,.2f}"
            )
            
            # ETAPA 1b: Registrar bonus_venda
            if coletor:
                coletor.registrar(
                    secao="Base de Vendas",
                    descricao=f"Aplicar bônus de venda",
                    entrada={"bonus_venda": bonus_base_venda},
                    saida={"base_vendas_com_bonus": base_vendas + bonus_base_venda},
                    logica="Adiciona bônus_venda à base de vendas",
                    condicao="Intercorrência bonus_venda vigente"
                )

        print_debug(f"Base final para cálculo da comissão: R$ {base_vendas:,.2f}")

        base_vendas += bonus_base_venda

        # --- % de comissão ---
        # Override de marca: ex "aplicar % da marca 20 em todos cargos da marca 10"
        perc_original = indice_comissao.get((func.cod_marca, func.cod_cargo), 0.0)
        cod_marca_efetivo = overrides.get("marca_override", {}).get(
            func.cod_marca, func.cod_marca
        )
        
        # Se houver override de marca, buscar % da marca substituída
        if cod_marca_efetivo != func.cod_marca:
            perc = indice_comissao.get((cod_marca_efetivo, func.cod_cargo), 0.0)
        else:
            perc = perc_original

        print_debug(f"Marca efetiva para busca de comissão: {cod_marca_efetivo}")
        print_debug(f"Percentual base encontrado: {perc * 100:.2f}%")
        
        # ETAPA 2: Registrar busca de percentual base
        if coletor:
            coletor.registrar(
                secao="Percentual Base",
                descricao=f"Buscar percentual para marca {func.cod_marca}, cargo {func.cod_cargo}",
                entrada={"marca": func.cod_marca, "cargo": func.cod_cargo},
                saida={"percentual": perc},
                logica=f"Consultou indice_comissao[({func.cod_marca}, {func.cod_cargo})]",
                condicao=f"Override de marca: {'Sim (' + str(cod_marca_efetivo) + ')' if cod_marca_efetivo != func.cod_marca else 'Não'}"
            )

        # Acréscimo de % por regra do mês (ex: +0,5% para marca 30)
        perc_original_com_override = perc
        perc += overrides.get("perc_adicional", {}).get(
            (func.cod_marca, func.cod_cargo), 0.0
        )
        print_debug(f"Percentual final após adicionais: {perc * 100:.2f}%")
        
        # ETAPA 2b: Registrar acréscimos de percentual
        if coletor and perc != perc_original_com_override:
            coletor.registrar(
                secao="Percentual - Overrides",
                descricao=f"Aplicar acréscimo de percentual",
                entrada={"perc_base": perc_original_com_override},
                saida={"perc_final": perc},
                logica=f"Adicionou {(perc - perc_original_com_override) * 100:.2f}% de acréscimo",
                condicao=f"Override perc_adicional ativo para maio/{ano}"
            )

        # --- Fator proporcional base ---
        fator = 1.0
        bonus = 0.0

        # Proporcional de admissão
        if admitido_no_mes:
            dias_ef = dias_trabalhados_admissao(func.data_admissao, ano, mes)
            fator_admissao = fator_proporcional(dias_ef, total_dias)
            fator = min(fator, fator_proporcional(dias_ef, total_dias))

            print_debug("Aplicando proporcional de admissão.")
            print_debug(f"Dias trabalhados desde admissão: {dias_ef} de {total_dias}")
            print_debug(f"Fator de admissão: {fator_admissao:.4f}")
            
            # ETAPA 3: Registrar proporcional de admissão
            if coletor:
                coletor.registrar(
                    secao="Fator Proporcional",
                    descricao="Aplicar proporcional de admissão",
                    entrada={"data_admissao": str(func.data_admissao), "dias_mes": total_dias},
                    saida={"fator_admissao": fator_admissao},
                    logica=f"({dias_ef} dias trabalhados) / ({total_dias} dias do mês)",
                    condicao="Admitido neste mês"
                )

        # Proporcional de demissão
        if demitido_no_mes:
            dias_ef = dias_trabalhados_demissao(func.data_demissao, ano, mes)
            fator_demissao = fator_proporcional(dias_ef, total_dias)
            fator = min(fator, fator_proporcional(dias_ef, total_dias))

            print_debug("Aplicando proporcional de demissão.")
            print_debug(f"Dias trabalhados até demissão: {dias_ef} de {total_dias}")
            print_debug(f"Fator de demissão: {fator_demissao:.4f}")

        # Intercorrências do mês
        for ic in intercorr_por_matricula.get(func.matricula, []):
            print_debug("")
            print_debug(f"Intercorrência encontrada: {ic.tipo}")
            print_debug(
                f"Início: {ic.data_inicio} | Fim: {ic.data_fim} | Valor: R$ {ic.valor:,.2f}"
            )

            if ic.tipo == "ferias" and ic.data_inicio and ic.data_fim:
                fator_f = calcular_fator_ferias(ic.data_inicio, ic.data_fim, ano, mes)
                fator = min(fator, fator_f)

                print_debug("Aplicando regra de férias.")
                print_debug(f"Fator de férias: {fator_f:.4f}")
                print_debug(f"Fator proporcional acumulado: {fator:.4f}")
                
                # ETAPA 4: Registrar férias
                if coletor:
                    coletor.registrar(
                        secao="Intercorrências",
                        descricao=f"Aplicar férias de {ic.data_inicio} a {ic.data_fim}",
                        entrada={"fator_anterior": fator / fator_f if fator_f > 0 else 1.0},
                        saida={"fator_novo": fator},
                        logica="Reduz fator proporcional pelos dias de férias",
                        condicao="Férias vigente no mês"
                    )

            elif ic.tipo == "licenca_maternidade" and ic.data_inicio:
                fator_l = calcular_fator_licenca_maternidade(ic.data_inicio, ano, mes)
                fator = min(fator, fator_l)

                print_debug("Aplicando regra de licença maternidade.")
                print_debug(f"Fator de licença maternidade: {fator_l:.4f}")
                print_debug(f"Fator proporcional acumulado: {fator:.4f}")
                
                # ETAPA 4: Registrar licença maternidade
                if coletor:
                    coletor.registrar(
                        secao="Intercorrências",
                        descricao=f"Aplicar licença maternidade a partir de {ic.data_inicio}",
                        entrada={"fator_anterior": fator / fator_l if fator_l > 0 else 1.0},
                        saida={"fator_novo": fator},
                        logica="Zera comissionamento a partir da data de início da licença",
                        condicao="Licença maternidade vigente no mês"
                    )

            elif ic.tipo == "afastamento" and ic.data_inicio and ic.data_fim:
                # Calcular dias de afastamento no mês
                primeiro_dia_mes = date(ano, mes, 1)
                ultimo_dia_mes = date(ano, mes, total_dias)
                inicio_ef = max(ic.data_inicio, primeiro_dia_mes)
                fim_ef = min(ic.data_fim, ultimo_dia_mes)

                if fim_ef >= inicio_ef:
                    dias_afastamento = (fim_ef - inicio_ef).days + 1
                    dias_trabalhados_no_mes = total_dias - dias_afastamento
                    ajuste = calcular_ajuste_afastamento(
                        vlr_base=base_vendas,
                        dias_afastamento=dias_afastamento,
                        dias_trabalhados=dias_trabalhados_no_mes,
                        total_dias=total_dias,
                    )
                    # O valor de afastamento já é o adicional — não reduz o fator geral
                    bonus += ajuste

                    print_debug("Aplicando regra de afastamento.")
                    print_debug(f"Dias de afastamento no mês: {dias_afastamento}")
                    print_debug(f"Dias trabalhados no mês: {dias_trabalhados_no_mes}")
                    print_debug(f"Ajuste de afastamento calculado: R$ {ajuste:,.2f}")
                    print_debug(f"Bônus acumulado: R$ {bonus:,.2f}")
                    
                    # ETAPA 4: Registrar afastamento
                    if coletor:
                        coletor.registrar(
                            secao="Intercorrências",
                            descricao=f"Aplicar afastamento de {ic.data_inicio} a {ic.data_fim}",
                            entrada={"dias_afastamento": dias_afastamento, "base_vendas": base_vendas},
                            saida={"ajuste_afastamento": ajuste},
                            logica="Calcula ajuste como MAX(proporcional, R$3.500)",
                            condicao="Afastamento vigente no mês"
                        )

            elif ic.tipo == "bonus_fixo":
                bonus += ic.valor

                print_debug("Aplicando bônus fixo.")
                print_debug(f"Valor do bônus fixo: R$ {ic.valor:,.2f}")
                print_debug(f"Bônus acumulado: R$ {bonus:,.2f}")
                
                # ETAPA 4: Registrar bônus fixo
                if coletor:
                    coletor.registrar(
                        secao="Intercorrências",
                        descricao="Adicionar bônus fixo",
                        entrada={"bonus_anterior": bonus - ic.valor},
                        saida={"bonus_novo": bonus},
                        logica=f"Adiciona R$ {ic.valor:.2f} ao bônus",
                        condicao="Bônus fixo vigente"
                    )

            elif ic.tipo == "perc_bonus":
                perc += ic.valor

                print_debug("Aplicando bônus percentual.")
                print_debug(f"Percentual adicional: {ic.valor * 100:.2f}%")
                print_debug(f"Percentual acumulado: {perc * 100:.2f}%")
                
                # ETAPA 4: Registrar bônus percentual
                if coletor:
                    coletor.registrar(
                        secao="Intercorrências",
                        descricao="Adicionar bônus percentual",
                        entrada={"perc_anterior": perc - ic.valor},
                        saida={"perc_novo": perc},
                        logica=f"Adiciona {ic.valor * 100:.2f}% ao percentual",
                        condicao="Bônus percentual vigente"
                    )

            elif ic.tipo == "admissao_bonus":
                # Bônus para admitidos até determinado dia
                if admitido_no_mes and func.data_admissao.day <= ic.data_inicio.day:
                    bonus += ic.valor

                    print_debug("Aplicando bônus de admissão.")
                    print_debug(f"Valor do bônus de admissão: R$ {ic.valor:,.2f}")
                    print_debug(f"Bônus acumulado: R$ {bonus:,.2f}")
                    
                    # ETAPA 4: Registrar bônus de admissão
                    if coletor:
                        coletor.registrar(
                            secao="Intercorrências",
                            descricao="Adicionar bônus de admissão",
                            entrada={"dia_admissao": func.data_admissao.day},
                            saida={"bonus_novo": bonus},
                            logica=f"Admitido até dia {ic.data_inicio.day}: adiciona R$ {ic.valor:.2f}",
                            condicao="Bônus de admissão vigente"
                        )

        # --- Comissão base ---
        valor_comissao_bruto = base_vendas * perc
        valor_comissao_proporcional = valor_comissao_bruto * fator

        # --- Bônus de meta por faixa (ex: dezembro) ---
        bonus_faixa = _calcular_bonus_faixa(
            eh_gerente=eh_gerente,
            cod_marca=func.cod_marca,
            base_vendas=base_vendas,
            overrides=overrides,
        )
        bonus += bonus_faixa

        if bonus_faixa:
            print_debug("Aplicando bônus por faixa.")
            print_debug(f"Bônus por faixa calculado: R$ {bonus_faixa:,.2f}")
            print_debug(f"Bônus total acumulado: R$ {bonus:,.2f}")
            
            # ETAPA 5: Registrar bônus por faixa
            if coletor:
                coletor.registrar(
                    secao="Bônus por Faixa",
                    descricao="Aplicar bônus por faixa de venda",
                    entrada={"base_vendas": base_vendas},
                    saida={"bonus_faixa": bonus_faixa},
                    logica="Consultou tabela de faixas e aplicou bônus conforme range",
                    condicao=f"{'Gerente' if eh_gerente else 'Funcionário'} - Marca {func.cod_marca}"
                )

        # ETAPA 6: Registrar comissão final
        if coletor:
            coletor.registrar(
                secao="Comissão Final",
                descricao="Calcular comissão bruta e proporcional",
                entrada={"base": base_vendas, "perc": perc * 100, "fator": fator},
                saida={"comissao_bruta": valor_comissao_bruto, "comissao_proporcional": valor_comissao_proporcional},
                logica=f"Comissão bruta = {base_vendas:.2f} × {perc * 100:.2f}%; Proporcional = bruta × {fator:.4f}",
                condicao="Cálculo padrão"
            )

        valor_final = valor_comissao_proporcional + bonus

        print_debug("")
        print_debug("---------- RESUMO DO CÁLCULO ----------")
        print_debug(f"Base de vendas: R$ {base_vendas:,.2f}")
        print_debug(f"Percentual de comissão: {perc * 100:.2f}%")
        print_debug(f"Comissão bruta = R$ {base_vendas:,.2f} x {perc * 100:.2f}% = R$ {valor_comissao_bruto:,.2f}")
        print_debug(f"Fator proporcional aplicado: {fator:.4f}")
        print_debug(f"Comissão proporcional = R$ {valor_comissao_bruto:,.2f} x {fator:.4f} = R$ {valor_comissao_proporcional:,.2f}")
        print_debug(f"Bônus total: R$ {bonus:,.2f}")
        print_debug(f"VALOR FINAL = R$ {valor_final:,.2f}")
        print_debug("----------------------------------------")

        # ETAPA 7: Registrar resultado final
        if coletor:
            coletor.registrar(
                secao="Resultado Final",
                descricao="Consolidar resultado final de comissão",
                entrada={"comissao_proporcional": valor_comissao_proporcional, "bonus_total": bonus},
                saida={"valor_final": valor_final},
                logica=f"Valor final = Comissão proporcional (R$ {valor_comissao_proporcional:.2f}) + Bônus (R$ {bonus:.2f})",
                condicao="Cálculo concluído com sucesso"
            )

        resultado = ResultadoComissionamentoDetalhado(
            matricula=func.matricula,
            cod_loja=func.cod_loja,
            cod_marca=func.cod_marca,
            base_vendas=base_vendas,
            perc_comissao=perc,
            valor_comissao_bruto=valor_comissao_bruto,
            ajuste_proporcional=fator,
            bonus=bonus,
            valor_final=valor_final,
            etapas=coletor.obter_etapas() if coletor else []
        )
        
        resultados.append(resultado)

    return resultados

```
</details>

---

[[Voltar]](../README.md)
