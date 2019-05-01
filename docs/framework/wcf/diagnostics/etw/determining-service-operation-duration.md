---
title: Determinando a duração da operação de serviço
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: fd7dec5784f50a0613b574822a31202a859b34c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999442"
---
# <a name="determining-service-operation-duration"></a>Determinando a duração da operação de serviço
Se o rastreamento analítico é habilitado em um aplicativo do Windows Communication Foundation (WCF), a duração de execução de uma operação de serviço pode facilmente ser determinada examinando o log de eventos.  Este tópico demonstra como determinar a quantidade de tempo que uma operação de serviço leva para ser concluído.  
  
### <a name="determining-service-operation-execution-duration"></a>Determinando a duração de execução da operação de serviço  
  
1. Abra o Visualizador de eventos clicando **inicie**, **execute**e inserindo `eventvwr.exe`.  
  
2. Se você ainda não tiver ativado rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor** . Selecione **modo de exibição**, **analíticos e de Logs de depuração**. Clique com botão direito **analítico** e selecione **Habilitar Log**. Deixe o Visualizador de eventos aberto para que os rastreamentos podem ser exibidos depois que a operação de serviço é executada.  
  
3. Em seguida, abra um aplicativo WCF que inclui um projeto de serviço e um projeto de cliente que interage com o serviço.  Você pode criar um aplicativo desse tipo, seguindo a [Tutorial de Introdução](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Se você tiver que instalar os exemplos WCF, você pode abrir o [Introdução ao](../../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto concluído criado no tutorial.  
  
4. Executar o aplicativo de servidor pressionando **F5**. Executar o aplicativo cliente clicando com o **Client** projeto e selecionando **Debug**, **iniciar uma nova instância**.  
  
5. No Visualizador de eventos, atualize o log analítico e classifique os eventos por ID do evento.  Procure eventos com a ID de evento [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Esses eventos mostram quais operações foram concluídas e qual foi a duração da operação.  O evento a seguir mostra a duração de uma operação de adição.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
