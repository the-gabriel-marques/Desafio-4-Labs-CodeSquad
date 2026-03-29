# Requisitos do Sistema - Plataforma de Eventos

## Requisitos Funcionais (RF)

* **RF01:** Como Participante, quero fazer login com e-mail e senha, para acessar a plataforma de forma segura.
  * *Critério de aceitação:* O sistema deve gerar um token JWT válido com tempo de expiração após o login bem-sucedido.
* **RF02:** Como Participante, quero clicar em "Inscrever-se" no evento, para garantir a minha participação.
  * *Critério de aceitação:* O sistema deve verificar a disponibilidade de vagas e exibir o erro "Sem vagas" caso o limite tenha sido atingido.
* **RF03:** Como Sistema, quero enviar as requisições de pagamento para uma Fila (MQ) com um Worker, para evitar o travamento da aplicação durante a comunicação com o Gateway.
  * *Critério de aceitação:* O status da inscrição deve ficar como "Pendente" até que o Worker receba o retorno (callback) do Gateway.
* **RF04:** Como Participante, quero que minha inscrição seja confirmada automaticamente, para que eu tenha certeza da minha vaga.
  * *Critério de aceitação:* A confirmação só pode ser emitida se o retorno do Gateway externo for "Aprovado".
* **RF05:** Como Participante, quero ter a opção de "retry" (tentar novamente) se meu pagamento falhar, para não perder a vaga por erro do cartão.
  * *Critério de aceitação:* O sistema deve registrar a falha no log e manter a inscrição pendente, liberando a opção de nova tentativa.
* **RF06:** Como Organizador, quero registrar o check-in do participante no evento, para confirmar sua presença real.
  * *Critério de aceitação:* O sistema deve exibir erro e bloquear o check-in caso seja realizado fora do horário estipulado.
* **RF07:** Como Participante, quero emitir meu certificado após a conclusão, para comprovar as horas cursadas.
  * *Critério de aceitação:* O botão de emitir certificado só deve ser liberado se o status do check-in estiver como "Confirmado".
* **RF08:** Como Organizador, quero cadastrar as informações do evento, para que os participantes possam se inscrever.
  * *Critério de aceitação:* A criação do evento exige a definição de um limite numérico máximo de vagas.
* **RF09:** Como Admin, quero ter acesso aos registros do sistema, para auditar erros e status das transações financeiras.
  * *Critério de aceitação:* O sistema deve registrar logs detalhados de retornos recusados, pendentes e falhas de autenticação de token.

---

## Requisitos Não Funcionais (RNF)

* **RNF01 (Segurança):** As senhas dos usuários devem ser obrigatoriamente protegidas e armazenadas no banco de dados utilizando criptografia de hash Bcrypt.
* **RNF02 (Segurança):** A proteção das rotas da API durante a jornada do evento deve ser feita via validação de token JWT. Caso inválido, a aplicação deve retornar o erro "Não autenticado".
* **RNF03 (Disponibilidade):** O sistema deve utilizar processamento assíncrono (Worker/Fila) para o checkout, garantindo que a plataforma principal não caia mesmo se o Gateway de pagamento externo demorar a responder.
* **RNF04 (Usabilidade):** O sistema deve fornecer feedback amigável e imediato em tela para o usuário final durante os cenários de erro ("Sem vagas" ou "Pagamento Recusado").
* **RNF05 (Mensurável / Desempenho):** O tempo de resposta para a validação inicial do token JWT e checagem de vagas não deve ultrapassar **2 segundos**, garantindo fluidez antes da tela de pagamento.
