---
title: 'Como: usar filtros'
ms.date: 03/30/2017
ms.assetid: f2c7255f-c376-460e-aa20-14071f1666e5
ms.openlocfilehash: 6c357f2f410362d56fc931529a9fe731df0a477e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968764"
---
# <a name="how-to-use-filters"></a><span data-ttu-id="20eee-102">Como: usar filtros</span><span class="sxs-lookup"><span data-stu-id="20eee-102">How To: Use Filters</span></span>
<span data-ttu-id="20eee-103">Este tópico descreve as etapas básicas necessárias para criar uma configuração de roteamento que usa vários filtros.</span><span class="sxs-lookup"><span data-stu-id="20eee-103">This topic outlines the basic steps required to create a routing configuration that uses multiple filters.</span></span> <span data-ttu-id="20eee-104">Neste exemplo, as mensagens são roteadas para duas implementações de um serviço de calculadora, regularCalc e roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="20eee-104">In this example, messages are routed to two implementations of a calculator service, regularCalc and roundingCalc.</span></span> <span data-ttu-id="20eee-105">Ambas as implementações dão suporte às mesmas operações; no entanto, um serviço arredonda todos os cálculos para o valor inteiro mais próximo antes de retornar.</span><span class="sxs-lookup"><span data-stu-id="20eee-105">Both implementations support the same operations; however one service rounds all calculations to the nearest integer value before returning.</span></span> <span data-ttu-id="20eee-106">Um aplicativo cliente deve ser capaz de indicar se deve usar a versão de arredondamento do serviço; Se nenhuma preferência de serviço for expressa, a mensagem terá o balanceamento de carga entre os dois serviços.</span><span class="sxs-lookup"><span data-stu-id="20eee-106">A client application must be able to indicate whether to  use the rounding version of the service; if no service preference is expressed then the message is load balanced between the two services.</span></span> <span data-ttu-id="20eee-107">As operações expostas por ambos os serviços são:</span><span class="sxs-lookup"><span data-stu-id="20eee-107">The operations exposed by both services are:</span></span>  
  
- <span data-ttu-id="20eee-108">Adicionar</span><span class="sxs-lookup"><span data-stu-id="20eee-108">Add</span></span>  
  
- <span data-ttu-id="20eee-109">Subtração</span><span class="sxs-lookup"><span data-stu-id="20eee-109">Subtract</span></span>  
  
- <span data-ttu-id="20eee-110">Multiplicar</span><span class="sxs-lookup"><span data-stu-id="20eee-110">Multiply</span></span>  
  
- <span data-ttu-id="20eee-111">Divisão</span><span class="sxs-lookup"><span data-stu-id="20eee-111">Divide</span></span>  
  
 <span data-ttu-id="20eee-112">Como os dois serviços implementam as mesmas operações, você não pode usar o filtro de ação, pois a ação especificada na mensagem não será exclusiva.</span><span class="sxs-lookup"><span data-stu-id="20eee-112">Because both services implement the same operations, you cannot use the Action filter, because the action specified in the message will not be unique.</span></span> <span data-ttu-id="20eee-113">Em vez disso, você deve fazer trabalho adicional para garantir que as mensagens sejam roteadas para os pontos de extremidade apropriados.</span><span class="sxs-lookup"><span data-stu-id="20eee-113">Instead you must do additional work to ensure that the messages are routed to the appropriate endpoints.</span></span>  
  
### <a name="determine-unique-data"></a><span data-ttu-id="20eee-114">Determinar dados exclusivos</span><span class="sxs-lookup"><span data-stu-id="20eee-114">Determine Unique Data</span></span>  
  
