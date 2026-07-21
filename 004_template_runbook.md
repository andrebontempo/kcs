---
tipo: runbook
serviço: [Nome do Serviço/Tecnologia]
público: [equipe-ti | administrador]
criticidade: [alta | critica]
plataforma: [Se aplicável, ex: Linux, Windows, Web]
versão: [Se aplicável, ex: PostgreSQL 17]
autor-responsavel: [Nome da Equipe, ex: Infraestrutura, Banco de Dados, Segurança]
revisao: [AAAA-MM, ex: 2027-01]
palavras-chave:
  - [palavra-chave-1]
  - [palavra-chave-2]
---

# Runbook — <operação crítica>

> **Instrução:** Substitua `<operação crítica>` no título acima pelo nome da rotina técnica crítica ou procedimento de emergência (ex: *Runbook — Recuperação completa pós corrupção do banco de dados*). Remova esta seção de instruções após o preenchimento.

## Objetivo
*Descreva resumidamente a finalidade desta operação crítica.*

## Quando executar
*Defina as condições exatas que justificam a execução deste runbook (ex: falha crítica de hardware, perda de sincronia de replicação, queda total do serviço).*

## Responsáveis
*Indique a equipe ou o papel profissional encarregado de executar a operação (ex: Administrador de Banco de Dados, Analista de Segurança).*

## Pré-requisitos
*Enumere os privilégios, credenciais de acesso temporário, ferramentas de monitoramento e recursos necessários antes de iniciar o runbook:*
* **[Pré-requisito 1]:** *[Descrição]*
* **[Pré-requisito 2]:** *[Descrição]*

## Passo a passo
*Detalhamento minucioso do procedimento de resposta e execução. Utilize listas ordenadas:*

1. **[Etapa 1]:** *[Descrição]*
   ```bash
   [comando_aqui]
   ```
2. **[Etapa 2]:** *[Descrição]*
   ```bash
   [comando_aqui]
   ```

## Pontos de verificação (Checkpoints)
*Indique como verificar o sucesso de etapas críticas intermediárias para evitar que um erro anterior comprometa o resto da operação.*

## Critério de sucesso
*Explique como confirmar se a operação foi concluída e se o sistema/serviço voltou ao seu estado ideal.*

## Plano de reversão (Rollback)
*Procedimento detalhado para desfazer as alterações e retornar o sistema ao estado anterior caso a execução do runbook falhe no meio do caminho.*

1. **[Passo 1 Rollback]:** *[Descrição]*
2. **[Passo 2 Rollback]:** *[Descrição]*

## Contatos (Escalonamento)
*Indique os contatos de plantão, especialistas ou gestores que devem ser acionados em caso de dúvidas ou se a reversão falhar.*
* **[Nome / Equipe]:** *[Telefone / Canal de comunicação / E-mail]*

## Referências
*Links internos e externos relevantes.*
* [Guia Técnico de Suporte](Link_Externo)
