# Roadmap — Java, ERP financeiro e carreira internacional

Plano inicial: 16 semanas, 2 horas por dia, 7 dias por semana (224 horas). Início: próximo dia disponível; D01 é o primeiro dia efetivamente estudado. Domingos são revisão e recuperação. Se um dia for perdido, retomar a sequência, sem dobrar a carga. Plano preparado em 29/10/2026; tarefas inicialmente não concluídas.

## Objetivo e experiência transferível

Construir uma aplicação financeira demonstrável e preparar candidaturas internacionais ainda no Brasil. A aprovação em entrevistas e a contratação com apoio migratório são resultados incertos; a mudança depende de proposta e documentação aplicável.

Formação em ADS, experiência profissional em consultoria e desenvolvimento sênior com Protheus/ADVPL/TL++, SQL e integrações formam a base. Destacar conhecimento de entradas e saídas financeiras, contas a pagar/receber e processos de controladoria somente nas atividades efetivamente realizadas. Não converter tempo em Protheus em anos de experiência Java ou em experiência DevOps sem evidências. Datas, cargos e resultados devem ser conferidos antes de entrar no currículo.

## Duas horas diárias

| Bloco | Minutos | Atividade |
|---|---:|---|
| Espanhol | 25 | 10 de escuta/leitura, 10 de fala e 5 de vocabulário; relacionar com a tarefa técnica |
| Curso ou referência | 30 | Aula do curso Java/Angular alinhada ao tema do dia; registrar a seção estudada |
| Implementação | 50 | Código, consulta, teste, experimento ou diagnóstico da tarefa diária |
| Evidência | 15 | Verificar resultado, registrar dúvida e fazer commit/push quando houver mudança útil |

Cursos não são horas adicionais. Se uma aula durar mais, dividir em dois dias. Não comprar outro curso antes de conferir se cobre os objetivos. W3Schools entra nos 30 minutos, como prática complementar; resolver variações próprias no projeto. Não copiar aulas ou enunciados protegidos para o repositório.

## Escopo e prioridades

1. Java + Spring Boot + PostgreSQL são o núcleo.
2. SQL Server/T-SQL é o segundo banco assumido; comparar o mesmo modelo e consultas em um laboratório separado, sem implementar dois backends simultâneos.
3. Angular cria uma interface pequena, seguindo o curso escolhido.
4. DevOps aplicado: Git, Linux, Maven, Docker, testes em CI, configuração, logs, publicação e rollback. AWS é a nuvem inicial; Azure pode substituir se as vagas-alvo justificarem, sem estudar ambas ao mesmo tempo.
5. Skills na IDE apoiam ensino, análise e revisão. IA dentro do produto e microsserviços são extensões após o núcleo estar pronto.

## Projeto central: ERP Finance Lab

Aplicação educacional independente, inspirada em problemas de ERP, usando apenas dados sintéticos e código próprio.

### Versão mínima

- Clientes/fornecedores e contas financeiras.
- Títulos a pagar/receber, emissão, vencimento, valor e situação.
- Baixa parcial/total, saldo em aberto e estorno auditável.
- Fluxo de caixa realizado e previsão, diferenciando movimento de caixa e competência.
- API REST, persistência PostgreSQL, testes, importação CSV e tela Angular essencial.
- Importação identifica linha inválida e duplicada, sem processar tudo silenciosamente.
- Segurança por usuário e autorização no backend.

### Depois da versão mínima

Conciliação de extrato simulado; integração com adaptador ERP simulado; serviço independente de notificações; assistente que consulta funções controladas. Não conectar ambientes TOTVS/clientes nem publicar dicionários, credenciais, dados pessoais ou código proprietário.

### Evidência de arquitetura

Começar como aplicação modular, com responsabilidades claras entre domínio, casos de uso, API e persistência. Documentar por que foi escolhida. Só extrair um serviço quando houver motivo e tempo. Uma arquitetura simples bem testada é uma entrega válida.

## Mapa semanal

