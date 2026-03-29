# Fluxos do Sistema - Plataforma de Eventos

**Link do Whimsical:** [https://whimsical.com/samuel1776/modelagem-de-fluxo-XJ5dFDmCUJoYYFVmh7RBg9]
*`![Fluxo de Eventos](/assets/Modelagem%20de%20fluxo.png)`*

### Resumo dos Fluxogramas
Os diagramas mapeiam as duas jornadas principais da Plataforma de Eventos. O primeiro fluxo, focado em **Inscrição e Pagamento**, detalha a validação de segurança via token JWT (ponto crítico de checagem para garantir o acesso restrito) e o processo de verificação de vagas. Ele ilustra a integração com o gateway externo de pagamento, tratando as exceções e os caminhos de sucesso, recusa ou pendência. Já o segundo fluxo, de **Check-in e Certificado**, demonstra o processo de validação da presença do Participante no dia do evento e as regras de negócio para a emissão do certificado, incluindo o tratamento de erros esperados (como check-in fora do horário).