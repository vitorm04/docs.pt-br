---
title: "Rastreamento de atividades em segurança de mensagens"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: db9b05217bbbf91bfc3cd315801b4e511f82d04c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-tracing-in-message-security"></a>Rastreamento de atividades em segurança de mensagens
Este tópico descreve o rastreamento de atividades para o processamento de segurança, o que acontece no seguinte três fases.  
  
-   Troca de negociação/SCT. Isso pode acontecer no transporte posteriormente (por meio de troca de dados binários) ou camada de mensagem (por meio de trocas de mensagens SOAP).  
  
-   Mensagem criptografia/descriptografia, com a autenticação e verificação de assinatura. Rastreamentos aparecem na atividade de ambiente, normalmente "ação de processo".  
  
-   Autorização e verificação. Isso pode acontecer localmente ou quando a comunicação entre pontos de extremidade.  
  
## <a name="negotiationsct-exchange"></a>Troca de negociação/SCT  
 Na fase de troca de negociação/SCT, são criados dois tipos de atividade no cliente: "Definir a sessão segura" e "Fechar sessão segura". "Configurar sessão segura" abrange rastreamentos de trocas de mensagens a primeira/RSTR/SCT, enquanto "Fechar sessão segura" inclui rastreamentos da mensagem de cancelamento.  
  
 No servidor, cada solicitação/resposta para a primeira/RSTR/SCT aparece em sua própria atividade. Se `propagateActivity` = `true` no servidor e para cliente, atividades no servidor têm a mesma ID e aparecem juntos na "instalação seguro sessão" quando visualizado no Visualizador de rastreamento de serviço.  
  
 Esse modelo de rastreamento de atividade é válido para a autenticação NTLM, autenticação de certificado e autenticação de senha/nome de usuário.  
  
 A tabela a seguir lista as atividades e rastreamentos para negociação e exchange SCT.  
  
||Ocorre quando a negociação/SCT trocar de tempo|Atividades|rastreamentos|  
|-|-------------------------------------------------|----------------|------------|  
|Transporte seguro<br /><br /> SSL (HTTPS)|Na primeira mensagem recebida.|Rastreamentos são emitidos na atividade de ambiente.|-Exchange rastreamentos<br />-Proteger o canal estabelecido<br />-Compartilhamento segredos obtidos.|  
|Camada de mensagem segura<br /><br /> (WSHTTP)|Na primeira mensagem recebida.|No cliente:<br /><br /> -"Instalação sessão segura" fora de processo "ação" da primeira mensagem, para cada solicitação/resposta para a primeira/RSTR/SCT.<br />-"Fechar a sessão segura" para a troca de cancelamento, fora de "atividade Proxy fechar". Essa atividade pode acontecer fora de algumas outras atividades ambiente, dependendo de quando a sessão segura está fechada.<br /><br /> No servidor:<br /><br /> -Uma atividade de "Processo ação" para cada solicitação/resposta para a primeira/SCT/Cancelar no servidor. Se `propagateActivity` = `true`, atividades RSTR/primeira/SCT são mescladas com "Definir a sessão de segurança" e Cancelar é mesclada com a atividade "Fechar" do cliente.<br /><br /> Há duas etapas para "Definir a sessão segura":<br /><br /> 1.  Negociação de autenticação. Isso é opcional se o cliente já tiver as credenciais apropriadas. Essa fase pode ser feita por meio do transporte seguro, ou as trocas de mensagens. No último caso, 1 ou 2 trocas de primeira/RSTR podem acontecer. Essas trocas, os rastreamentos são emitidos em novas atividades de solicitação/resposta criadas anteriormente.<br />2.  Proteger o estabelecimento da sessão SCT (), no qual uma troca de primeira/RSTR acontece aqui. Isso tem as mesmas atividades de ambiente, conforme descrito anteriormente.|-Exchange rastreamentos<br />-Proteger o canal estabelecido<br />-Compartilhamento segredos obtidos.|  
  
> [!NOTE]
>  No modo de segurança misto, autenticação de negociação ocorre em trocas de binárias, mas SCT acontece na troca de mensagens. No modo de transporte puro, negociação ocorre apenas no transporte sem atividades adicionais.  
  
## <a name="message-encryption-and-decryption"></a>Descriptografia e criptografia de mensagens  
 A tabela a seguir lista as atividades e rastreamentos de criptografia/descriptografia de mensagem, bem como autenticação de assinatura.  
  
||Transporte seguro<br /><br /> (HTTPS, SSL) e a camada de mensagem de segurança<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Hora em que mensagem criptografia/descriptografia, bem como autenticação de assinatura acontece|Na mensagem recebida|  
|Atividades|Rastreamentos são emitidos na atividade de ProcessAction no cliente e no servidor.|  
|rastreamentos|-sendSecurityHeader (remetente):<br />-Mensagem de entrada<br />-Criptografar dados de solicitação<br />-receiveSecurityHeader (destinatário):<br />-Verificar a assinatura<br />-Descriptografar dados de resposta<br />-Autenticação|  
  
> [!NOTE]
>  No modo de transporte puro, mensagem de criptografia/descriptografia ocorre apenas no transporte sem atividades adicionais.  
  
## <a name="authorization-and-verification"></a>Autorização e verificação  
 A tabela a seguir lista as atividades e rastreamentos para autorização.  
  
||Quando ocorre a autorização do tempo|Atividades|rastreamentos|  
|-|-------------------------------------|----------------|------------|  
|Local (padrão)|Depois que a mensagem é descriptografada no servidor|Rastreamentos são emitidos na atividade de ProcessAction no servidor.|Usuário autorizado.|  
|Remoto|Depois que a mensagem é descriptografada no servidor|Rastreamentos são emitidos em uma nova atividade invocada pela atividade ProcessAction.|Usuário autorizado.|
