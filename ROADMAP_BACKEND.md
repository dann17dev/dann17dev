# Roadmap de portfólio — Backend, APIs e softwares empresariais

**Autor:** Danilo Matos · [GitHub](https://github.com/dann17dev)  
**Planejamento inicial:** 30/10/2026  
**Status:** planejamento publicado; os softwares abaixo ainda não foram implementados por este roadmap.

## Objetivo

Construir evidências práticas de desenvolvimento backend em Java, APIs e SQL, aproveitando a experiência em Protheus e regras de negócio. O resultado esperado em 16 semanas é um software financeiro demonstrável e um MVP de integração. Pedidos e estoque entram como evolução posterior. O prazo é uma estimativa de execução, não uma promessa de senioridade em outra linguagem.

## Divisão por software

| Software | Repositório proposto (a criar) | Problema resolvido | Escopo |
| --- | --- | --- | --- |
| Finance Core | financial-api | Organizar obrigações, recebimentos e caixa | Prioridade 1: MVP completo |
| ERP Integration Hub | erp-integration-service | Receber pedidos externos com rastreabilidade e reprocessamento | Prioridade 2: MVP com ERP simulado |
| Order & Stock | order-stock-api | Controlar pedidos, reservas e movimentações | Próximo ciclo, após os dois primeiros |
| Interface financeira | financial-web | Operar o Finance Core pelo navegador | Interface Angular enxuta; não é outro backend |

Os nomes acima são propostas, não links para repositórios existentes. Este arquivo centraliza o plano no repositório do perfil. Cada software terá seu próprio histórico quando seu repositório for criado.

## Direção técnica

- Backend principal: Java + Spring Boot; PostgreSQL como banco inicial.
- Organização inicial: aplicação modular, com separação de API, aplicação, domínio e persistência quando útil.
- Regras financeiras: valores decimais exatos; política explícita de arredondamento; transações.
- Contratos: API REST documentada com OpenAPI e exemplos de requisições.
- Qualidade: testes unitários de regras e testes de integração com banco.
- Operação: Docker, migrações de banco, configuração por ambiente, logs e CI.
- Frontend: Angular após estabilizar o fluxo financeiro principal.
- Protheus: adaptador independente, exemplos próprios em ADVPL/TL++ e ambiente autorizado para integração real.
- SQL Server: exercício posterior de adaptação de consultas; não manter dois bancos no MVP.
- Fixar versões compatíveis no início da implementação e registrar a escolha. Não adotar uma versão apenas por ser a mais recente.
- Começar simples: filas e serviços adicionais entram quando houver um problema demonstrável.

## Software 1 — Finance Core

### MVP

- [ ] Clientes e fornecedores com validações.
- [ ] Contas a pagar e a receber com valor, vencimento, contraparte e situação.
- [ ] Parcelamento preservando o total, incluindo tratamento de centavos.
- [ ] Baixa parcial e total com histórico.
- [ ] Estorno rastreável, sem apagar o histórico financeiro.
- [ ] Política didática configurável de juros simples, multa e desconto.
- [ ] Saldo em aberto e fluxo de caixa previsto e realizado.
- [ ] Filtros por período, situação e contraparte; paginação.
- [ ] Autenticação e permissões de leitura e operação.
- [ ] Documentação, dados fictícios e execução reproduzível.

### Exemplos de contrato a implementar

| Método | Caminho proposto | Finalidade |
| --- | --- | --- |
| POST | /api/v1/parties | Cadastrar cliente ou fornecedor |
| POST | /api/v1/titles | Criar título financeiro |
| GET | /api/v1/titles | Consultar títulos paginados |
| POST | /api/v1/titles/{id}/settlements | Registrar baixa |
| POST | /api/v1/settlements/{id}/reversals | Estornar baixa |
| GET | /api/v1/cash-flow | Consultar previsão e realização |

As rotas são um desenho inicial. O contrato executável será publicado com a implementação.

### Critérios de aceite essenciais

1. Título de R$ 1.000,00 com baixa de R$ 400,00 mantém saldo de R$ 600,00.
2. Repetição da mesma baixa com a mesma chave de idempotência não altera o saldo outra vez.
3. A mesma chave com conteúdo diferente produz conflito.
4. Duas baixas simultâneas não permitem pagar acima do saldo disponível.
5. Parcelar R$ 100,00 em três títulos preserva R$ 100,00 no total.
6. Valor negativo, contraparte inexistente e baixa indevida são rejeitados.
7. Estorno mantém autoria, motivo e vínculo com a baixa original.
8. Perfil de consulta não pode efetuar baixa.
9. O caixa realizado considera movimentos efetivados; a previsão considera saldos pendentes.
10. As fórmulas financeiras são regras didáticas documentadas, sem alegação de conformidade bancária ou fiscal.

## Software 2 — ERP Integration Hub

### MVP

- [ ] Receber pedido com identificador externo.
- [ ] Validar cliente, itens, quantidades e valores.
- [ ] Persistir solicitação antes de enviá-la ao destino.
- [ ] Consultar estados: recebido, processando, integrado e falhou.
- [ ] Impedir duplicidade pelo identificador externo e origem.
- [ ] Integrar com simulador de ERP executável sem licença Protheus.
- [ ] Simular timeout, rejeição e indisponibilidade.
- [ ] Reprocessar falhas transitórias com limite e intervalo.
- [ ] Tratar retorno incerto: consultar destino antes de reenviar quando possível.
- [ ] Correlacionar logs sem expor credenciais ou dados pessoais.
- [ ] Documentar adaptador Protheus e diferenciar simulação de integração validada.

### Critérios de aceite

- O mesmo pedido enviado duas vezes gera um único pedido no destino.
- Falha de validação não entra em repetição automática.
- Queda temporária do destino deixa registro consultável.
- Reprocessamento preserva histórico e quantidade de tentativas.
- Reinício da aplicação não perde solicitações persistidas.
- A demonstração funciona integralmente com dados fictícios.

## Software 3 — Order & Stock

Próximo ciclo: catálogo, pedidos, reserva, cancelamento e movimentação de estoque.

Critérios centrais: duas compras concorrentes da última unidade não geram venda excedente; cancelar uma reserva libera o saldo uma única vez; toda movimentação possui origem rastreável.

Antes de começar, revisar o repositório existente sistema_estoque para decidir entre evolução e projeto novo. Não presumir qualidade ou cobertura sem ler e executar o código.

## Sequência de 16 semanas

Premissa de planejamento: 2 horas por dia, 5 dias por semana, aproximadamente 160 horas. Se necessário, reduzir o escopo do segundo software para proteger a qualidade do primeiro.

| Semana | Foco | Entrega verificável |
| --- | --- | --- |
| 1 | Java aplicado, domínio financeiro e ambiente | Projeto inicial executando, regra de saldo e primeiro teste |
| 2 | HTTP, validação e tratamento de erros | Cadastro de contraparte via API |
| 3 | SQL, migrações e persistência | Títulos gravados e consultados no PostgreSQL |
| 4 | Consultas e parcelamento | Filtros paginados e total de parcelas correto |
| 5 | Baixas | Baixa parcial/total com testes e transação |
| 6 | Robustez financeira | Idempotência, concorrência e estorno testados |
| 7 | Segurança | Login e matriz de permissões verificada |
| 8 | Indicadores financeiros | Caixa previsto/realizado e regras documentadas |
| 9 | Qualidade e operação | CI, Docker e execução limpa documentada |
| 10 | Demonstração | Interface Angular mínima e roteiro do Finance Core |
| 11 | Integração | Contrato de pedidos e ERP simulado |
| 12 | Persistência da integração | Recepção, estados e consulta de resultado |
| 13 | Resiliência | Timeout, repetição limitada e deduplicação testados |
| 14 | Experiência Protheus | Desenho do adaptador e exemplos próprios; validar se houver ambiente |
| 15 | Apresentação técnica | README dos projetos, diagrama e exemplos de API |
| 16 | Revisão e publicação | Demo reproduzível, correções e primeira versão marcada |

## Primeira semana — tarefas de 2 horas

| Dia | Tarefa | Critério de conclusão | Commit sugerido |
| --- | --- | --- | --- |
| 1 | Criar financial-api, escolher versões e iniciar projeto | Aplicação inicia; README explica o comando | chore: bootstrap financial api |
| 2 | Modelar título e saldo com Java | Título de 1000 menos baixa de 400 retorna 600 em teste | feat: model financial title balance |
| 3 | Definir invariantes | Valores inválidos são rejeitados com testes | test: cover invalid settlement scenarios |
| 4 | Expor primeiro fluxo HTTP | Requisição válida funciona e inválida tem erro consistente | feat: expose financial title endpoint |
| 5 | Revisar e explicar o fluxo | Executar os testes e explicar o código sem seguir o curso | docs: document first financial api flow |

Se um passo exigir mais tempo, estender a tarefa e registrar o bloqueio. Não criar commits vazios para preencher atividade.

## Rotina de aprendizado

- 20 minutos: estudar o conceito necessário para a tarefa.
- 70 minutos: implementar uma pequena entrega.
- 20 minutos: executar testes e revisar comportamento.
- 10 minutos: registrar aprendizado, commit e próximo passo.

Para cada funcionalidade, responder: qual problema resolve, qual regra protege, o que falha, como o teste demonstra e qual alternativa foi descartada.

## Fluxo de Git e tarefas

1. Criar uma tarefa pequena com problema e critério de aceite.
2. Abrir branch curta, por exemplo feat/partial-settlement.
3. Implementar e testar.
4. Fazer commits com mudança real: feat, fix, test, docs ou chore.
5. Abrir PR com problema, solução e validação.
6. Revisar diff e verificações antes de integrar.
7. Atualizar o progresso apenas quando o critério for cumprido.

Commits não serão feitos automaticamente em dias futuros. A rotina depende do trabalho executado e publicado em cada sessão.

## Modelo de tarefa

Título: [Finance Core] Implementar baixa parcial

Problema: registrar recebimentos parciais sem perder o saldo em aberto.

Critérios:
- [ ] Baixa de 400 em título de 1000 deixa saldo de 600.
- [ ] Valor maior que o saldo é rejeitado.
- [ ] Repetição com mesma chave não duplica a operação.
- [ ] Testes passam e exemplo de API está documentado.

Evidência: link do PR, resultado dos testes e exemplo de requisição/resposta.

## Padrão mínimo para apresentar cada software

- Problema de negócio e público.
- Status honesto: planejado, em desenvolvimento ou demonstrável.
- Funcionalidades concluídas e limitações.
- Arquitetura enxuta e justificativas.
- Instruções para executar a partir de um clone limpo.
- Dados de demonstração fictícios.
- Exemplos de API e testes.
- Vídeo curto ou capturas do fluxo funcionando.
- README em português e resumo em inglês quando estiver demonstrável.
- Nenhum código de empregador, cliente, credencial ou dado real.

## Indicadores de progresso

- Fluxos completos demonstráveis.
- Critérios de aceite aprovados.
- Execução reproduzível.
- Capacidade de explicar decisões e corrigir falhas.
- Histórico de commits coerente.

## Estado inicial

- [x] Perfil GitHub identificado: dann17dev.
- [x] Plano organizado por software e por semana.
- [ ] Repositório financial-api criado.
- [ ] Primeiro código Java executado e testado.
- [ ] Primeira demonstração da API publicada.
- [ ] Finance Core MVP concluído.
- [ ] ERP Integration Hub MVP concluído.

Este planejamento inicia a organização do portfólio; não representa softwares já entregues.