1. <span data-ttu-id="20eee-115">Como ambas as implementações de serviço manipulam as mesmas operações e são, essencialmente, idênticas além dos dados que elas retornam, os dados base contidos nas mensagens enviadas de aplicativos cliente não são exclusivos o suficiente para permitir que você determine como rotear o Quest.</span><span class="sxs-lookup"><span data-stu-id="20eee-115">Because both service implementations handle the same operations, and are essentially identical other than the data that they return, the base data contained in messages sent from client applications is not unique enough to allow you to determine how to route the request.</span></span> <span data-ttu-id="20eee-116">Mas se o aplicativo cliente adicionar um valor de cabeçalho exclusivo à mensagem, você poderá usar esse valor para determinar como a mensagem deve ser roteada.</span><span class="sxs-lookup"><span data-stu-id="20eee-116">But if the client application adds a unique header value to the message, then you can use this value to determine how the message should be routed.</span></span>  
  
     <span data-ttu-id="20eee-117">Para este exemplo, se o aplicativo cliente precisar que a mensagem seja processada pela calculadora de arredondamento, ele adicionará um cabeçalho personalizado usando o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="20eee-117">For this example, if the client application needs the message to be processed by the rounding calculator, it adds a custom header by using the following code:</span></span>  
  
    ```csharp  
    messageHeadersElement.Add(MessageHeader.CreateHeader("RoundingCalculator",   
                                   "http://my.custom.namespace/", "rounding"));  
    ```  
  
     <span data-ttu-id="20eee-118">Agora você pode usar o filtro XPath para inspecionar mensagens para esse cabeçalho e rotear mensagens que contêm o cabeçalho para o serviço roundCalc.</span><span class="sxs-lookup"><span data-stu-id="20eee-118">You can now use the XPath filter to inspect messages for this header, and route messages containing the header to the roundCalc service.</span></span>  
  
2. <span data-ttu-id="20eee-119">Além disso, o serviço de roteamento expõe dois pontos de extremidade de serviço virtual que podem ser usados com os filtros EndpointName, EndpointAddress ou PrefixEndpointAddress para rotear exclusivamente as mensagens de entrada para uma implementação de calculadora específica com base no ponto de extremidade para o qual o aplicativo cliente envia a solicitação.</span><span class="sxs-lookup"><span data-stu-id="20eee-119">Additionally the Routing Service exposes two virtual service endpoints that can be used with the EndpointName, EndpointAddress, or PrefixEndpointAddress filters to uniquely route incoming messages to a specific calculator implementation based on the endpoint to which the client application submits the request.</span></span>  
  
### <a name="define-endpoints"></a><span data-ttu-id="20eee-120">Definir pontos de extremidade</span><span class="sxs-lookup"><span data-stu-id="20eee-120">Define Endpoints</span></span>  
  
1. <span data-ttu-id="20eee-121">Ao definir os pontos de extremidade usados pelo serviço de roteamento, primeiro você deve determinar a forma do canal usado por seus clientes e serviços.</span><span class="sxs-lookup"><span data-stu-id="20eee-121">When defining the endpoints used by the Routing Service, you should first determine the shape of the channel used by your clients and services.</span></span> <span data-ttu-id="20eee-122">Nesse cenário, os serviços de destino usam um padrão de solicitação-resposta, portanto <xref:System.ServiceModel.Routing.IRequestReplyRouter> , o é usado.</span><span class="sxs-lookup"><span data-stu-id="20eee-122">In this scenario both the destination services use a request-reply pattern, so the <xref:System.ServiceModel.Routing.IRequestReplyRouter> is used.</span></span> <span data-ttu-id="20eee-123">O exemplo a seguir define os pontos de extremidade de serviço expostos pelo serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="20eee-123">The following example defines the service endpoints exposed by the Routing Service.</span></span>  
  
    ```xml  
    <services>  
          <service behaviorConfiguration="routingConfiguration"  
                   name="System.ServiceModel.Routing.RoutingService">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost/routingservice/router" />  
              </baseAddresses>  
            </host>  
            <!--Set up the inbound endpoints for the Routing Service-->  
            <!--first create the general router endpoint-->  
            <endpoint address="general"  
                      binding="wsHttpBinding"  
                      name="routerEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--create a virtual endpoint for the regular calculator service-->  
            <endpoint address="regular/calculator"  
                      binding="wsHttpBinding"  
                      name="calculatorEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
            <!--now create a virtual endpoint for the rounding calculator-->  
            <endpoint address="rounding/calculator"  
                      binding="wsHttpBinding"  
                      name="roundingEndpoint"  
                      contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
          </service>  
    </services>  
    ```  
  
     <span data-ttu-id="20eee-124">Com essa configuração, o serviço de roteamento expõe três pontos de extremidade separados.</span><span class="sxs-lookup"><span data-stu-id="20eee-124">With this configuration, the Routing Service exposes three separate endpoints.</span></span> <span data-ttu-id="20eee-125">Dependendo das opções de tempo de execução, o aplicativo cliente envia mensagens para um desses endereços.</span><span class="sxs-lookup"><span data-stu-id="20eee-125">Depending on run-time choices, the client application sends messages to one of these addresses.</span></span> <span data-ttu-id="20eee-126">As mensagens que chegam em um dos pontos de extremidade de serviço "virtual" ("arredondamento/calculadora" ou "regular/calculadora") são encaminhadas para a implementação da calculadora correspondente.</span><span class="sxs-lookup"><span data-stu-id="20eee-126">Messages arriving at one of the "virtual" service endpoints ("rounding/calculator" or "regular/calculator") are forwarded to the corresponding calculator implementation.</span></span> <span data-ttu-id="20eee-127">Se o aplicativo cliente não enviar a solicitação para um ponto de extremidade específico, a mensagem será endereçada ao ponto de extremidade geral.</span><span class="sxs-lookup"><span data-stu-id="20eee-127">If the client application doesn’t send the request to a particular endpoint, the message is addressed to the general endpoint.</span></span> <span data-ttu-id="20eee-128">Independentemente do ponto de extremidade escolhido, o aplicativo cliente também pode optar por incluir o cabeçalho personalizado para indicar que a mensagem deve ser encaminhada à implementação da calculadora de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="20eee-128">Regardless of the endpoint chosen, the client application may also choose to include the custom header to indicate that the message should be forwarded to the rounding calculator implementation.</span></span>  
  
