---
title: "Filtros avançados"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a9d7ce5029e0f5b95b98dd4f44e42f6c07bb8e1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="advanced-filters"></a><span data-ttu-id="63e37-102">Filtros avançados</span><span class="sxs-lookup"><span data-stu-id="63e37-102">Advanced Filters</span></span>
<span data-ttu-id="63e37-103">Este exemplo demonstra um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="63e37-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="63e37-104">O serviço de roteamento é um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] componente que torna mais fácil incluir um roteador baseado em conteúdo em seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63e37-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="63e37-105">Este exemplo se adapta o padrão [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] exemplo de cálculo para se comunicar usando o serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="63e37-105">This sample adapts the standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Calculator sample to communicate using the routing service.</span></span> <span data-ttu-id="63e37-106">Este exemplo mostra como definir a lógica de roteamento baseado em conteúdo com o uso de filtros de mensagem e tabelas de filtro de mensagem.</span><span class="sxs-lookup"><span data-stu-id="63e37-106">This sample shows how to define content-based routing logic through the use of message filters and message filter tables.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="63e37-107">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="63e37-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="63e37-108">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="63e37-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="63e37-109">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="63e37-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="63e37-110">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="63e37-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a><span data-ttu-id="63e37-111">Detalhes de exemplo</span><span class="sxs-lookup"><span data-stu-id="63e37-111">Sample Details</span></span>  
 <span data-ttu-id="63e37-112">A tabela a seguir mostra os filtros de mensagem que são adicionados à tabela de filtro de mensagem do serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="63e37-112">The following table shows the message filters that are added to the message filter table of the routing service.</span></span>  
  
