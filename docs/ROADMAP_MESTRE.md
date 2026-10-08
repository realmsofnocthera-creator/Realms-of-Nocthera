# Realms of Nocthera — Roadmap Mestre

**v2 · atualizado em 08/10/2026**

Reorganizado a partir do Roadmap Mestre de 06/10/2026 e da auditoria técnica de 08/10/2026.

> A ordem das etapas é uma PROPOSTA: o Yuri aprova ou muda. Etapas marcadas como NOVA foram adicionadas nesta versão. Os números entre parênteses são as fases do roadmap antigo. Nenhuma regra de jogo foi inventada: o que depende do Yuri está marcado como Decisão.

## Sumário

- [Como ler](#como-ler)
- [Onde estamos](#onde-estamos)
- [Visão geral das etapas](#visão-geral-das-etapas)
- [Etapa 0 — Fundação](#etapa-0-fundação)
- [Etapa 0.5 — Fundação técnica e segurança](#etapa-05-fundação-técnica-e-segurança)
- [Etapa 1 — Motor de combate completo](#etapa-1-motor-de-combate-completo)
- [Etapa 2 — Classes, subclasses e habilidades](#etapa-2-classes-subclasses-e-habilidades)
- [Etapa 3 — Itens e Equipamentos](#etapa-3-itens-e-equipamentos)
- [Etapa 3.5 — Painel do Mestre](#etapa-35-painel-do-mestre)
- [Etapa 4 — Mundo mínimo e economia base (Vertical Slice)](#etapa-4-mundo-mínimo-e-economia-base-vertical-slice)
- [Etapa 4.5 — UX/UI e Onboarding (tutorial)](#etapa-45-uxui-e-onboarding-tutorial)
- [Etapa 5 — Aprofundamento do PvE e Provações](#etapa-5-aprofundamento-do-pve-e-provações)
- [Etapa 6 — Retenção e meta-progressão](#etapa-6-retenção-e-meta-progressão)
- [Etapa 6.5 — Integridade e Anti-cheat](#etapa-65-integridade-e-anti-cheat)
- [Etapa 7 — Social e multiplayer](#etapa-7-social-e-multiplayer)
- [Etapa 8 — Mundo vivo e endgame](#etapa-8-mundo-vivo-e-endgame)
- [Etapa 8.5 — Monetização](#etapa-85-monetização)
- [Etapa 9 — Pré-lançamento](#etapa-9-pré-lançamento)
- [Trilha contínua](#trilha-contínua)
- [Decisões pendentes](#decisões-pendentes-do-yuri)
- [Apêndice A — Achados da auditoria](#apêndice-a--achados-da-auditoria-de-08102026)
- [Apêndice B — Mapa do roadmap antigo](#apêndice-b--mapa-do-roadmap-antigo-para-o-novo)

## Como ler

| Status | Significado |
| --- | --- |
| ✅ Feito | Feito |
| 🟡 Parcial | Parcial ou em andamento |
| ⬜ A fazer | Não feito |
| ⏸ Adiado | Adiado por decisão |
| ❓ Decisão | Depende de decisão do Yuri |

**Lógica da ordem**

- O motor de combate vem primeiro: itens, monstros, habilidades e PvP usam ou alimentam ele.
- Itens vêm antes de loot, lojas, crafting e comércio.
- Mundo (regiões, bestiário) vem antes de quests, caçadas, provações e dungeons.
- Social, PvP e mundo vivo só entram quando o jogo solo estiver sólido.
- NOVO — Segurança e integridade de dados vêm antes de qualquer conteúdo novo: a Etapa 0.5 corrige o que hoje permite forjar sessão, manipular combate e perder dados.
- NOVO — O Painel do Mestre vem antes do conteúdo em massa (bestiário de 30 a 50 criaturas, itens, lojas): conteúdo se ajusta sem deploy.
- NOVO — UX/UI e Onboarding entram logo após o Vertical Slice, quando já existe jogo ponta a ponta para testar com pessoas reais.
- NOVO — Anti-cheat avançado vem antes de qualquer sistema que mova valor entre jogadores (comércio, leilão, PvP). Monetização só depois da economia estável.
- NOVO — Performance é um orçamento contínuo; a otimização formal fica na Etapa 9, mas os ganhos baratos (imagens) entram já na 0.5.
- Cada etapa tem um portão de saída: a próxima só começa com o portão cumprido.

## Onde estamos

- **Feito:** Contas completas, perfil público, HUD/hub, criação de personagem, ficha, tela de Desenvolvimento, Diamantes (servidor), dados e desbloqueio das subclasses (servidor), combate automático 1x1 com 7 elementos e vitrine de Provações.
- **Auditoria:** Auditoria técnica de 08/10/2026: 28 arquivos e 269 testes passando; tsc e ESLint sem erros. Porém foram encontrados 5 pontos críticos (sessão forjável, semente de combate controlada pelo cliente, persistência que perde dados, dependência com vulnerabilidade crítica, login sem rate limit). Detalhes no Apêndice A.
- **Agora:** Próximo passo proposto: Etapa 0.5 (Fundação técnica e segurança). Depois, retomar a Etapa 1 na Ordem 46B.

## Visão geral das etapas

| Etapa | Nome | Status | Portão de saída |
| --- | --- | --- | --- |
| 0 | Fundação _(concluída)_ | ✅ Feito | — |
| 0.5 | Fundação técnica e segurança _(NOVA · próxima)_ | ⬜ A fazer | Testes de regressão para A1, B1, C1 e C2; npm audit sem críticos ou altos nas dependências de produção (ou exceção documentada); build de produção sem flags de ignorar erro; CI verde; decisões A2 e B2 tomadas; snapshot do combate idêntico. |
| 1 | Motor de combate completo _(em andamento)_ | 🟡 Parcial | Snapshot idêntico em cada ordem de refatoração; build e testes limpos; habilidades de subclasse e bônus de equipamento entrando só pelo registro e pela ficha de combate; decisões de 1.2 a 1.8 fechadas. |
| 2 | Classes, subclasses e habilidades | 🟡 Parcial | Kits das 12 subclasses funcionando no motor, troca de habilidade testada, testes limpos. |
| 3 | Itens e Equipamentos | ⬜ A fazer | Equipar e desequipar muda o combate só pela ficha de combate, sem alterar o motor. |
| 3.5 | Painel do Mestre _(NOVA)_ | ⬜ A fazer | Nenhuma rota administrativa acessível sem papel verificado no servidor, com testes de autorização; toda alteração gera log; rollback de conteúdo testado; um monstro novo criado pelo painel aparece no combate sem deploy. |
| 4 | Mundo mínimo e economia base (Vertical Slice) | ⬜ A fazer | Marco Vertical Slice (45): conta, personagem, combate, uma região, loot, inventário, equipamento e de 3 a 5 monstros funcionando de ponta a ponta. |
| 4.5 | UX/UI e Onboarding (tutorial) _(NOVA)_ | ⬜ A fazer | Um jogador novo, em teste com 5 a 8 pessoas reais, chega ao primeiro combate sem ajuda externa; telas principais validadas em celular; nenhum problema crítico de acessibilidade em aberto. |
| 5 | Aprofundamento do PvE e Provações | ⬜ A fazer | Painel já operando (3.5); quests, caçadas e dungeons solo jogáveis; cada provação liberada valida nível no servidor. |
| 6 | Retenção e meta-progressão | ⬜ A fazer | — |
| 6.5 | Integridade e Anti-cheat _(NOVA)_ | ⬜ A fazer | Nenhum fluxo que mova valor sem transação atômica, ledger e idempotência; testes adversariais verdes; alertas visíveis no Painel do Mestre. |
| 7 | Social e multiplayer | ⬜ A fazer | — |
| 8 | Mundo vivo e endgame | ⬜ A fazer | — |
| 8.5 | Monetização _(NOVA)_ | ⬜ A fazer | Compra ponta a ponta em sandbox com estorno funcionando; ledger confere; termos e privacidade publicados; nenhum produto vendido que quebre a linha de justiça definida. |
| 9 | Pré-lançamento | ⬜ A fazer | Orçamentos de desempenho cumpridos, teste de carga aprovado, backup restaurado com sucesso em ensaio, Analytics coletando com consentimento, termos publicados e Beta fechado concluído. |

## Etapa 0 — Fundação

**Status da etapa:** ✅ Feito · concluída

Identidade, regras base, arquitetura, contas, perfil, raças, classes, criação de personagem, Desenvolvimento, HUD e o primeiro combate automático.

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ✅ Feito | 0.1 | **Identidade** — nome, tema visual, direção artística, ambientação, gênero, plataformas, mobile-first (0) |
| ✅ Feito | 0.2 | **Regras base** — nível máximo 30 no Grau 1, XP, 7 atributos, HP, Mana, Sobreescudo, dano, defesa, velocidade, morte (0). Decididos: sem Stamina, sem crítico, sem esquiva. |
| ✅ Feito | 0.3 | **Arquitetura** — web, backend, API, autenticação, validação server-side, persistência; banco com jogadores, personagens, raças, classes, atributos, monstros, combates e transações (1) |
| ✅ Feito | 0.4 | **Contas** — cadastro, login, logout, sessões, ID único, recuperação de senha, verificação de e-mail (2). Atenção: ver Etapa 0.5 (A2), pois recuperação e verificação dependem do Firebase Auth no cliente. |
| ✅ Feito | 0.5 | **Perfil** — nome de usuário único globalmente, avatar por classe, perfil público (2) |
| ✅ Feito | 0.6 | **6 raças completas** — com ativas cadastradas só como dado (3) |
| ✅ Feito | 0.7 | **6 classes** — com progressão automática (4) |
| ✅ Feito | 0.8 | **Criação de personagem em 5 etapas** — ficha redesenhada, ícones de habilidade com balão, lupa de atributos (5) |
| ✅ Feito | 0.9 | **Tela de Desenvolvimento** — distribuição de pontos e reset (100 diamantes) no servidor; moeda Diamantes só no servidor (5, 6) |
| ✅ Feito | 0.10 | **HUD/hub** — navegação, responsividade, vitrine de Provações (1) |
| ✅ Feito | 0.11 | **Combate automático 1x1** — iniciativa, turnos, dano, defesa, Sobreescudo, vitória, derrota, morte, XP, ouro, level up, battle log (8, 9) |
| ✅ Feito | 0.12 | **Elementos** — 7 elementos integrados ao combate (Ordem 22) |
| 🟡 Parcial | 0.13 | **Tela /menu** — 9 cards de vitrine (Conquistas, Coleção, Buscar, Produção, Mochila, Resgate, Ranking, Check-in, Anúncios): confirmar que a Ordem 27 foi concluída |

## Etapa 0.5 — Fundação técnica e segurança

**Status da etapa:** ⬜ A fazer · NOVA · próxima

Corrige os pontos críticos encontrados na auditoria antes de acrescentar conteúdo. Não muda regras de jogo nem o motor de combate (o teste de fotografia continua valendo). Prioridades: P0 = bloqueia qualquer abertura ao público; P1 = fazer nesta etapa; P2 = pode acompanhar a etapa.

### A. Sessão e conta

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer **P0** | 0.5-A1 | **Sessão forjável** — hoje o segredo da assinatura cai num valor padrão derivado de projectId e appId, ambos públicos em firebase-applet-config.json, e o token não expira (src/server/auth.ts). Exigir SESSION_SECRET (a aplicação não sobe sem ele em produção), verificar expiração (exp), permitir rotação do segredo. Critério: teste prova que um token assinado com o segredo antigo é rejeitado. |
| ❓ Decisão **P0** | 0.5-A2 | **Unificar a autenticação** — hoje coexistem o Firebase Auth no cliente (e-mail e Google) e um login próprio com senha no Firestore (src/app/api/auth/email/route.ts). Escolher um e remover o outro, migrando contas. Recuperação de senha e verificação de e-mail só existem no Firebase Auth. |
| ⬜ A fazer **P1** | 0.5-A3 | **Rate limiting** — login, cadastro e rotas que escrevem (por IP e por conta), com bloqueio progressivo e resposta 429. |
| ⬜ A fazer **P1** | 0.5-A4 | **Política de senha e sessão revogável** — mínimo de 6 caracteres hoje; mensagens que não revelem se o e-mail existe; logout que invalida a sessão no servidor. |
| ⬜ A fazer **P2** | 0.5-A5 | **Limpeza de superfície** — passwordHash fora de documentos legíveis pelo dono (regra get de users); atalho test-token isolado em helper de teste, fora do código de produção. |

### B. Integridade do combate

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer **P0** | 0.5-B1 | **Semente gerada no servidor** — src/app/api/combat/start/route.ts aceita seed do corpo da requisição e o combate é determinístico por semente: quem chama a API escolhe uma semente vencedora. Ignorar seed do cliente em produção e gravar a semente no log do combate (auditoria e replay). |
| ❓ Decisão **P0** | 0.5-B2 | **Limite provisório de batalhas** — hoje não há cooldown, custo ou teto: dá para farmar XP e ouro sem limite. Definir um limite mínimo provisório até a regra de recursos (1.7) existir. Valor decidido pelo Yuri. |
| ⬜ A fazer **P1** | 0.5-B3 | **Idempotência do resultado** — id de combate único para impedir aplicação dupla de XP e ouro em reenvios. |

### C. Persistência e dados

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer **P0** | 0.5-C1 | **Firestore como fonte única** — memoryStore e memoryUsers só existem em testes; em produção, falha de gravação vira erro para o cliente, nunca sucesso silencioso (hoje o cadastro responde 201 mesmo se a gravação falhar). |
| ⬜ A fazer **P0** | 0.5-C2 | **Transações no lugar do mutex** — o mutex por uid só vale em uma instância do servidor (dívida já listada). Usar transações do Firestore (ou controle por versão) em combate, distribuição de pontos, Diamantes, ouro e subclasse. |
| ⬜ A fazer **P1** | 0.5-C3 | **Unicidade de nome por índice** — hoje a checagem e a busca por nome leem a coleção characters inteira (select nome) em characterService.ts: custo O(n) e sujeito a corrida. Criar documento-índice nomes/{nomeNormalizado} gravado em transação. |
| ⬜ A fazer **P1** | 0.5-C4 | **Falhas observáveis** — logs estruturados, timeout e retry controlados nas operações do Firestore (hoje só console.error). |
| ⬜ A fazer **P2** | 0.5-C5 | **Exportação agendada do Firestore** — primeira camada de backup, a rotina completa fecha na Etapa 9. |

### D. Build, dependências e qualidade

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer **P0** | 0.5-D1 | **Atualizar Next.js e dependências** — next 15.4.9 está marcado como deprecado por falha de segurança e o npm audit aponta severidade crítica; também há alertas altos em @grpc/grpc-js, postcss e sharp. Atualizar e rodar npm audit no CI. |
| ⬜ A fazer **P1** | 0.5-D2 | **Build que realmente valida** — remover ignoreBuildErrors e ignoreDuringBuilds de next.config.ts e provar o build de produção completo (dívida já listada). |
| ⬜ A fazer **P1** | 0.5-D3 | **Um gerenciador de pacotes** — package-lock.json está fora de sincronia (npm ci falha: faltam @vitest/coverage-v8 e outros) e existe bun.lock junto. Manter um só e ressincronizar. |
| ⬜ A fazer **P1** | 0.5-D4 | **CI no GitHub Actions** — npm ci, lint, tsc, test, build e audit em cada push e PR. Regra fixa do roadmap (build e test limpos) passa a ser automática. |
| ⬜ A fazer **P2** | 0.5-D5 | **Higiene do repositório** — tirar tsconfig.tsbuildinfo e scripts/next.bin.bak do git e ajustar o .gitignore; padronizar imports (@/); atualizar a árvore do README; remover @google/genai se continuar sem uso. |
| ⬜ A fazer **P2** | 0.5-D6 | **Headers de segurança** — CSP, HSTS e afins em next.config.ts; revisar allowedDevOrigins. |

### E. Ganhos rápidos de performance

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer **P1** | 0.5-E1 | **Comprimir imagens** — public/ pesa cerca de 69 MB e 51 arquivos passam de 500 KB (ícones de habilidade chegam a ~1,9 MB). Converter para WebP/AVIF e redimensionar ao tamanho de uso (dívida já listada). |
| ⬜ A fazer **P2** | 0.5-E2 | **Duplicatas e next/image** — 22 ícones existem em src/assets/icons e em public/icons; há cerca de 48 usos de img e nenhum de next/image. |

**Portão de saída:** Testes de regressão para A1, B1, C1 e C2; npm audit sem críticos ou altos nas dependências de produção (ou exceção documentada); build de produção sem flags de ignorar erro; CI verde; decisões A2 e B2 tomadas; snapshot do combate idêntico.

## Etapa 1 — Motor de combate completo

**Status da etapa:** 🟡 Parcial · em andamento

Base de todo o resto. As 6 classes antigas continuam no combat.ts; o que for novo (subclasses, equipamento, raciais ativas) entra por um registro de habilidades e por uma ficha de combate pronta.

### 1.1 Motor: rede de segurança e registro de habilidades (Ordens 45 a 48)

| Status | ID | Item |
| --- | --- | --- |
| ✅ Feito | 1.1.1 | **Ordens 45, 45b e 46A** — teste de fotografia (540 lutas e um caso com Sobreescudo), helpers genéricos em src/game/combate/efeitos.ts, 12 testes de equivalência |
| 🟡 Parcial | 1.1.2 | **Ordem 46B (só leitura)** — grafo de imports entre index.ts e combat.ts e auditoria dos números das skills contra o canônico |
| ⬜ A fazer | 1.1.3 | **Ordem 47** — interface comum de habilidade e registro em src/game/combate/, consultado só quando o espaço tem habilidade de subclasse |
| ⬜ A fazer | 1.1.4 | **Ordem 48** — Berserker e Colosso como piloto no registro |
| ⬜ A fazer | 1.1.5 | **Ficha de combate** — raça, classe, subclasse e equipamento preenchem a ficha, junto da Etapa 3 |
| ⏸ Adiado | 1.1.6 | **Migrar as 6 classes antigas para fora do combat.ts** — decidido não migrar agora; só se virar problema real (o arquivo tem cerca de 3.000 linhas) |

### 1.2 Catálogo de bônus e regra de soma

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 1.2.1 | **Tipos de bônus fixo** — lista do que o motor entende (+atributo, +% dano, +% mitigação, +% HP máx, +% ignorar defesa, resistências etc.) |
| ❓ Decisão | 1.2.2 | **Regra de soma** — proposta: aditiva, igual aos elementos |

### 1.3 Tipos de dano

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 1.3.1 | **Subtipos físicos** — Impacto, Cortante, Perfurante (proposta: +40/−40 como nos elementos) |
| ❓ Decisão | 1.3.2 | **Categoria de corpo nos monstros** — blindado, rocha, sem armadura, escamoso, blindagem média |
| ❓ Decisão | 1.3.3 | **Campo de tipo de dano no atacante** — vazio até existir arma |

### 1.4 Resistências

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 1.4.1 | **Resistências raciais** — Anão, Elfo, Orc, Vampiro (confirmar se é dano recebido ou resistência a status) |
| ❓ Decisão | 1.4.2 | **Passiva Resistência Ancestral do Anão** |
| ❓ Decisão | 1.4.3 | **Resistência a status** — proposta: reduz a chance de ativação |

### 1.5 Elementos

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 1.5.1 | **Preencher elementoAtaque nos monstros** — hoje nenhum tem |
| ⬜ A fazer | 1.5.2 | **Feiticeiro sem elemento por enquanto** — decisão futura |

### 1.6 Efeitos de status

| Status | ID | Item |
| --- | --- | --- |
| 🟡 Parcial | 1.6.1 | **Bloco B** — Sangramento, Veneno, Podridão Escarlate: implementado na Ordem 23; confirmar fechamento |
| ⬜ A fazer | 1.6.2 | **Bloco C** — Congelamento, Sono, Loucura, Paralisia, Maldição (alteram o fluxo do turno e interagem com o ataque duplo por Agilidade) |
| ❓ Decisão | 1.6.3 | **Imunidade de chefes a status** |
| ❓ Decisão | 1.6.4 | **Quem aplica status** — só monstros ou também skills de jogador |
| ❓ Decisão | 1.6.5 | **Queimadura** — estava no roadmap antigo, mas não consta nos efeitos canônicos; não incluída até confirmação |

### 1.7 Recursos

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 1.7.1 | **Regeneração de Mana durante e depois do combate** — valores a definir |
| ❓ Decisão | 1.7.2 | **Recuperação de Sobreescudo** |
| ⬜ A fazer | 1.7.3 | **Regeneração fora de combate (5)** |
| ⬜ A fazer | 1.7.4 | **Passiva Herança Arcana do Elfo** — depende da regeneração de Mana |

### 1.8 Habilidades raciais ativas

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 1.8.1 | **As 6 ativas** — Instinto de Sobrevivência, Fúria da Forja, Graça de Alfheim, Fúria Orc, Drenar Sangue, Sopro Dracônico: hoje só dado; precisam de regra de disparo automático, custo de Mana e recarga |

### 1.9 Prioridade de combate (8)

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 1.9.1 | **Buff e debuff formais** — status, resistências e fraquezas como condição |
| ⏸ Adiado | 1.9.2 | **Quantidade de inimigos** — o combate segue 1x1 |

### 1.10 Pendências de skills

| Status | ID | Item |
| --- | --- | --- |
| ✅ Feito | 1.10.1 | **Ira do Bárbaro** — resolvida pelo Yuri: vale o que está no código (+30% dano; abaixo de 30% HP, +50% dano e For +9, Vig +5, Vit +5). Nenhuma correção necessária. |
| ❓ Decisão | 1.10.2 | **Regra de acúmulo de bônus temporários** — entre classe, subclasse e raça |
| ⬜ A fazer | 1.10.3 | **Bônus temporários do Milagre Divino** |
| ⏸ Adiado | 1.10.4 | **Transferência de dano do Juramento do Guardião** — só faz sentido com grupo |

### 1.11 Finalização

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 1.11.1 | **Empate** |
| ⬜ A fazer | 1.11.2 | **Gancho de loot** — fecha na Etapa 3 |

**Portão de saída:** Snapshot idêntico em cada ordem de refatoração; build e testes limpos; habilidades de subclasse e bônus de equipamento entrando só pelo registro e pela ficha de combate; decisões de 1.2 a 1.8 fechadas.

## Etapa 2 — Classes, subclasses e habilidades

**Status da etapa:** 🟡 Parcial

### 2.1 Subclasses (Especialização, 4)

| Status | ID | Item |
| --- | --- | --- |
| ✅ Feito | 2.1.1 | **12 subclasses aprovadas** — divisão fixa dos 40 pontos, dados e funções puras, desbloqueio e troca no servidor (travados por fragmentos de alma) |
| ✅ Feito | 2.1.2 | **Modelo de habilidades equipadas por espaço** — Ordem 42 |
| 🟡 Parcial | 2.1.3 | **Kits** — Bárbaro aprovado (Berserker e Colosso); as outras 5 classes, uma por vez |
| ❓ Decisão | 2.1.4 | **Tiers 1 a 4 no motor** — passiva, básico, especial, ultimate; custo em fragmentos por tier |
| ⬜ A fazer | 2.1.5 | **Tela de Subclasse** — e troca de habilidade por espaço |
| ⬜ A fazer | 2.1.6 | **Fonte dos fragmentos de alma** — batalha sangrenta: é conteúdo, entra na Etapa 5 |

### 2.2 Habilidades (7)

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 2.2.1 | **Melhorar nível de habilidade e ascensão** — botões travados no Desenvolvimento |
| ❓ Decisão | 2.2.2 | **Pontos de habilidade (6)** |
| ⬜ A fazer | 2.2.3 | **Debuff, defensiva formal, evolução** |
| ❓ Decisão | 2.2.4 | **Invocação** — ainda não definida se existirá |
| ⏸ Adiado | 2.2.5 | **Alcance e Área** — só fazem sentido com grupo |

### 2.3 Outros

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 2.3.1 | **Compatibilidade raça × classe (3)** |
| ⬜ A fazer | 2.3.2 | **Aparência e História do personagem (5)** — baixa prioridade, pode entrar a qualquer momento |
| ❓ Decisão | 2.3.3 | **Novas classes** — meta de 8 a 10 (temos 6): só depois das subclasses estáveis |

**Portão de saída:** Kits das 12 subclasses funcionando no motor, troca de habilidade testada, testes limpos.

## Etapa 3 — Itens e Equipamentos

**Status da etapa:** ⬜ A fazer

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 3.1 | **Catálogo de itens base no banco (1)** |
| ⬜ A fazer | 3.2 | **Inventário (12)** — ativa o card Mochila do Menu |
| ❓ Decisão | 3.3 | **Equipamentos (11)** — CANÔNICO: itens dão só atributos e bônus fixos. Pendentes: raridade e multiplicadores, quantidade de slots, 3 a 5 itens de teste |
| ⬜ A fazer | 3.4 | **Tipos de arma** — preenchendo o subtipo de dano físico (liga com 1.3) |
| ⬜ A fazer | 3.5 | **Loot e drops dos monstros, além do ouro (9, 10)** |
| ⬜ A fazer | 3.6 | **Destravar Equipamentos e Alma na ficha** — e Equipamentos no perfil público |

**Portão de saída:** Equipar e desequipar muda o combate só pela ficha de combate, sem alterar o motor.

## Etapa 3.5 — Painel do Mestre

**Status da etapa:** ⬜ A fazer · NOVA

Permite ao Yuri e aos Mestres ajustar o jogo sem mexer em código: adicionar, editar, remover e desativar conteúdo, e administrar jogadores. Hoje monstros, raças, classes e kits moram em src/rules/*.ts, então qualquer ajuste exige deploy. Depende da Etapa 0.5 (autenticação segura) e da Etapa 3 (catálogo de itens). Absorve o item «Painel administrativo mínimo» (39) e os logs administrativos (38), antes previstos na Etapa 5.

### 3.5.1 Acesso e papéis

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 3.5.1.1 | **Papéis (RBAC)** — Dono, Mestre, Moderador e Suporte (somente leitura), definidos por custom claims do Firebase. |
| ⬜ A fazer | 3.5.1.2 | **Autorização sempre no servidor** — rota /mestre e todas as APIs administrativas validam o papel no servidor; esconder botão não conta como proteção. |
| ⬜ A fazer | 3.5.1.3 | **Segundo fator para papéis administrativos** — e sessão administrativa curta. |

### 3.5.2 Camada de conteúdo editável

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 3.5.2.1 | **O que migrar de código para banco** — proposta: monstros e itens primeiro; raças, classes e kits ficam em código por enquanto, protegidos pelo teste de fotografia. |
| ⬜ A fazer | 3.5.2.2 | **Conteúdo com versão** — schema validado, rascunho → publicado, histórico e rollback, cache curto no servidor. |
| ⬜ A fazer | 3.5.2.3 | **Simulador antes de publicar** — rodar N lutas de um monstro novo contra níveis e classes e mostrar taxa de vitória e duração. |

### 3.5.3 CRUD de conteúdo

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 3.5.3.1 | **Monstros** — adicionar, editar, duplicar, desativar e remover (exclusão lógica); campos de elemento, corpo e resistências quando existirem. |
| ⬜ A fazer | 3.5.3.2 | **Itens, tabelas de drop e lojas** — entram junto com a Etapa 3 e a economia da Etapa 4. |
| ⬜ A fazer | 3.5.3.3 | **Regiões, NPCs, quests, provações** — entram conforme as etapas correspondentes. |
| ⬜ A fazer | 3.5.3.4 | **Anúncios e eventos agendados** — alimenta o card Anúncios do Menu e prepara as Etapas 6 e 8. |

### 3.5.4 Gestão de jogadores

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 3.5.4.1 | **Busca e visualização** — por nome, uid ou e-mail; ficha completa e histórico de transações. |
| ⬜ A fazer | 3.5.4.2 | **Ajustes com motivo obrigatório** — ouro, Diamantes, XP, fragmentos de alma; conceder ou remover item; resetar personagem. |
| ⬜ A fazer | 3.5.4.3 | **Sanções** — advertir, suspender com prazo, banir e desbanir. |
| ⬜ A fazer | 3.5.4.4 | **Exclusão de conta e exportação de dados** — base para atender LGPD (liga com 9.4). |

### 3.5.5 Auditoria e operação

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 3.5.5.1 | **Log administrativo imutável (38)** — quem, o quê, antes e depois, motivo, quando e IP; nenhuma ação sem registro. |
| ⬜ A fazer | 3.5.5.2 | **Feature flags e modo manutenção** — ligar e desligar sistemas sem deploy. |
| ⬜ A fazer | 3.5.5.3 | **Dashboard operacional** — usuários ativos, economia (ouro e Diamantes criados e removidos), erros e fila de revisões; alimentado por 9.1. |
| ❓ Decisão | 3.5.5.4 | **Sistema de Mestres (40)** — canal manual de WhatsApp com código de vínculo: permanece na Etapa 8, a menos que o Yuri queira antecipar. |

**Portão de saída:** Nenhuma rota administrativa acessível sem papel verificado no servidor, com testes de autorização; toda alteração gera log; rollback de conteúdo testado; um monstro novo criado pelo painel aparece no combate sem deploy.

## Etapa 4 — Mundo mínimo e economia base (Vertical Slice)

**Status da etapa:** ⬜ A fazer

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 4.1 | **Lore geográfica antes das regiões** — Cosmologia, Continentes, Reinos, Facções, Grandes conflitos, Eventos históricos (0). O Yuri define; nada será inventado. |
| ⬜ A fazer | 4.2 | **Regiões (15)** |
| ⬜ A fazer | 4.3 | **Bestiário de 30 a 50 criaturas** — com lore, região, resistências, fraquezas, elementos e comportamento (10); rebalancear o Cavaleiro do Vazio. Cadastrado pelo Painel do Mestre (3.5). |
| ⬜ A fazer | 4.4 | **Spawn, respawn, monstros raros e elites (10)** |
| ⬜ A fazer | 4.5 | **NPCs (17)** |
| ⬜ A fazer | 4.6 | **Economia base** — lojas NPC e balanceamento de ouro (14); ativa o botão Loja do Hub |
| ⬜ A fazer | 4.7 | **Banco e armazenamento (13)** |
| ⬜ A fazer | 4.8 | **Farm completo (21)** — escolher região ou atividade, repetição, resultado acumulado |
| ⬜ A fazer | 4.9 | **Exploração e XP de exploração (16, 6)** |

**Portão de saída:** Marco Vertical Slice (45): conta, personagem, combate, uma região, loot, inventário, equipamento e de 3 a 5 monstros funcionando de ponta a ponta.

## Etapa 4.5 — UX/UI e Onboarding (tutorial)

**Status da etapa:** ⬜ A fazer · NOVA

Com o Vertical Slice pronto, existe jogo de ponta a ponta para testar com pessoas reais. Esta etapa revisa a experiência e cria o primeiro contato do jogador (FTUE).

### 4.5.1 UX/UI

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 4.5-U1 | **Auditoria heurística** — login, criação, hub, ficha, Desenvolvimento, combate, Provações e Menu; mapa de navegação e lista de atritos. |
| ⬜ A fazer | 4.5-U2 | **Design system** — tokens (src/theme/theme.ts), componentes base (botão, modal, balão, cartão, barras de HP, Mana e Sobreescudo) e estados padrão: vazio, carregando, erro e travado. |
| ⬜ A fazer | 4.5-U3 | **Mobile-first de verdade** — teste em aparelhos reais Android e iOS, áreas de toque de pelo menos 44 px, safe areas, rotação. Versão desktop (pendência da Trilha) com layout a decidir. |
| ⬜ A fazer | 4.5-U4 | **Acessibilidade** — contraste, foco por teclado, textos alternativos, respeito a prefers-reduced-motion e não depender só de cor (elementos e status). |
| ⬜ A fazer | 4.5-U5 | **Feedback de combate** — battle log legível, barras animadas, resumo pós-combate, XP e ouro em destaque. |
| ⬜ A fazer | 4.5-U6 | **Bloqueios explicados** — botões travados do Hub e do Menu dizem o que falta (nível ou sistema) em vez de ficarem mortos. |
| ❓ Decisão | 4.5-U7 | **Textos e idiomas** — revisão de pt-BR, glossário (Sobreescudo, Fragmentos de Alma etc.) e se o inglês entra no futuro (prepara i18n). |
| ⬜ A fazer | 4.5-U8 | **Pendências de identidade** — Logo, Público-alvo e ícones das linhagens do Draconiano (SVGs provisórios). |

### 4.5.2 Onboarding (tutorial)

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 4.5-O1 | **Fluxo do primeiro acesso** — cadastro → criação → primeiro combate guiado → primeira distribuição de pontos → primeira recompensa. Métrica: tempo até o primeiro combate. |
| ⬜ A fazer | 4.5-O2 | **Tutorial contextual** — dicas na primeira vez de cada tela ou sistema (atributos, habilidades, subclasse, itens quando existirem); pode pular e reabrir pelo Menu; progresso salvo no servidor. |
| ❓ Decisão | 4.5-O3 | **Missões de boas-vindas** — checklist inicial e recompensa (valores decididos pelo Yuri). |
| ⬜ A fazer | 4.5-O4 | **Ajuda e feedback** — glossário in-game, FAQ e botão de enviar feedback ou relatar problema. |
| ⬜ A fazer | 4.5-O5 | **Instrumentação do funil** — eventos mínimos de onboarding, que alimentam o Analytics completo (9.1). |

**Portão de saída:** Um jogador novo, em teste com 5 a 8 pessoas reais, chega ao primeiro combate sem ajuda externa; telas principais validadas em celular; nenhum problema crítico de acessibilidade em aberto.

## Etapa 5 — Aprofundamento do PvE e Provações

**Status da etapa:** ⬜ A fazer

### 5.1 Conteúdo PvE

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 5.1.1 | **Quests e XP de quests (18, 6)** |
| ⬜ A fazer | 5.1.2 | **Caçadas (22)** |
| ⬜ A fazer | 5.1.3 | **Profissões e XP de profissões (19, 6)** — depois Crafting (20); ativa o card Produção |
| ⬜ A fazer | 5.1.4 | **Dungeons em versão solo (23)** — versão em grupo só com a Etapa 7 |
| ⬜ A fazer | 5.1.5 | **Bosses regionais e batalha sangrenta** — fragmentos de alma |
| ⏸ Adiado | 5.1.6 | **Maestrias (4)** — retomar aqui, pois dependem de categorias de arma e tipos de monstro. Conceito decidido: 100 níveis por trilha, marcos a cada 10. |
| ⬜ A fazer | 5.1.7 | **Árvore de habilidades, sinergias e combos (7)** — ampliação dos builds |
| ✅ Feito | 5.1.8 | **Painel administrativo mínimo e logs administrativos (39, 38)** — movidos para a Etapa 3.5 |

### 5.2 Provações

| Status | ID | Item |
| --- | --- | --- |
| 🟡 Parcial | 5.2.1 | **Vitrine de Provações** — tela /provacoes com 7 provações e nível requerido (src/rules/provacoes.ts); ainda sem regras de jogo. |
| ⬜ A fazer | 5.2.2 | **Entrada validada no servidor** — o nível requerido é conferido no servidor ao iniciar qualquer provação, não só na tela. |
| ⬜ A fazer | 5.2.3 | **Recompensas e limites por provação** — ligados à economia (Etapa 4) e ao anti-cheat (6.5). |

### Mapa das 7 Provações

| Provação | Nível | Depende de | Etapa |
| --- | --- | --- | --- |
| Provação da Caçada | 2 | Caçadas (22) + regiões e bestiário (Etapa 4) | Etapa 5 |
| Provação da Torre Celestial | 5 | Formato ainda não definido no roadmap | Decisão do Yuri |
| Provação do Guerreiro | 12 | Formato ainda não definido no roadmap | Decisão do Yuri |
| Provação de Dungeons | 15 | Dungeons solo (23); em grupo na Etapa 7 | Etapa 5 |
| Provação de Chefe Mundial | 18 | World State (29) e World Bosses (30) | Etapa 8 |
| Provação de Batalha Sangrenta | 20 | Fragmentos de alma e bosses (Etapa 2.1) | Etapa 5 |
| Teste de Equipe | 25 | Party (24) e combate em grupo | Etapa 7 |

**Portão de saída:** Painel já operando (3.5); quests, caçadas e dungeons solo jogáveis; cada provação liberada valida nível no servidor.

## Etapa 6 — Retenção e meta-progressão

**Status da etapa:** ⬜ A fazer

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 6.1 | **Conquistas e Títulos (33, 2, 6)** — hoje só placeholders travados; ativa o card Conquistas |
| ⬜ A fazer | 6.2 | **Molduras e títulos do perfil** — listas vazias hoje |
| ⬜ A fazer | 6.3 | **Sistema diário e semanal (34)** — inclui Check-in e Resgate |
| ⬜ A fazer | 6.4 | **Eventos aleatórios (35)** |
| ⬜ A fazer | 6.5 | **Notificações (41)** |
| ❓ Decisão | 6.6 | **Como o jogador obtém Diamantes** — liga com a Monetização (8.5) |

> Os botões travados do Hub e as vitrines do Menu são destravados quando o sistema correspondente existir.

## Etapa 6.5 — Integridade e Anti-cheat

**Status da etapa:** ⬜ A fazer · NOVA

O princípio «servidor é a fonte da verdade» já existe; esta etapa o torna verificável e acrescenta detecção. É pré-requisito para comércio, leilão e PvP, porque a partir dali um exploit afeta outros jogadores. A parte de rate limiting e sessão avançada (37), antes prevista «até a Etapa 5», fecha aqui no mais tardar, e o básico já está na 0.5.

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 6.5-1 | **Modelo de ameaças documentado** — duplicação de itens, bots de farm, multiconta, automação de requisições, corridas de concorrência, manipulação de semente e relógio, abuso de estorno. |
| ⬜ A fazer | 6.5-2 | **Idempotência e atomicidade em tudo que move valor** — ouro, Diamantes, itens, XP e fragmentos. |
| ⬜ A fazer | 6.5-3 | **Ledger da economia** — toda mudança vira transação imutável com saldo antes e depois; reconciliação periódica (soma do ledger igual ao saldo). |
| ⬜ A fazer | 6.5-4 | **Detecção de anomalias** — XP e ouro por hora acima do teto, regularidade inumana de ações, picos por IP ou dispositivo; pontuação de risco e fila de revisão no Painel do Mestre. |
| ❓ Decisão | 6.5-5 | **Anti-bot** — Firebase App Check ou reCAPTCHA em cadastro e ações sensíveis; escolha da ferramenta a decidir. |
| ⬜ A fazer | 6.5-6 | **Multiconta e fraude** — limites por IP e dispositivo respeitando a LGPD; e-mail verificado obrigatório para comércio. |
| ⬜ A fazer | 6.5-7 | **Sanções e apelação** — aviso, suspensão, banimento e limite silencioso; tudo auditado no log administrativo. |
| ⬜ A fazer | 6.5-8 | **Testes adversariais no CI** — token forjado, replay, requisições concorrentes, payload manipulado. |
| ⬜ A fazer | 6.5-9 | **Preparação para PvP e comércio** — resultado de PvP só no servidor com semente do servidor, detecção de win-trading, limites e período de segurança em transferências. |

**Portão de saída:** Nenhum fluxo que mova valor sem transação atômica, ledger e idempotência; testes adversariais verdes; alertas visíveis no Painel do Mestre.

## Etapa 7 — Social e multiplayer

**Status da etapa:** ⬜ A fazer

Ordem sugerida: Social, comércio, Guildas, Party, PvP.

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 7.1 | **Sistema social (25)** — ativa Buscar e Ranking |
| ⬜ A fazer | 7.2 | **Mercado, comércio entre jogadores e leilão (14)** — só depois da Etapa 6.5 |
| ⬜ A fazer | 7.3 | **Guildas (26)** |
| ❓ Decisão | 7.4 | **Party (24)** — o combate hoje é 1x1; decidir se grupo muda essa regra antes de começar. Libera o Teste de Equipe. |
| ⬜ A fazer | 7.5 | **PvP (27)** — usa a ficha de combate nos dois lados |
| ❓ Decisão | 7.6 | **Ressurreição (0)** — só necessária com grupo e PvP |

> Antes de iniciar: reavaliar a base técnica (tempo real, instâncias, custo do Firestore) para grupos e PvP.

## Etapa 8 — Mundo vivo e endgame

**Status da etapa:** ⬜ A fazer

Ordem sugerida: World State primeiro, pois os demais dependem dele.

### Entregas

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 8.1 | **World State (29)** |
| ⬜ A fazer | 8.2 | **Eventos mundiais (31)** |
| ⬜ A fazer | 8.3 | **World Bosses (30)** — libera a Provação de Chefe Mundial |
| ⬜ A fazer | 8.4 | **Notícias do mundo (32)** |
| ⬜ A fazer | 8.5 | **Política e guerras (28)** |
| ⬜ A fazer | 8.6 | **Sistema de Mestres (40)** — ligado ao canal manual de WhatsApp com código de vínculo; pode subir de etapa se for operado só à mão |
| ⬜ A fazer | 8.7 | **Endgame (36) e Grau 2** — nunca assumir que o nível 30 é permanente |

## Etapa 8.5 — Monetização

**Status da etapa:** ⬜ A fazer · NOVA

Só começa com economia base estável (Etapa 4), anti-cheat (6.5) e Painel do Mestre (3.5). Todas as decisões de modelo e preços são do Yuri. Os itens jurídicos abaixo são uma lista de verificação, não parecer: validar com assessoria jurídica.

### 8.5.1 Modelo e produtos

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 8.5-1 | **Modelo de negócio** — gratuito com compras opcionais? Quais produtos: Diamantes, Passe de Batalha, cosméticos (molduras, títulos, avatares), conveniência. |
| ❓ Decisão | 8.5-2 | **Linha de justiça** — o que pode e o que não pode ser comprado se afetar poder de combate («pagar para vencer»). |
| ❓ Decisão | 8.5-3 | **Diamantes gratuitos** — como o jogador obtém Diamantes sem pagar (liga com a Etapa 6). |
| ❓ Decisão | 8.5-4 | **Catálogo e preços** — faixas de preço em reais; Loja e Passe de Batalha do Hub saem da vitrine. |

### 8.5.2 Pagamentos

| Status | ID | Item |
| --- | --- | --- |
| ❓ Decisão | 8.5-5 | **Gateway e métodos** — Pix e cartão; escolha do provedor e custos. |
| ⬜ A fazer | 8.5-6 | **Checkout no servidor** — webhooks assinados, idempotência, conciliação com o ledger (6.5), recibo. |
| ⬜ A fazer | 8.5-7 | **Reembolso e estorno** — estorno revoga o produto; tratamento de chargeback e abuso. |
| ⬜ A fazer | 8.5-8 | **Ambiente de teste** — compra ponta a ponta em sandbox antes de qualquer cobrança real. |

### 8.5.3 Passe de Batalha

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 8.5-9 | **Trilhas gratuita e premium por temporada** — XP do passe e recompensas; depende de Temporadas (9.8). |

### 8.5.4 Conformidade (validar com assessoria jurídica)

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 8.5-10 | **Termos de uso e política de privacidade** — LGPD: base legal, consentimento, direitos do titular. |
| ⬜ A fazer | 8.5-11 | **Direito do consumidor** — prazo de arrependimento, reembolso, comunicação de preços. |
| ❓ Decisão | 8.5-12 | **Regras de lojas de aplicativos** — caso publique em lojas: comissão e regras para moeda virtual. |
| ❓ Decisão | 8.5-13 | **Classificação indicativa e menores** — limites de gasto e consentimento parental, se aplicável. |
| ❓ Decisão | 8.5-14 | **Transparência de recompensas aleatórias** — se houver caixas ou sorteios pagos, divulgação de probabilidades. |

### 8.5.5 Métricas

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 8.5-15 | **Métricas de monetização** — conversão, receita por pagante, retenção de pagantes (alimenta 9.1). |

**Portão de saída:** Compra ponta a ponta em sandbox com estorno funcionando; ledger confere; termos e privacidade publicados; nenhum produto vendido que quebre a linha de justiça definida.

## Etapa 9 — Pré-lançamento

**Status da etapa:** ⬜ A fazer

### 9.1 Analytics (42)

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 9.1-1 | **Plano de medição** — perguntas de negócio → dicionário de eventos versionado (nomes e propriedades), sem dados pessoais nos eventos e uid pseudonimizado. |
| ❓ Decisão | 9.1-2 | **Ferramenta** — Firebase Analytics/GA4 com BigQuery, ou alternativa (ex.: PostHog); decisão e custo. |
| ⬜ A fazer | 9.1-3 | **Consentimento (LGPD)** — aviso, aceite e opção de recusar. |
| ⬜ A fazer | 9.1-4 | **Funis e retenção** — cadastro → personagem → primeiro combate; retorno em D1, D7 e D30; sessões e tempo de jogo. |
| ⬜ A fazer | 9.1-5 | **Telemetria de balanceamento** — taxa de vitória por monstro, nível, classe e raça; duração do combate; XP e ouro por hora. |
| ⬜ A fazer | 9.1-6 | **Economia** — fontes e sumidouros de ouro e Diamantes; sinais de inflação. |
| ⬜ A fazer | 9.1-7 | **Erros e observabilidade** — monitoramento de erros no cliente e no servidor, alertas, healthcheck e página de status. |
| ⬜ A fazer | 9.1-8 | **Dashboards no Painel do Mestre** — liga com 3.5.5. |

### 9.2 Performance e otimização

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 9.2-1 | **Orçamentos de desempenho** — metas propostas, a calibrar: LCP abaixo de 2,5 s em 4G médio, CLS abaixo de 0,1, tempo de resposta p95 das APIs abaixo de 300 ms e limite de JS inicial por rota; medidos por Lighthouse e Web Vitals em usuários reais. |
| ⬜ A fazer | 9.2-2 | **Pipeline de imagens** — geração automática de WebP/AVIF em tamanhos responsivos, carregamento preguiçoso, next/image e sprites para ícones (continua o 0.5-E1). |
| ⬜ A fazer | 9.2-3 | **Frontend** — divisão de código por rota, remover dependências sem uso, memoização das telas pesadas (CombatArena), pré-carregamento, cache de assets e PWA a avaliar para mobile. |
| ⬜ A fazer | 9.2-4 | **Backend e Firestore** — menos leituras por requisição (hoje cada rota relê o personagem), projeção de campos, índices, paginação em ranking e histórico, cache curto; custo por jogador ativo. |
| ⬜ A fazer | 9.2-5 | **Motor de combate** — medir lutas por segundo em resolverCombate e garantir que não trava o servidor; mover para worker se necessário. |
| ⬜ A fazer | 9.2-6 | **Escalabilidade e rede** — instâncias mínimas e concorrência no Cloud Run, CDN, cabeçalhos de cache imutáveis, compressão Brotli. |
| ⬜ A fazer | 9.2-7 | **Orçamento no CI** — falha o build se o tamanho do bundle ou das imagens passar do limite. |

### 9.3 a 9.8 Testes, conta, backup e lançamento

| Status | ID | Item |
| --- | --- | --- |
| ⬜ A fazer | 9.3 | **Testes formais (44)** — carga, estresse, segurança (revisão externa ou pentest), matriz de aparelhos móveis e ensaio de recuperação de desastre. |
| ⬜ A fazer | 9.4 | **Exclusão de conta e alteração de senha (2)** — mais exportação dos dados do jogador (LGPD). |
| ⬜ A fazer | 9.5 | **Backup (43)** — hoje só ZIP manual do AI Studio; rotina automatizada e restauração ensaiada antes do Beta. |
| ⬜ A fazer | 9.6 | **Beta (46)** — fechado e depois aberto, com critérios de entrada e saída, canal de feedback e métricas. |
| ⬜ A fazer | 9.7 | **Lançamento (47)** |
| ⬜ A fazer | 9.8 | **Temporadas e atualizações (48)** |

**Portão de saída:** Orçamentos de desempenho cumpridos, teste de carga aprovado, backup restaurado com sucesso em ensaio, Analytics coletando com consentimento, termos publicados e Beta fechado concluído.

## Trilha contínua

Em paralelo, em todas as etapas.

- **Segurança (37):** Feito: validação server-side e regras do Firestore. A fazer: básico na 0.5; rate limiting avançado, sessão avançada e detecção de comportamento anormal na 6.5, sempre antes de qualquer comércio entre jogadores.
- **Logs (38):** Feito: transações de ouro e XP. A fazer: logs administrativos (3.5.5), histórico completo e ledger (6.5).
- **Testes (44):** Feito: 269 testes unitários em 28 arquivos (eram 209 no roadmap anterior). Regra fixa: toda ordem fecha com npm run build e npm test limpos; a partir da 0.5, também CI verde.
- **Backup (43):** Hoje só ZIP manual do AI Studio: baixar periodicamente. Exportação agendada na 0.5 e rotina real antes do Beta (9.5).
- **Performance:** Orçamento contínuo: nenhuma etapa aumenta o peso das imagens ou do bundle acima do limite definido em 9.2; ganhos baratos já na 0.5.
- **Identidade e interface:** Logo, Público-alvo, versão desktop e ícones das linhagens do Draconiano (SVGs provisórios): tratados na 4.5.
- **Dívidas técnicas:** Mutex por uid só vale em uma instância (0.5-C2); imagens pesadas (0.5-E1); build de produção completo ainda sem prova (0.5-D2); confirmar a Ordem 27.

## Decisões pendentes do Yuri

| Item | Decisão | Etapa | O que bloqueia |
| --- | --- | --- | --- |
| 0.5-A2 | Qual autenticação manter: Firebase Auth ou login próprio | 0.5 | Bloqueia a remoção do sistema duplicado e a migração de contas |
| 0.5-B2 | Limite provisório de batalhas (cooldown, custo ou teto) | 0.5 | Bloqueia o fechamento da integridade do combate |
| 1.2 a 1.8 | Catálogo de bônus, tipos de dano, resistências, status, recursos e raciais ativas | 1 | Bloqueia o portão da Etapa 1 |
| 2.1 | Custo em fragmentos por tier; pontos de habilidade; compatibilidade raça × classe; invocação; novas classes | 2 | Bloqueia kits e telas de Subclasse |
| 3 | Raridade e multiplicadores, quantidade de slots, itens de teste | 3 | Bloqueia equipamentos |
| 3.5.2 | O que migrar de código para o banco e em que ordem | 3.5 | Define o escopo do Painel |
| 4 | Lore geográfica (cosmologia, continentes, reinos, facções) | 4 | Bloqueia regiões e bestiário |
| 4.5 | Layout da versão desktop; idiomas; recompensa de boas-vindas | 4.5 | Bloqueia a conclusão de UX e Onboarding |
| 5.2 | Formato da Provação da Torre Celestial e da Provação do Guerreiro | 5 | Bloqueia essas duas provações |
| 6 | Como obter Diamantes gratuitamente | 6 e 8.5 | Bloqueia o loop da economia premium |
| 6.5-5 | Ferramenta anti-bot (App Check, reCAPTCHA ou outra) | 6.5 | Bloqueia a proteção de cadastro |
| 7 | Party altera ou não a regra de combate 1x1; ressurreição | 7 | Bloqueia Party, PvP em grupo e Teste de Equipe |
| 8.5 | Modelo de negócio, linha de justiça, preços, gateway, regras de lojas, classificação e caixas aleatórias | 8.5 | Bloqueia toda a Monetização |
| 9.1-2 | Ferramenta de analytics e de monitoramento de erros | 9 | Bloqueia a coleta de dados |

## Apêndice A — Achados da auditoria de 08/10/2026

Auditoria feita lendo o código e rodando testes, tsc, ESLint e npm audit em uma cópia do projeto.

| Severidade | Achado | Onde | Item do roadmap |
| --- | --- | --- | --- |
| Crítico | Segredo de sessão padrão público; token sem expiração | src/server/auth.ts | 0.5-A1 |
| Crítico | Semente do combate vem do cliente; sem cooldown ou custo | src/app/api/combat/start/route.ts | 0.5-B1, B2 |
| Crítico | memoryStore como fonte real; gravações no Firestore engolem erros; mutex só em 1 instância | src/server/characterService.ts, src/app/api/auth/email/route.ts | 0.5-C1, C2 |
| Crítico | next 15.4.9 com advisory crítico; alertas altos em grpc-js, postcss e sharp | package.json | 0.5-D1 |
| Alto | Login e cadastro sem rate limit | src/app/api/auth/email/route.ts | 0.5-A3 |
| Médio | Build ignora erros de TypeScript e ESLint | next.config.ts | 0.5-D2 |
| Médio | Dois sistemas de autenticação em paralelo | src/lib/firebase.ts, src/app/api/auth/email/route.ts | 0.5-A2 |
| Médio | Unicidade de nome varre a coleção characters inteira | src/server/characterService.ts | 0.5-C3 |
| Médio | package-lock.json fora de sincronia; bun.lock junto | raiz do repositório | 0.5-D3 |
| Médio | public/ com 69 MB; 51 imagens acima de 500 KB; 22 ícones duplicados | public/, src/assets/ | 0.5-E1, E2 |
| Baixo | Hash de senha em documento legível pelo dono; atalho test-token | firestore.rules, src/server/auth.ts | 0.5-A5 |
| Baixo | Arquivos gerados no git; README desatualizado; @google/genai sem uso | tsconfig.tsbuildinfo, scripts/next.bin.bak, README.md | 0.5-D5 |

## Apêndice B — Mapa do roadmap antigo para o novo

| Nova etapa | Fases do roadmap antigo |
| --- | --- |
| Etapa 0 | fases 1, 3, 5, 6 (base), 8 e 9 (base) e partes das fases 0 e 2 |
| Etapa 0.5 (NOVA) | fases 37, 38 (base) e 43 (base); dívidas técnicas; achados da auditoria de 08/10/2026 |
| Etapa 1 | fases 8 e 9, mais resistências, elementos e regeneração (fases 0, 5 e 7) |
| Etapa 2 | fase 4, mais habilidades (7) e pontos de habilidade (6) |
| Etapa 3 | fases 11 e 12, mais loot (9, 10) |
| Etapa 3.5 (NOVA) | fases 39 e 38 (antes na Etapa 5); parte da fase 40 |
| Etapa 4 | fases 10, 13, 14 (base), 15, 16, 17, 21 e 45 |
| Etapa 4.5 (NOVA) | UX/UI, onboarding e pendências de identidade da Trilha |
| Etapa 5 | fases 18, 19, 20, 22 e 23; Provações |
| Etapa 6 | fases 33, 34, 35 e 41 |
| Etapa 6.5 (NOVA) | fase 37 (parte avançada, antes «até a Etapa 5») |
| Etapa 7 | fases 24, 25, 26, 27 e 14 (comércio) |
| Etapa 8 | fases 28, 29, 30, 31, 32, 36 e 40 |
| Etapa 8.5 (NOVA) | Monetização, Loja, Passe de Batalha e Diamantes |
| Etapa 9 | fases 42, 44 (formal), 46, 47 e 48; Analytics e Performance |
| Trilha contínua | fases 37, 38, 43 e 44 |