2. <span data-ttu-id="20eee-129">O exemplo a seguir define os pontos de extremidade do cliente (destino) para os quais o serviço de roteamento roteia as mensagens.</span><span class="sxs-lookup"><span data-stu-id="20eee-129">The following example defines the client (destination) endpoints that the Routing Service routes messages to.</span></span>  
  
    ```xml  
    <client>  
          <endpoint name="regularCalcEndpoint"  
                    address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
  
          <endpoint name="roundingCalcEndpoint"  
                    address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                    binding="netTcpBinding"  
                    contract="*" />  
    </client>  
    ```  
  
     <span data-ttu-id="20eee-130">Esses pontos de extremidade são usados na tabela de filtro para indicar o ponto de final de destino para o qual a mensagem é enviada quando corresponde a um filtro específico.</span><span class="sxs-lookup"><span data-stu-id="20eee-130">These endpoints are used in the filter table to indicate the destination endpoint the message is sent to when it matches a specific filter.</span></span>  
  
### <a name="define-filters"></a><span data-ttu-id="20eee-131">Definir filtros</span><span class="sxs-lookup"><span data-stu-id="20eee-131">Define Filters</span></span>  
  
1. <span data-ttu-id="20eee-132">Para rotear mensagens com base no cabeçalho personalizado "RoundingCalculator" que o aplicativo cliente adiciona à mensagem, defina um filtro que usa uma consulta XPath para verificar a presença desse cabeçalho.</span><span class="sxs-lookup"><span data-stu-id="20eee-132">To route messages based on the "RoundingCalculator" custom header that the client application adds to the message, define a filter that uses an XPath query to check for the presence of this header.</span></span> <span data-ttu-id="20eee-133">Como esse cabeçalho é definido usando um namespace personalizado, adicione também uma entrada de namespace que define um prefixo de namespace personalizado de "Custom" que é usado na consulta XPath.</span><span class="sxs-lookup"><span data-stu-id="20eee-133">Because this header is defined by using a custom namespace, also add a namespace entry that defines a custom namespace prefix of "custom" that is used in the XPath query.</span></span> <span data-ttu-id="20eee-134">O exemplo a seguir define a seção de roteamento, a tabela de namespace e o filtro XPath necessários.</span><span class="sxs-lookup"><span data-stu-id="20eee-134">The following example defines the necessary routing section, namespace table, and XPath filter.</span></span>  
  
    ```xml  
    <routing>  
          <!-- use the namespace table element to define a prefix for our custom namespace-->  
          <namespaceTable>  
            <add prefix="custom" namespace="http://my.custom.namespace/"/>  
          </namespaceTable>  
          <filters>  
            <!--define the different message filters-->  
            <!--define an xpath message filter to look for the custom header coming from the client-->  
            <filter name="XPathFilter" filterType="XPath"   
                    filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
          </filters>  
    </routing>  
    ```  
  
     <span data-ttu-id="20eee-135">Esse **MessageFilter** procura um cabeçalho RoundingCalculator na mensagem que contém um valor de "arredondamento".</span><span class="sxs-lookup"><span data-stu-id="20eee-135">This **MessageFilter** looks for a RoundingCalculator header in the message that contains a value of "rounding".</span></span> <span data-ttu-id="20eee-136">Esse cabeçalho é definido pelo cliente para indicar que a mensagem deve ser roteada para o serviço roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="20eee-136">This header is set by the client to indicate that the message should be routed to the roundingCalc service.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20eee-137">O prefixo do namespace S12 é definido por padrão na tabela de namespace e representa o namespace `http://www.w3.org/2003/05/soap-envelope`.</span><span class="sxs-lookup"><span data-stu-id="20eee-137">The s12 namespace prefix is defined by default in the namespace table, and represents the namespace `http://www.w3.org/2003/05/soap-envelope`.</span></span>
  
