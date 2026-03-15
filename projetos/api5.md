
## ✅ Projeto – *GeoMaps*
**Semestre:** Quinto Semestre – 2025-2  
**Empresa Parceira:** Visiona Tecnologia Espacial S.A | Professor Responsável: *Gérson*  

---

### 📌 Problema

Grande parte das propriedades rurais no Brasil não possui um endereço formal ou CEP definido, o que dificulta processos logísticos, entrega de serviços e registro de localizações exatas. Embora o Cadastro Ambiental Rural tenha avançado na regularização ambiental, ele não resolve a ausência de identificação territorial clara. Essa falta de endereçamento impacta o acesso a serviços públicos, limita ações governamentais e prejudica atividades comerciais e agrícolas que dependem da localização precisa de propriedades.

---

### ✅ Solução Desenvolvida

Um aplicativo móvel (Android/React Native) para endereçamento digital de imóveis do CAR, roteirização rural, registro colaborativo de condições de vias e exibição de alertas,visuaização das propriedades, multinível de usuários e painel do administrador.

---

### 🔗 Link do Repositório Git
- GitHub: [Acessar](https://github.com/Phoenix-Team-Fatec/geo-maps)

---

### 🧰 Tecnologias Utilizadas

| Tecnologia                                   | Onde foi utilizada                                                                 |
|---------------------------------------------|------------------------------------------------------------------------------------|
| **React Native (TypeScript/JavaScript)**    | Desenvolvimento do aplicativo móvel (telas de login, registro, mapa, perfil etc.) |
| **FastAPI**          | Criação das APIs de usuários, propriedades, plus codes, ocorrências e certificados |
| **Banco NoSQL (MongoDB)**           | Persistência de propriedades, ocorrências, usuários e histórico de plus code      |
| **APIs de Mapas e GPS (Map/Location)**      | Exibição de mapa, geolocalização, registro de propriedades e rotas                |
| **Weather API**                             | Consulta de clima para enriquecer alertas e ocorrências                           |
| **AWS**        | Plataforma de nuvem utilizada para hospedagem e deploy da aplicação web.            |
| **GitHub / Git Flow**                       | Versionamento, PRs, merges e organização do fluxo de desenvolvimento              |

---

### 👨‍💻 Contribuições Pessoais

Atuei como **Scrum Master**,e no desenvolvimento técnico (backend e mobile). Minhas contribuições podem ser divididas em **papel de processo** e **entregas técnicas**.

#### Como Scrum Master

- Condução de **cerimônias Scrum** (daily, planning, review e retrospectiva), mantendo foco em impedimentos e acompanhamento de Sprint Goals.  
- Apoio ao Product Owner na **organização e priorização do backlog**, decompondo épicos como: endereçamento digital (Plus Code), propriedades no mapa, ocorrências, rotas, alertas e modo offline.  
- Facilitação da **comunicação entre squads de backend e frontend**, reduzindo retrabalho em integrações.  
- Monitoramento da **velocidade do time**, ajuste de capacidade e acompanhamento de entregas entre Sprints.  
- Gestão de **Pull Requests e merges** principais, garantindo integração contínua das branches de feature com `develop` (protegi a branch master e develop, para que alterações fossem deitas nela era necessário ser revisadas e aceitas).

#### Como Desenvolvedor (Backend e Mobile)

- **Autenticação e rotas de usuário**  
  - Implementação e/ou integração das rotas de **registro e autenticação** (UserRegisterandAuthRoutes), com JWT.  
  - Ajustes de fluxo de login e telas estilizadas de autenticação no app.  

- **Funcionalidades administrativas e certificados**  
  - Desenvolvimento e merge da *feature/admin-functions* no backend.  
  - Implementação da geração de **certificados em PDF** (*feature/certificado_pdf*), incluindo merges e correções.  

- **Integração com Weather API e filtros de Plus Code**  
  - Implementação da *feature/weather-api* para obter dados meteorológicos e integrar aos cenários de alerta/ocorrência.  
  - Desenvolvimento da *feature/Filter_Pluscode_Router* para filtrar e roteirizar propriedades/endereços por Plus Code.  

- **Correções de ocorrências e estabilidade da API**  
  - Ajustes na *feature/fix-ocorrencia*, corrigindo problemas de registro/consulta de ocorrências.  

- **Desenvolvimento do app GeoMaps (frontend mobile)**  
  - Criação e ajustes nas **telas de login, cadastro e perfil** (`feature/register-screens`, `feature/profile-tab`, ajustes de login e atualização de informações).  
  - Implementação da lógica para **gerar Plus Code no mapa e por coordenadas**, bem como correções de add Plus Code.  
  - Funcionalidade para **listar propriedades do usuário e exibi-las no mapa**, incluindo cores e estados:  
    - `propriedade aparece no mapa`  
    - `Correções de add pluscode`  
  - Desenvolvimento de **alertas e rotas**:  
    - `feature/integrando_botao_alertas` (botão de alertas);  
    - `feature/Trancing_Routes` (traçado de rotas).  
  - Implementação e correções de **Plus Code no mapa e histórico** (`plus code no mapa`, `removendo plus code do mapa`, `Atualizando plus code e vendo histórico`).  
  - Entrega da **funcionalidade de mapa offline** (`feature/offline-map`) e correções de UI do mapa (`fix/map-ui`).  

- **Integração contínua e qualidade do código**  
  - Merge frequente de branches de feature para `develop` nos dois repositórios (backend e frontend), garantindo integração estável:  
    - PRs: `#1`, `#2`, `#5`, `#6`, `#7`, `#8`, `#9`, `#10`, `#11`, `#12`, `#13`, `#16`, `#19`, `#21`, `#22`, `#23`, `#24`, `#25`, `#27`, `#28` etc.  
  - Resolução de conflitos, ajuste de estrutura de pastas e refinamento de componentes conforme o projeto evoluía.

Alguns Commits 

- *Merge pull request #11 – develop*  
- *Merge pull request #10 – feature/admin-functions*  
- *Merge pull request #9 – develop*  
- *Merge pull request #8 – feature/weather-api*  
- *Merge pull request #7 – feature/Filter_Pluscode_Router*  
- *Merge pull request #6 – feature/fix-ocorrencia*  
- *Merge pull request #5 – feature/certificado_pdf*  
- *Merge pull request #2 – feature/certificado_pdf*  
- *Merge pull request #1 – feature/UserRegisterandAuthRoutes*  
- *Merge pull request #28 – develop*  
- *Merge pull request #27 – fix/map-ui*  
- *Merge pull request #25 – feature/offline-map*  
- *Merge pull request #24 – develop*  
- *Merge pull request #23 – feature/profile-tab*  
- *plus code no mapa* / *removendo plus code do mapa* / *Atualizando plus code e vendo histórico*  
- *Merge pull request #22 – feature/Trancing_Routes*  
- *Merge pull request #21 – feature/integrando_botao_alertas*  
- *Correções de add pluscode* / *gerar plus code no mapa e por coordenadas*  
- *propriedade aparece no mapa*  
- *Merge pull request #19, #16, #13, #12, #11, #9, #7, #2, #1 – feature/register-screens, feature/tela_login_estilizada, feature/pluscode-screen, feature/list_user_properties*  

Esses commits mostram tanto minha coordenação e integração de PRs quanto minha participação direta no **desenvolvimento técnico** do GeoMaps.

<details>

  
```
const getPlusCodePoint = (feature: any) => {
  const pc = feature?.pluscode;
  if (!pc) return null;
  const c = pc.cordinates ?? pc.coordinates; // backend pode mandar 'cordinates' ou 'coordinates'
  const lat = c?.latitude ?? c?.lat ?? c?.Latitude;
  const lng = c?.longitude ?? c?.lng ?? c?.Longitude;
  if (!Number.isFinite(lat) || !Number.isFinite(lng)) return null;
  return { latitude: Number(lat), longitude: Number(lng) };
};

...

 {!isNavigating && userProperties.map((feature, idx) => {
        const point = getPlusCodePoint(feature);
        if (!point) return null;

        // textos úteis para o tooltip
        const title = feature?.pluscode?.surname
          ? `Plus Code • ${feature.pluscode.surname}`
          : 'Plus Code';
        const description = feature?.pluscode?.pluscode_cod ?? '';

        return (
          <Marker
            key={`pluscode-${feature.id || idx}`}
            coordinate={point}
            title={title}
            description={description}
          >
            {/* Ícone customizado (bolinha com ícone) - opcional */}
            <View style={{
              backgroundColor: '#10b981',
              borderRadius: 18,
              width: 36,
              height: 36,
              alignItems: 'center',
              justifyContent: 'center',
              borderWidth: 3,
              borderColor: '#FFF',
              shadowColor: '#000',
              shadowOffset: { width: 0, height: 2 },
              shadowOpacity: 0.3,
              shadowRadius: 4,
              elevation: 4,
            }}>
              <Ionicons name="add-circle" size={20} color="#fff" />
            </View>
          </Marker>
        );
      })}

```
</details>

---

[[Voltar]](../README.md)

