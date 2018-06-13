---
title: Determinando a duração da operação de serviço
ms.date: 03/30/2017
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
ms.openlocfilehash: 8c86ccc09979071e0678be792f4937d526e23fa7
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33804957"
---
# <a name="determining-service-operation-duration"></a>Determinando a duração da operação de serviço
Se o rastreamento analítico é habilitado em um aplicativo do Windows Communication Foundation (WCF), a duração da execução de uma operação de serviço pode facilmente ser determinada examinando o log de eventos.  Este tópico demonstra como determinar a quantidade de tempo para concluir uma operação de serviço.  
  
### <a name="determining-service-operation-execution-duration"></a>Determinando a duração de execução de operação de serviço  
  
1.  Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.  
  
2.  Se você ainda não ativou o rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** . Selecione **exibição**, **Mostrar analítica e Logs de depuração**. Clique com botão direito **analítico** e selecione **Habilitar Log**. Deixe o Visualizador de eventos aberto para que os rastreamentos podem ser exibidos depois que a operação de serviço é executada.  
  
3.  Em seguida, abra um aplicativo WCF que inclui um projeto de serviço e um projeto de cliente que interage com esse serviço.  Você pode criar um aplicativo desse tipo, seguindo o [Tutorial de Introdução](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Se você tiver instalados os exemplos de WCF, você pode abrir o [Introdução](../../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto completo criado no tutorial.  
  
4.  Execute o aplicativo de servidor pressionando **F5**. Executar o aplicativo cliente clicando no **cliente** projeto e selecionando **depurar**, **iniciar uma nova instância**.  
  
5.  No Visualizador de eventos, atualize o log analítico e classifique os eventos por ID do evento.  Procure eventos com ID de evento [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Esses eventos mostram quais operações foram concluídas e qual foi a duração da operação.  O evento a seguir mostra a duração de uma operação de adição.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