2. <span data-ttu-id="20eee-138">Você também deve definir filtros que procuram mensagens recebidas nos dois pontos de extremidade virtuais.</span><span class="sxs-lookup"><span data-stu-id="20eee-138">You must also define filters that look for messages received on the two virtual endpoints.</span></span> <span data-ttu-id="20eee-139">O primeiro ponto de extremidade virtual é o ponto de extremidade "regular/Calculator".</span><span class="sxs-lookup"><span data-stu-id="20eee-139">The first virtual endpoint is the "regular/calculator" endpoint.</span></span> <span data-ttu-id="20eee-140">O cliente pode enviar solicitações para esse ponto de extremidade para indicar que a mensagem deve ser roteada para o serviço regularCalc.</span><span class="sxs-lookup"><span data-stu-id="20eee-140">The client can send requests to this endpoint to indicate that the message should be routed to the regularCalc service.</span></span> <span data-ttu-id="20eee-141">A configuração a seguir define um filtro que usa <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> o para determinar se a mensagem chegou por um ponto de extremidade com o nome especificado em FilterData.</span><span class="sxs-lookup"><span data-stu-id="20eee-141">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter> to determine if the message arrived through an endpoint with the name specified in filterData.</span></span>  
  
    ```xml  
    <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
    <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
    ```  
  
     <span data-ttu-id="20eee-142">Se uma mensagem for recebida pelo ponto de extremidade de serviço chamado "calculatorEndpoint", esse filtro será `true`avaliado como.</span><span class="sxs-lookup"><span data-stu-id="20eee-142">If a message is received by the service endpoint named "calculatorEndpoint", this filter evaluates to `true`.</span></span>  
  
3. <span data-ttu-id="20eee-143">Em seguida, defina um filtro que procura mensagens enviadas ao endereço do roundingEndpoint.</span><span class="sxs-lookup"><span data-stu-id="20eee-143">Next, define a filter that looks for messages sent to the address of the roundingEndpoint.</span></span> <span data-ttu-id="20eee-144">O cliente pode enviar solicitações para esse ponto de extremidade para indicar que a mensagem deve ser roteada para o serviço roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="20eee-144">The client can send requests to this endpoint to indicate that the message should be routed to the roundingCalc service.</span></span> <span data-ttu-id="20eee-145">A configuração a seguir define um filtro que usa <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> o para determinar se a mensagem chegou no ponto de extremidade "arredondamento/calculadora".</span><span class="sxs-lookup"><span data-stu-id="20eee-145">The following configuration defines a filter that uses the <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter> to determine if the message arrived at the "rounding/calculator" endpoint.</span></span>  
  
    ```xml  
    <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
    <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress"  
            filterData="http://localhost/routingservice/router/rounding/"/>  
    ```  
  
     <span data-ttu-id="20eee-146">Se uma mensagem for recebida em um endereço que começa com `http://localhost/routingservice/router/rounding/` , esse filtro será avaliado como **true**.</span><span class="sxs-lookup"><span data-stu-id="20eee-146">If a message is received at an address that begins with `http://localhost/routingservice/router/rounding/` then this filter evaluates to **true**.</span></span> <span data-ttu-id="20eee-147">Como o endereço base usado por essa configuração é `http://localhost/routingservice/router` e o endereço especificado para o roundingEndpoint é "arredondamento/calculadora", o endereço completo usado para se comunicar com esse `http://localhost/routingservice/router/rounding/calculator`ponto de extremidade é, que corresponde a esse filtro.</span><span class="sxs-lookup"><span data-stu-id="20eee-147">Because the base address used by this configuration is `http://localhost/routingservice/router` and the address specified for the roundingEndpoint is "rounding/calculator", the full address used to communicate with this endpoint is `http://localhost/routingservice/router/rounding/calculator`, which matches this filter.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20eee-148">O filtro PrefixEndpointAddress não avalia o nome do host ao executar uma correspondência, pois um único host pode ser referenciado usando uma variedade de nomes de host que podem ser de todas as maneiras válidas de se referir ao host do aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="20eee-148">The PrefixEndpointAddress filter does not evaluate the host name when performing a match, because a single host can be referred to by using a variety of host names that may all be valid ways of referring to the host from the client application.</span></span> <span data-ttu-id="20eee-149">Por exemplo, todas as seguintes opções podem se referir ao mesmo host:</span><span class="sxs-lookup"><span data-stu-id="20eee-149">For example, all of the following may refer to the same host:</span></span>  
    >   
    > - <span data-ttu-id="20eee-150">localhost</span><span class="sxs-lookup"><span data-stu-id="20eee-150">localhost</span></span>  
    > - <span data-ttu-id="20eee-151">127.0.0.1</span><span class="sxs-lookup"><span data-stu-id="20eee-151">127.0.0.1</span></span>  
    > - `www.contoso.com`  
    > - <span data-ttu-id="20eee-152">ContosoWeb01</span><span class="sxs-lookup"><span data-stu-id="20eee-152">ContosoWeb01</span></span>  
  