| Semana | Foco | Entrega verificável |
|---|---|---|
| 1 | Diagnóstico, Java e Git | Regras simples executáveis e histórico compreensível |
| 2 | Classes e comportamento | Modelo financeiro com invariantes e testes |
| 3 | Coleções, datas, exceções e testes | Apuração de vencidos, recebimentos e estornos |
| 4 | Banco relacional e SQL | Modelo PostgreSQL e consultas financeiras |
| 5 | Segundo banco | Laboratório SQL Server e comparação de dialetos |
| 6 | Spring Boot e HTTP | API inicial com validação e documentação |
| 7 | JPA e transações | Persistência e migrações reproduzíveis |
| 8 | Segurança e qualidade | Autorização e testes dos fluxos críticos |
| 9 | Importações e automações | CSV validado, reprocessamento e logs |
| 10 | Angular/TypeScript | Interface pequena com dados simulados |
| 11 | Angular integrado | Fluxo cadastro, consulta e baixa pela interface |
| 12 | DevOps local e CI | Build, testes e contêiner reproduzíveis |
| 13 | AWS e operação | Ambiente de demonstração ou roteiro local validado |
| 14 | Integrações e arquitetura | Adaptador simulado e análise de falhas |
| 15 | Skills e portfólio | Fluxos de apoio à IDE avaliados e documentação |
| 16 | Entrevistas e candidaturas | Demo, CV, casos profissionais e candidaturas direcionadas |

## Backlog diário — 112 sessões

Cada item inclui os quatro blocos da rotina. As seis primeiras sessões da semana implementam o objetivo; a sétima revisa, recupera pendências e apresenta em espanhol. Concluir significa verificar o resultado e registrar evidência, não apenas assistir aula.

### Semana 1 — Diagnóstico e fundamentos
- [ ] D01 — Preparar JDK compatível com a versão estável escolhida do Spring, IDE, Git e Maven; executar um programa. Registrar versões e diagnóstico inicial.
- [ ] D02 — Praticar tipos, variáveis e operadores; representar valores com BigDecimal e documentar a escolha.
- [ ] D03 — Condições e regras: rejeitar valor negativo e vencimento ausente; escrever exemplos de entrada/saída.
- [ ] D04 — Laços e métodos: totalizar entradas e saídas de uma lista de valores.
- [ ] D05 — Usar debugger para investigar um saldo incorreto; registrar hipótese, causa e correção.
- [ ] D06 — Criar README inicial e commit descritivo; resolver exercícios próprios baseados no tema do curso.
- [ ] D07 — Revisar sem tutorial: calcular saldo inicial + entradas - saídas; apresentar em espanhol por 1 minuto.

### Semana 2 — Classes, regras e testes
- [ ] D08 — Desenhar Cliente, Fornecedor e TituloFinanceiro, com responsabilidades e exemplos.
- [ ] D09 — Implementar construtores e encapsulamento; impedir estado inválido.
- [ ] D10 — Separar pagar/receber por tipo; justificar composição ou herança conforme a necessidade.
- [ ] D11 — Criar serviço de baixa usando interfaces quando trouxerem benefício real.
- [ ] D12 — Escrever testes JUnit para valores, saldo e baixa válida.
- [ ] D13 — Testar pagamento acima do saldo, zero e valor inválido; corrigir regras.
- [ ] D14 — Explicar classes e responsabilidades em espanhol; revisar se o código reflete as regras.

### Semana 3 — Dados em memória e cenários financeiros
- [ ] D15 — Usar List e Map para localizar e agrupar títulos; explicar critérios de escolha.
- [ ] D16 — Trabalhar LocalDate e vencimento; testar datas-limite.
- [ ] D17 — Implementar baixa parcial e testar saldo remanescente.
- [ ] D18 — Implementar estorno com rastreabilidade, evitando apagar o histórico.
- [ ] D19 — Tratar erros com exceções úteis; separar erro de entrada e falha técnica.
- [ ] D20 — Refatorar duplicações; comparar leitura com laços e streams sem complicar a solução.
- [ ] D21 — Executar testes e demonstrar um fluxo completo pelo terminal em espanhol.

### Semana 4 — PostgreSQL e interpretação de dados
- [ ] D22 — Modelar entidades, cardinalidades e normalização; desenhar o modelo relacional.
- [ ] D23 — Criar tabelas com PK, FK, UNIQUE, CHECK e tipos monetários adequados.
- [ ] D24 — Inserir massa sintética e consultar valores nulos, duplicados e registros órfãos.
- [ ] D25 — Criar JOINs para títulos, participantes e baixas; conferir resultados manualmente.
- [ ] D26 — Criar relatórios por mês, categoria e situação usando GROUP BY e HAVING.
- [ ] D27 — Demonstrar COMMIT/ROLLBACK e uma operação financeira atômica.
- [ ] D28 — Explicar diferença entre faturamento, contas a receber e caixa; validar consultas.