|<span data-ttu-id="63e37-113">Filtro</span><span class="sxs-lookup"><span data-stu-id="63e37-113">Filter</span></span>|<span data-ttu-id="63e37-114">Regra</span><span class="sxs-lookup"><span data-stu-id="63e37-114">Rule</span></span>|<span data-ttu-id="63e37-115">Prioridade</span><span class="sxs-lookup"><span data-stu-id="63e37-115">Priority</span></span>|  
|------------|----------|--------------|  
|<span data-ttu-id="63e37-116">Se (tem cabeçalho)</span><span class="sxs-lookup"><span data-stu-id="63e37-116">If (has header)</span></span>|<span data-ttu-id="63e37-117">Arredondamento</span><span class="sxs-lookup"><span data-stu-id="63e37-117">Rounding</span></span>|<span data-ttu-id="63e37-118">2</span><span class="sxs-lookup"><span data-stu-id="63e37-118">2</span></span>|  
|<span data-ttu-id="63e37-119">Se (apareceram na Ep2)</span><span class="sxs-lookup"><span data-stu-id="63e37-119">If (showed up on Ep2)</span></span>|<span data-ttu-id="63e37-120">Normal</span><span class="sxs-lookup"><span data-stu-id="63e37-120">Regular</span></span>|<span data-ttu-id="63e37-121">1</span><span class="sxs-lookup"><span data-stu-id="63e37-121">1</span></span>|  
|<span data-ttu-id="63e37-122">Se (aparecia com endereço2)</span><span class="sxs-lookup"><span data-stu-id="63e37-122">If (showed up with Address2)</span></span>|<span data-ttu-id="63e37-123">Arredondamento</span><span class="sxs-lookup"><span data-stu-id="63e37-123">Rounding</span></span>|<span data-ttu-id="63e37-124">1</span><span class="sxs-lookup"><span data-stu-id="63e37-124">1</span></span>|  
|<span data-ttu-id="63e37-125">Se (RoundRobin1)</span><span class="sxs-lookup"><span data-stu-id="63e37-125">If (RoundRobin1)</span></span>|<span data-ttu-id="63e37-126">Normal</span><span class="sxs-lookup"><span data-stu-id="63e37-126">Regular</span></span>|<span data-ttu-id="63e37-127">0</span><span class="sxs-lookup"><span data-stu-id="63e37-127">0</span></span>|  
|<span data-ttu-id="63e37-128">Se (RoundRobin2)</span><span class="sxs-lookup"><span data-stu-id="63e37-128">If (RoundRobin2)</span></span>|<span data-ttu-id="63e37-129">Arredondamento</span><span class="sxs-lookup"><span data-stu-id="63e37-129">Rounding</span></span>|<span data-ttu-id="63e37-130">0</span><span class="sxs-lookup"><span data-stu-id="63e37-130">0</span></span>|  
  
 <span data-ttu-id="63e37-131">As tabelas de filtro de mensagem e filtros de mensagem podem ser criadas e configuradas por meio de código ou no arquivo de configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="63e37-131">The message filters and message filter tables can be created and configured either through code or in the application configuration file.</span></span> <span data-ttu-id="63e37-132">Para este exemplo, você pode encontrar as tabelas de filtro de mensagem definidas por meio de código no arquivo RoutingService\routing.cs ou definidas no arquivo de configuração do aplicativo no arquivo RoutingService\App.config e filtros de mensagem.</span><span class="sxs-lookup"><span data-stu-id="63e37-132">For this sample, you can find the message filters and message filter tables defined through code in the RoutingService\routing.cs file, or defined in the application configuration file in the RoutingService\App.config file.</span></span> <span data-ttu-id="63e37-133">Os parágrafos a seguir descrevem como as tabelas de filtro de mensagem e filtros de mensagem são criadas para este exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="63e37-133">The following paragraphs describe how the message filters and message filter tables are created for this sample through code.</span></span>  
  
 <span data-ttu-id="63e37-134">Primeiro, um <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> procura o cabeçalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="63e37-134">First, an <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> looks for the custom header.</span></span> <span data-ttu-id="63e37-135">Observe que <xref:System.ServiceModel.WSHttpBinding> resulta em uma versão de envelope usando SOAP 1.2, portanto, a instrução XPath é definida para usar o namespace de SOAP 1.2.</span><span class="sxs-lookup"><span data-stu-id="63e37-135">Note that <xref:System.ServiceModel.WSHttpBinding> results in an envelope version using SOAP 1.2, so the XPath statement is defined to use the SOAP 1.2 namespace.</span></span> <span data-ttu-id="63e37-136">O Gerenciador de namespace padrão para <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s já define um prefixo para o namespace de SOAP 1.2, /s12, que pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="63e37-136">The default namespace manager for <xref:System.ServiceModel.Dispatcher.XPathMessageFilter>s already defines a prefix for the SOAP 1.2 namespace, /s12, which can be used.</span></span> <span data-ttu-id="63e37-137">No entanto, o Gerenciador de namespace padrão não tem o namespace personalizado que o cliente usa para definir o valor real do cabeçalho, portanto esse prefixo deve ser definido.</span><span class="sxs-lookup"><span data-stu-id="63e37-137">However, the default namespace manager does not have the custom namespace that the client uses to define the actual header value, so that prefix must be defined.</span></span> <span data-ttu-id="63e37-138">Qualquer mensagem que aparece com esse cabeçalho corresponde a este filtro.</span><span class="sxs-lookup"><span data-stu-id="63e37-138">Any message that shows up with this header matches this filter.</span></span>  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 <span data-ttu-id="63e37-139">O segundo filtro for um <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, que corresponde a qualquer mensagem que foi recebida o `calculatorEndpoint`.</span><span class="sxs-lookup"><span data-stu-id="63e37-139">The second filter is an <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>, which matches any message that was received on the `calculatorEndpoint`.</span></span> <span data-ttu-id="63e37-140">O nome do ponto de extremidade é definido quando um objeto de ponto de extremidade de serviço é criado.</span><span class="sxs-lookup"><span data-stu-id="63e37-140">The endpoint name is defined when a service endpoint object is created.</span></span>  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 <span data-ttu-id="63e37-141">O terceiro filtro é um <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span><span class="sxs-lookup"><span data-stu-id="63e37-141">The third filter is a <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>.</span></span> <span data-ttu-id="63e37-142">Isso corresponde a qualquer mensagem que aparecem em um ponto de extremidade com um endereço que corresponde ao prefixo do endereço (ou a parte frontal) fornecido.</span><span class="sxs-lookup"><span data-stu-id="63e37-142">This matches any message that showed up on an endpoint with an address that matches the address prefix (or the front portion) provided.</span></span> <span data-ttu-id="63e37-143">Neste exemplo, o prefixo de endereço é definido como "http://localhost/routingservice/router/rounding/".</span><span class="sxs-lookup"><span data-stu-id="63e37-143">In this example the address prefix is defined as "http://localhost/routingservice/router/rounding/".</span></span> <span data-ttu-id="63e37-144">Isso significa que as mensagens de entrada que são endereçadas para "http://localhost/routingservice/router/rounding/ *" correspondem a este filtro.</span><span class="sxs-lookup"><span data-stu-id="63e37-144">This means that any incoming messages that are addressed to "http://localhost/routingservice/router/rounding/*" are matched by this filter.</span></span> <span data-ttu-id="63e37-145">Nesse caso, é mensagens que aparecem no ponto de extremidade de arredondamento cálculo, que tem o endereço de "http://localhost/routingservice/router/rounding/calculator".</span><span class="sxs-lookup"><span data-stu-id="63e37-145">In this case, it is messages that show up on the Rounding Calculator endpoint, which has the address of "http://localhost/routingservice/router/rounding/calculator".</span></span>  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 <span data-ttu-id="63e37-146">Os dois últimos filtros de mensagem são personalizados <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span><span class="sxs-lookup"><span data-stu-id="63e37-146">The last two message filters are custom <xref:System.ServiceModel.Dispatcher.MessageFilter>s.</span></span> <span data-ttu-id="63e37-147">Neste exemplo, um filtro de mensagem "RoundRobin" é usado.</span><span class="sxs-lookup"><span data-stu-id="63e37-147">In this example, a "RoundRobin" message filter is used.</span></span> <span data-ttu-id="63e37-148">Esse filtro de mensagem é criado no arquivo RoutingService\RoundRobinMessageFilter.cs fornecido.</span><span class="sxs-lookup"><span data-stu-id="63e37-148">This message filter is created in the provided RoutingService\RoundRobinMessageFilter.cs file.</span></span> <span data-ttu-id="63e37-149">Esses filtros, quando definidos para o mesmo grupo, alternam entre relatórios se eles correspondem a mensagem e que eles não, de modo que apenas um deles responde `true` por vez.</span><span class="sxs-lookup"><span data-stu-id="63e37-149">These filters, when set to the same group, alternate between reporting that they match the message and that they do not, such that only one of them responds `true` at a time.</span></span>  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 <span data-ttu-id="63e37-150">Em seguida, todas as mensagens são adicionadas a um <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span><span class="sxs-lookup"><span data-stu-id="63e37-150">Next, all of those messages are added to a <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>.</span></span> <span data-ttu-id="63e37-151">Dessa forma, as prioridades são especificadas para influenciar a ordem na qual a tabela de filtro de mensagem executa os filtros.</span><span class="sxs-lookup"><span data-stu-id="63e37-151">In doing so, priorities are specified to influence the order in which the message filter table executes the filters.</span></span> <span data-ttu-id="63e37-152">Quanto maior a prioridade, mais cedo que o filtro é executado; Quanto menor a prioridade, depois de um filtro é executado.</span><span class="sxs-lookup"><span data-stu-id="63e37-152">The higher the priority, the sooner the filter is executed; the lower the priority, the later a filter is executed.</span></span> <span data-ttu-id="63e37-153">Assim, um filtro com prioridade 2 é executado antes de um filtro com prioridade 1.</span><span class="sxs-lookup"><span data-stu-id="63e37-153">Thus a filter at priority 2 runs before a filter at priority 1.</span></span> <span data-ttu-id="63e37-154">O nível de prioridade padrão se nenhum for especificado é 0.</span><span class="sxs-lookup"><span data-stu-id="63e37-154">The default priority level if none is specified is 0.</span></span> <span data-ttu-id="63e37-155">Uma tabela de filtro de mensagem executa todos os filtros em um nível de prioridade determinada antes de passar para o próximo nível de prioridade mais baixo.</span><span class="sxs-lookup"><span data-stu-id="63e37-155">A message filter table executes all of the filters at a given priority level before moving to the next lowest priority level.</span></span> <span data-ttu-id="63e37-156">Se uma correspondência for encontrada em uma prioridade específica, em seguida, a tabela de filtro de mensagem não continue tentando localizar correspondências com a próxima prioridade inferior.</span><span class="sxs-lookup"><span data-stu-id="63e37-156">If a match is found at a particular priority, then the message filter table does not continue trying to find matches at the next lower priority.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63e37-157">Embora este exemplo mostra como usar as prioridades de filtro de mensagem, em geral é mais funcionais e melhor design para design e configurar seus filtros de modo que eles não exigem priorização funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="63e37-157">While this example shows how to use message filter priorities, in general it is more performant and better design to design and configure your filters such that they do not require prioritization to function correctly.</span></span>  
  
 <span data-ttu-id="63e37-158">O primeiro filtro a ser adicionado é o filtro XPath e sua prioridade é definida como 2.</span><span class="sxs-lookup"><span data-stu-id="63e37-158">The first filter to be added is the XPath filter and its priority is set to 2.</span></span> <span data-ttu-id="63e37-159">Este é o primeiro filtro de mensagem que é executado.</span><span class="sxs-lookup"><span data-stu-id="63e37-159">This is the first message filter that executes.</span></span> <span data-ttu-id="63e37-160">Se ele encontrar o cabeçalho personalizado, independentemente do que os resultados dos outros filtros seriam, a mensagem é roteada para o ponto de extremidade de arredondamento Calculadora.</span><span class="sxs-lookup"><span data-stu-id="63e37-160">If it finds the custom header, regardless of what the results of the other filters would be, the message is routed to the Rounding Calculator endpoint.</span></span>  
  
 <span data-ttu-id="63e37-161">Com prioridade 1, os dois filtros são adicionados.</span><span class="sxs-lookup"><span data-stu-id="63e37-161">At priority 1, two filters are added.</span></span> <span data-ttu-id="63e37-162">Novamente, esses executado somente se o filtro XPath com prioridade 2 não coincide com a mensagem.</span><span class="sxs-lookup"><span data-stu-id="63e37-162">Again, these only run if the XPath filter at priority 2 does not match the message.</span></span> <span data-ttu-id="63e37-163">Esses dois filtros mostram dois modos diferentes para determinar onde a mensagem foi tratada quando ele aparecia.</span><span class="sxs-lookup"><span data-stu-id="63e37-163">These two filters show two different ways to determine where the message was addressed when it showed up.</span></span> <span data-ttu-id="63e37-164">Como os dois filtros efetivamente verificam para ver se a mensagem chegou em um dos dois pontos de extremidade, eles podem ser executados no mesmo nível de prioridade porque eles são não ambos retornam `true` ao mesmo tempo.</span><span class="sxs-lookup"><span data-stu-id="63e37-164">Because the two filters effectively check to see whether the message arrived at one of the two endpoints, they can be run at the same priority level because they do not both return `true` at the same time.</span></span>  
  
 <span data-ttu-id="63e37-165">Por fim, com prioridade 0 (prioridade mais baixa), execute o RoundRobin mensagem filtros.</span><span class="sxs-lookup"><span data-stu-id="63e37-165">Finally, at Priority 0 (the lowest priority) run the RoundRobin message filters.</span></span> <span data-ttu-id="63e37-166">Como os filtros são configurados com o mesmo nome de grupo, somente um deles corresponde a cada vez.</span><span class="sxs-lookup"><span data-stu-id="63e37-166">Because the filters are configured with the same group name, only one of them matches at a time.</span></span> <span data-ttu-id="63e37-167">Como todas as mensagens com o cabeçalho personalizado tem sido roteadas e todos os resolvidos para os pontos de extremidade específicos virtualizados, mensagens tratadas por filtros de mensagem RoundRobin são apenas as mensagens que foram resolvidas para o ponto de extremidade de roteador padrão sem personalizado cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="63e37-167">Because all messages with the custom header have been routed and all those addressed to the specific virtualized endpoints, messages handled by the RoundRobin message filters are only messages that were addressed to the default router endpoint without the custom header.</span></span> <span data-ttu-id="63e37-168">Como alternar essas mensagens em uma mensagem para cada chamada, metade das operações de ir para o ponto de extremidade de calculadora Regular e a outra metade, vá para o ponto de extremidade de arredondamento Calculadora.</span><span class="sxs-lookup"><span data-stu-id="63e37-168">Because these messages switch on a message for each call, half of the operations go to the Regular Calculator endpoint and the other half go to the Rounding Calculator endpoint.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="63e37-169">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="63e37-169">To use this sample</span></span>  
  
