---
title: "Reconfiguração dinâmica"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3146da86dcbe22f72ebedec57c87ac0a29ed1946
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="dynamic-reconfiguration"></a><span data-ttu-id="bf974-102">Reconfiguração dinâmica</span><span class="sxs-lookup"><span data-stu-id="bf974-102">Dynamic Reconfiguration</span></span>
<span data-ttu-id="bf974-103">Este exemplo demonstra o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="bf974-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="bf974-104">O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bf974-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="bf974-105">Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculadora de exemplo para se comunicar usando o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="bf974-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the routing service.</span></span> <span data-ttu-id="bf974-106">Este exemplo mostra como o serviço de roteamento pode ser reconfigurado dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="bf974-106">This sample shows how the routing service can be dynamically reconfigured during runtime.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bf974-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="bf974-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="bf974-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="bf974-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="bf974-109">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="bf974-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="bf974-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="bf974-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a><span data-ttu-id="bf974-111">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="bf974-111">Sample Details</span></span>  
 <span data-ttu-id="bf974-112">Para reconfigurar o serviço de roteamento dinamicamente em tempo de execução, este exemplo aciona um timer cada cinco segundos que cria um novo <xref:System.ServiceModel.Routing.RoutingConfiguration> do objeto e o aplica.</span><span class="sxs-lookup"><span data-stu-id="bf974-112">To dynamically reconfigure the routing service during runtime, this sample fires a timer every five seconds that creates a new <xref:System.ServiceModel.Routing.RoutingConfiguration> object and applies it.</span></span> <span data-ttu-id="bf974-113">Essa configuração faz referência o ponto de extremidade de calculadora regular ou o ponto de extremidade de arredondamento Calculadora.</span><span class="sxs-lookup"><span data-stu-id="bf974-113">This configuration references either the regular Calculator endpoint or the Rounding Calculator endpoint.</span></span> <span data-ttu-id="bf974-114">O aplicativo cliente de calculadora tem suas mensagens retornadas de um serviço ou a outra, dependendo do que o serviço de roteamento está configurado para direcionar para nesse momento.</span><span class="sxs-lookup"><span data-stu-id="bf974-114">The Calculator Client application has its messages returned from one service or the other, depending on which one the routing service is configured to route to at that time.</span></span>  
  
 <span data-ttu-id="bf974-115">Capabilitiy do serviço de roteamento de reconfiguração dinâmica por meio de um comportamento personalizado é usado.</span><span class="sxs-lookup"><span data-stu-id="bf974-115">The routing service’s capabilitiy for dynamic reconfiguration through a custom behavior is used.</span></span> <span data-ttu-id="bf974-116">Este comportamento personalizado anexa uma extensão de serviço, que contém um timer de segmento simples que é acionado a cada cinco segundos, o que resulta em um retorno de chamada para o `UpdateRules` método.</span><span class="sxs-lookup"><span data-stu-id="bf974-116">This custom behavior attaches a service extension, which contains a simple thread timer that fires every five seconds, which results in a callback to the `UpdateRules` method.</span></span> <span data-ttu-id="bf974-117">Esse retorno de chamada cria e aplica-se a nova configuração de roteamento.</span><span class="sxs-lookup"><span data-stu-id="bf974-117">This callback creates and applies the new routing configuration.</span></span> <span data-ttu-id="bf974-118">Em uma implantação real, esse retorno de chamada provavelmente seria obtido como resultado de algum outro tipo de evento, como uma notificação de evento do SQL ou um anúncio de WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="bf974-118">In an actual deployment, this callback would likely be accomplished as a result of some other type of event, such as a SQL-Event notification, or a WS-Discovery announcement.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="bf974-119">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="bf974-119">To use this sample</span></span>  
  
1.  <span data-ttu-id="bf974-120">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra DynamicReconfiguration.sln.</span><span class="sxs-lookup"><span data-stu-id="bf974-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open DynamicReconfiguration.sln.</span></span>  
  
