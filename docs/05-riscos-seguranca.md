# Riscos de Segurança

Descrição dos Riscos identificados na plataforma, com seus respectivos cenários, impactos e formas de mitigação.

---

## 1. Acesso indevido (Autorização)

### Cenário
Um participante tenta acessar funcionalidades restritas, como editar eventos ou visualizar relatórios administrativos.

### Impacto
- Comprometimento da Confidencialidade: Exposição de dados sensíveis
- Perda de Integridade: Alteração ou exclusão não autorizada de eventos e configurações críticas
- Escala de Privilégio: Comprometimento da integridade do sistema, Usuários comuns assumindo funções de administrador/organizador

### Mitigação
- RBAC & ABAC: Implementar Controle de Acesso Baseado em Funções (Role-Based) e Atributos (Attribute-Based)
- Backend-First Validation: Não confiar somente em verificações de interface (UI/Frontend); cada requisição ao servidor deve validar a propriedade do recurso solicitado
- Deny by Default: Configurar o sistema para que, por padrão, todo acesso seja negado, exigindo permissão explícita para cada endpoint

---

## 2. Exposição de Dados Sensíveis e Pessoais (Dados)

### Cenário
A plataforma expõe informações identificáveis (PII) através de logs de erro detalhados, respostas excessivas da API (Excessive Data Exposure) ou tráfego de rede não criptografado, permitindo a interceptação ou extração massiva de dados.

### Impacto
- Sanções Jurídicas: Multas pesadas e processos judiciais baseados na LGPD (Lei Geral de Proteção de Dados)
- Danos Reputacionais: Perda crítica de credibilidade perante o mercado e usuários
- Risco de Engenharia Social: Dados vazados podem ser usados para ataques direcionados (phishing) contra os usuários

### Mitigação
- Data Masking & Minimization: Retornar apenas o estritamente necessário nas APIs.
- Utilizar HTTPS em todas as requisições
- Sanitização de Logs: Restringir dados retornados pela API (princípio do mínimo necessário), implementar filtros para garantir que senhas, tokens e dados sensíveis não sejam registrados em arquivos de log do servidor.

---

## 3. Falha de autenticação e Gestão de Sessão (Login/Sessão)

### Cenário
Exploração de mecanismos de login fracos por meio de ataques de força bruta, preenchimento de credenciais (Credential Stuffing) ou sequestro de sessão (Session Hijacking) devido a tokens de longa duração ou falta de expiração.

### Impacto
- Acesso indevido a contas
- Ações maliciosas em nome do usuário
- Comprometimento de dados

### Mitigação
- Exigir senhas fortes (mínimo de caracteres e complexidade)
- Implementar segundo fator de autenticação para contas com privilégios elevados
- Bloquear após múltiplas tentativas (ex: 5 tentativas)
- Implementar autenticação com token e expiração de sessão
