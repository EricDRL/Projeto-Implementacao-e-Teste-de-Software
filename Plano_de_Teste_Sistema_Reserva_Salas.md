# Plano de Teste - Sistema de Reserva de Salas

## 1. Introdução
Este plano de teste descreve a abordagem para testar o **Sistema de Reservas de Salas**, cujo objetivo é permitir que usuários autorizados reservem salas para suas turmas de forma eficiente. O foco deste plano é assegurar a qualidade e confiabilidade do software antes do lançamento.

## 2. Objetivos
- Validar a conformidade de todas as funcionalidades em relação aos requisitos funcionais (**RF-01** a **RF-08**).
- Validar a conformidade com os requisitos não funcionais de desempenho, auditoria e isolamento de unidades (**RNF-01** a **RNF-03**).

## 3. Escopo
O teste abrangerá todas as funcionalidades principais do sistema:
- Criação, edição e cancelamento de reservas.
- Atribuição de reserva de sala a uma turma e um professor.
- Restrição de agendamento na janela permitida (07h30 às 22h30).
- Controle de permissões por perfil (Docente vs. Coordenação).
- Bloqueio de salas em manutenção.
- Disparo de notificações e geração de trilha de auditoria/logs.

## 4. Estratégia de Teste
- **Testes Unitários:** Executados pelos desenvolvedores para verificar funcionalidades individualmente.
- **Testes de Integração:** Validação da comunicação e integração entre diferentes módulos do sistema.
- **Testes de Sistema:** Verificação do comportamento do sistema de ponta a ponta.
- **Testes de Aceitação:** Realizados pelos usuários finais em ambiente de homologação/produção simulada.

## 5. Casos de Teste
Serão elaborados casos de teste para cada funcionalidade, cobrindo fluxos principais, alternativos, casos de borda e testes de carga/estresse.

### Exemplo de Caso de Teste
| Campo | Detalhes |
| :--- | :--- |
| **Identificador** | `CT-01` - Criação de Reserva com Sucesso |
| **Descrição** | Validar a criação de reserva para turma compatível em sala disponível. |
| **Pré-condições** | Usuário autenticado como Professor; Sala 101 ativa, sem manutenções, capacidade para 40 alunos; Horário das 14h às 16h livre. |
| **Passos** | 1. Acessar a tela de nova reserva.<br>2. Selecionar Sala 101, data corrente e horário das 14h00 às 16h00.<br>3. Vincular a Turma A (30 alunos) e confirmar. |
| **Resultado Esperado** | Reserva confirmada; agenda da Sala 101 bloqueada no período; registro gerado no log de auditoria; notificação enviada ao professor. |

## 6. Ambiente de Teste
Ambiente dedicado replicando a infraestrutura, configurações e regras de rede do ambiente de produção.

## 7. Recursos
- **Equipe de Teste:** 2 testadores (QA).
- **Infraestrutura:** Servidor dedicado espelhado com a configuração de produção.
- **Massa de Dados:** Dados sintéticos representativos cobrindo diferentes perfis, salas, turmas e históricos de agendamento.

## 8. Cronograma

| Fase de Teste | Período |
| :--- | :--- |
| Testes Unitários | Semana 1 |
| Testes de Integração | Semana 1 |
| Testes de Sistema | Semana 2 |
| Testes de Aceitação | Semana 2 |

## 9. Critérios de Aceitação
- 100% dos casos de teste planejados executados.
- 0 defeitos críticos (*Blocker* / *Critical*) abertos.
- Defeitos importantes corrigidos e validados em reteste.

## 10. Gestão de Riscos
- **Atrasos no desenvolvimento:** Impacto direto no cronograma de homologação.
- **Concorrência (dupla reserva):** Riscos de reserva simultânea para o mesmo horário/sala.
- **Capacidade física:** Alocação indevida de turmas maiores que a lotação máxima da sala.
- **Controle de acesso:** Edição não autorizada de reservas por usuários sem perfil de Coordenação.
- **Notificações:** Falha ou atraso no disparo de e-mails/alertas de cancelamento e alteração.

## 11. Responsabilidades
- **Desenvolvimento:** Correção de bugs, suporte técnico e disponibilização de builds estáveis.
- **QA / Testes:** Elaboração, execução, registro de evidências e reporte de métricas de qualidade.

## 12. Comunicação
Emissão de relatórios diários de status (*Daily Bug Reports*) e relatório consolidado de encerramento de ciclo para alinhamento com a gerência e equipe técnica.

## 13. Aprovação e Governança
Documento sujeito à revisão e aprovação técnica antes do início da execução dos testes. Alterações de escopo exigirão alinhamento formal entre as partes.

## 14. Considerações Finais
Este plano consolida as diretrizes de qualidade do Sistema de Reserva de Salas, assegurando a aderência aos requisitos funcionais e não funcionais estabelecidos.