2.  <span data-ttu-id="bf974-121">Para abrir **Solution Explorer**, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="bf974-121">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="bf974-122">Pressione **F5** ou **CTRL + SHIFT + B** em [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bf974-122">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="bf974-123">Se você gostaria de iniciar os projetos necessários quando você pressiona **F5**, a solução e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="bf974-123">If you would like to auto-launch the necessary projects when you press **F5**, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="bf974-124">Selecione o **projeto de inicialização** nó **propriedades comuns** no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="bf974-124">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="bf974-125">Selecione o **vários projetos de inicialização** botão de opção e defina todos os projetos para que o **iniciar** ação.</span><span class="sxs-lookup"><span data-stu-id="bf974-125">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="bf974-126">Se você compilar o projeto com **CTRL + SHIFT + B**, você deve iniciar os seguintes aplicativos:</span><span class="sxs-lookup"><span data-stu-id="bf974-126">If you build the project with **CTRL+SHIFT+B**, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="bf974-127">Calculadora de cliente (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="bf974-127">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="bf974-128">Serviço de cálculo (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="bf974-128">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="bf974-129">O serviço de roteamento Calculadora (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="bf974-129">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="bf974-130">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="bf974-130">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="bf974-131">Na janela do console do cliente Calculadora, pressione ENTER para iniciar o cliente e chamar as operações de serviço da Calculadora.</span><span class="sxs-lookup"><span data-stu-id="bf974-131">In the console window of the Calculator Client, press ENTER to start the client and to call the Calculator service operations.</span></span>  
  
     <span data-ttu-id="bf974-132">O serviço de roteamento encaminha mensagens para o cálculo de arredondamento e a Calculadora regular alternadamente como as alterações de configuração de roteamento dinamicamente a cada cinco segundos.</span><span class="sxs-lookup"><span data-stu-id="bf974-132">The routing service routes messages to the Rounding Calculator and to the regular Calculator alternately as the routing configuration changes dynamically every five seconds.</span></span> <span data-ttu-id="bf974-133">Dependendo de qual ponto de extremidade do serviço de roteamento está configurado para enviar mensagens para existem saídas diferentes na janela do console do cliente.</span><span class="sxs-lookup"><span data-stu-id="bf974-133">Depending on which endpoint the routing service is configured to send messages to there are different outputs in the client console window.</span></span>  
  
5.  <span data-ttu-id="bf974-134">Continue a pressionar ENTER repetidamente durante mais de cinco segundos e observe a alteração nos resultados do serviço.</span><span class="sxs-lookup"><span data-stu-id="bf974-134">Continue pressing ENTER repeatedly over more than five seconds and observe the change in the results from the service.</span></span>  
  
    1.  <span data-ttu-id="bf974-135">A seguir está que a saída retornada se o serviço de roteador está configurado para rotear mensagens para o serviço de cálculo de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="bf974-135">The following is the output returned if the Router Service is configured to route messages to the Rounding Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="bf974-136">A seguir está que a saída retornada se o serviço de roteamento está configurado para rotear mensagens para o serviço da Calculadora regular.</span><span class="sxs-lookup"><span data-stu-id="bf974-136">The following is the output returned if the routing service is configured to route messages to the regular Calculator service.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  <span data-ttu-id="bf974-137">O serviço de cálculo e o serviço de cálculo de arredondamento também imprimam um log das operações invocado para as janelas do console do respectivos.</span><span class="sxs-lookup"><span data-stu-id="bf974-137">The Calculator Service and the Rounding Calculator Service also print out a log of the operations invoked to their respective console windows.</span></span>  
  
7.  <span data-ttu-id="bf974-138">Na janela do console de cliente, digite "Sair" e pressione ENTER para sair.</span><span class="sxs-lookup"><span data-stu-id="bf974-138">In the client console window, type "quit" and press ENTER to exit.</span></span>  
  
8.  <span data-ttu-id="bf974-139">Pressione ENTER nas janelas do console de serviços para encerrar os serviços.</span><span class="sxs-lookup"><span data-stu-id="bf974-139">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="scenario"></a><span data-ttu-id="bf974-140">Cenário</span><span class="sxs-lookup"><span data-stu-id="bf974-140">Scenario</span></span>  
 <span data-ttu-id="bf974-141">Este exemplo demonstra o roteador que atua como um roteador baseado em conteúdo, permitindo que vários tipos ou implementação de serviços a serem expostas por meio de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="bf974-141">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="bf974-142">Cenário do mundo real</span><span class="sxs-lookup"><span data-stu-id="bf974-142">Real World Scenario</span></span>  
 <span data-ttu-id="bf974-143">A Contoso deseja virtualizar todos os seus serviços para expor apenas um ponto de extremidade publicamente por meio do qual eles oferecem acesso a vários tipos diferentes de serviços.</span><span class="sxs-lookup"><span data-stu-id="bf974-143">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="bf974-144">Nesse caso, eles utilizam baseado em conteúdo capacidades de roteamento do serviço de roteamento para determinar onde as solicitações de entrada devem ser enviadas.</span><span class="sxs-lookup"><span data-stu-id="bf974-144">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf974-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf974-145">See Also</span></span>  
 [<span data-ttu-id="bf974-146">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="bf974-146">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
