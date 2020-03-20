---
title: Olá Mundo com o serviço de roteamento
ms.date: 03/30/2017
ms.assetid: 0f4b0d5b-6522-4ad5-9f3a-baa78316d7d1
ms.openlocfilehash: 86a2981e8b861da9d5ccf0a34fe037f3ef419aab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183642"
---
# <a name="hello-world-with-the-routing-service"></a><span data-ttu-id="5f023-102">Olá Mundo com o serviço de roteamento</span><span class="sxs-lookup"><span data-stu-id="5f023-102">Hello World with the Routing Service</span></span>
<span data-ttu-id="5f023-103">Esta amostra demonstra o Serviço de Roteamento da Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5f023-103">This sample demonstrates the Windows Communication Foundation (WCF) Routing Service.</span></span> <span data-ttu-id="5f023-104">O Serviço de Roteamento é um componente WCF que facilita a inclusão de um roteador baseado em conteúdo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5f023-104">The Routing Service is a WCF component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="5f023-105">Esta amostra adapta a amostra padrão da calculadora WCF para se comunicar usando o Serviço de Roteamento.</span><span class="sxs-lookup"><span data-stu-id="5f023-105">This sample adapts the standard WCF Calculator Sample to communicate using the Routing Service.</span></span> <span data-ttu-id="5f023-106">Nesta amostra, o cliente Calculadora é configurado para enviar mensagens para um ponto final exposto pelo roteador.</span><span class="sxs-lookup"><span data-stu-id="5f023-106">In this sample, the Calculator client is configured to send messages to an endpoint exposed by the router.</span></span> <span data-ttu-id="5f023-107">O Serviço de Roteamento está configurado para aceitar todas as mensagens enviadas a ele e encaminhá-las para um ponto final que corresponde ao serviço Calculadora.</span><span class="sxs-lookup"><span data-stu-id="5f023-107">The Routing Service is configured to accept all messages sent to it and to forward them to an endpoint that corresponds to the Calculator service.</span></span> <span data-ttu-id="5f023-108">Assim, as mensagens enviadas pelo cliente são recebidas pelo roteador e redirecionadas para o serviço de Calculadora real.</span><span class="sxs-lookup"><span data-stu-id="5f023-108">Thus messages sent from the client are received by the router and re-routed to the actual Calculator service.</span></span> <span data-ttu-id="5f023-109">As mensagens do serviço Calculadora são enviadas de volta para o roteador, que por sua vez as repassa ao cliente calculadora.</span><span class="sxs-lookup"><span data-stu-id="5f023-109">Messages from the Calculator service are sent back to the router, which in turn passes them back to the Calculator client.</span></span>

### <a name="to-use-this-sample"></a><span data-ttu-id="5f023-110">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="5f023-110">To use this sample</span></span>

1. <span data-ttu-id="5f023-111">Usando o Visual Studio 2012, abra HelloRoutingService.sln.</span><span class="sxs-lookup"><span data-stu-id="5f023-111">Using Visual Studio 2012, open HelloRoutingService.sln.</span></span>