1.  <span data-ttu-id="63e37-170">Usando [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], abra AdvancedFilters.sln.</span><span class="sxs-lookup"><span data-stu-id="63e37-170">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedFilters.sln.</span></span>  
  
2.  <span data-ttu-id="63e37-171">Para abrir **Solution Explorer**, selecione **Solution Explorer** do **exibição** menu.</span><span class="sxs-lookup"><span data-stu-id="63e37-171">To open **Solution Explorer**, select **Solution Explorer** from the **View** menu.</span></span>  
  
3.  <span data-ttu-id="63e37-172">Pressione F5 ou CTRL + SHIFT + B no [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="63e37-172">Press F5 or CTRL+SHIFT+B in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="63e37-173">Se você quiser iniciar os projetos necessários quando você pressionar F5, a solução e selecione **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="63e37-173">If you would like to auto-launch the necessary projects when you press F5, right-click the solution and select **Properties**.</span></span> <span data-ttu-id="63e37-174">Selecione o **projeto de inicialização** nó **propriedades comuns** no painel esquerdo.</span><span class="sxs-lookup"><span data-stu-id="63e37-174">Select the **Startup Project** node under **Common Properties** in the left pane.</span></span> <span data-ttu-id="63e37-175">Selecione o **vários projetos de inicialização** botão de opção e defina todos os projetos para que o **iniciar** ação.</span><span class="sxs-lookup"><span data-stu-id="63e37-175">Select the **Multiple Startup Projects**  radio button and set all of the projects to have the **Start** action.</span></span>  
  
    2.  <span data-ttu-id="63e37-176">Se você compilar o projeto com CTRL + SHIFT + B, inicie os seguintes aplicativos:</span><span class="sxs-lookup"><span data-stu-id="63e37-176">If you build the project with CTRL+SHIFT+B, you must start the following applications:</span></span>  
  
        1.  <span data-ttu-id="63e37-177">Calculadora de cliente (. / CalculatorClient/bin/client.exe)</span><span class="sxs-lookup"><span data-stu-id="63e37-177">Calculator Client (./CalculatorClient/bin/client.exe)</span></span>  
  
        2.  <span data-ttu-id="63e37-178">Serviço de cálculo (. / CalculatorService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="63e37-178">Calculator Service (./CalculatorService/bin/service.exe)</span></span>  
  
        3.  <span data-ttu-id="63e37-179">O serviço de roteamento Calculadora (. / RoundingCalcService/bin/service.exe)</span><span class="sxs-lookup"><span data-stu-id="63e37-179">Routing Calculator Service (./RoundingCalcService/bin/service.exe)</span></span>  
  
        4.  <span data-ttu-id="63e37-180">RoutingService (. / RoutingService/bin/RoutingService.exe)</span><span class="sxs-lookup"><span data-stu-id="63e37-180">RoutingService (./RoutingService/bin/RoutingService.exe)</span></span>  
  
4.  <span data-ttu-id="63e37-181">Na janela do console do cliente Calculadora, pressione ENTER para iniciar o cliente.</span><span class="sxs-lookup"><span data-stu-id="63e37-181">In the console window of the Calculator client, press ENTER to start the client.</span></span> <span data-ttu-id="63e37-182">O cliente retorna uma lista de pontos de extremidade de destino à sua escolha.</span><span class="sxs-lookup"><span data-stu-id="63e37-182">The client returns a list of destination endpoints to choose from.</span></span>  
  
5.  <span data-ttu-id="63e37-183">Escolha um ponto de extremidade de destino, digitando seu letra correspondente e pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="63e37-183">Choose a destination endpoint by typing its corresponding letter and press ENTER.</span></span>  
  
6.  <span data-ttu-id="63e37-184">Em seguida, o cliente solicita se você deseja adicionar um cabeçalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="63e37-184">Next, the client asks you if you want to add a custom header.</span></span> <span data-ttu-id="63e37-185">Pressione s para Sim ou N para não e, em seguida, pressione ENTER.</span><span class="sxs-lookup"><span data-stu-id="63e37-185">Press Y for Yes or N for No, then press ENTER.</span></span>  
  
7.  <span data-ttu-id="63e37-186">Dependendo das seleções feitas, você deve ver resultados diferentes.</span><span class="sxs-lookup"><span data-stu-id="63e37-186">Depending on the selections you made, you should see different outputs.</span></span>  
  
    1.  <span data-ttu-id="63e37-187">A seguir está que a saída retornada se você adicionou um cabeçalho personalizado para as mensagens.</span><span class="sxs-lookup"><span data-stu-id="63e37-187">The following is the output returned if you added a custom header to the messages.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  <span data-ttu-id="63e37-188">A seguir está que a saída retornada se você escolher o ponto de extremidade de arredondamento Calculadora sem um cabeçalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="63e37-188">The following is the output returned if you chose the Rounding Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  <span data-ttu-id="63e37-189">A seguir está que a saída retornada se você escolher o ponto de extremidade de calculadora regulares sem um cabeçalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="63e37-189">The following is the output returned if you chose the Regular Calculator endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  <span data-ttu-id="63e37-190">A seguir está que a saída retornada se você escolher o ponto de extremidade de roteador padrão sem um cabeçalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="63e37-190">The following is the output returned if you chose the Default Router endpoint without a custom header.</span></span>  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  <span data-ttu-id="63e37-191">O serviço de cálculo e o serviço de cálculo de arredondamento também imprime um log das operações invocado para as janelas do console do respectivos.</span><span class="sxs-lookup"><span data-stu-id="63e37-191">The Calculator Service and the Rounding Calculator Service also prints out a log of the operations invoked to their respective console windows.</span></span>  
  
9. <span data-ttu-id="63e37-192">Na janela do console de cliente, digite `quit` e pressione ENTER para sair.</span><span class="sxs-lookup"><span data-stu-id="63e37-192">In the client console window, type `quit` and press ENTER to exit.</span></span>  
  
10. <span data-ttu-id="63e37-193">Pressione ENTER nas janelas do console de serviços para encerrar os serviços.</span><span class="sxs-lookup"><span data-stu-id="63e37-193">Press ENTER in the services console windows to terminate the services.</span></span>  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="63e37-194">Configuráveis por meio de código ou App. config</span><span class="sxs-lookup"><span data-stu-id="63e37-194">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="63e37-195">O vem de exemplo configurado para usar um arquivo App. config para definir o comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="63e37-195">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="63e37-196">Você também pode alterar o nome do arquivo RoutingService\App.config para algo diferente para que ele não é reconhecido e remova a chamada de método para `ConfigureRouterViaCode()` em RoutingService\routing.cs.</span><span class="sxs-lookup"><span data-stu-id="63e37-196">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and uncomment the method call to `ConfigureRouterViaCode()` in RoutingService\routing.cs.</span></span> <span data-ttu-id="63e37-197">Um método resulta no mesmo comportamento do roteador.</span><span class="sxs-lookup"><span data-stu-id="63e37-197">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="63e37-198">Cenário</span><span class="sxs-lookup"><span data-stu-id="63e37-198">Scenario</span></span>  
 <span data-ttu-id="63e37-199">Este exemplo demonstra o roteador que atua como um roteador baseado em conteúdo, permitindo que vários tipos ou implementação de serviços a serem expostas por meio de um ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="63e37-199">This sample demonstrates the router acting as a content-based router allowing multiple types or implementation of services to be exposed through one endpoint.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="63e37-200">Cenário do mundo real</span><span class="sxs-lookup"><span data-stu-id="63e37-200">Real World Scenario</span></span>  
 <span data-ttu-id="63e37-201">A Contoso deseja virtualizar todos os seus serviços para expor apenas um ponto de extremidade publicamente por meio do qual eles oferecem acesso a vários tipos diferentes de serviços.</span><span class="sxs-lookup"><span data-stu-id="63e37-201">Contoso wants to virtualize all of their services to expose only one endpoint publicly through which they offer access to multiple different types of services.</span></span> <span data-ttu-id="63e37-202">Nesse caso, eles utilizam baseado em conteúdo capacidades de roteamento do serviço de roteamento para determinar onde as solicitações de entrada devem ser enviadas.</span><span class="sxs-lookup"><span data-stu-id="63e37-202">In this case they utilize the routing service’s content-based routing capabilities to determine where the incoming requests should be sent.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e37-203">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63e37-203">See Also</span></span>  
 [<span data-ttu-id="63e37-204">Exemplos de persistência e hospedagem de AppFabric</span><span class="sxs-lookup"><span data-stu-id="63e37-204">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