### Semana 5 — SQL Server e diferenças de dialeto
- [ ] D29 — Preparar ambiente de desenvolvimento SQL Server compatível com a máquina ou alternativa de laboratório; registrar conexão sem segredos.
- [ ] D30 — Recriar o modelo reduzido em T-SQL; comparar identity, tipos e datas.
- [ ] D31 — Executar as mesmas consultas nos dois bancos e comparar resultados.
- [ ] D32 — Praticar CTE e funções de janela em um relatório financeiro.
- [ ] D33 — Comparar paginação, funções de texto e datas entre PostgreSQL e SQL Server.
- [ ] D34 — Avaliar consulta com plano de execução e índice; medir antes e depois na massa sintética.
- [ ] D35 — Documentar resultados e limites; fazer exercícios SQL complementares no W3Schools.

### Semana 6 — API com Spring Boot
- [ ] D36 — Criar projeto Spring Boot com Maven; entender dependências, configuração e injeção.
- [ ] D37 — Implementar GET/POST de títulos com armazenamento provisório em memória.
- [ ] D38 — Usar DTOs e validação; definir respostas HTTP e mensagens de erro.
- [ ] D39 — Implementar baixa como operação de negócio; não aceitar alterações arbitrárias no saldo.
- [ ] D40 — Implementar filtros e paginação com limites.
- [ ] D41 — Documentar API/OpenAPI e exemplos reproduzíveis de chamadas.
- [ ] D42 — Demonstrar requisição, resposta e erro; apresentação em espanhol.

### Semana 7 — Persistência e consistência
- [ ] D43 — Conectar PostgreSQL com configuração externa; mapear entidades JPA.
- [ ] D44 — Criar migração inicial e dados sintéticos de desenvolvimento.
- [ ] D45 — Persistir títulos e baixas; delimitar transação no caso de uso.
- [ ] D46 — Investigar consultas geradas e evitar carregamentos desnecessários/N+1 no fluxo estudado.
- [ ] D47 — Reproduzir duas baixas concorrentes e escolher proteção contra inconsistência.
- [ ] D48 — Criar teste de integração do fluxo de baixa com banco de teste.
- [ ] D49 — Recriar banco vazio por migrações e conferir saldo final esperado.

### Semana 8 — Segurança e validação de ponta a ponta
- [ ] D50 — Definir quem pode consultar, cadastrar e dar baixa; registrar matriz de permissões.
- [ ] D51 — Implementar autenticação com mecanismos suportados pelo Spring Security; não criar criptografia própria.
- [ ] D52 — Aplicar autorização no backend; testar acesso negado entre usuários.
- [ ] D53 — Testar erros de validação, recurso inexistente e conflito de negócio na API.
- [ ] D54 — Proteger configurações e logs contra vazamento de credenciais e dados.
- [ ] D55 — Revisar testes críticos e limitações; selecionar candidaturas compatíveis para entender lacunas.
- [ ] D56 — Marco: demonstrar API segura e consistente; repetir semanas necessárias se não conseguir explicar o fluxo.

### Semana 9 — Importação e automações
- [ ] D57 — Definir layout CSV de títulos e exemplos de linhas válidas e inválidas.
- [ ] D58 — Implementar leitura e validação por linha; produzir relatório de erros.
- [ ] D59 — Criar chave de identificação da importação e impedir duplicação.
- [ ] D60 — Definir atomicidade por lote/linha e testar importação parcialmente inválida.
- [ ] D61 — Registrar início, término, quantidade e falha de cada execução com identificador.
- [ ] D62 — Simular falha e reprocessar sem duplicar efeitos.
- [ ] D63 — Demonstrar ganho operacional com um conjunto fixo de dados; documentar medição.

### Semana 10 — Angular e TypeScript
- [ ] D64 — Seguir curso: tipos, funções, objetos e async em TypeScript; revisar JavaScript necessário.
- [ ] D65 — Criar app Angular e componentes com responsabilidades pequenas.
- [ ] D66 — Criar lista de títulos com dados simulados e estados de carregamento/vazio.
- [ ] D67 — Implementar formulário com validação e mensagens claras.
- [ ] D68 — Estudar serviços e injeção de dependência; separar acesso a dados da tela.
- [ ] D69 — Implementar rotas e navegação; conferir comportamento pelo teclado.
- [ ] D70 — Explicar em espanhol componente, serviço e fluxo de dados.

