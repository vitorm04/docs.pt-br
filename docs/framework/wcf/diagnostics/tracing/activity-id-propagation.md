---
title: Propagação de ID de atividade
ms.date: 03/30/2017
ms.assetid: cd1c1ae5-cc8a-4f51-90c9-f7b476bcfe70
ms.openlocfilehash: 642d4da49f90d3fc6f2b0dfc9896d724acb075b5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651818"
---
# <a name="activity-id-propagation"></a>Propagação de ID de atividade
Propagação ocorre quando o rastreamento de atividade de ServiceModel é habilitado (ServiceModel propagação) ou desabilitado (propagação de atividade de usuário para usuário).  
  
## <a name="servicemodel-activity-tracing-is-enabled"></a>O rastreamento de atividade de ServiceModel está habilitado  
 Se ServiceModel ActivityTracing estiver habilitado, a propagação ocorre entre atividades ProcessAction.  
  
### <a name="server"></a>Servidor  
 Quando o `propagateActivity` atributo é definido como `true` no cliente e servidor, a ID do `ProcessAction` atividade no servidor é idêntica à ID no propagada `ActivityId` cabeçalho da mensagem.  
  
 Quando nenhum `ActivityId` cabeçalho está presente na mensagem (ou seja, `propagateActivity` = `false` no cliente), ou quando `propagateActivity` = `false` no servidor, o servidor gera uma nova ID de atividade.  
  
### <a name="client"></a>Cliente  
 Se o cliente tem thread único de forma síncrona, o cliente ignora quaisquer configurações de `propagateActivity` no cliente ou servidor. Em vez disso, a resposta é tratada na atividade de solicitação. Se o cliente é síncrona ou assíncrona multithreaded, `propagateActivity` = `true` no cliente e há um cabeçalho de ID de atividade na mensagem enviada pelo servidor, o cliente recupera a ID de atividade de mensagem e transfere para o Atividade de ação do processo que contém a ID de atividade propagada. Caso contrário, o cliente transfere de atividade de mensagens do processo para uma nova atividade de ação de processo. Essa transferência extra para uma nova atividade de ação de processo é feita para manter a consistência. Dentro desta atividade, o cliente recupera a ID de atividade da atividade BeginCall do contexto de thread local, quando o thread é alocado para o processamento de mensagem de resposta. Em seguida, transfere para a atividade de ação do processo inicial.  
  
 Se o cliente duplex, o cliente atua como servidor no recebimento da mensagem.  
  
### <a name="propagation-in-fault-messages"></a>Propagação em mensagens de falha  
 Não há nenhuma diferença na manipulação válido e mensagens de falha. Se `propagateActivity` = `true`, a ID de atividade adicionada para os cabeçalhos de mensagem de falha SOAP é idêntica à atividade de ambiente.  
  
## <a name="servicemodel-activity-tracing-is-disabled"></a>Rastreamento de atividade de ServiceModel está desabilitado  
 Se ServiceModel ActivityTracing estiver desabilitada, a propagação ocorre entre atividades de código do usuário diretamente sem passar por meio de atividades de ServiceModel. Uma ID de atividade definida pelo usuário também é propagada por meio do cabeçalho da ID de atividade de mensagem.  
  
 Se `propagateActivity` = `true` e `ActivityTracing` = `off` para um ouvinte de rastreamento de ServiceModel (independentemente se o rastreamento está habilitado no ServiceModel), a seguir ocorrem no cliente ou servidor:  
  
- Após enviar a resposta ou solicitação de operação, a ID de atividade no TLS é propagada fora do código do usuário até que uma mensagem é formada. Um cabeçalho de ID de atividade também é inserido na mensagem antes de serem enviado.  
  
- No recebimento de solicitação ou recebimento de resposta, a ID da atividade é recuperada do cabeçalho da mensagem assim que o objeto de mensagem recebida é criado. A ID de atividade no TLS é propagada, assim que a mensagem desaparecerá de escopo até que o código do usuário seja atingido.  
  
 Essas ações garantem que o usuário rastreamentos aparecerão na mesma atividade se a propagação está ativa. No entanto, ele faz nenhuma garantia em rastreamentos de ServiceModel. Rastreamentos de ServiceModel ocorrerem em uma atividade de código do usuário apenas se o processamento desses rastreamentos for executado no mesmo thread em que a atividade de código do usuário foi definida.  
  
 Em geral, os rastreamentos de ServiceModel podem ser observados nos seguintes locais:  
  
- Se o rastreamento de ServiceModel está desabilitado, todos os rastreamentos emitidos aparecem em atividades do usuário. Se a propagação é habilitada no cliente e servidor, esses rastreamentos será na mesma atividade.  
  
- Se o rastreamento de ServiceModel está habilitado, mas ActivityTracing estiver desabilitado, os rastreamentos de usuário aparecem na mesma atividade se a propagação é habilitada em ambas as extremidades. Os rastreamentos de ServiceModel aparecem na atividade de 0000 padrão, a menos que elas ocorrerem no mesmo thread que o processamento de código do usuário em que a atividade está inicialmente definida.  
  
- Se o rastreamento de ServiceModel e ActivityTracing estiverem habilitadas, os rastreamentos do usuário aparecem nas atividades definidas pelo usuário e os rastreamentos de ServiceModel aparecem nas atividades definidas de ServiceModel. Propagação ocorre no nível de ServiceModel.
