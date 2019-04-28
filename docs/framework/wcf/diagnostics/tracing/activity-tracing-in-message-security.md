---
title: Rastreamento de atividades em segurança de mensagens
ms.date: 03/30/2017
ms.assetid: 68862534-3b2e-4270-b097-8121b12a2c97
ms.openlocfilehash: c3bd36598fd903dc016959149e563174624d084b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61912646"
---
# <a name="activity-tracing-in-message-security"></a>Rastreamento de atividades em segurança de mensagens
Este tópico descreve o rastreamento de atividade para processamento de segurança, o que acontece a seguir três fases.  
  
- Troca de negociação/SCT. Isso pode acontecer no transporte posteriormente (por meio de troca de dados binários) ou camada de mensagem (por meio de trocas de mensagens SOAP).  
  
- Mensagem de criptografia/descriptografia, com autenticação e verificação de assinatura. Os rastreamentos aparecem na atividade de ambiente, normalmente "ação de processo".  
  
- A autorização e verificação. Isso pode acontecer localmente ou quando a comunicação entre pontos de extremidade.  
  
## <a name="negotiationsct-exchange"></a>Troca de negociação/SCT  
 Na fase de negociação/SCT de exchange, são criados dois tipos de atividade no cliente: "Configurar a sessão segura" e "Fechar sessão segura". "Configurar a sessão segura" abrange os rastreamentos para as trocas de mensagens RSTR/RST/SCT, enquanto "Fechar sessão segura" inclui os rastreamentos da mensagem de cancelamento.  
  
 No servidor, cada solicitação/resposta de RST/RSTR/SCT aparece em sua própria atividade. Se `propagateActivity` = `true` sobre o cliente e servidor, as atividades no servidor têm a mesma ID em aparecem juntas na "Instalação Secure sessão" quando visualizado por meio do Visualizador de rastreamento de serviço.  
  
 Esse modelo de rastreamento de atividade é válido para a autenticação NTLM, autenticação de certificado e autenticação de nome e senha do usuário.  
  
 A tabela a seguir lista as atividades e os rastreamentos para negociação e exchange SCT.  
  
||Quando o exchange de negociação/SCT acontece de hora|Atividades|Rastreamentos|  
|-|-------------------------------------------------|----------------|------------|  
|Transporte seguro<br /><br /> (HTTPS, SSL)|Na primeira mensagem recebida.|Rastreamentos são emitidos na atividade de ambiente.|-Exchange rastreamentos<br />-Proteger o canal estabelecido<br />-Compartilhamento de segredos obtidos.|  
|Camada de mensagem segura<br /><br /> (WSHTTP)|Na primeira mensagem recebida.|No cliente:<br /><br /> -"Instalação segura Session" fora de "Processo de ação" da primeira mensagem, para cada solicitação/resposta de RST/RSTR/SCT.<br />-"Fechar sessão segura" para a troca de cancelar, fora da "atividade de Proxy fechar". Essa atividade pode acontecer fora de alguma outra atividade ambiente, dependendo de quando a sessão segura é fechada.<br /><br /> No servidor:<br /><br /> -Uma atividade de "Ação de processo" para cada solicitação/resposta de RST/SCT/Cancelar no servidor. Se `propagateActivity` = `true`, atividades RST/RSTR/SCT são mescladas com "Definir a segurança Session" e Cancelar é mesclada com a atividade "Fechar" do cliente.<br /><br /> Há dois estágios para "Definir backup Session seguro":<br /><br /> 1.  Negociação de autenticação. Isso é opcional se o cliente já tiver as credenciais apropriadas. Essa fase pode ser feita por meio de transporte seguro, ou por meio de trocas de mensagens. No último caso, trocas RST/RSTR 1 ou 2 podem acontecer. Para essas trocas, os rastreamentos são emitidos em novas atividades de solicitação/resposta criadas anteriormente.<br />2.  Proteger o estabelecimento da sessão (SCT), no qual uma troca RST/RSTR ocorre aqui. Isso tem as mesmas atividades de ambientes, conforme descrito anteriormente.|-Exchange rastreamentos<br />-Proteger o canal estabelecido<br />-Compartilhamento de segredos obtidos.|  
  
> [!NOTE]
>  No modo de segurança mista, autenticação de negociação ocorre em trocas de binárias, mas SCT acontece na troca de mensagens. No modo de transporte puro, negociação ocorre apenas no transporte com nenhuma outra atividade.  
  
## <a name="message-encryption-and-decryption"></a>Descriptografia e criptografia de mensagens  
 A tabela a seguir lista as atividades e os rastreamentos de criptografia/descriptografia de mensagem, bem como autenticação de assinatura.  
  
||Transporte seguro<br /><br /> (HTTPS, SSL) e proteger a camada de mensagem<br /><br /> (WSHTTP)|  
|-|---------------------------------------------------------------------------------|  
|Hora em que a criptografia/descriptografia da mensagem, assim como acontece de autenticação de assinatura|Na mensagem recebida|  
|Atividades|Rastreamentos são emitidos na atividade de ProcessAction no cliente e servidor.|  
|Rastreamentos|-   sendSecurityHeader (sender):<br />-Mensagem de entrada<br />-Criptografar dados de solicitação<br />-   receiveSecurityHeader (receiver):<br />-Verifique se a assinatura<br />-Descriptografar os dados de resposta<br />-Autenticação|  
  
> [!NOTE]
>  No modo de transporte puro, criptografia/descriptografia mensagem ocorre apenas no transporte com nenhuma outra atividade.  
  
## <a name="authorization-and-verification"></a>Autorização e verificação  
 A tabela a seguir lista as atividades e os rastreamentos para autorização.  
  
||Quando a autorização acontece de hora|Atividades|Rastreamentos|  
|-|-------------------------------------|----------------|------------|  
|Local (padrão)|Depois que a mensagem é descriptografada no servidor|Rastreamentos são emitidos na atividade de ProcessAction no servidor.|Usuário autorizado.|  
|Remoto|Depois que a mensagem é descriptografada no servidor|Rastreamentos são emitidos em uma nova atividade invocada pela atividade ProcessAction.|Usuário autorizado.|
