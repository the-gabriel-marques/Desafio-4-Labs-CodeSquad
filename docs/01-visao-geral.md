# Visão Geral - Plataforma de Eventos com Check-in

### O que é e para quem serve
A Plataforma de Eventos com Check-in é um sistema web criado para centralizar e facilitar a gestão de ponta a ponta de eventos. Ela atende tanto aos **organizadores**, que precisam de uma ferramenta confiável para controlar a venda de ingressos e a presença no dia, quanto aos **participantes**, oferecendo uma jornada fluida que vai desde a inscrição até a emissão do certificado.

### Perfis de Usuário
O sistema possui controle de acesso baseado em três perfis principais:

* **Admin:** É o administrador global do sistema. Tem acesso irrestrito para monitorar a plataforma, gerenciar os Organizadores, atuar no suporte técnico e garantir que as regras de negócio e segurança sejam cumpridas.
* **Organizador:** É o dono do evento. É responsável por criar as páginas dos eventos, gerenciar a quantidade de vagas, acompanhar o status dos pagamentos e controlar a operação de check-in no dia do evento.
* **Participante:** É o usuário final. Acessa a plataforma para visualizar os eventos disponíveis, realizar sua inscrição, efetuar o pagamento, realizar o check-in de presença e baixar seu certificado após a conclusão.

### Fluxos Principais
O escopo inicial do projeto (Semana 2) foca em garantir o funcionamento perfeito de dois processos críticos:

1.  **Inscrição + Pagamento:** Engloba a jornada do Participante desde o clique em "Inscrever-se" até a comunicação com o gateway de pagamento, tratando o bloqueio de vagas, tempo de expiração e os cenários de pagamento aprovado, recusado ou pendente.
2.  **Check-in + Certificado:** Cobre a operação no dia do evento, validando se o Participante está no local e horário corretos para confirmar a presença, liberando em seguida a geração automática do certificado, com tratamento para exceções (como check-in fora do horário).
