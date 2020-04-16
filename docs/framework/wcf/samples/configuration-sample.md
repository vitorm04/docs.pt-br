---
title: Exemplo de configuração
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: 52747e6d964022d5028b0edb91dc8bc0ac0e82bc
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463964"
---
# <a name="configuration-sample"></a><span data-ttu-id="2c36f-102">Exemplo de configuração</span><span class="sxs-lookup"><span data-stu-id="2c36f-102">Configuration Sample</span></span>
<span data-ttu-id="2c36f-103">Esta amostra demonstra o uso de um arquivo de configuração para tornar um serviço desvendado.</span><span class="sxs-lookup"><span data-stu-id="2c36f-103">This sample demonstrates the use of a configuration file to make a service discoverable.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c36f-104">Esta amostra implementa a descoberta na configuração.</span><span class="sxs-lookup"><span data-stu-id="2c36f-104">This sample implements discovery in configuration.</span></span> <span data-ttu-id="2c36f-105">Para obter uma amostra que implemente a descoberta em código, consulte [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span><span class="sxs-lookup"><span data-stu-id="2c36f-105">For a sample that implements discovery in code, see [Basic](../../../../docs/framework/wcf/samples/basic-sample.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="2c36f-106">Os exemplos podem mais ser instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="2c36f-106">The samples may already be installed on your computer.</span></span> <span data-ttu-id="2c36f-107">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="2c36f-107">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="2c36f-108">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="2c36f-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="2c36f-109">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="2c36f-109">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a><span data-ttu-id="2c36f-110">Configuração de Serviço</span><span class="sxs-lookup"><span data-stu-id="2c36f-110">Service Configuration</span></span>  
 <span data-ttu-id="2c36f-111">O arquivo de configuração nesta amostra demonstra dois recursos:</span><span class="sxs-lookup"><span data-stu-id="2c36f-111">The configuration file in this sample demonstrates two features:</span></span>  
  
- <span data-ttu-id="2c36f-112">Tornando o serviço descubro acima de um padrão. <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint></span><span class="sxs-lookup"><span data-stu-id="2c36f-112">Making the service discoverable over a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>.</span></span>  
  
- <span data-ttu-id="2c36f-113">Ajustando as informações relacionadas à descoberta para o ponto final do aplicativo do serviço e ajustando algumas das configurações relacionadas à descoberta no ponto final padrão.</span><span class="sxs-lookup"><span data-stu-id="2c36f-113">Adjusting discovery-related information for the service’s application endpoint and adjusting some of the discovery-related settings on the standard endpoint.</span></span>  
  
 <span data-ttu-id="2c36f-114">Para habilitar a detecção, algumas alterações devem ser feitas no arquivo de configuração do aplicativo para o serviço:</span><span class="sxs-lookup"><span data-stu-id="2c36f-114">To enable discovery, a few changes must be made in the application configuration file for the service:</span></span>  
  
- <span data-ttu-id="2c36f-115">Um ponto final de descoberta `<service>` deve ser adicionado ao elemento.</span><span class="sxs-lookup"><span data-stu-id="2c36f-115">A discovery endpoint must be added to the `<service>` element.</span></span> <span data-ttu-id="2c36f-116">Este é <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> um ponto final padrão.</span><span class="sxs-lookup"><span data-stu-id="2c36f-116">This is a standard <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> endpoint.</span></span> <span data-ttu-id="2c36f-117">Este é um ponto final do sistema que o tempo de execução associa ao serviço de descoberta.</span><span class="sxs-lookup"><span data-stu-id="2c36f-117">This is a system endpoint that the runtime associates with the discovery service.</span></span> <span data-ttu-id="2c36f-118">O serviço de descoberta ouve mensagens neste ponto final.</span><span class="sxs-lookup"><span data-stu-id="2c36f-118">The discovery service listens for messages on this endpoint.</span></span>  
  