4. <span data-ttu-id="20eee-153">O filtro final deve dar suporte ao roteamento de mensagens que chegam ao ponto de extremidade geral sem o cabeçalho personalizado.</span><span class="sxs-lookup"><span data-stu-id="20eee-153">The final filter must support the routing of messages that arrive at the general endpoint without the custom header.</span></span> <span data-ttu-id="20eee-154">Para esse cenário, as mensagens devem alternar entre os serviços regularCalc e roundingCalc.</span><span class="sxs-lookup"><span data-stu-id="20eee-154">For this scenario, the messages should alternate between the regularCalc and roundingCalc services.</span></span> <span data-ttu-id="20eee-155">Para dar suporte ao roteamento "round robin" dessas mensagens, use um filtro personalizado que permita que uma instância de filtro corresponda a cada mensagem processada.</span><span class="sxs-lookup"><span data-stu-id="20eee-155">To support the "round robin" routing of these messages,  use a custom filter that allows one filter instance to match for each message processed.</span></span>  <span data-ttu-id="20eee-156">O seguinte define duas instâncias de um RoundRobinMessageFilter, que são agrupadas para indicar que elas devem ser alternadas entre si.</span><span class="sxs-lookup"><span data-stu-id="20eee-156">The following defines two instances of a RoundRobinMessageFilter, which are grouped together to indicate that they should alternate between each other.</span></span>  
  
    ```xml  
    <!-- Set up the custom message filters.  In this example,   
         we'll use the example round robin message filter,   
         which alternates between the references-->  
    <filter name="RoundRobinFilter1" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    <filter name="RoundRobinFilter2" filterType="Custom"  
                    customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly"  
                    filterData="group1"/>  
    ```  
  
     <span data-ttu-id="20eee-157">Durante o tempo de execução, esse tipo de filtro alterna entre todas as instâncias de filtro definidas deste tipo que são configuradas como o mesmo grupo em uma coleção.</span><span class="sxs-lookup"><span data-stu-id="20eee-157">During run time, this filter type alternates between all defined filter instances of this type that are configured as the same group into one collection.</span></span> <span data-ttu-id="20eee-158">Isso faz com que as mensagens processadas por esse filtro personalizado `true` sejam `RoundRobinFilter1` alternadas entre retornar para e `RoundRobinFilter2`.</span><span class="sxs-lookup"><span data-stu-id="20eee-158">This causes messages processed by this custom filter to alternate between returning `true` for `RoundRobinFilter1` and `RoundRobinFilter2`.</span></span>  
  
### <a name="define-filter-tables"></a><span data-ttu-id="20eee-159">Definir tabelas de filtro</span><span class="sxs-lookup"><span data-stu-id="20eee-159">Define Filter Tables</span></span>  
  