2. <span data-ttu-id="5f023-112">Pressione F5 ou CTRL+SHIFT+B.</span><span class="sxs-lookup"><span data-stu-id="5f023-112">Press F5 or CTRL+SHIFT+B.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5f023-113">Se você pressionar F5, o Cliente calculadora é automaticamente iniciado.</span><span class="sxs-lookup"><span data-stu-id="5f023-113">If you press F5, the Calculator Client automatically starts.</span></span> <span data-ttu-id="5f023-114">Se você pressionar CTRL+SHIFT+B (build), você deve começar a seguir os aplicativos você mesmo.</span><span class="sxs-lookup"><span data-stu-id="5f023-114">If you press CTRL+SHIFT+B (build), you must start following applications yourself.</span></span>
    >
    > 1. <span data-ttu-id="5f023-115">Cliente da calculadora (./CalculadoraCliente/bin/cliente.exe</span><span class="sxs-lookup"><span data-stu-id="5f023-115">Calculator client (./CalculatorClient/bin/client.exe</span></span>
    > 2. <span data-ttu-id="5f023-116">Serviço de calculadora (./CalculadoraService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="5f023-116">Calculator service (./CalculatorService/bin/service.exe)</span></span>
    > 3. <span data-ttu-id="5f023-117">Serviço de roteamento (./RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="5f023-117">Routing service (./RoutingService/bin/RoutingService.exe)</span></span>

3. <span data-ttu-id="5f023-118">Pressione ENTER para iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="5f023-118">Press ENTER to start the client.</span></span>

     <span data-ttu-id="5f023-119">Você deve ver o seguinte resultado:</span><span class="sxs-lookup"><span data-stu-id="5f023-119">You should see the following output:</span></span>

    ```console
     Add(100,15.99) = 115.99

     Subtract(145,76.54) = 68.46

     Multiply(9,81.25) = 731.25

     Divide(22,7) = 3.14285714285714
    ```

## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="5f023-120">Configurável via Código ou App.Config</span><span class="sxs-lookup"><span data-stu-id="5f023-120">Configurable via Code or App.Config</span></span>
 <span data-ttu-id="5f023-121">Os navios de amostra configurados para usar um arquivo App.config para definir o comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="5f023-121">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="5f023-122">Você também pode alterar o nome do arquivo App.config para outra coisa para que ele não seja reconhecido e descomentar a chamada do método para ConfigureRouterViaCode().</span><span class="sxs-lookup"><span data-stu-id="5f023-122">You can also change the name of the App.config file to something else so that it is not recognized and uncomment the method call to ConfigureRouterViaCode().</span></span> <span data-ttu-id="5f023-123">Qualquer método resulta no mesmo comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="5f023-123">Either method results in the same behavior from the router.</span></span>

### <a name="scenario"></a><span data-ttu-id="5f023-124">Cenário</span><span class="sxs-lookup"><span data-stu-id="5f023-124">Scenario</span></span>
 <span data-ttu-id="5f023-125">Esta amostra demonstra o roteador agindo como uma bomba de mensagem básica.</span><span class="sxs-lookup"><span data-stu-id="5f023-125">This sample demonstrates the router acting as a basic message pump.</span></span> <span data-ttu-id="5f023-126">O serviço de roteamento funciona como um nó proxy transparente configurado para passar mensagens diretamente para um conjunto pré-configurado de pontos finais de destino.</span><span class="sxs-lookup"><span data-stu-id="5f023-126">The routing service acts as a transparent proxy node configured to pass messages directly to a preconfigured set of destination endpoints.</span></span>

### <a name="real-world-scenario"></a><span data-ttu-id="5f023-127">Cenário do Mundo Real</span><span class="sxs-lookup"><span data-stu-id="5f023-127">Real World Scenario</span></span>
 <span data-ttu-id="5f023-128">Contoso quer aumentar a flexibilidade que tem na nomenclatura, endereçamento, configuração e segurança de seus serviços.</span><span class="sxs-lookup"><span data-stu-id="5f023-128">Contoso wants to increase the flexibility it has in the naming, addressing, configuration, and security of its services.</span></span> <span data-ttu-id="5f023-129">Para isso, eles colocam uma bomba de mensagem básica na frente de seus serviços para atuar como um ponto final voltado para o público.</span><span class="sxs-lookup"><span data-stu-id="5f023-129">To do this, they place a basic message pump in front of their services to act as a public facing endpoint.</span></span> <span data-ttu-id="5f023-130">Isso permite que eles coloquem segurança adicional na frente de seus serviços reais e facilitem a implementação de soluções dimensionadas ou versão de serviço em uma data posterior.</span><span class="sxs-lookup"><span data-stu-id="5f023-130">This allows them to place additional security in front of their actual services and make it easier to implement scaled out solutions or service versioning at a later date.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5f023-131">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5f023-131">The samples may already be installed on your computer.</span></span> <span data-ttu-id="5f023-132">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="5f023-132">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5f023-133">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="5f023-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5f023-134">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="5f023-134">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\HelloRoutingService`  
  
## <a name="see-also"></a><span data-ttu-id="5f023-135">Confira também</span><span class="sxs-lookup"><span data-stu-id="5f023-135">See also</span></span>

- <span data-ttu-id="5f023-136">[Hospedagem de AppFabric e persistência Exemplos](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="5f023-136">[AppFabric Hosting and Persistence Samples](https://docs.microsoft.com/previous-versions/appfabric/ff383418(v=azure.10))</span></span>