- <span data-ttu-id="2c36f-119">Um `<serviceDiscovery>` comportamento é `<serviceBehaviors>` adicionado à seção.</span><span class="sxs-lookup"><span data-stu-id="2c36f-119">A `<serviceDiscovery>` behavior is added to the `<serviceBehaviors>` section.</span></span> <span data-ttu-id="2c36f-120">Isso permite que o serviço seja descoberto em tempo de execução e `Probe` `Resolve` usa o ponto final de descoberta mencionado anteriormente para ouvir a descoberta e as mensagens.</span><span class="sxs-lookup"><span data-stu-id="2c36f-120">This enables the service to be discovered at runtime and uses the discovery endpoint mentioned previously to listen for discovery `Probe` and `Resolve` messages.</span></span> <span data-ttu-id="2c36f-121">Com essas duas adições, o serviço é descoberto no ponto final de descoberta especificado.</span><span class="sxs-lookup"><span data-stu-id="2c36f-121">With these two additions, the service is discoverable at the discovery endpoint specified.</span></span>  
  
 <span data-ttu-id="2c36f-122">O seguinte trecho de configuração mostra um serviço com um ponto final de aplicativo e um ponto final de descoberta definido:</span><span class="sxs-lookup"><span data-stu-id="2c36f-122">The following config snippet shows a service with an application endpoint and a discovery endpoint defined:</span></span>  
  
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
  
 <span data-ttu-id="2c36f-123">Para aproveitar os anúncios, você precisará adicionar um ponto final de anúncio.</span><span class="sxs-lookup"><span data-stu-id="2c36f-123">To take advantage of announcements, you will need to add an announcement endpoint.</span></span> <span data-ttu-id="2c36f-124">Para fazer isso, modifique o arquivo de configuração conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c36f-124">To do this, modify the configuration file as shown in the following code.</span></span>  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 <span data-ttu-id="2c36f-125">Adicionar um ponto final de anúncio ao comportamento do serviço de descoberta cria um cliente de anúncio padrão para o serviço.</span><span class="sxs-lookup"><span data-stu-id="2c36f-125">Adding an announcement endpoint to the discovery service behavior creates a default announcement client for the service.</span></span> <span data-ttu-id="2c36f-126">Isso garante que o serviço enviará um comunicado online e offline quando o serviço for aberto e fechado, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="2c36f-126">This guarantees that the service will send an online and offline announcement when the service is opened and closed respectively.</span></span>  
  
 <span data-ttu-id="2c36f-127">Este arquivo de configuração vai além apenas dessas etapas simples, modificando comportamentos adicionais.</span><span class="sxs-lookup"><span data-stu-id="2c36f-127">This configuration file goes beyond just those simple steps by modifying additional behaviors.</span></span> <span data-ttu-id="2c36f-128">É possível controlar informações relacionadas à descoberta usando pontos finais específicos.</span><span class="sxs-lookup"><span data-stu-id="2c36f-128">It is possible to control discovery-related information by using specific endpoints.</span></span> <span data-ttu-id="2c36f-129">Ou seja, um usuário pode controlar se um ponto final pode ser <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> descoberto e o usuário também pode marcar esse ponto final com metadados XML personalizados.</span><span class="sxs-lookup"><span data-stu-id="2c36f-129">That is, a user can control whether an endpoint can be discovered and the user can also mark that endpoint with <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> and custom XML metadata.</span></span> <span data-ttu-id="2c36f-130">Para fazer isso, o `behaviorConfiguration` usuário deve adicionar uma propriedade ao ponto final do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c36f-130">To do this, the user must add a `behaviorConfiguration` property to the application endpoint.</span></span> <span data-ttu-id="2c36f-131">Neste caso, a seguinte propriedade é adicionada ao ponto final do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c36f-131">In this case, the following property is added to the application endpoint.</span></span>  
  
