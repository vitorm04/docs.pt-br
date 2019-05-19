---
title: Cenários assíncronos usando HTTP, TCP ou pipe nomeado
ms.date: 03/30/2017
ms.assetid: a4d62402-43a4-48a4-9ced-220633ebc4ce
ms.openlocfilehash: 48957ec0abd1b4b0623f9b613fcd94912a38845b
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881673"
---
# <a name="asynchronous-scenarios-using-http-tcp-or-named-pipe"></a>Cenários assíncronos usando HTTP, TCP ou pipe nomeado
Este tópico descreve as atividades e transferências para cenários diferentes de solicitação/resposta assíncrono, com solicitações de vários threads usando HTTP, TCP ou pipe nomeado.  
  
## <a name="asynchronous-requestreply-without-errors"></a>Solicitação/resposta assíncrona sem erros  
 Esta seção descreve as atividades e os transfere para um cenário de solicitação/resposta assíncrono, com clientes de vários threads.  
  
 A atividade do chamador termina quando `beginCall` retorna, e `endCall` retorna. Se um retorno de chamada é chamado, o retorno de chamada retorna.  
  
 A atividade de chamada termina quando `beginCall` retorna, `endCall` retorna, ou quando o retorno de chamada retorna se ele foi chamado a partir dessa atividade.  
  
### <a name="asynchronous-client-without-callback"></a>Cliente assíncrono sem retorno de chamada  
  
#### <a name="propagation-is-enabled-on-both-sides-using-http"></a>Propagação está habilitada nos dois lados, usando HTTP  
 ![Cliente assíncrono com nenhum retorno de chamada onde propagateActivity está definida como true em ambos os lados.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-no-callback.gif)   
  
 Se `propagateActivity` = `true`, ProcessMessage indica qual atividade ProcessAction para transferir para o.  
  
 Para cenários com base em HTTP, ReceiveBytes é invocado na primeira mensagem a enviar e existe para o tempo de vida da solicitação.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-http"></a>Propagação está desabilitada nos lados seja, usando HTTP  
 Se `propagateActivity` = `false` em ambos os lados, ProcessMessage não indica qual atividade ProcessAction para transferir para o. Portanto, uma nova atividade ProcessAction temporária com uma nova ID é invocada. Quando a resposta assíncrona é comparada à solicitação no código de ServiceModel, a ID de atividade podem ser recuperada do contexto local. A atividade ProcessAction real pode ser transferida para, com essa ID.  
  
 ![Cliente assíncrono com nenhum retorno de chamada onde propagateActivity é definido como false em ambos os lados.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-either-side.gif)  
    
 Para cenários com base em HTTP, ReceiveBytes é invocado na primeira mensagem a enviar e existe para o tempo de vida da solicitação.  
  
 Uma atividade de ação de processo é criada em um cliente assíncrono quando `propagateActivity` = `false` no chamador ou receptor e, quando a mensagem de resposta não inclui um cabeçalho Action.  
  
#### <a name="propagation-is-enabled-on-both-sides-using-tcp-or-named-pipe"></a>Propagação está habilitada nos dois lados, usando o TCP ou Pipe nomeado  
 ![Cliente assíncrono com nenhum retorno de chamada onde propagateActivity é definido como true em ambos os lados e nomeado TCP/pipe.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-enabled-using-tcp.gif)  
  
 Para um cenário baseado em TCP ou Pipe nomeado, ReceiveBytes é invocado quando o cliente é aberto e existe para o tempo de vida da conexão.  
  
 Semelhante à primeira imagem, se `propagateActivity` = `true`, ProcessMessage indica qual atividade ProcessAction para transferir para o.  
  
#### <a name="propagation-is-disabled-on-either-sides-using-tcp-or-named-pipe"></a>Propagação está desabilitada nos lados seja, usando o TCP ou Pipe nomeado  
 Para um cenário baseado em TCP ou Pipe nomeado, ReceiveBytes é invocado quando o cliente é aberto e existe para o tempo de vida da conexão.  
  
 Semelhante à imagem de segundo, se `propagateActivity` = `false` em ambos os lados, ProcessMessage não indica qual atividade ProcessAction para transferir para o. Portanto, uma nova atividade ProcessAction temporária com uma nova ID é invocada. Quando a resposta assíncrona é comparada à solicitação no código de ServiceModel, a ID de atividade podem ser recuperada do contexto local. A atividade ProcessAction real pode ser transferida para, com essa ID.  
  
 ![Cliente assíncrono com nenhum retorno de chamada onde propagateActivity é definido como false em ambos os lados e chamado TCP/pipe.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-scenario-propagation-disabled-using-tcp.gif)  
    
### <a name="asynchronous-client-with-callback"></a>Cliente assíncrono com retorno de chamada  
 Esse cenário adiciona as atividades G e um ', para o retorno de chamada e `endCall`e suas transferências de entrada/saída.  
  
 Esta seção demonstra apenas usando HTTP com `propragateActivity` = `true`. No entanto, as atividades adicionais e transferências também se aplicam a outros casos (ou seja, `propagateActivity` = `false`, usando o TCP ou Pipe nomeado).  
  
 O retorno de chamada cria uma nova atividade (G) quando o cliente chama o código do usuário para notificar que os resultados estão prontos. Código do usuário, em seguida, chamar `endCall` dentro do retorno de chamada (conforme mostrado na Figura 5) ou fora o retorno de chamada (Figura 6). Porque não se sabe qual atividade de usuário `endCall` está sendo chamado, essa atividade é rotulado como `A’`. É possível que A' pode ser idêntico a ou diferente da.  
  
 ![Mostra um cliente assíncrono com retorno de chamada, endcall no retorno de chamada.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-in-callback.gif)  
    
 ![Mostra um cliente assíncrono com retorno de chamada, endcall fora do retorno de chamada.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-client-callback-endcall-outside-callback.gif)  
    
### <a name="asynchronous-server-with-callback"></a>Servidor assíncrono com retorno de chamada  
 ![Mostra um servidor assíncrono com retorno de chamada.](./media/asynchronous-scenarios-using-http-tcp-or-named-pipe/asynchronous-server-callback.gif)  
    
 A pilha de canais chama de volta o cliente no recebimento de mensagens: rastreamentos para esse processamento são emitidos na própria atividade ProcessRequest.  
  
## <a name="asynchronous-requestreply-with-errors"></a>Solicitação/resposta assíncrona com erros  
 Erros de mensagem de falha são recebidos durante `endCall`. Caso contrário, as atividades e as transferências são semelhantes aos cenários anteriores.  
  
## <a name="asynchronous-one-way-with-or-without-errors"></a>Assíncrono unidirecional com ou sem erros  
 Nenhuma resposta ou a falha é retornada ao cliente.
