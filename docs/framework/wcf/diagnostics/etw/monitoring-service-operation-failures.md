---
title: "Monitorando operações de serviços com falha"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59472ba3-8ebf-4479-bd7b-f440d5e636cb
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 42506f7f32d0174b4f980f4e94d370cf4c137276
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="monitoring-service-operation-failures"></a><span data-ttu-id="02f7b-102">Monitorando operações de serviços com falha</span><span class="sxs-lookup"><span data-stu-id="02f7b-102">Monitoring Service Operation Failures</span></span>
<span data-ttu-id="02f7b-103">Se o rastreamento analítico é habilitado para um aplicativo, falhas de serviço podem facilmente ser monitoradas no Visualizador de eventos.</span><span class="sxs-lookup"><span data-stu-id="02f7b-103">If analytic tracing is enabled for an application, service failures can easily be monitored in the event viewer.</span></span>  <span data-ttu-id="02f7b-104">Este tópico demonstra como determinar quando uma operação de serviço falha e como determinar o que causou a falha.</span><span class="sxs-lookup"><span data-stu-id="02f7b-104">This topic demonstrates how to determine when a service operation fails, and how to determine what caused the failure.</span></span>  
  
### <a name="determining-service-operation-failure-information"></a><span data-ttu-id="02f7b-105">Determinando as informações de falha de operação de serviço</span><span class="sxs-lookup"><span data-stu-id="02f7b-105">Determining service operation failure information</span></span>  
  
1.  <span data-ttu-id="02f7b-106">Abra o Visualizador de eventos clicando **iniciar**, **executar**e digitando `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="02f7b-106">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
2.  <span data-ttu-id="02f7b-107">Se você ainda não ativou o rastreamento analítico, expanda **Applications and Services Logs**, **Microsoft**, **Windows**, **aplicativos de servidor de aplicativo** .</span><span class="sxs-lookup"><span data-stu-id="02f7b-107">If you haven’t enabled analytic tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="02f7b-108">Selecione **exibição**, **Mostrar analítica e Logs de depuração**.</span><span class="sxs-lookup"><span data-stu-id="02f7b-108">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="02f7b-109">Clique com botão direito **analítico** e selecione **Habilitar Log**.</span><span class="sxs-lookup"><span data-stu-id="02f7b-109">Right-click **Analytic** and select **Enable Log**.</span></span> <span data-ttu-id="02f7b-110">Visualizador de eventos deixe aberto para que os rastreamentos podem ser exibidos depois que a operação de serviço falhará.</span><span class="sxs-lookup"><span data-stu-id="02f7b-110">Leave Event Viewer open so that traces can be viewed after the service operation fails.</span></span>  
  
3.  <span data-ttu-id="02f7b-111">Em seguida, abra o exemplo criado o [Tutorial de Introdução](../../../../../docs/framework/wcf/getting-started-tutorial.md) na [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Observe que você deve executar [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] como um administrador para que o serviço pode ser criado.</span><span class="sxs-lookup"><span data-stu-id="02f7b-111">Next, open the sample created in the [Getting Started Tutorial](../../../../../docs/framework/wcf/getting-started-tutorial.md) in [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] Note that you must run [!INCLUDE[vs_current_long](../../../../../includes/vs-current-long-md.md)] as an administrator so that the service can be created.</span></span> <span data-ttu-id="02f7b-112">Se você tiver o [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] exemplos instalados, você pode abrir o [Introdução](../../../../../docs/framework/wcf/samples/getting-started-sample.md), que contém o projeto completo criado no tutorial.</span><span class="sxs-lookup"><span data-stu-id="02f7b-112">If you have the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] samples installed, you can open the [Getting Started](../../../../../docs/framework/wcf/samples/getting-started-sample.md), which contains the completed project created in the tutorial.</span></span>  
  
4.  <span data-ttu-id="02f7b-113">No arquivo Program.cs no projeto de servidor, adicione a seguinte linha de código para o início do `Divide` método o `CalculatorService` classe:</span><span class="sxs-lookup"><span data-stu-id="02f7b-113">In the Program.cs file in the Server project, add the following line of code to the start of the `Divide` method in the `CalculatorService` class:</span></span>  
  
    ```  
    if (n2 == 0) throw new DivideByZeroException();  
    ```  
  
5.  <span data-ttu-id="02f7b-114">No arquivo Program.cs no projeto cliente, altere o valor atribuído ao valor2 como zero:</span><span class="sxs-lookup"><span data-stu-id="02f7b-114">In the Program.cs file in the Client project, change the value assigned to value2 to zero:</span></span>  
  
    ```  
    //Call the Divide service operation  
    value1 = 22.00D;  
    value2 = 0.00D;  
    result = client.Divide(value1, value2);  
    Console.WriteLine("Divide({0}, {1}) = {2}", value1, value2, result);  
    ```  
  
6.  <span data-ttu-id="02f7b-115">Execute o aplicativo de servidor sem depuração pressionando **Ctrl + F5**.</span><span class="sxs-lookup"><span data-stu-id="02f7b-115">Execute the server application without debugging by pressing **Ctrl+F5**.</span></span>  
  
7.  <span data-ttu-id="02f7b-116">Abra um prompt de comando do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="02f7b-116">Open a Visual Studio command prompt.</span></span>  <span data-ttu-id="02f7b-117">Navegue até o diretório de cliente e executar o cliente de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="02f7b-117">Navigate to the client directory and execute the client from the command line.</span></span>  
  
8.  <span data-ttu-id="02f7b-118">No Visualizador de eventos, desabilitar e atualize o log analítico e classifique os eventos por ID do evento.</span><span class="sxs-lookup"><span data-stu-id="02f7b-118">In Event Viewer, disable and refresh the Analytic log and sort the events by Event ID.</span></span>  <span data-ttu-id="02f7b-119">Procure um evento com ID de evento [ServiceException 219 -](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), que descreve a falha do serviço.</span><span class="sxs-lookup"><span data-stu-id="02f7b-119">Look for an event with Event ID [219 - ServiceException](../../../../../docs/framework/wcf/diagnostics/etw/219-serviceexception.md), which describes the service failure.</span></span>  
  
    ```Output  
    There was an unhandled exception of type 'System.DivideByZeroException' during message processing.  Full Exception ToString: System.DivideByZeroException: Attempted to divide by zero.  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="02f7b-120">Eventos são armazenados em buffer quando estão sendo enviados para o Visualizador de eventos; o evento de falha pode não aparecer imediatamente.</span><span class="sxs-lookup"><span data-stu-id="02f7b-120">Events are buffered when being sent to the event viewer; the failure event may not appear right away.</span></span>
