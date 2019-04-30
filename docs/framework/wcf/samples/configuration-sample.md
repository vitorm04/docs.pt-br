---
title: Exemplo de configuração
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 48f66c4110d048f714dae0943f97f3f4aa7cd419
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62002226"
---
# <a name="configuration-sample"></a><span data-ttu-id="9d763-102">Exemplo de configuração</span><span class="sxs-lookup"><span data-stu-id="9d763-102">Configuration Sample</span></span>
<span data-ttu-id="9d763-103">Este exemplo demonstra o uso de um arquivo de configuração para tornar um serviço detectável.</span><span class="sxs-lookup"><span data-stu-id="9d763-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d763-104">Este exemplo implementa descoberta na configuração.</span><span class="sxs-lookup"><span data-stu-id="9d763-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="9d763-105">Para obter um exemplo que implementa a descoberta no código, consulte [básica](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="9d763-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d763-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="9d763-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9d763-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="9d763-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9d763-108">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="9d763-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9d763-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="9d763-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="9d763-110">Configuração de Serviço</span><span class="sxs-lookup"><span data-stu-id="9d763-110">Service Configuration</span></span>  
 <span data-ttu-id="9d763-111">O arquivo de configuração neste exemplo demonstra dois recursos:</span><span class="sxs-lookup"><span data-stu-id="9d763-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="9d763-112">Tornando o serviço podem ser descobertos ao longo de um padrão <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span><span class="sxs-lookup"><span data-stu-id="9d763-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="9d763-113">Ajustando informações relacionadas a descoberta para o serviço ponto de extremidade do aplicativo e ajustar algumas das configurações relacionadas à descoberta no ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="9d763-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="9d763-114">Para habilitar a descoberta, algumas alterações devem ser feitas no arquivo de configuração do aplicativo para o serviço:</span><span class="sxs-lookup"><span data-stu-id="9d763-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="9d763-115">Um ponto de extremidade de descoberta deve ser adicionado para o `<service>` elemento.</span><span class="sxs-lookup"><span data-stu-id="9d763-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="9d763-116">Este é um padrão <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9d763-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="9d763-117">Esse é um ponto de extremidade do sistema que o tempo de execução associa com o serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="9d763-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="9d763-118">O serviço de descoberta escuta as mensagens nesse ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="9d763-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="9d763-119">Um `<serviceDiscovery>` comportamento é adicionado para o `<serviceBehaviors>` seção.</span><span class="sxs-lookup"><span data-stu-id="9d763-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="9d763-120">Isso permite que o serviço seja descoberto em tempo de execução e usa o ponto de extremidade de descoberta mencionado anteriormente para ouvir de descoberta `Probe` e `Resolve` mensagens.</span><span class="sxs-lookup"><span data-stu-id="9d763-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="9d763-121">Com essas duas adições, o serviço é detectável no ponto de extremidade de descoberta especificado.</span><span class="sxs-lookup"><span data-stu-id="9d763-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="9d763-122">O trecho de configuração a seguir mostra um serviço com um ponto de extremidade do aplicativo e um ponto de extremidade de descoberta definido:</span><span class="sxs-lookup"><span data-stu-id="9d763-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 <span data-ttu-id="9d763-123">Para tirar proveito dos anúncios, você precisará adicionar um ponto de extremidade de comunicado.</span><span class="sxs-lookup"><span data-stu-id="9d763-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="9d763-124">Para fazer isso, modifique o arquivo de configuração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d763-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="9d763-125">Adicionar um ponto de extremidade de comunicado para o comportamento de serviço de descoberta cria um cliente de anúncio padrão para o serviço.</span><span class="sxs-lookup"><span data-stu-id="9d763-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="9d763-126">Isso garante que o serviço enviará um comunicado online e offline quando o serviço é aberto e fechado, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="9d763-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="9d763-127">Esse arquivo de configuração vai além apenas essas etapas simples, modificando comportamentos adicionais.</span><span class="sxs-lookup"><span data-stu-id="9d763-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="9d763-128">É possível controlar informações relacionadas à descoberta por meio de pontos de extremidade específicos.</span><span class="sxs-lookup"><span data-stu-id="9d763-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="9d763-129">Ou seja, um usuário pode controlar se um ponto de extremidade pode ser descoberto e o usuário também pode marcar o ponto de extremidade com <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> e metadados XML personalizados.</span><span class="sxs-lookup"><span data-stu-id="9d763-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="9d763-130">Para fazer isso, o usuário deve adicionar um `behaviorConfiguration` propriedade para o ponto de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d763-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="9d763-131">Nesse caso, a propriedade a seguir é adicionada para o ponto de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d763-131">In this case, the following property is added to the application endpoint.</span></span>  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 <span data-ttu-id="9d763-132">Agora, por meio do elemento de configuração de comportamento, você pode controlar atributos relacionados à descoberta.</span><span class="sxs-lookup"><span data-stu-id="9d763-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="9d763-133">Nesse caso, os dois escopos são adicionados para o ponto de extremidade do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9d763-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 <span data-ttu-id="9d763-134">Para obter mais informações sobre escopos, consulte [FindCriteria e descoberta localizar](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="9d763-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="9d763-135">Você também pode controlar os detalhes específicos do ponto de extremidade de descoberta.</span><span class="sxs-lookup"><span data-stu-id="9d763-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="9d763-136">Isso é feito por meio de <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span><span class="sxs-lookup"><span data-stu-id="9d763-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="9d763-137">Neste exemplo, a versão do protocolo usado é modificada, bem como adicionar um `maxResponseDelay` atributo conforme mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="9d763-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="9d763-138">Este é o arquivo de configuração completo usado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="9d763-138">The following is the complete configuration file used in this example:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a><span data-ttu-id="9d763-139">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="9d763-139">Client Configuration</span></span>  
 <span data-ttu-id="9d763-140">No arquivo de configuração do aplicativo para o cliente, uma `standardEndpoint` do tipo `dynamicEndpoint` é usado para utilizar descoberta, conforme mostrado no seguinte trecho de config.</span><span class="sxs-lookup"><span data-stu-id="9d763-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 <span data-ttu-id="9d763-141">Quando um cliente estiver usando um `dynamicEndpoint`, o tempo de execução executa a descoberta automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9d763-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="9d763-142">Várias configurações são usadas durante a descoberta, como aquelas definidas no `discoveryClientSettings` seção, que especifica o tipo de ponto de extremidade de descoberta para usar:</span><span class="sxs-lookup"><span data-stu-id="9d763-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="9d763-143">Os critérios de localização usados para pesquisar serviços:</span><span class="sxs-lookup"><span data-stu-id="9d763-143">The find criteria used to search for services:</span></span>  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 <span data-ttu-id="9d763-144">Este exemplo amplia esse recurso e modifica o <xref:System.ServiceModel.Discovery.FindCriteria> usado pelo cliente, bem como algumas propriedades do padrão `updDiscoveryEndpoint` usada para descoberta.</span><span class="sxs-lookup"><span data-stu-id="9d763-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="9d763-145">O <xref:System.ServiceModel.Discovery.FindCriteria> são modificadas para usar um escopo e uma determinada `scopeMatchBy` algoritmo, bem como critérios de encerramento personalizada.</span><span class="sxs-lookup"><span data-stu-id="9d763-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="9d763-146">Além disso, o exemplo também mostra como um cliente pode enviar os elementos XML usando `Probe` mensagens.</span><span class="sxs-lookup"><span data-stu-id="9d763-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="9d763-147">Por fim, algumas alterações são feitas para o <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, como a versão do protocolo usado e as configurações de UDP específicas, conforme mostrado no seguinte arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="9d763-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 <span data-ttu-id="9d763-148">A seguir está a configuração de cliente completa usada no exemplo.</span><span class="sxs-lookup"><span data-stu-id="9d763-148">The following is the complete client configuration used in the sample.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="9d763-149">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="9d763-149">To use this sample</span></span>  
  