`behaviorConfiguration="endpointBehaviorConfiguration"`  
  
 <span data-ttu-id="2c36f-132">Agora, através do elemento de configuração de comportamento, você pode controlar atributos relacionados à descoberta.</span><span class="sxs-lookup"><span data-stu-id="2c36f-132">Now, through the behavior configuration element, you can control discovery-related attributes.</span></span> <span data-ttu-id="2c36f-133">Neste caso, dois escopos são adicionados ao ponto final do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2c36f-133">In this case, two scopes are added to the application endpoint.</span></span>  
  
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
  
 <span data-ttu-id="2c36f-134">Para obter mais informações sobre escopos, consulte [Discovery Find e FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span><span class="sxs-lookup"><span data-stu-id="2c36f-134">For more information about scopes, see [Discovery Find and FindCriteria](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md).</span></span>  
  
 <span data-ttu-id="2c36f-135">Você também pode controlar detalhes específicos do ponto final da descoberta.</span><span class="sxs-lookup"><span data-stu-id="2c36f-135">You can also control specific details of the discovery endpoint.</span></span> <span data-ttu-id="2c36f-136">Isso é feito <xref:System.ServiceModel.Configuration.StandardEndpointsSection>através do .</span><span class="sxs-lookup"><span data-stu-id="2c36f-136">This is done through the <xref:System.ServiceModel.Configuration.StandardEndpointsSection>.</span></span> <span data-ttu-id="2c36f-137">Nesta amostra, a versão do protocolo usado é `maxResponseDelay` modificada, bem como a adição de um atributo como mostrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c36f-137">In this sample, the version of the protocol used is modified as well as adding a `maxResponseDelay` attribute as shown in the following code example.</span></span>  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 <span data-ttu-id="2c36f-138">A seguir está o arquivo de configuração completa usado neste exemplo:</span><span class="sxs-lookup"><span data-stu-id="2c36f-138">The following is the complete configuration file used in this example:</span></span>  
  
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
  
## <a name="client-configuration"></a><span data-ttu-id="2c36f-139">Configuração do cliente</span><span class="sxs-lookup"><span data-stu-id="2c36f-139">Client Configuration</span></span>  
 <span data-ttu-id="2c36f-140">No arquivo de configuração do `standardEndpoint` aplicativo `dynamicEndpoint` para o cliente, um tipo é usado para utilizar a descoberta como mostrado no trecho de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c36f-140">In the application configuration file for the client, a `standardEndpoint` of type `dynamicEndpoint` is used to utilize discovery as shown in the following config snippet.</span></span>  
  
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
  
 <span data-ttu-id="2c36f-141">Quando um cliente `dynamicEndpoint`está usando um , o tempo de execução executa a descoberta automaticamente.</span><span class="sxs-lookup"><span data-stu-id="2c36f-141">When a client is using a `dynamicEndpoint`, the runtime performs discovery automatically.</span></span> <span data-ttu-id="2c36f-142">Várias configurações são usadas durante a `discoveryClientSettings` descoberta, como as definidas na seção, que especifica o tipo de ponto final de descoberta a ser usado:</span><span class="sxs-lookup"><span data-stu-id="2c36f-142">Various settings are used during discovery, such as those defined in the  `discoveryClientSettings` section, which specifies the type of discovery endpoint to use:</span></span>  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 <span data-ttu-id="2c36f-143">Os critérios de busca utilizados para a busca de serviços:</span><span class="sxs-lookup"><span data-stu-id="2c36f-143">The find criteria used to search for services:</span></span>  
  
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
  
 <span data-ttu-id="2c36f-144">Esta amostra estende esse recurso <xref:System.ServiceModel.Discovery.FindCriteria> e modifica o usado pelo cliente, `updDiscoveryEndpoint` bem como algumas propriedades do padrão usado para descoberta.</span><span class="sxs-lookup"><span data-stu-id="2c36f-144">This sample extends this feature and modifies the <xref:System.ServiceModel.Discovery.FindCriteria> used by the client, as well as some properties of the standard `updDiscoveryEndpoint` used for discovery.</span></span> <span data-ttu-id="2c36f-145">Os <xref:System.ServiceModel.Discovery.FindCriteria> são modificados para usar `scopeMatchBy` um escopo e um algoritmo específico, bem como critérios de terminação personalizados.</span><span class="sxs-lookup"><span data-stu-id="2c36f-145">The <xref:System.ServiceModel.Discovery.FindCriteria> are modified to use a scope and a specific `scopeMatchBy` algorithm, as well as custom termination criteria.</span></span> <span data-ttu-id="2c36f-146">Além disso, a amostra também mostra como um `Probe` cliente pode enviar elementos XML usando mensagens.</span><span class="sxs-lookup"><span data-stu-id="2c36f-146">Furthermore, the sample also shows how a client can send XML elements using `Probe` messages.</span></span> <span data-ttu-id="2c36f-147">Por fim, algumas alterações <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>são feitas no , como a versão do protocolo usado e configurações específicas de UDP, como mostrado no arquivo de configuração a seguir.</span><span class="sxs-lookup"><span data-stu-id="2c36f-147">Lastly, some changes are made to the <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint>, such as the version of the protocol used and UDP-specific settings as shown in the following configuration file.</span></span>  
  
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
  
 <span data-ttu-id="2c36f-148">A seguir está a configuração completa do cliente usada na amostra.</span><span class="sxs-lookup"><span data-stu-id="2c36f-148">The following is the complete client configuration used in the sample.</span></span>  
  
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
</configuration>
```  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="2c36f-149">Para usar este exemplo</span><span class="sxs-lookup"><span data-stu-id="2c36f-149">To use this sample</span></span>  
  
1. <span data-ttu-id="2c36f-150">Esta amostra usa pontos finais HTTP e, para executar esta amostra, devem ser adicionadas ACLs url adequadas.</span><span class="sxs-lookup"><span data-stu-id="2c36f-150">This sample uses HTTP endpoints and to run this sample, proper URL ACLs must be added.</span></span> <span data-ttu-id="2c36f-151">Para obter mais informações, consulte [Configuração HTTP e HTTPS](../feature-details/configuring-http-and-https.md).</span><span class="sxs-lookup"><span data-stu-id="2c36f-151">For more information, see [Configuring HTTP and HTTPS](../feature-details/configuring-http-and-https.md).</span></span> <span data-ttu-id="2c36f-152">A execução do seguinte comando em um privilégio elevado deve adicionar as ACLs apropriadas.</span><span class="sxs-lookup"><span data-stu-id="2c36f-152">Executing the following command at an elevated privilege should add the appropriate ACLs.</span></span> <span data-ttu-id="2c36f-153">Você pode querer substituir seu Domínio e Nome de Usuário pelos seguintes argumentos se o comando não funcionar como está.</span><span class="sxs-lookup"><span data-stu-id="2c36f-153">You may want to substitute your Domain and Username for the following arguments if the command does not work as is.</span></span> `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2. <span data-ttu-id="2c36f-154">Compile a solução.</span><span class="sxs-lookup"><span data-stu-id="2c36f-154">Build the solution.</span></span>  
  
3. <span data-ttu-id="2c36f-155">Execute o executável de serviço a partir do diretório de compilação.</span><span class="sxs-lookup"><span data-stu-id="2c36f-155">Run the service executable from the build directory.</span></span>  
  
4. <span data-ttu-id="2c36f-156">Execute o cliente executável.</span><span class="sxs-lookup"><span data-stu-id="2c36f-156">Run the client executable.</span></span> <span data-ttu-id="2c36f-157">Observe que o cliente é capaz de localizar o serviço.</span><span class="sxs-lookup"><span data-stu-id="2c36f-157">Note that the client is able to locate the service.</span></span>  
