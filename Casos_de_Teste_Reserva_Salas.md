# Casos de Teste - Sistema de Reserva de Salas

Serão criados casos de teste para cada requisito funcional e não funcional do sistema, abrangendo cenários positivos e negativos, bem como casos de limite (capacidade máxima, limites de horário).

---

### CT-01: Reservar Sala Disponível (RF-01)
- **Descrição:** Verificar se é possível reservar uma sala disponível para uma turma compatível.
- **Pré-condições:** Usuário está logado no sistema; sala disponível no período; turma compatível com capacidade e recursos da sala.
- **Passos:**
  1. Acessar a tela de reserva.
  2. Selecionar sala, data, horário e turma.
  3. Clicar no botão "Confirmar".
- **Resultado Esperado:** A reserva é criada e exibida na agenda da sala.

---

### CT-02: Impedir Sobreposição de Horário (RF-02)
- **Descrição:** Verificar se o sistema impede reservar a mesma sala em horário já ocupado.
- **Pré-condições:** Sala já possui reserva confirmada em um horário X.
- **Passos:**
  1. Selecionar a mesma sala e data.
  2. Selecionar horário sobreposto ao da reserva existente.
  3. Tentar confirmar.
- **Resultado Esperado:** Sistema impede a nova reserva e exibe mensagem de conflito de horário.

---

### CT-03: Impedir Turma Acima da Capacidade (RF-03)
- **Descrição:** Verificar se o sistema impede reserva quando a turma excede a capacidade da sala.
- **Pré-condições:** Sala com capacidade definida (ex.: 30 lugares); turma com número de alunos maior que a capacidade.
- **Passos:**
  1. Selecionar sala e horário disponíveis.
  2. Selecionar turma incompatível com a capacidade.
  3. Tentar confirmar a reserva.
- **Resultado Esperado:** Sistema bloqueia a reserva e informa que a capacidade foi excedida.

---

### CT-04: Bloquear Sala em Manutenção (RF-04)
- **Descrição:** Verificar se o sistema bloqueia reserva de sala em manutenção.
- **Pré-condições:** Sala marcada como em manutenção para o período desejado.
- **Passos:**
  1. Selecionar a sala em manutenção.
  2. Selecionar data/horário dentro do período de manutenção.
  3. Tentar confirmar a reserva.
- **Resultado Esperado:** Sistema bloqueia a reserva e informa indisponibilidade por manutenção.

---

### CT-05: Respeitar Janela de Horário Permitida (RF-05)
- **Descrição:** Verificar se o sistema permite reservas apenas entre 07h30 e 22h30.
- **Pré-condições:** Usuário está logado no sistema; sala e turma compatíveis.
- **Passos:**
  1. Tentar reservar um horário dentro do intervalo (ex.: 08h00).
  2. Tentar reservar um horário fora do intervalo (ex.: 06h00 ou 23h00).
- **Resultado Esperado:** A reserva dentro do intervalo é aceita; a reserva fora do intervalo é bloqueada, com mensagem informando o horário permitido.

---

### CT-06: Permissão para Alterar Reserva de Outro Professor (RF-06)
- **Descrição:** Verificar se apenas a coordenação pode alterar reserva de outro professor.
- **Pré-condições:** Reserva pertence a um professor; existe um segundo usuário com perfil de professor e outro com perfil de coordenação.
- **Passos:**
  1. Logar como professor e tentar alterar reserva de outro professor.
  2. Logar como coordenação e alterar a mesma reserva.
- **Resultado Esperado:** O professor tem a operação negada; a coordenação consegue realizar a alteração com sucesso.

---

### CT-07: Cancelamento Libera Horário e Registra Histórico (RF-07)
- **Descrição:** Verificar se o cancelamento de uma reserva libera o horário e gera registro no histórico.
- **Pré-condições:** Reserva ativa existente para a sala e horário.
- **Passos:**
  1. Acessar a reserva.
  2. Selecionar a opção de cancelamento.
  3. Confirmar o cancelamento.
- **Resultado Esperado:** O horário é liberado para novas reservas e o cancelamento é registrado no histórico.

---

### CT-08: Notificação em Alteração ou Cancelamento (RF-08)
- **Descrição:** Verificar se alterações ou cancelamentos geram notificação ao responsável.
- **Pré-condições:** Reserva existente vinculada a um responsável.
- **Passos:**
  1. Alterar ou cancelar a reserva.
  2. Verificar as notificações do responsável.
- **Resultado Esperado:** Notificação é enviada automaticamente informando a alteração ou o cancelamento.

---

### CT-09: Tempo de Resposta da Busca (RNF-01)
- **Descrição:** Verificar se a busca de salas/horários responde em até 2 segundos.
- **Pré-condições:** Base de dados com volume representativo de salas e reservas.
- **Passos:**
  1. Executar busca por sala/horário disponível.
  2. Medir o tempo de resposta.
- **Resultado Esperado:** A resposta é retornada em até 2 segundos.

---

### CT-10: Trilha de Auditoria (RNF-02)
- **Descrição:** Verificar se as operações do sistema possuem trilha de auditoria.
- **Pré-condições:** Usuário autenticado com permissão para criar, alterar e cancelar reservas.
- **Passos:**
  1. Criar, alterar e cancelar uma reserva.
  2. Consultar o log/trilha de auditoria.
- **Resultado Esperado:** Cada operação fica registrada com usuário, data/hora e ação realizada.

---

### CT-11: Acesso Restrito por Unidade (RNF-03)
- **Descrição:** Verificar se o acesso é limitado às unidades autorizadas do usuário.
- **Pré-condições:** Usuário autenticado com acesso restrito a uma ou mais unidades específicas.
- **Passos:**
  1. Tentar visualizar ou reservar sala de uma unidade não autorizada.
- **Resultado Esperado:** Sistema bloqueia o acesso e exibe mensagem de permissão insuficiente.
