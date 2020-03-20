---
title: Cenários assíncronos usando HTTP, TCP ou pipe nomeado
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 6ae96c0aac5010adf37eb78ed57d1549885ece58
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185779"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Cenários assíncronos usando HTTP, TCP ou pipe nomeado
Este tópico descreve as atividades e transferências para diferentes cenários de solicitação/resposta assíncronas, com solicitações multithreaded usando HTTP, TCP ou pipe nomeado.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Solicitação/Resposta assíncrona sem erros  
 Esta seção descreve as atividades e transferências para um cenário assíncrono de solicitação/resposta, com clientes multithreaded.  
  
 A atividade do `beginCall` chamador `endCall` termina quando retorna e retorna. Se um retorno de chamada for chamado, o retorno de chamada retorna.  
  
 A atividade chamada `beginCall` termina `endCall` quando retorna, retorna ou quando o retorno de chamada retorna se for chamado dessa atividade.  
  
### <a name="asynchronous-client-without-callback"></a>Cliente assíncrono sem Retorno de Chamada  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>A propagação é habilitada em ambos os lados, usando HTTP  
 ![Cliente assíncrono sem retorno de chamada onde propagaçãoActivity é definido como verdadeiro em ambos os lados.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)
  
 Se `propagateActivity=true`, ProcessMessage indicar para qual atividade processAction será transferida.  
  
 Para cenários baseados em HTTP, o ReceiveBytes é invocado na primeira mensagem a ser enviada e existe durante toda a vida útil da solicitação.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>A propagação é desativada em ambos os lados, usando HTTP  
 Se `propagateActivity=false` em ambos os lados, processMessage não indicar para qual atividade processAction será transferida. Portanto, uma nova atividade temporária processAction com um novo ID é invocada. Quando a resposta assíncrona é compatível com a solicitação no código ServiceModel, o ID de atividade pode ser recuperado do contexto local. A atividade processaction real pode ser transferida para com esse ID.  
  
 ![Cliente assíncrono sem retorno de chamada onde propagaatividade é definido como falso em ambos os lados.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  

 Para cenários baseados em HTTP, o ReceiveBytes é invocado na primeira mensagem a ser enviada e existe durante toda a vida útil da solicitação.  
  
 Uma atividade process action é criada em um `propagateActivity=false` cliente assíncrono quando no chamador ou no callee, e quando a mensagem de resposta não inclui um cabeçalho de ação.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>A propagação está ativada em ambos os lados, usando TCP ou Pipe nomeado  
 ![Cliente assíncrono sem retorno de chamada onde propagaçãoAAtividade é definida como verdadeira em ambos os lados e chamada pipe/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Para um cenário baseado em Pipe ou TCP, o ReceiveBytes é invocado quando o cliente é aberto e existe durante toda a vida útil da conexão.  
  
 Semelhante à primeira imagem, se `propagateActivity=true`, ProcessMessage indica para qual atividade processAction transferir.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>A propagação é desativada em ambos os lados, usando TCP ou Pipe nomeado  
 Para um cenário baseado em Pipe ou TCP, o ReceiveBytes é invocado quando o cliente é aberto e existe durante toda a vida útil da conexão.  
  
 Semelhante à segunda imagem, se `propagateActivity=false` em ambos os lados, processMessage não indica qual atividade processAction transferir. Portanto, uma nova atividade temporária processAction com um novo ID é invocada. Quando a resposta assíncrona é compatível com a solicitação no código ServiceModel, o ID de atividade pode ser recuperado do contexto local. A atividade processaction real pode ser transferida para com esse ID.  
  
 ![Cliente assíncrono sem retorno de chamada onde propagaçãoActivity é definido como falso em ambos os lados e chamado pipe/TCP.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  

### <a name="asynchronous-client-with-callback"></a>Cliente assíncrono com Callback  
 Este cenário adiciona atividades G e A', para o retorno de chamada e `endCall`, e suas transferências para dentro/para fora.  
  
 Esta seção só `propagateActivity` = `true`demonstra o uso de HTTP com . No entanto, as atividades adicionais e transferências `propagateActivity` = `false`também se aplicam aos outros casos (isto é, usando TCP ou Named-Pipe).  
  
 O retorno de chamada cria uma nova atividade (G) quando o cliente liga para o código do usuário para notificar que os resultados estão prontos. Em seguida, `endCall` o código do usuário chama dentro do retorno de chamada (como mostrado na Figura 5) ou fora do retorno de chamada (Figura 6). Como não se sabe `endCall` de qual atividade do usuário `A’`está sendo chamada, essa atividade é rotulada . É possível que A' possa ser idêntico ou diferente de A.  
  
 ![Mostra um cliente assíncrono com retorno de chamada, chamada final em retorno de chamada.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  

 ![Mostra um cliente assíncrono com retorno de chamada, chamada de chamada externa.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  

### <a name="asynchronous-server-with-callback"></a>Servidor assíncrono com retorno de chamada  
 ![Mostra um servidor assíncrono com retorno de chamada.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  

 A pilha de canais chama de volta o cliente no Message Receive: os rastreamentos para esse processamento são emitidos na própria atividade ProcessRequest.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Solicitação/resposta assíncrona com erros  
 Erros de mensagem `endCall`de falha são recebidos durante . Caso contrário, as atividades e transferências são semelhantes aos cenários anteriores.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Caminho síncrono unidirecional com ou sem erros  
 Nenhuma resposta ou falha é devolvida ao cliente.
