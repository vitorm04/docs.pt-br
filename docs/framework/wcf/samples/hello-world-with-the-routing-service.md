---
title: Olá Mundo com o serviço de roteamento
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 802135f61e1744acbfe5ae5fe4a6e92ec49d46b2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650035"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="278b7-102">Olá Mundo com o serviço de roteamento</span><span class="sxs-lookup"><span data-stu-id="278b7-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="278b7-103">Este exemplo demonstra o serviço de roteamento do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="278b7-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="278b7-104">O serviço de roteamento é um componente do WCF que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="278b7-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="278b7-105">Este exemplo se adapta a amostragem de calculadora padrão do WCF para se comunicar usando o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="278b7-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="278b7-106">Neste exemplo, o cliente de calculadora é configurado para enviar mensagens para um ponto de extremidade exposto pelo roteador.</span><span class="sxs-lookup"><span data-stu-id="278b7-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="278b7-107">O serviço de roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-las a um ponto de extremidade que corresponde ao serviço de calculadora.</span><span class="sxs-lookup"><span data-stu-id="278b7-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="278b7-108">Portanto, as mensagens enviadas do cliente são recebidas pelo roteador e roteadas para o serviço da Calculadora real.</span><span class="sxs-lookup"><span data-stu-id="278b7-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="278b7-109">Mensagens do serviço de calculadora são enviadas de volta para o roteador, que por sua vez passa de volta para o cliente de calculadora.</span><span class="sxs-lookup"><span data-stu-id="278b7-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="278b7-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="278b7-110">To use this sample</span></span>

1. <span data-ttu-id="278b7-111">Usando o Visual Studio 2012, abra HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="278b7-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="278b7-112">Pressione F5 ou CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="278b7-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    >  <span data-ttu-id="278b7-113">Se você pressionar F5, o cliente de calculadora é iniciado automaticamente.</span><span class="sxs-lookup"><span data-stu-id="278b7-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="278b7-114">Se você pressionar CTRL + SHIFT + B (build), você deve iniciar as seguir aplicativos por conta própria.</span><span class="sxs-lookup"><span data-stu-id="278b7-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="278b7-115">Cliente de Calculadora (./CalculatorClient/bin/client.exe</span><span class="sxs-lookup"><span data-stu-id="278b7-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="278b7-116">Serviço da Calculadora (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="278b7-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="278b7-117">Serviço de roteamento (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="278b7-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="278b7-118">Pressione ENTER para iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="278b7-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="278b7-119">Você deverá ver a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="278b7-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="278b7-120">Configurável por meio de código ou App. config</span><span class="sxs-lookup"><span data-stu-id="278b7-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="278b7-121">O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="278b7-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="278b7-122">Você também pode alterar o nome do arquivo App. config para algo diferente para que ele não é reconhecido e remova a chamada de método para ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="278b7-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="278b7-123">Qualquer um dos métodos resulta no mesmo comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="278b7-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="278b7-124">Cenário</span><span class="sxs-lookup"><span data-stu-id="278b7-124">Scenario</span></span>
 <span data-ttu-id="278b7-125">Este exemplo demonstra o roteador que atua como uma bomba de mensagem básica.</span><span class="sxs-lookup"><span data-stu-id="278b7-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="278b7-126">O serviço de roteamento atua como um nó de proxy transparente configurado para passar mensagens diretamente para um conjunto predefinido de pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="278b7-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="278b7-127">Cenário do mundo real</span><span class="sxs-lookup"><span data-stu-id="278b7-127">Real World Scenario</span></span>
 <span data-ttu-id="278b7-128">A Contoso deseja aumentar a flexibilidade que ele tem na nomenclatura, endereçamento, configuração e segurança de seus serviços.</span><span class="sxs-lookup"><span data-stu-id="278b7-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="278b7-129">Para fazer isso, eles colocam uma bomba de mensagens básicas na frente de seus serviços para atuar como um ponto de extremidade voltado para o público.</span><span class="sxs-lookup"><span data-stu-id="278b7-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="278b7-130">Isso permite colocar uma segurança adicional na frente de seus serviços reais e torná-lo mais fácil de implementar escalado horizontalmente soluções ou controle de versão do serviço em uma data posterior.</span><span class="sxs-lookup"><span data-stu-id="278b7-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
>  <span data-ttu-id="278b7-131">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="278b7-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="278b7-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="278b7-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="278b7-133">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="278b7-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="278b7-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="278b7-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="278b7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="278b7-135">See also</span></span>

- [<span data-ttu-id="278b7-136">Hospedagem de AppFabric e persistência exemplos</span><span class="sxs-lookup"><span data-stu-id="278b7-136">AppFabric Hosting and Persistence Samples</span></span>](https://go.microsoft.com/fwlink/?LinkId=193961)