1. <span data-ttu-id="20eee-160">Para associar os filtros a pontos de extremidade específicos do cliente, você deve colocá-los em uma tabela de filtro.</span><span class="sxs-lookup"><span data-stu-id="20eee-160">To associate the filters with specific client endpoints, you must place them within a filter table.</span></span> <span data-ttu-id="20eee-161">Esse cenário de exemplo também usa configurações de prioridade de filtro, que é uma configuração opcional que permite que você indique a ordem na qual os filtros são processados.</span><span class="sxs-lookup"><span data-stu-id="20eee-161">This example scenario also uses filter priority settings, which is an optional setting that allows you to indicate the order in which filters are processed.</span></span> <span data-ttu-id="20eee-162">Se nenhuma prioridade de filtro for especificada, todos os filtros serão avaliados simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="20eee-162">If no filter priority is specified, all filters are evaluated simultaneously.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="20eee-163">Embora a especificação de uma prioridade de filtro permita que você controle a ordem na qual os filtros são processados, isso pode afetar negativamente o desempenho do serviço de roteamento.</span><span class="sxs-lookup"><span data-stu-id="20eee-163">While specifying a filter priority allows you to control the order in which filters are processed, it can adversely affect the performance of the Routing Service.</span></span> <span data-ttu-id="20eee-164">Quando possível, construa a lógica de filtro para que o uso de prioridades de filtro não seja necessário.</span><span class="sxs-lookup"><span data-stu-id="20eee-164">When possible, construct filter logic so that the use of filter priorities is not required.</span></span>  
  
     <span data-ttu-id="20eee-165">O seguinte define a tabela de filtro e adiciona o "XPathFilter" definido anteriormente à tabela com uma prioridade de 2.</span><span class="sxs-lookup"><span data-stu-id="20eee-165">The following defines the filter table and adds the "XPathFilter" defined earlier to the table with a priority of 2.</span></span> <span data-ttu-id="20eee-166">Essa entrada também especifica que, se `XPathFilter` o corresponder à mensagem, a mensagem será roteada para `roundingCalcEndpoint`o.</span><span class="sxs-lookup"><span data-stu-id="20eee-166">This entry also specifies that if the `XPathFilter` matches the message, the message will be routed to the `roundingCalcEndpoint`.</span></span>  
  
    ```xml  
    <routing>  
    ...      <filters>  
    ...      </filters>  
          <filterTables>  
            <table name="filterTable1">  
              <entries>  
                <!--add the filters to the message filter table-->  
                <!--first look for the custom header, and if we find it,  
                    send the message to the rounding calc endpoint-->  
                <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
              </entries>  
            </table>  
          <filterTables>  
    </routing>  
    ```  
  
     <span data-ttu-id="20eee-167">Ao especificar uma prioridade de filtro, os filtros de prioridade mais alta são avaliados primeiro.</span><span class="sxs-lookup"><span data-stu-id="20eee-167">When specifying a filter priority, the highest priority filters are evaluated first.</span></span> <span data-ttu-id="20eee-168">Se um ou mais filtros em um nível de prioridade específico corresponderem, nenhum filtro em níveis de prioridade mais baixos será avaliado.</span><span class="sxs-lookup"><span data-stu-id="20eee-168">If one or more filters at a specific priority level match, no filters at lower priority levels will be evaluated.</span></span> <span data-ttu-id="20eee-169">Para esse cenário, 2 é a prioridade mais alta especificada e esta é a única entrada de filtro nesse nível.</span><span class="sxs-lookup"><span data-stu-id="20eee-169">For this scenario, 2 is the highest priority specified and this is the only filter entry at this level.</span></span>  
  
2. <span data-ttu-id="20eee-170">As entradas de filtro foram definidas para verificar se uma mensagem é recebida em um ponto de extremidade específico inspecionando o nome do ponto de extremidade ou o prefixo do endereço.</span><span class="sxs-lookup"><span data-stu-id="20eee-170">Filter entries were defined to check to see if a message is received on a specific endpoint by inspecting the endpoint name or the address prefix.</span></span> <span data-ttu-id="20eee-171">As entradas a seguir adicionam ambas as entradas de filtro à tabela de filtro e as associamos aos pontos de extremidade de destino para os quais a mensagem será roteada.</span><span class="sxs-lookup"><span data-stu-id="20eee-171">The following entries add both of these filter entries to the filter table and associate them with the destination endpoints that the message will be routed to.</span></span> <span data-ttu-id="20eee-172">Esses filtros são definidos com uma prioridade de 1 para indicar que eles só devem ser executados se o filtro XPath anterior não coincidir com a mensagem.</span><span class="sxs-lookup"><span data-stu-id="20eee-172">These filters are set to a priority of 1 to indicate that they should only run if the previous XPath filter did not match the message.</span></span>  
  
    ```xml  
    <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
    <!--we determine this through the endpoint name, or through the address prefix-->  
    <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
    <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
    ```  
  
     <span data-ttu-id="20eee-173">Como esses filtros têm uma prioridade de filtro igual a 1, eles só serão avaliados se o filtro no nível de prioridade 2 não corresponder à mensagem.</span><span class="sxs-lookup"><span data-stu-id="20eee-173">Because these filters have a filter priority of 1, they will only be evaluated if the filter at priority level 2 does not match the message.</span></span> <span data-ttu-id="20eee-174">Além disso, como os dois filtros têm o mesmo nível de prioridade, eles serão avaliados simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="20eee-174">Also, because both filters have the same priority level they will be evaluated simultaneously.</span></span> <span data-ttu-id="20eee-175">Como ambos os filtros são mutuamente exclusivos, é possível apenas um ou o outro para corresponder a uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="20eee-175">Because both filters are mutually exclusive, it is possible for only one or the other to match a message.</span></span>  
  
