---
title: "Olá Mundo com o serviço de roteamento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ba910afe91af07ecbdb2c71bba2fa496c52f2f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="eba1a-102">Olá Mundo com o serviço de roteamento</span><span class="sxs-lookup"><span data-stu-id="eba1a-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="eba1a-103">Este exemplo demonstra o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="eba1a-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Routing Service.</span></span> <span data-ttu-id="eba1a-104">O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="eba1a-104">The Routing Service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="eba1a-105">Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculadora de exemplo para se comunicar usando o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="eba1a-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="eba1a-106">Neste exemplo, o cliente de cálculo é configurado para enviar mensagens a um ponto de extremidade exposto pelo roteador.</span><span class="sxs-lookup"><span data-stu-id="eba1a-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="eba1a-107">O serviço de roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-los para um ponto de extremidade que corresponde ao serviço de cálculo.</span><span class="sxs-lookup"><span data-stu-id="eba1a-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="eba1a-108">Assim mensagens enviadas do cliente são recebidas pelo roteador e roteadas para o serviço da Calculadora real.</span><span class="sxs-lookup"><span data-stu-id="eba1a-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="eba1a-109">Mensagens do serviço de cálculo são enviadas para o roteador, que por sua vez passa de volta para o cliente de cálculo.</span><span class="sxs-lookup"><span data-stu-id="eba1a-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>  
  
### <a name="to-use-this-sample"></a><span data-ttu-id="eba1a-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="eba1a-110">To use this sample</span></span>  
  
1.  <span data-ttu-id="eba1a-111">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="eba1a-111">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open HelloRoutingService.sln.</span></span>  
  
2.  <span data-ttu-id="eba1a-112">Pressione F5 ou CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="eba1a-112">Press F5 or CTRL+SHIFT+B.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eba1a-113">Se você pressionar F5, o cliente de cálculo é iniciado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="eba1a-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="eba1a-114">Se você pressionar CTRL + SHIFT + B (compilação), você deve iniciar a seguir aplicativos por conta própria.</span><span class="sxs-lookup"><span data-stu-id="eba1a-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>  
    >   
    >  1.  <span data-ttu-id="eba1a-115">Cliente de cálculo (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="eba1a-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>  
    > 2.  <span data-ttu-id="eba1a-116">Serviço de cálculo (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="eba1a-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>  
    > 3.  <span data-ttu-id="eba1a-117">O serviço de roteamento (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="eba1a-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>  
  
3.  <span data-ttu-id="eba1a-118">Pressione ENTER para iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="eba1a-118">Press ENTER to start the client.</span></span>  
  
     <span data-ttu-id="eba1a-119">Você verá a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="eba1a-119">You should see the following output:</span></span>  
  
     <span data-ttu-id="eba1a-120">Add(100,15.99) = 115.99</span><span class="sxs-lookup"><span data-stu-id="eba1a-120">Add(100,15.99) = 115.99</span></span>  
  
     <span data-ttu-id="eba1a-121">Subtract(145,76.54) = 68.46</span><span class="sxs-lookup"><span data-stu-id="eba1a-121">Subtract(145,76.54) = 68.46</span></span>  
  
     <span data-ttu-id="eba1a-122">MULTIPLY(9,81.25) = 731.25</span><span class="sxs-lookup"><span data-stu-id="eba1a-122">Multiply(9,81.25) = 731.25</span></span>  
  
     <span data-ttu-id="eba1a-123">Divide(22,7) = 3.14285714285714</span><span class="sxs-lookup"><span data-stu-id="eba1a-123">Divide(22,7) = 3.14285714285714</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="eba1a-124">Configuráveis por meio de código ou App. config</span><span class="sxs-lookup"><span data-stu-id="eba1a-124">Configurable via Code or App.Config</span></span>  
 <span data-ttu-id="eba1a-125">O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="eba1a-125">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="eba1a-126">Você também pode alterar o nome do arquivo App. config para algo diferente para que ele não é reconhecido e remova a chamada de método para ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="eba1a-126">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="eba1a-127">Um método resulta no mesmo comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="eba1a-127">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="eba1a-128">Cenário</span><span class="sxs-lookup"><span data-stu-id="eba1a-128">Scenario</span></span>  
 <span data-ttu-id="eba1a-129">Este exemplo demonstra o roteador que atua como uma bomba de mensagem básica.</span><span class="sxs-lookup"><span data-stu-id="eba1a-129">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="eba1a-130">O serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto predefinido de pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="eba1a-130">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="eba1a-131">Cenário do mundo real</span><span class="sxs-lookup"><span data-stu-id="eba1a-131">Real World Scenario</span></span>  
 <span data-ttu-id="eba1a-132">A Contoso deseja aumentar a flexibilidade que ele tem na nomenclatura, endereçamento, configuração e segurança de seus serviços.</span><span class="sxs-lookup"><span data-stu-id="eba1a-132">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="eba1a-133">Para fazer isso, eles fizerem uma bomba de mensagem básica na frente de seus serviços para atuar como um ponto de extremidade oposto público.</span><span class="sxs-lookup"><span data-stu-id="eba1a-133">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="eba1a-134">Isso permite colocar segurança adicional na frente de seus serviços reais e torná-lo mais fácil de implementar expandida soluções ou controle de versão do serviço em uma data posterior.</span><span class="sxs-lookup"><span data-stu-id="eba1a-134">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eba1a-135">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="eba1a-135">The samples may already be installed on your computer.</span></span> <span data-ttu-id="eba1a-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="eba1a-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eba1a-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="eba1a-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eba1a-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="eba1a-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="eba1a-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eba1a-139">See Also</span></span>  
 [<span data-ttu-id="eba1a-140">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="eba1a-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
