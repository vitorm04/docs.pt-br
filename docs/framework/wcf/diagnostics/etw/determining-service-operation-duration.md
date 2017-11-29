---
title: "Determinando a duração da operação de serviço"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e8a93a2c-2c20-48b3-8986-57e90e9aa908
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 63a8c92713ee452da2439475ac526229d1e5741c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="determining-service-operation-duration"></a>Determinando a duração da operação de serviço
Se o rastreamento analítico é habilitado em um [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] aplicativo, a duração da execução de uma operação de serviço pode facilmente ser determinada examinando o log de eventos.  Este tópico demonstra como determinar a quantidade de tempo para concluir uma operação de serviço.  
  
### <a name="determining-service-operation-execution-duration"></a>Determinando a duração de execução de operação de serviço  
  
1.  Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.  
  
2.  Se você ainda não ativou o rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** . Selecione **exibição**, **Mostrar analítica e Logs de depuração**. Clique com botão direito **analítico** e selecione **Habilitar Log**. Deixe o Visualizador de eventos aberto para que os rastreamentos podem ser exibidos depois que a operação de serviço é executada.  
  
3.  Em seguida, abra um [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] aplicativo que inclui um projeto de serviço e um projeto de cliente que interage com esse serviço.  Você pode criar um aplicativo desse tipo, seguindo o [Tutorial de Introdução](../../../../../docs/framework/wcf/getting-started-tutorial.md).  Se você tiver o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemplos instalados, você pode abrir o [Introdução](../../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto completo criado no tutorial.  
  
4.  Execute o aplicativo de servidor pressionando **F5**. Executar o aplicativo cliente clicando no **cliente** projeto e selecionando **depurar**, **iniciar uma nova instância**.  
  
5.  No Visualizador de eventos, atualize o log analítico e classifique os eventos por ID do evento.  Procure eventos com ID de evento [214 - OperationCompleted](../../../../../docs/framework/wcf/diagnostics/etw/214-operationcompleted.md).  Esses eventos mostram quais operações foram concluídas e qual foi a duração da operação.  O evento a seguir mostra a duração de uma operação de adição.  
  
    ```Output  
    An OperationInvoker completed the call to the 'Add' method.  The method call duration was '3' ms.  
    ```