3. <span data-ttu-id="20eee-176">Se uma mensagem não corresponder a nenhum dos filtros anteriores, a mensagem foi recebida por meio do ponto de extremidade de serviço genérico e não continha informações de cabeçalho que indicam onde encaminhá-lo.</span><span class="sxs-lookup"><span data-stu-id="20eee-176">If a message does not match any of the previous filters, then the message was received through the generic service endpoint and contained no header information that indicates where to route it.</span></span> <span data-ttu-id="20eee-177">Essas mensagens devem ser tratadas pelo filtro personalizado, que equilibra a carga entre os dois serviços de calculadora.</span><span class="sxs-lookup"><span data-stu-id="20eee-177">These messages are to be handled by the custom filter, which load balances them between the two calculator services.</span></span> <span data-ttu-id="20eee-178">O exemplo a seguir demonstra como adicionar as entradas de filtro à tabela de filtro; cada filtro é associado a um dos dois pontos de extremidade de destino.</span><span class="sxs-lookup"><span data-stu-id="20eee-178">The following example demonstrates how to add the filter entries to the filter table; each filter is associated with one of the two destination endpoints.</span></span>  
  
    ```xml  
    <!--if none of the other filters have matched,   
        this message showed up on the default router endpoint,   
        with no custom header-->  
    <!--round robin these requests between the two services-->  
    <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
    <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
    ```  
  
     <span data-ttu-id="20eee-179">Como essas entradas especificam uma prioridade de 0, elas só serão avaliadas se nenhum filtro de prioridade mais alta corresponder à mensagem.</span><span class="sxs-lookup"><span data-stu-id="20eee-179">Because these entries specify a priority of 0, they will only be evaluated if no filter of a higher priority matches the message.</span></span> <span data-ttu-id="20eee-180">Além disso, como ambas têm a mesma prioridade, elas são avaliadas simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="20eee-180">Also, since both are of the same priority, they are evaluated simultaneously.</span></span>  
  
     <span data-ttu-id="20eee-181">Conforme mencionado anteriormente, o filtro personalizado usado por essas definições de filtro avalia apenas uma ou outra como `true` para cada mensagem recebida.</span><span class="sxs-lookup"><span data-stu-id="20eee-181">As mentioned previously, the custom filter used by these filter definitions only evaluates one or the other as `true` for each message received.</span></span> <span data-ttu-id="20eee-182">Como apenas dois filtros são definidos usando esse filtro, com a mesma configuração de grupo especificada, o efeito é que o serviço de roteamento alterna entre o envio para o regularCalcEndpoint e o RoundingCalcEndpoint.</span><span class="sxs-lookup"><span data-stu-id="20eee-182">Because only two filters are defined using this filter, with the same specified group setting, the effect is that the Routing Service alternates between sending to the regularCalcEndpoint and the RoundingCalcEndpoint.</span></span>  
  
4. <span data-ttu-id="20eee-183">Para avaliar as mensagens em relação aos filtros, a tabela de filtros deve primeiro ser associada aos pontos de extremidade de serviço que serão usados para receber mensagens.</span><span class="sxs-lookup"><span data-stu-id="20eee-183">To evaluate messages against the filters, the filter table must first be associated with the service endpoints that will be used to receive messages.</span></span>  <span data-ttu-id="20eee-184">O exemplo a seguir demonstra como associar a tabela de roteamento com os pontos de extremidade de serviço usando o comportamento de roteamento:</span><span class="sxs-lookup"><span data-stu-id="20eee-184">The following example demonstrates how to associate the routing table with the service endpoints by using the routing behavior:</span></span>  
  
    ```xml  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    ```  
  