### Semana 11 — Aplicação integrada
- [ ] D71 — Conectar Angular à API; configurar URLs por ambiente.
- [ ] D72 — Implementar autenticação na interface sem confiar nela para autorização.
- [ ] D73 — Mostrar filtros, paginação e respostas de erro reais.
- [ ] D74 — Implementar cadastro e baixa com atualização coerente da tela.
- [ ] D75 — Criar painel simples de entradas, saídas e saldo; conferir cálculos com SQL.
- [ ] D76 — Testar fluxo crítico na interface e corrigir problema observado.
- [ ] D77 — Gravar demonstração curta e revisar clareza visual e funcional.

### Semana 12 — DevOps e operação local
- [ ] D78 — Praticar shell/Linux: processos, portas, variáveis, permissões e leitura de logs no laboratório.
- [ ] D79 — Criar imagem Docker da aplicação e configuração reproduzível.
- [ ] D80 — Subir app e banco com Docker Compose; configurar healthcheck e persistência.
- [ ] D81 — Criar workflow de CI para build e testes em pull requests.
- [ ] D82 — Simular mudança quebrada e verificar que a CI acusa a falha.
- [ ] D83 — Documentar versão, release e rollback; ligar experiências Protheus de ambiente/deploy apenas ao que foi efetivamente realizado.
- [ ] D84 — Executar instalação limpa seguindo somente README; corrigir etapas ausentes.

### Semana 13 — Cloud e observação
- [ ] D85 — Desenhar opção AWS mínima com custo estimado; decidir se o laboratório será hospedado ou apenas local.
- [ ] D86 — Estudar IAM, rede e segredos; definir acessos mínimos e restrições de exposição.
- [ ] D87 — Publicar demonstração se conta e orçamento estiverem disponíveis; alternativamente ensaiar release em ambiente local equivalente e registrar limite.
- [ ] D88 — Configurar logs e healthcheck; investigar falha simulada.
- [ ] D89 — Executar backup e restauração da base de laboratório.
- [ ] D90 — Documentar desligamento/remoção de recursos e acompanhamento de custos.
- [ ] D91 — Demonstrar deploy/rollback e explicar em espanhol; distinguir o que foi executado do que é somente desenho.

### Semana 14 — Integração e microsserviços
- [ ] D92 — Definir contrato de um adaptador ERP simulado, com dados fictícios.
- [ ] D93 — Implementar cliente HTTP com timeout e tratamento de resposta inválida.
- [ ] D94 — Simular indisponibilidade; aplicar retentativas limitadas apenas onde forem seguras.
- [ ] D95 — Definir evento de pagamento e discutir duplicação e consistência eventual.
- [ ] D96 — Se o núcleo estiver pronto, implementar consumidor pequeno com fila; caso contrário, concluir o adaptador e registrar extensão futura.
- [ ] D97 — Testar repetição/falha e documentar propriedade dos dados e correlação de logs.
- [ ] D98 — Registrar decisão: manter aplicação modular ou extrair serviço; justificar custos e benefícios.

### Semana 15 — Skills e portfólio
- [ ] D99 — Identificar assistente da IDE e formato suportado; especificar Tutor Java com pistas, tentativa e revisão.
- [ ] D100 — Implementar instruções do tutor no formato da IDE; testar em exercício novo e registrar resultado.
- [ ] D101 — Especificar/revisar skill de análise de demanda com critérios de aceite e perguntas úteis.
- [ ] D102 — Especificar skill de revisão Java/SQL; testar se encontra um erro real e se evita sugerir mudanças sem evidência.
- [ ] D103 — Documentar limites da IA e comparar uma tarefa com e sem apoio, sem inventar economia de tempo.
- [ ] D104 — Preparar README inglês, arquitetura, modelo relacional, API e imagens da aplicação.
- [ ] D105 — Revisar material público, executar projeto e identificar quais tarefas ainda não foram concluídas.

### Semana 16 — Empregabilidade
- [ ] D106 — Mapear experiência real em Protheus financeiro: situação, ação e resultado verificável.
- [ ] D107 — Atualizar currículo espanhol/inglês separando trabalho profissional e projetos Java.
- [ ] D108 — Selecionar vagas compatíveis e registrar exigências de idioma, Java, localização e apoio migratório.
- [ ] D109 — Simular entrevista Java: classes, coleções, exceções, transações e REST.
- [ ] D110 — Simular entrevista SQL: JOINs, duplicidade, agregações, índices e leitura de dados.
- [ ] D111 — Fazer demo em espanhol, adaptar carta à vaga e enviar candidaturas direcionadas.
- [ ] D112 — Avaliar evidências e retornos; definir próximo ciclo com experiência real, idioma e lacunas prioritárias.

