---
title: Configuração simplificada
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 7df686188099aea45cac81ea94a49b98e5c65f89
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48034617"
---
# <a name="simplified-configuration"></a><span data-ttu-id="0604e-102">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="0604e-102">Simplified Configuration</span></span>
<span data-ttu-id="0604e-103">Configurar serviços Windows Communication Foundation (WCF) pode ser uma tarefa complexa.</span><span class="sxs-lookup"><span data-stu-id="0604e-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="0604e-104">Há muitas opções diferentes e nem sempre é fácil determinar quais configurações são necessárias.</span><span class="sxs-lookup"><span data-stu-id="0604e-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="0604e-105">Enquanto os arquivos de configuração de aumentam a flexibilidade dos serviços WCF, eles também são a fonte para muitos difíceis de encontrar problemas.</span><span class="sxs-lookup"><span data-stu-id="0604e-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="0604e-106">resolve esses problemas e fornece uma maneira de reduzir o tamanho e a complexidade da configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="0604e-106"> addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="0604e-107">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="0604e-107">Simplified Configuration</span></span>  
 <span data-ttu-id="0604e-108">Em arquivos de configuração de serviço do WCF, o <`system.serviceModel`> seção contém um <`service`> elemento para cada serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="0604e-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="0604e-109">O <`service`> elemento contém uma coleção de <`endpoint`> elementos que especificam os pontos de extremidade expostos para cada serviço e, opcionalmente, um conjunto de comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="0604e-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="0604e-110">O <`endpoint`> elementos especificam o endereço, associação, e o contrato exposto pelo ponto de extremidade e, opcionalmente, configuração de associação e os comportamentos de ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0604e-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="0604e-111">O <`system.serviceModel`> seção também contém um <`behaviors`> elemento que permite que você especifique comportamentos de serviço ou ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="0604e-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="0604e-112">A exemplo a seguir mostra o <`system.serviceModel`> seção de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0604e-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true">  
        <serviceDebug includeExceptionDetailInFaults="false">  
      </behavior>  
    </serviceBehaviors>  
  </behaviors>  
  <bindings>  
   <basicHttpBinding>  
      <binding name=MyBindingConfig"  
               maxBufferSize="100"  
               maxReceiveBufferSize="100" />  
   </basicHttpBinding>  
   </bindings>   <services>  
    <service behaviorConfiguration="MyServiceBehavior"  
             name="MyService">  
      <endpoint address=""  
                binding="basicHttpBinding"  
                contract="ICalculator"  
                bindingConfiguration="MyBindingConfig" />  
      <endpoint address="mex"  
                binding="mexHttpBinding"  
                contract="IMetadataExchange"/>  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="0604e-113">torna a configuração de um serviço WCF mais fácil, removendo o requisito para o <`service`> elemento.</span><span class="sxs-lookup"><span data-stu-id="0604e-113"> makes configuring a WCF service easier by removing the requirement for the <`service\`> element.</span></span> <span data-ttu-id="0604e-114">Se você não adicionar um <`service`> seção ou adicionar pontos de extremidade em um <`service`> seção e seu serviço não definir programaticamente qualquer ponto de extremidade e, em seguida, um conjunto de pontos de extremidade padrão são automaticamente adicionados ao seu serviço, um para cada endereço base do serviço e para cada contrato implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="0604e-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="0604e-115">Em cada um desses pontos de extremidade, o endereço do ponto de extremidade corresponde ao endereço base, a associação é determinada pelo esquema de endereço base e o contrato é aquele implementado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="0604e-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="0604e-116">Se você não precisar especificar quaisquer pontos de extremidade ou comportamentos de serviço ou fazer quaisquer alterações de configuração de associação, você não precisará especificar um arquivo de configuração de serviço em todos os.</span><span class="sxs-lookup"><span data-stu-id="0604e-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="0604e-117">Se um serviço implementa dois contratos e o host de transportes HTTP e TCP permite que o host serviço cria quatro pontos de extremidade padrão, um para cada contrato usando cada transporte.</span><span class="sxs-lookup"><span data-stu-id="0604e-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="0604e-118">Para criar pontos de extremidade padrão que o host de serviço deve saber quais associações para usar.</span><span class="sxs-lookup"><span data-stu-id="0604e-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="0604e-119">Essas configurações são especificadas em um <`protocolMappings`> seção dentro de <`system.serviceModel`> seção.</span><span class="sxs-lookup"><span data-stu-id="0604e-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="0604e-120">O <`protocolMappings`> seção contém uma lista de esquemas de protocolo de transporte mapeados para tipos de associação.</span><span class="sxs-lookup"><span data-stu-id="0604e-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="0604e-121">O host de serviço usa os endereços base passados para ele para determinar a associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="0604e-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="0604e-122">O exemplo a seguir usa o <`protocolMappings`> elemento.</span><span class="sxs-lookup"><span data-stu-id="0604e-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="0604e-123">Alterando os elementos de configuração padrão, como associações ou comportamentos, pode afetar os serviços definidos nos níveis inferiores da hierarquia de configuração, já que pode estar usando essas associações padrão e comportamentos.</span><span class="sxs-lookup"><span data-stu-id="0604e-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="0604e-124">Assim, a pessoa que altera o padrão de associações e comportamentos de precisa estar ciente de que essas alterações podem afetar outros serviços na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="0604e-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0604e-125">Serviços hospedados em serviços de informações da Internet (IIS) ou o serviço de ativação de processos do Windows (WAS) usam o diretório virtual como seu endereço de base.</span><span class="sxs-lookup"><span data-stu-id="0604e-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="0604e-126">No exemplo anterior, um ponto de extremidade com um endereço base que começa com o esquema "http" usa o <xref:System.ServiceModel.BasicHttpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0604e-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="0604e-127">Um ponto de extremidade com um endereço base que começa com o esquema de "NET. TCP" usa o <xref:System.ServiceModel.NetTcpBinding>.</span><span class="sxs-lookup"><span data-stu-id="0604e-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="0604e-128">Você pode substituir as configurações em um arquivo App. config ou Web. config local.</span><span class="sxs-lookup"><span data-stu-id="0604e-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="0604e-129">Cada elemento dentro de <`protocolMappings`> seção deve especificar um esquema e uma associação.</span><span class="sxs-lookup"><span data-stu-id="0604e-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="0604e-130">Opcionalmente, ele pode especificar um `bindingConfiguration` atributo que especifica uma configuração de associação dentro de <`bindings`> seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="0604e-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="0604e-131">Se nenhum `bindingConfiguration` for especificado, a configuração de associação anônima do tipo de ligação apropriado é usada.</span><span class="sxs-lookup"><span data-stu-id="0604e-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="0604e-132">Comportamentos de serviço são configurados para os pontos de extremidade padrão com o uso anônimo <`behavior`> seções dentro de <`serviceBehaviors`> seções.</span><span class="sxs-lookup"><span data-stu-id="0604e-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="0604e-133">Qualquer um sem nome <`behavior`> elementos dentro de <`serviceBehaviors`> são usados para configurar comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="0604e-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="0604e-134">Por exemplo, o arquivo de configuração a seguir permite que a publicação de metadados de serviço para todos os serviços dentro do host.</span><span class="sxs-lookup"><span data-stu-id="0604e-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
```xml  
<system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>    <!-- No <service> tag is necessary. Default endpoints are added to the service -->  
    <!-- The service behavior with name="" is picked up by the service -->  
 </system.serviceModel>  
