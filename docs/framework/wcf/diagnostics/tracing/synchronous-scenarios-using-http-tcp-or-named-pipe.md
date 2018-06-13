---
title: Cenários síncronos utilizando HTTP, TCP ou pipe nomeado
ms.date: 03/30/2017
ms.assetid: 7e90af1b-f8f6-41b9-a63a-8490ada502b1
ms.openlocfilehash: 11a5d8f43d12d35728c65c7a60ad8a4fa2fc1b3a
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33810168"
---
# <a name="synchronous-scenarios-using-http-tcp-or-named-pipe"></a>Cenários síncronos utilizando HTTP, TCP ou pipe nomeado
Este tópico descreve as atividades e transferências para cenários diferentes de solicitação/resposta síncrona, com um cliente de thread único, usando HTTP, TCP ou pipe nomeado. Consulte [cenários assíncronos usando HTTP, TCP ou Pipe nomeado](../../../../../docs/framework/wcf/diagnostics/tracing/asynchronous-scenarios-using-http-tcp-or-named-pipe.md) para obter mais informações sobre solicitações de multi-threads.  
  
## <a name="synchronous-requestreply-without-errors"></a>Solicitação/resposta síncrona sem erros  
 Esta seção descreve as atividades e transferências para um cenário de solicitação/resposta síncrona válida, com o cliente de thread único.  
  
### <a name="client"></a>Cliente  
  
#### <a name="establishing-communication-with-service-endpoint"></a>Estabelecer comunicação com o ponto de extremidade de serviço  
 Um cliente é criado e aberto. Para cada uma dessas etapas, a atividade de ambiente (A) é transferida para um "construir" (B) e o cliente "aberta" (C) atividade, respectivamente. Para cada atividade que estão sendo transferida para a atividade de ambiente é suspenso até que haja uma transferência novamente, ou seja, até que o código de ServiceModel é executado.  
  
#### <a name="making-a-request-to-service-endpoint"></a>Fazer uma solicitação ao ponto de extremidade de serviço  
 A atividade de ambiente é transferida para uma atividade de "ProcessAction" (D). Essa atividade, uma mensagem de solicitação é enviada e uma mensagem de resposta é recebida. A atividade termina quando o controle retorna ao código do usuário. Como esta é uma solicitação síncrona, a atividade de ambiente suspende até que o controle retorna.  
  
#### <a name="closing-communication-with-service-endpoint"></a>Fechando a comunicação com o ponto de extremidade de serviço  
 Atividade de fechamento do cliente (I) é criada da atividade de ambiente. Isso é idêntico à nova e aberto.  
  
### <a name="server"></a>Servidor  
  
#### <a name="setting-up-a-service-host"></a>Configuração de um Host de serviço  
 Novas e abra as atividades do ServiceHost (N e O) são criadas da atividade de ambiente (M).  
  
 Uma atividade de ouvinte (P) é criada de abrir um ServiceHost para cada ouvinte. A atividade de ouvinte espera para receber e processar dados.  
  
#### <a name="receiving-data-on-the-wire"></a>Recebendo dados durante a transmissão  
 Quando os dados chegam na conexão, uma atividade de "ReceiveBytes" é criada se ela ainda não existir (P) para processar os dados recebidos. Essa atividade pode ser reutilizada para várias mensagens dentro de uma fila ou a conexão.  
  
 A atividade ReceiveBytes inicia uma atividade ProcessMessage (R) se ele tem dados suficientes para formar uma mensagem de ação SOAP.  
  
 Atividade R, os cabeçalhos de mensagem são processados e o cabeçalho activityID é verificado. Se esse cabeçalho estiver presente, a ID da atividade é definida como a atividade de ProcessAction; Caso contrário, é criada uma nova ID.  
  
 Atividade de ProcessAction (S) é criada e que estão sendo transferidos para, quando a chamada é processada. Essa atividade termina quando todo o processamento relacionado à mensagem de entrada é concluído, incluindo a execução de código do usuário (T) e enviar a mensagem de resposta, se aplicável.  
  
#### <a name="closing-a-service-host"></a>Fechando um Host de serviço  
 Atividade de fechamento do ServiceHost (Z) é criada da atividade de ambiente.  
  
 ![Cenários síncronos utilizando HTTP&#47;TCP&#47; Pipes nomeados](../../../../../docs/framework/wcf/diagnostics/tracing/media/sync.gif "sincronização")  
  
 Em \<nome de unidade: >, `A` é um símbolo de atalho que descreve a atividade no texto anterior e na tabela 3. `Name` é um nome abreviado da atividade.  
  
 Se `propagateActivity` = `true`, ação de processo no cliente e de serviço tem a mesma ID de atividade.  
  
## <a name="synchronous-requestreply-with-errors"></a>Solicitação/resposta síncrona com erros  
 A única diferença com o cenário anterior é que uma mensagem de falha SOAP é retornada como uma mensagem de resposta. Se `propagateActivity` = `true`, a ID de atividade da mensagem de solicitação é adicionada à mensagem de falha de SOAP.  
  
## <a name="synchronous-one-way-without-errors"></a>Síncrona unidirecional sem erros  
 A única diferença com o primeiro cenário é que nenhuma mensagem será retornada para o servidor. Para protocolos baseados em HTTP, um status (válido ou erro) ainda será retornado ao cliente. Isso ocorre porque o HTTP é o único protocolo com uma semântica de solicitação-resposta que faz parte da pilha de protocolos WCF. Como o processamento de TCP é oculta de WCF, nenhuma confirmação é enviada ao cliente.  
  
## <a name="synchronous-one-way-with-errors"></a>Síncrona unidirecional com erros  
 Se ocorrer um erro ao processar a mensagem (P ou posterior), nenhuma notificação será retornada ao cliente. Isso é idêntico ao cenário de "Síncrono unidirecional sem erros". Você não deve usar um cenário unidirecional, se você quiser receber uma mensagem de erro.  
  
## <a name="duplex"></a>Duplex  
 A diferença nos cenários anteriores é que o cliente atua como um serviço, em que ele cria atividades ReceiveBytes e ProcessMessage, semelhantes aos cenários assíncronos.
