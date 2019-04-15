---
ms.openlocfilehash: c9d6111edcfeec6852f23cc0768833de32e61022
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235054"
---
### <a name="error-codes-for-maxrequestlength-or-maxreceivedmessagesize-are-different"></a>Códigos de erro de maxRequestLength ou maxReceivedMessageSize são diferentes

|   |   |
|---|---|
|Detalhes|Mensagens nos serviços Web WCF hospedadas no IIS (Serviços de Informações da Internet) ou no ASP.NET Development Server que excedam maxRequestLength (no ASP.NET) ou maxReceivedMessageSize (no WCF) têm códigos de erro diferentes. O código de status HTTP foi alterado de 400 (Solicitação Incorreta) para 413 (Entidade de Solicitação Muito Longa), e as mensagens que excederam as configurações de maxRequestLength ou maxReceivedMessageSize lançarão uma exceção <xref:System.ServiceModel.ProtocolException?displayProperty=name>. Isso inclui os casos em que o modo de transferência é Streamed.|
|Sugestão|Essa alteração facilita a depuração nos casos em que o comprimento da mensagem excede os limites permitidos pelo ASP.NET ou WCF. É necessário modificar os códigos que executam o processamento baseado em um código de status HTTP 400.|
|Escopo|Microsoft Edge|
|Versão|4.5|
|Tipo|Tempo de execução|