## <a name="example"></a><span data-ttu-id="20eee-185">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20eee-185">Example</span></span>  
 <span data-ttu-id="20eee-186">A seguir está uma lista completa do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="20eee-186">The following is a complete listing of the configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright (c) Microsoft Corporation. All rights reserved -->  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service behaviorConfiguration="routingConfiguration"  
               name="System.ServiceModel.Routing.RoutingService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost/routingservice/router" />  
          </baseAddresses>  
        </host>  
        <!--Set up the inbound endpoints for the Routing Service-->  
        <!--first create the general router endpoint-->  
        <endpoint address="general"  
                  binding="wsHttpBinding"  
                  name="routerEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--create a virtual endpoint for the regular calculator service-->  
        <endpoint address="regular/calculator"  
                  binding="wsHttpBinding"  
                  name="calculatorEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
        <!--now create a virtual endpoint for the rounding calculator-->  
        <endpoint address="rounding/calculator"  
                  binding="wsHttpBinding"  
                  name="roundingEndpoint"  
                  contract="System.ServiceModel.Routing.IRequestReplyRouter" />  
  
      </service>  
    </services>  
    <behaviors>  
      <!--default routing service behavior definition-->  
      <serviceBehaviors>  
        <behavior name="routingConfiguration">  
          <routing filterTableName="filterTable1" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
    <client>  
<!--set up the destination endpoints-->  
      <endpoint name="regularCalcEndpoint"  
                address="net.tcp://localhost:9090/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
  
      <endpoint name="roundingCalcEndpoint"  
                address="net.tcp://localhost:8080/servicemodelsamples/service/"  
                binding="netTcpBinding"  
                contract="*" />  
    </client>  
    <routing>  
      <!-- use the namespace table element to define a prefix for our custom namespace-->  
      <namespaceTable>  
        <add prefix="custom" namespace="http://my.custom.namespace/"/>  
      </namespaceTable>  
      <filters>  
        <!--define the different message filters-->  
        <!--define an xpath message filter to look for the custom header coming from the client-->  
        <filter name="XPathFilter" filterType="XPath" filterData="/s12:Envelope/s12:Header/custom:RoundingCalculator = 'rounding'"/>  
  
        <!--define an endpoint name filter looking for messages that show up on the virtual regular calculator endpoint-->  
        <filter name="EndpointNameFilter" filterType="EndpointName" filterData="calculatorEndpoint"/>  
  
        <!--define a filter looking for messages that show up with the address prefix.  The corresponds to the rounding calc virtual endpoint-->  
        <filter name="PrefixAddressFilter" filterType="PrefixEndpointAddress" filterData="http://localhost/routingservice/router/rounding/"/>  
  
        <!--Set up the custom message filters.  In this example, we'll use the example round robin message filter, which alternates between the references-->  
        <filter name="RoundRobinFilter1" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
        <filter name="RoundRobinFilter2" filterType="Custom" customType="CustomFilterAssembly.RoundRobinMessageFilter, CustomFilterAssembly" filterData="group1"/>  
      </filters>  
      <filterTables>  
        <table name="filterTable1">  
          <entries>  
            <!--add the filters to the message filter table-->  
            <!--first look for the custom header, and if we find it, send the message to the rounding calc endpoint-->  
            <add filterName="XPathFilter" endpointName="roundingCalcEndpoint" priority="2"/>  
  
            <!--if the header wasn't there, send the message based on which virtual endpoint it arrived at-->  
            <!--we determine this through the endpoint name, or through the address prefix-->  
            <add filterName="EndpointNameFilter" endpointName="regularCalcEndpoint" priority="1"/>  
            <add filterName="PrefixAddressFilter" endpointName="roundingCalcEndpoint" priority="1"/>  
  
            <!--if none of the other filters have matched, this message showed up on the default router endpoint, with no custom header-->  
            <!--round robin these requests between the two services-->  
            <add filterName="RoundRobinFilter1" endpointName="regularCalcEndpoint" priority="0"/>  
            <add filterName="RoundRobinFilter2" endpointName="roundingCalcEndpoint" priority="0"/>  
          </entries>  
        </table>  
      </filterTables>  
    </routing>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="20eee-187">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20eee-187">See also</span></span>

- [<span data-ttu-id="20eee-188">Serviços de roteamento</span><span class="sxs-lookup"><span data-stu-id="20eee-188">Routing Services</span></span>](../../../../docs/framework/wcf/samples/routing-services.md)