## GitHub: organização e rotina

Este roadmap pertence ao repositório de perfil. Evoluir a implementação em um repositório próprio, sugerido: erp-finance-lab. Não criar uma aplicação vazia por semana. Laboratórios SQL podem ficar em databases/postgresql e databases/sqlserver; documentação em docs e diário em learning-log. Não declarar workflows, testes ou aplicações como existentes antes da implementação.

### Sessão diária

1. Escolher apenas o próximo item e identificar critério de aceite.
2. Trabalhar em branch curta quando houver mudança de código; revisar diff e executar verificação pertinente.
3. Fazer commit descritivo de mudança real: feat: add partial settlement; test: cover overpayment; docs: explain transaction boundary.
4. Fazer push ao final quando houver mudança útil. Em dias de estudo, registrar uma descoberta própria ou consulta testada. Não gerar commits vazios para preencher contribuições.
5. Atualizar checkbox somente após concluir e registrar a próxima dúvida.

### Modelo de diário

Data / Dxx:
- Objetivo e aula do curso:
- O que implementei ou investiguei:
- Evidência: teste, consulta, imagem, commit ou PR:
- Decisão que consigo explicar:
- Como usei IA e como conferi o resultado:
- Espanhol praticado:
- Dúvida e próxima ação:

### Modelo de tarefa/issue

Título: [Dxx] resultado concreto.
Contexto: problema que a tarefa resolve.
Aceite: comportamento observável, cenário inválido e evidência.
Tempo: uma sessão de 2h incluindo idioma e estudo; dividir se exceder.
Dependência: item anterior necessário.
Resultado: link para commit/PR e verificação feita.

## Espanhol progressivo

Semanas 1–4: apresentação pessoal e explicação de regras simples. Semanas 5–8: explicar dados, erros e APIs. Semanas 9–12: reunião curta sobre progresso e bloqueios. Semanas 13–16: demonstração e entrevista com perguntas inesperadas. Gravar 1 áudio semanal; comparar clareza e autonomia. Se o nível inicial for básico, não presumir B2 em quatro meses. Inglês continua relevante para vagas internacionais; avaliar exigências sem prometer fluência simultânea.

## Rubrica de aprendizagem

| Grau | Evidência |
|---|---|
| 1 | Entende e explica exemplo conhecido |
| 2 | Implementa com apoio e documentação |
| 3 | Implementa, testa e depura tarefa nova com autonomia |
| 4 | Compara alternativas e justifica consequências |
| 5 | Sustenta e evolui solução em produção com responsabilidade real |

Meta inicial: grau 3 no núcleo Java/API/SQL; grau 2 em Angular, cloud e skills; noções demonstráveis de sistemas distribuídos. Não equivale a senioridade Java ou DevOps. Produção, salário e apoio migratório dependem de experiências e seleção reais. Portfólio e cursos fortalecem a candidatura, mas não garantem emprego em 16 semanas.

## Marcos para ajustar escopo

- Semana 4: não avançar sem explicar cálculo financeiro e relacionamentos.
- Semana 8: priorizar API, transações e segurança se houver pendências; reduzir interface.
- Semana 12: se núcleo não estiver demonstrável, adiar microsserviços e IA no produto.
- Semana 16: uma entrega confiável, documentada e compreendida é melhor evidência do que várias incompletas.

## Referências

- Curso Java já escolhido: preencher título/link e relacionar aulas ao backlog.
- Curso Angular: preencher após escolha; priorizar TypeScript, componentes, serviços, HTTP, rotas, formulários e testes.
- Java: https://dev.java/learn/
- Spring: https://spring.io/guides/
- Testes Spring: https://docs.spring.io/spring-boot/reference/testing/
- PostgreSQL: https://www.postgresql.org/docs/current/
- SQL Server/T-SQL: https://learn.microsoft.com/training/paths/get-started-querying-with-transact-sql/
- Angular: https://angular.dev/tutorials/learn-angular
- Docker: https://docs.docker.com/get-started/
- AWS: https://aws.amazon.com/getting-started/
- Prática Java: https://www.w3schools.com/java/java_exercises.asp
- Prática SQL: https://www.w3schools.com/sql/sql_exercises.asp

W3Schools complementa a prática e permite acompanhar exercícios; o GitHub será o portfólio principal. Publicar soluções próprias e reflexões, sem expor credenciais ou material dos cursos. Este arquivo é um plano: não contém afirmação de que as competências e entregas já foram concluídas.
