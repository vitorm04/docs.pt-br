---
title: Cenários síncronos utilizando HTTP, TCP ou pipe nomeado
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 28e612b190f4993e1ce7da0d1083c4e55f827d4a
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653997"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Cenários síncronos utilizando HTTP, TCP ou pipe nomeado
Este tópico descreve as atividades e transferências para cenários diferentes de solicitação/resposta síncrona, com um cliente de thread único, usando HTTP, TCP ou pipe nomeado. Ver [cenários assíncronos usando HTTP, TCP ou Pipe nomeado](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) para obter mais informações sobre solicitações com multithread.  
  
## <a name="synchronous-requestreply-without-errors"></a>Solicitação/resposta síncrona sem erros  
 Esta seção descreve as atividades e os transfere para um cenário válido de solicitação/resposta síncrona, com o cliente de thread único.  
  
### <a name="client"></a>Cliente  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Estabelecer comunicação com o ponto de extremidade de serviço  
 Um cliente é criado e aberto. Para cada uma dessas etapas, a atividade de ambiente (A) é transferida para uma "Cliente de construir" (B) e "Cliente abra" (C) a atividade, respectivamente. Para cada atividade que estão sendo transferida para, a atividade de ambiente é suspenso até que haja uma transferência de volta, ou seja, até que o código de ServiceModel é executado.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Fazendo uma solicitação ao ponto de extremidade de serviço  
 A atividade de ambiente é transferida para uma atividade de "ProcessAction" (D). Dentro desta atividade, uma mensagem de solicitação é enviada, e uma mensagem de resposta é recebida. A atividade termina quando o controle retorna ao código do usuário. Como esta é uma solicitação síncrona, a atividade de ambiente suspende até que o controle retorna.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Fechando a comunicação com o ponto de extremidade de serviço  
 Atividade de fechamento do cliente (I) é criada da atividade de ambiente. Isso é idêntico ao novo e aberto.  
  
### <a name="server"></a>Servidor  
  
#### <a name="setting-up-a-service-host"></a>Como configurar um Host de serviço  
 Livre e novas atividades do ServiceHost (N e S) são criadas da atividade de ambiente (M).  
  
 Uma atividade de ouvinte (P) é criada de abrir um ServiceHost para cada ouvinte. A atividade de escuta aguarda para receber e processar dados.  
  
#### <a name="receiving-data-on-the-wire"></a>Receber dados durante a transmissão  
 Quando os dados chegam durante a transmissão, uma atividade de "ReceiveBytes" será criada se ela ainda não existir (P) para processar os dados recebidos. Essa atividade pode ser reutilizada para várias mensagens dentro de uma fila ou a conexão.  
  
 A atividade ReceiveBytes inicia uma atividade de ProcessMessage (R), se ele tiver dados suficientes para formar uma mensagem de ação SOAP.  
  
 Na atividade de R, os cabeçalhos de mensagens são processados e o cabeçalho de activityID é verificado. Se esse cabeçalho estiver presente, a ID de atividade é definida como a atividade de ProcessAction; Caso contrário, uma nova ID é criada.  
  
 Atividade ProcessAction (S) é criada e transferidos para, quando a chamada é processada. Essa atividade termina quando todo o processamento relacionado à mensagem de entrada for concluída, incluindo a execução de código do usuário (T) e enviar a mensagem de resposta, se aplicável.  
  
#### <a name="closing-a-service-host"></a>Fechando um Host de serviço  
 Atividade de fechamento do ServiceHost (Z) é criada da atividade de ambiente.  
  
 ![Diagrama mostrando cenários síncronos: HTTP, TCP ou pipes nomeados.](./media/synchronous-scenarios-using-http-tcp-or-named-pipe/synchronous-scenario-http-tcp-named-pipes.gif)  
  
 Na \<nome de unidade: >, `A` é um símbolo de atalho que descreve a atividade no texto anterior e na tabela 3. `Name` é um nome abreviado da atividade.  
  
 Se `propagateActivity` = `true`, ação de processo no cliente e serviço têm a mesma ID de atividade.  
  
## <a name="synchronous-requestreply-with-errors"></a>Solicitação/resposta síncrona com erros  
 A única diferença com o cenário anterior é que uma mensagem de falha SOAP é retornada como uma mensagem de resposta. Se `propagateActivity` = `true`, a ID de atividade da mensagem de solicitação é adicionada à mensagem de falha de SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Síncrona unidirecional sem erros  
 A única diferença com o primeiro cenário é que nenhuma mensagem será retornada para o servidor. Para protocolos baseados em HTTP, um status (válido ou erro) ainda é retornada ao cliente. Isso ocorre porque o HTTP é o único protocolo com uma semântica de solicitação-resposta que faz parte da pilha do protocolo do WCF. Como o processamento de TCP é oculto do WCF, nenhuma confirmação é enviada ao cliente.  
  
## <a name="synchronous-one-way-with-errors"></a>Síncrona unidirecional com erros  
 Se ocorrer um erro ao processar a mensagem (Q ou além), nenhuma notificação é retornada ao cliente. Isso é idêntico ao cenário "Unidirecional síncrona sem erros". Você não deve usar um cenário unidirecional para receber uma mensagem de erro.  
  
## <a name="duplex"></a>Duplex  
 A diferença com os cenários anteriores é que o cliente atua como um serviço, em que ele cria as atividades ReceiveBytes e ProcessMessage, semelhantes aos cenários assíncronos.