1. <span data-ttu-id="9d763-150">Este exemplo usa pontos de extremidade HTTP e executar isso URL de exemplo, apropriado ACLs deve ser adicionado ver [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) para obter detalhes.</span><span class="sxs-lookup"><span data-stu-id="9d763-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added see [Configuring HTTP and HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) for details.</span></span> <span data-ttu-id="9d763-151">Executando o seguinte comando para um nível de privilégio elevado deve adicionar as ACLs apropriado.</span><span class="sxs-lookup"><span data-stu-id="9d763-151">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="9d763-152">Você talvez queira substituir seu domínio e nome de usuário para os argumentos a seguir, se o comando não funcionar como está.</span><span class="sxs-lookup"><span data-stu-id="9d763-152">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="9d763-153">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="9d763-153">Build the solution.</span></span>  
  
3. <span data-ttu-id="9d763-154">Execute o executável do serviço de diretório de compilação.</span><span class="sxs-lookup"><span data-stu-id="9d763-154">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="9d763-155">Execute o executável do cliente.</span><span class="sxs-lookup"><span data-stu-id="9d763-155">Run the client executable.</span></span> <span data-ttu-id="9d763-156">Observe que o cliente é capaz de localizar o serviço.</span><span class="sxs-lookup"><span data-stu-id="9d763-156">Note that the client is able to locate the service.</span></span>  
