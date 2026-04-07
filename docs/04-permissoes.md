# Matriz de Permissões

Esta matriz define o que cada perfil pode fazer dentro da plataforma de eventos.

Perfis:
- Admin
- Organizador
- Participante

Legenda de ações:
- C = Criar
- V = Ver
- E = Editar
- D = Deletar/Cancelar
- X = Não permitido

---

## Tabela de Permissões

| Recurso        | Admin        | Organizador        | Participante |
|----------------|-------------|--------------------|--------------|
| Evento         | C, V, E, D  | C, V, E            | V            |
| Inscrição      | V, D        | V                  | C, V, D      |
| Pagamento      | V           | V                  | V            |
| Check-in       | V           | C, V               | V            |
| Certificado    | V           | V                  | V            |
| Relatórios     | V           | V                  | X            |

---

## Observações importantes

- A aprovação de pagamento é automática e realizada por um gateway externo, não sendo uma ação manual de nenhum perfil.
- O check-in é registrado pelo Organizador, conforme regra de negócio do sistema.
- O certificado é liberado automaticamente após a confirmação do check-in, sendo apenas visualizado pelo Participante.
- O acesso aos relatórios é restrito ao Admin e Organizador, garantindo a segurança das informações.

---

## Descrição das permissões

### Admin
- Gerencia toda a plataforma
- Possui acesso completo aos dados e relatórios
- Atua na auditoria e monitoramento do sistema

### Organizador
- Cria e gerencia eventos
- Acompanha inscrições e check-ins
- Visualiza relatórios dos seus eventos

### Participante
- Realiza inscrição em eventos
- Acompanha status do pagamento
- Visualiza certificado após participação
