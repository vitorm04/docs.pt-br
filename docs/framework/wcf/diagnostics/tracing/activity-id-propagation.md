---
title: "Propagação de ID de atividade"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f7543a79f351cf1f1e9c6d8c316684d9bfc3155
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="activity-id-propagation"></a>Propagação de ID de atividade
Propagação acontece quando o rastreamento de atividades de ServiceModel está habilitado (ServiceModel propagação) ou desabilitado (propagação de atividade de usuário para usuário).  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>Rastreamento de atividade de ServiceModel está habilitado  
 Se ServiceModel ActivityTracing estiver habilitado, a propagação ocorre entre ProcessAction atividades.  
  
### <a name="server"></a>Servidor  
 Quando o `propagateActivity` atributo é definido como `true` no cliente e servidor, a ID do `ProcessAction` atividade no servidor é idêntica ao ID no propagadas `ActivityId` cabeçalho da mensagem.  
  
 Quando nenhum `ActivityId` cabeçalho está presente na mensagem (ou seja, `propagateActivity` = `false` no cliente), ou quando `propagateActivity` = `false` no servidor, o servidor gera uma nova ID de atividade.  
  
### <a name="client"></a>Cliente  
 Se o cliente tem thread único de forma síncrona, o cliente ignora as configurações de `propagateActivity` no cliente ou servidor. Em vez disso, a resposta é tratada na atividade de solicitação. Se o cliente é assíncrono ou síncrono multithread, `propagateActivity` = `true` no cliente e há um cabeçalho de identificação de atividade na mensagem enviada pelo servidor, o cliente recupera a ID de atividade da mensagem e transfere para o Atividade de ação do processo que contém a ID de atividade propagadas. Caso contrário, o cliente transfere de atividade de mensagens do processo para uma nova atividade de ação de processo. Essa transferência extra para uma nova atividade de ação de processo é feita para manter a consistência. Dentro dessa atividade, o cliente recupera a ID de atividade da atividade BeginCall do contexto de thread local, quando o thread está alocado para o processamento de mensagem de resposta. Em seguida, transfere para a atividade de ação do processo inicial.  
  
 Se o cliente é duplex, o cliente atua como servidor ao receber a mensagem.  
  
### <a name="propagation-in-fault-messages"></a>Propagação em mensagens de falha  
 Não há nenhuma diferença na manipulação válido e mensagens de falha. Se `propagateActivity` = `true`, a ID de atividade adicionada para os cabeçalhos de mensagem de falha SOAP é idêntica à atividade de ambiente.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>Rastreamento de atividade de ServiceModel está desabilitado  
 Se ServiceModel ActivityTracing estiver desabilitada, a propagação ocorre entre as atividades de código do usuário diretamente, sem passar por meio de atividades de ServiceModel. Uma ID de atividade definida pelo usuário também é propagada por meio do cabeçalho de identificação de atividade da mensagem.  
  
 Se `propagateActivity` = `true` e `ActivityTracing` = `off` para um ouvinte de rastreamento de ServiceModel (independentemente se o rastreamento está habilitado no ServiceModel), o seguinte acontece no cliente ou servidor:  
  
-   Enviar resposta ou solicitação de operação, a ID de atividade no TLS é propagada fora do código do usuário até que uma mensagem é formada. Um cabeçalho de identificação de atividade também será inserido na mensagem antes de serem enviado.  
  
-   No recebimento de solicitação ou resposta de recebimento, a ID da atividade é recuperada do cabeçalho da mensagem assim que o objeto de mensagem recebida é criado. A ID de atividade no TLS é propagada assim que a mensagem desaparecerá do escopo até que o código do usuário for atingido.  
  
 Essas ações garantem que o usuário rastreamentos aparecerão na mesma atividade se a propagação está ativa. No entanto, ele não dá nenhuma garantia em rastreamentos de ServiceModel. Rastreamentos de ServiceModel ocorrem em uma atividade de código do usuário apenas se o processamento desses rastreamentos for executado no mesmo thread em que a atividade de código do usuário foi definida.  
  
 Em geral, os rastreamentos de ServiceModel podem ser observados nos seguintes locais:  
  
-   Se o rastreamento de ServiceModel está desabilitado, todos os rastreamentos emitidos aparecem nas atividades do usuário. Se a propagação está habilitada no cliente e servidor, os rastreamentos serão na mesma atividade.  
  
-   Se o rastreamento de ServiceModel está habilitado, mas ActivityTracing está desabilitado, rastreamentos de usuário aparecem na mesma atividade se propagação estiver habilitada em ambas as extremidades. Rastreamentos de ServiceModel aparecem na atividade 0000 padrão, a menos que eles ocorrerem no mesmo thread que o processamento de código do usuário em que a atividade é definida inicialmente.  
  
-   Se o rastreamento de ServiceModel e ActivityTracing estiverem habilitados, rastreamentos de usuário aparecem nas atividades definidas pelo usuário e rastreamentos de ServiceModel aparecem nas atividades definidas ServiceModel. Propagação ocorre no nível de ServiceModel.