```  
  
 <span data-ttu-id="0604e-135">Comportamentos de ponto de extremidade são configurados com o uso anônimo <`behavior`> seções dentro de <`serviceBehaviors`> seções.</span><span class="sxs-lookup"><span data-stu-id="0604e-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="0604e-136">O exemplo a seguir é um arquivo de configuração equivalente no início deste tópico que usa o modelo de configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="0604e-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
```xml  
<system.serviceModel>
    <behaviors>
      <serviceBehaviors>
        <behavior>
          <serviceMetadata httpGetEnabled="true" />
          <serviceDebug includeExceptionDetailInFaults="false" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
    <bindings>
       <basicHttpBinding>
          <binding maxBufferSize="100"
                   maxReceiveBufferSize="100" />
       </basicHttpBinding>
    </bindings>
    <!-- No <service> tag is necessary. Default endpoints will be added to the service -->
    <!-- The service behavior with name="" will be picked up by the service -->
    <protocolMapping>
      <add scheme="http" binding="basicHttpBinding" />
  </protocolMapping>
  </system.serviceModel>
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="0604e-137">Esse recurso se relaciona apenas a configuração de serviço do WCF, não a configuração de cliente.</span><span class="sxs-lookup"><span data-stu-id="0604e-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="0604e-138">A maioria das vezes, a configuração de cliente do WCF será gerada por uma ferramenta como svcutil.exe ou adicionar uma referência de serviço do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0604e-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="0604e-139">Se você estiver configurando um cliente WCF manualmente, será necessário adicionar um \<cliente > elemento para a configuração e especificar qualquer ponto de extremidade que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="0604e-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0604e-140">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0604e-140">See Also</span></span>  
 [<span data-ttu-id="0604e-141">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="0604e-141">Configuring Services Using Configuration Files</span></span>](../../../docs/framework/wcf/configuring-services-using-configuration-files.md)  
 [<span data-ttu-id="0604e-142">Configurando associações para serviços</span><span class="sxs-lookup"><span data-stu-id="0604e-142">Configuring Bindings for Services</span></span>](../../../docs/framework/wcf/configuring-bindings-for-wcf-services.md)  
 [<span data-ttu-id="0604e-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="0604e-143">Configuring System-Provided Bindings</span></span>](../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="0604e-144">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="0604e-144">Configuring Services</span></span>](../../../docs/framework/wcf/configuring-services.md)  
 <span data-ttu-id="0604e-145">[Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a) (Configurando aplicativos do Windows Communication Foundation)</span><span class="sxs-lookup"><span data-stu-id="0604e-145">[Configuring Windows Communication Foundation Applications](https://msdn.microsoft.com/library/13cb368e-88d4-4c61-8eed-2af0361c6d7a)</span></span>  
 [<span data-ttu-id="0604e-146">Configurando serviços do WCF em código</span><span class="sxs-lookup"><span data-stu-id="0604e-146">Configuring WCF Services in Code</span></span>](../../../docs/framework/wcf/configuring-wcf-services-in-code.md)
