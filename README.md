# VALLOO – Projeto Conformidade Cadastral

**MANUAL OPERACIONAL – Equipe de Relacionamento**  
Março 2026 · **CONFIDENCIAL**

*Agradecimento especial à equipe responsável pelo desenvolvimento: Silver Squad (Deivid, Alisson e Carla).*

> Este documento é de uso interno e confidencial da Valloo. Não deve ser compartilhado fora da organização sem autorização prévia.

---

## Sumário

1. [Objetivo](#1-objetivo)  
2. [Origem Regulatória](#2-origem-regulatória)  
3. [Como Funciona (IRREGULARES)](#3-como-funciona-irregulares)  
4. [Situações Bloqueadas (Documentos Irregulares)](#4-situações-bloqueadas-documentos-irregulares)  
5. [Mensagens ao Cliente](#5-mensagens-ao-cliente)  
6. [Impactos](#6-impactos-apenas-irregulares)  
7. [Scripts de Relacionamento](#7-scripts-de-relacionamento-irregulares)  
8. [Exemplos Práticos](#8-exemplos-práticos-apenas-irregulares)  
9. [FAQ Rápido](#9-faq-rápido-para-atendimento)  

---

## 1. Objetivo

Garantir que todos os cadastros realizados no sistema **Issuer** contenham documentos (CPF/CNPJ) com situação cadastral **regular** na Receita Federal, impedindo a inclusão de pessoas físicas ou jurídicas em situação irregular.

**Benefícios:**

- Mitigação de riscos regulatórios.  
- Prevenção de fraudes de identidade.  
- Conformidade com boas práticas de KYC (*Know Your Customer*).  
- Proteção da reputação da Valloo e de seus clientes.

> **FOCO EXCLUSIVO: Documentos IRREGULARES**
>
> - Bloqueia **novos cadastros** com documentos irregulares.  
> - Inativa **contas existentes** com documentos irregulares.  
> - Documentos **regulares** funcionam normalmente.

---

## 2. Origem Regulatória

### Base Legal

- **Resolução BACEN 4.753/2019** – KYC e diligência devida.  
- **Circular BACEN 3.978/2020** – Prevenção à Lavagem de Dinheiro.  
- **Lei 9.613/1998** – Lei de Lavagem de Dinheiro.

A funcionalidade atende às exigências de **validação obrigatória da situação cadastral** para mitigação de riscos em operações financeiras.

---

## 3. Como Funciona (IRREGULARES)

### 3.1. Fluxo Visual

```text
CPF/CNPJ informado
        ↓
   Consulta Receita Federal
        ↓
   Documento irregular?
        ↓
   ├── SIM  → ❌ Bloqueia cadastro / Inativa conta existente
   └── NÃO  → ✅ Libera cadastro / Mantém conta ativa
```

### 3.2. O que acontece automaticamente
Toda tentativa de cadastro com CPF/CNPJ passa pela validação.

A consulta é realizada em tempo real com a Receita Federal.

O sistema bloqueia cadastros com documentos irregulares.

Contas já existentes com documento irregular são inativadas automaticamente.

Não há intervenção manual necessária por parte das equipes operacionais.



## 4. Situações Bloqueadas (Documentos Irregulares)

### 4.1. CPF – Situações que impedem cadastro

| ❌ Situação       | Impacto            |
| ---------------- | ------------------ |
| Suspenso         | Bloqueia + Inativa |
| Cancelado        | Bloqueia + Inativa |
| Titular Falecido | Bloqueia + Inativa |
| Nulo             | Bloqueia + Inativa |


### 4.2. CNPJ – Situações que impedem cadastro

| ❌ Situação | Impacto            |
| ---------- | ------------------ |
| Suspenso   | Bloqueia + Inativa |
| Cancelado  | Bloqueia + Inativa |
| Baixado    | Bloqueia + Inativa |
| Inapto     | Bloqueia + Inativa |

❌ Situação cadastral não permite o cadastro.
Verifique a regularidade do documento na Receita Federal antes de tentar novamente.


## 5. Mensagens ao Cliente

### 5.1. Novos cadastros irregulares
Quando o documento estiver irregular na Receita Federal:

❌ Situação cadastral não permite o cadastro.
Verifique a regularidade do documento na Receita Federal.

Quando o CPF/CNPJ não existir na base da Receita Federal:

❌ CPF/CNPJ não existe na Receita Federal.
Verifique os dados informados e utilize um documento válido.

### 5.2. Características das mensagens
São apresentadas imediatamente após a consulta.

Não revelam detalhes da situação cadastral (por segurança).

Orientam o usuário a verificar a situação diretamente na Receita Federal.


## 6. Impactos (APENAS IRREGULARES)

### 6.1. Impacto por público

| Público           | Impacto                                              |
| ----------------- | ---------------------------------------------------- |
| Novos Usuários    | ❌ Não conseguem cadastrar documentos irregulares.    |
| Contas Existentes | ❌ Inativadas automaticamente se documento irregular. |



### 6.2. Documentos Regulares

Documentos REGULARES: ✅ Zero impacto – funcionam normalmente, sem qualquer bloqueio ou restrição adicional.

## 7. Scripts de Relacionamento (IRREGULARES)
Sugestões de scripts para uso pela Equipe de Relacionamento em atendimentos.

## 7.1. Para novos cadastros bloqueados

Script sugerido:
> "O cadastro foi bloqueado porque o CPF/CNPJ está irregular na Receita Federal (por exemplo: suspenso, cancelado, inapto, entre outros).
> Solução: É necessário regularizar o documento diretamente na Receita Federal. Após a regularização, um novo cadastro poderá ser realizado normalmente."


7.2. Para contas inativadas

Script sugerido:
>"Sua conta foi inativada automaticamente porque o CPF/CNPJ consta como irregular na Receita Federal (detecção feita hoje pelo nosso sistema).
Situações afetadas: Suspenso, Cancelado, Baixado, Inapto, Titular Falecido ou Nulo.
Solução:

Regularizar a situação do CPF/CNPJ diretamente na Receita Federal.
>Após a regularização, solicitar a reativação da conta pelos nossos canais de atendimento."



## 8. Exemplos Práticos (APENAS IRREGULARES)

### 8.1. Exemplo 1 – Novo cadastro suspenso
Situação: CPF consta como Suspenso na Receita Federal.

> Ação do sistema: ❌ Cadastro bloqueado.

Mensagem apresentada:

> "Situação cadastral não permite o cadastro."

### 8.2. Exemplo 2 – Conta existente baixada
Situação: CNPJ de conta já existente passa a constar como Baixado.

> Ação do sistema: ❌ Conta inativada pela rotina diária automática.

Notificação sugerida ao cliente:

> "Conta inativada – CNPJ baixado na Receita Federal."

### 8.3. Exemplo 3 – Cadastro via arquivo (lote)
Situação: Arquivo com 100 registros enviados para cadastro.

Resultado: 5 registros com documentos irregulares são rejeitados.

Ação do sistema:

Os 95 registros regulares são processados normalmente.

O arquivo de retorno indica as rejeições, detalhando a situação cadastral de cada documento irregular.



## 9. FAQ Rápido para Atendimento
### 9.1. "Minha conta foi inativada! Por quê?"
Resposta sugerida:
> "Nossa rotina automática detectou que o CPF/CNPJ está irregular na Receita Federal (por exemplo: suspenso ou inapto).

> Para voltar a utilizar a conta, é necessário regularizar o documento na Receita Federal e, em seguida, solicitar a reativação pelos nossos canais de atendimento."

### 9.2. "Essa inativação é manual?"
Resposta sugerida:
> "Não. A inativação é automática e ocorre diariamente, para garantir conformidade com as normas do Banco Central. Todas as contas passam por essa validação recorrente."

### 9.3. "Posso cadastrar mesmo assim?"
Resposta sugerida:
> "Não é possível concluir novos cadastros com CPF/CNPJ irregular.

> Para contas já existentes, quando o documento se torna irregular, a conta é inativada automaticamente pelo sistema."
