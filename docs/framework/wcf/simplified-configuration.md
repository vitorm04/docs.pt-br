---
title: Configuração simplificada
ms.date: 03/30/2017
ms.assetid: dcbe1f84-437c-495f-9324-2bc09fd79ea9
ms.openlocfilehash: 4e316290c045b75896c61e36c1646440c18678e2
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249624"
---
# <a name="simplified-configuration"></a><span data-ttu-id="57170-102">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="57170-102">Simplified Configuration</span></span>
<span data-ttu-id="57170-103">Configurar os serviços da Windows Communication Foundation (WCF) pode ser uma tarefa complexa.</span><span class="sxs-lookup"><span data-stu-id="57170-103">Configuring Windows Communication Foundation (WCF) services can be a complex task.</span></span> <span data-ttu-id="57170-104">Existem muitas opções diferentes e nem sempre é fácil determinar quais configurações são necessárias.</span><span class="sxs-lookup"><span data-stu-id="57170-104">There are many different options and it is not always easy to determine what settings are required.</span></span> <span data-ttu-id="57170-105">Embora os arquivos de configuração aumentem a flexibilidade dos serviços WCF, eles também são a fonte para muitos problemas difíceis de encontrar.</span><span class="sxs-lookup"><span data-stu-id="57170-105">While configuration files increase the flexibility of WCF services, they also are the source for many hard to find problems.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="57170-106">resolve esses problemas e fornece uma maneira de reduzir o tamanho e a complexidade da configuração do serviço.</span><span class="sxs-lookup"><span data-stu-id="57170-106">addresses these problems and provides a way to reduce the size and complexity of service configuration.</span></span>  
  
## <a name="simplified-configuration"></a><span data-ttu-id="57170-107">Configuração simplificada</span><span class="sxs-lookup"><span data-stu-id="57170-107">Simplified Configuration</span></span>  
 <span data-ttu-id="57170-108">Nos arquivos de configuração `system.serviceModel` de serviço WCF, a seção> <contém um elemento <`service`> para cada serviço hospedado.</span><span class="sxs-lookup"><span data-stu-id="57170-108">In WCF service configuration files, the <`system.serviceModel`> section contains a <`service`> element for each service hosted.</span></span> <span data-ttu-id="57170-109">O `service` elemento> <contém `endpoint` uma coleção de elementos <> que especificam os pontos finais expostos para cada serviço e, opcionalmente, um conjunto de comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="57170-109">The <`service`> element contains a collection of <`endpoint`> elements that specify the endpoints exposed for each service and optionally a set of service behaviors.</span></span> <span data-ttu-id="57170-110">Os `endpoint` elementos <> especificam o endereço, a vinculação e o contrato expostos pelo ponto final e, opcionalmente, vinculando comportamentos de configuração e ponto final.</span><span class="sxs-lookup"><span data-stu-id="57170-110">The <`endpoint`> elements specify the address, binding, and contract exposed by the endpoint, and optionally binding configuration and endpoint behaviors.</span></span> <span data-ttu-id="57170-111">A `system.serviceModel` seção <> `behaviors` também contém um elemento> <que permite especificar comportamentos de serviço ou ponto final.</span><span class="sxs-lookup"><span data-stu-id="57170-111">The <`system.serviceModel`> section also contains a <`behaviors`> element that allows you to specify service or endpoint behaviors.</span></span> <span data-ttu-id="57170-112">O exemplo a `system.serviceModel` seguir mostra a seção> <de um arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="57170-112">The following example shows the <`system.serviceModel`> section of a configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
    <serviceBehaviors>  
      <behavior name="MyServiceBehavior">  
        <serviceMetadata httpGetEnabled="true" />  
        <serviceDebug includeExceptionDetailInFaults="false" />  
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
  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="57170-113">facilita a configuração de um serviço WCF `service` removendo o requisito para o <> elemento.</span><span class="sxs-lookup"><span data-stu-id="57170-113">makes configuring a WCF service easier by removing the requirement for the <`service`> element.</span></span> <span data-ttu-id="57170-114">Se você não adicionar `service` uma <> seção `service` ou adicionar quaisquer pontos finais em uma seção de> <e seu serviço não definir programáticamente quaisquer pontos finais, então um conjunto de pontos finais padrão são automaticamente adicionados ao seu serviço, um para cada endereço base de serviço e para cada contrato implementado pelo seu serviço.</span><span class="sxs-lookup"><span data-stu-id="57170-114">If you do not add a <`service`>  section or add any endpoints in a <`service`> section and your service does not programmatically define any endpoints, then a set of default endpoints are automatically added to your service, one for each service base address and for each contract implemented by your service.</span></span> <span data-ttu-id="57170-115">Em cada um desses pontos finais, o endereço de ponto final corresponde ao endereço base, a vinculação é determinada pelo esquema de endereço base e o contrato é o implementado pelo seu serviço.</span><span class="sxs-lookup"><span data-stu-id="57170-115">In each of these endpoints, the endpoint address corresponds to the base address, the binding is determined by the base address scheme and the contract is the one implemented by your service.</span></span> <span data-ttu-id="57170-116">Se você não precisar especificar quaisquer pontos finais ou comportamentos de serviço ou fazer quaisquer alterações de configuração vinculantes, você não precisa especificar um arquivo de configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="57170-116">If you do not need to specify any endpoints or service behaviors or make any binding setting changes, you do not need to specify a service configuration file at all.</span></span> <span data-ttu-id="57170-117">Se um serviço implementar dois contratos e o host habilitar tanto o TRANSPORTE HTTP quanto o TCP, o host de serviço criará quatro pontos finais padrão, um para cada contrato usando cada transporte.</span><span class="sxs-lookup"><span data-stu-id="57170-117">If a service implements two contracts and the host enables both HTTP and TCP transports the service host creates four default endpoints, one for each contract using each transport.</span></span> <span data-ttu-id="57170-118">Para criar pontos finais padrão, o host de serviço deve saber quais vinculações usar.</span><span class="sxs-lookup"><span data-stu-id="57170-118">To create default endpoints the service host must know what bindings to use.</span></span> <span data-ttu-id="57170-119">Essas configurações são especificadas `protocolMappings` em uma `system.serviceModel` seção de> <na seção <>.</span><span class="sxs-lookup"><span data-stu-id="57170-119">These settings are specified in a <`protocolMappings`> section within the <`system.serviceModel`> section.</span></span> <span data-ttu-id="57170-120">A `protocolMappings` seção <> contém uma lista de esquemas de protocolo de transporte mapeados para tipos de vinculação.</span><span class="sxs-lookup"><span data-stu-id="57170-120">The <`protocolMappings`> section contains a list of transport protocol schemes mapped to binding types.</span></span> <span data-ttu-id="57170-121">O host de serviço usa os endereços base passados para ele para determinar qual vinculação usar.</span><span class="sxs-lookup"><span data-stu-id="57170-121">The service host uses the base addresses passed to it to determine which binding to use.</span></span> <span data-ttu-id="57170-122">O exemplo a `protocolMappings` seguir usa o elemento> <.</span><span class="sxs-lookup"><span data-stu-id="57170-122">The following example uses the <`protocolMappings`> element.</span></span>  
  
> [!WARNING]
> <span data-ttu-id="57170-123">A alteração de elementos de configuração padrão, como vinculações ou comportamentos, pode afetar os serviços definidos em níveis mais baixos da hierarquia de configuração, uma vez que eles podem estar usando essas vinculações e comportamentos padrão.</span><span class="sxs-lookup"><span data-stu-id="57170-123">Changing default configuration elements, such as bindings or behaviors, might affect services defined in lower levels of the configuration hierarchy, since they might be using these default bindings and behaviors.</span></span> <span data-ttu-id="57170-124">Assim, quem altera as vinculações e comportamentos padrão precisa estar ciente de que essas mudanças podem afetar outros serviços na hierarquia.</span><span class="sxs-lookup"><span data-stu-id="57170-124">Thus, whoever changes default bindings and behaviors needs to be aware that these changes might affect other services in the hierarchy.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="57170-125">Os serviços hospedados no Internet Information Services (IIS) ou no Windows Process Activation Service (WAS) usam o diretório virtual como endereço base.</span><span class="sxs-lookup"><span data-stu-id="57170-125">Services hosted under Internet Information Services (IIS) or Windows Process Activation Service (WAS) use the virtual directory as their base address.</span></span>  
  
```xml  
<protocolMapping>  
  <add scheme="http"     binding="basicHttpBinding" bindingConfiguration="MyBindingConfiguration"/>  
  <add scheme="net.tcp"  binding="netTcpBinding"/>  
  <add scheme="net.pipe" binding="netNamedPipeBinding"/>  
  <add scheme="net.msmq" binding="netMSMQBinding"/>  
</protocolMapping>  
```  
  
 <span data-ttu-id="57170-126">No exemplo anterior, um ponto final com um endereço base que <xref:System.ServiceModel.BasicHttpBinding>começa com o esquema "http" usa o .</span><span class="sxs-lookup"><span data-stu-id="57170-126">In the previous example, an endpoint with a base address that starts with the "http" scheme uses the <xref:System.ServiceModel.BasicHttpBinding>.</span></span> <span data-ttu-id="57170-127">Um ponto final com um endereço base que começa com <xref:System.ServiceModel.NetTcpBinding>o esquema "net.tcp" usa o .</span><span class="sxs-lookup"><span data-stu-id="57170-127">An endpoint with a base address that starts with the "net.tcp" scheme uses the <xref:System.ServiceModel.NetTcpBinding>.</span></span> <span data-ttu-id="57170-128">Você pode substituir as configurações em um arquivo local App.config ou Web.config.</span><span class="sxs-lookup"><span data-stu-id="57170-128">You can override settings in a local App.config or Web.config file.</span></span>  
  
 <span data-ttu-id="57170-129">Cada elemento dentro `protocolMappings` da seção <> deve especificar um esquema e uma vinculação.</span><span class="sxs-lookup"><span data-stu-id="57170-129">Each element within the <`protocolMappings`> section must specify a scheme and a binding.</span></span> <span data-ttu-id="57170-130">Opcionalmente, ele `bindingConfiguration` pode especificar um atributo `bindings` que especifica uma configuração de vinculação dentro da seção <> do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="57170-130">Optionally it can specify a `bindingConfiguration` attribute that specifies a binding configuration within the <`bindings`> section of the configuration file.</span></span> <span data-ttu-id="57170-131">Se `bindingConfiguration` não for especificado, a configuração de vinculação anônima do tipo de vinculação apropriada é usada.</span><span class="sxs-lookup"><span data-stu-id="57170-131">If no `bindingConfiguration` is specified, the anonymous binding configuration of the appropriate binding type is used.</span></span>  
  
 <span data-ttu-id="57170-132">Os comportamentos de serviço são configurados para `behavior` os pontos finais `serviceBehaviors` padrão usando seções de> de <anônimos nas seções <>.</span><span class="sxs-lookup"><span data-stu-id="57170-132">Service behaviors are configured for the default endpoints by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span> <span data-ttu-id="57170-133">Quaisquer elementos `behavior` de> `serviceBehaviors` <não nomeados dentro de <> são usados para configurar comportamentos de serviço.</span><span class="sxs-lookup"><span data-stu-id="57170-133">Any unnamed <`behavior`> elements within <`serviceBehaviors`> are used to configure service behaviors.</span></span> <span data-ttu-id="57170-134">Por exemplo, o arquivo de configuração a seguir permite a publicação de metadados de serviço para todos os serviços dentro do host.</span><span class="sxs-lookup"><span data-stu-id="57170-134">For example, the following configuration file enables service metadata publishing for all services within the host.</span></span>  
  
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
  
 <span data-ttu-id="57170-135">Os comportamentos de ponto final são `behavior` configurados usando `serviceBehaviors` seções de> de <anônimos dentro de <seções>.</span><span class="sxs-lookup"><span data-stu-id="57170-135">Endpoint behaviors are configured by using anonymous <`behavior`> sections within <`serviceBehaviors`> sections.</span></span>  
  
 <span data-ttu-id="57170-136">O exemplo a seguir é um arquivo de configuração equivalente ao do início deste tópico que usa o modelo de configuração simplificada.</span><span class="sxs-lookup"><span data-stu-id="57170-136">The following example is a configuration file equivalent to the one at the beginning of this topic that uses the simplified configuration model.</span></span>  
  
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
> <span data-ttu-id="57170-137">Esse recurso diz respeito apenas à configuração do serviço WCF, não à configuração do cliente.</span><span class="sxs-lookup"><span data-stu-id="57170-137">This feature relates only to WCF service configuration, not client configuration.</span></span> <span data-ttu-id="57170-138">Na maioria das vezes, a configuração do cliente WCF será gerada por uma ferramenta como svcutil.exe ou adicionando uma referência de serviço do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="57170-138">Most times, WCF client configuration will be generated by a tool such as svcutil.exe or adding a service reference from Visual Studio.</span></span> <span data-ttu-id="57170-139">Se você estiver configurando manualmente um cliente WCF, você precisará adicionar um \<elemento de> cliente à configuração e especificar quaisquer pontos finais que você deseja chamar.</span><span class="sxs-lookup"><span data-stu-id="57170-139">If you are manually configuring a WCF client you will need to add a \<client> element to the configuration and specify any endpoints you wish to call.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57170-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="57170-140">See also</span></span>

- [<span data-ttu-id="57170-141">Configurando serviços usando arquivos de configuração</span><span class="sxs-lookup"><span data-stu-id="57170-141">Configuring Services Using Configuration Files</span></span>](configuring-services-using-configuration-files.md)
- [<span data-ttu-id="57170-142">Configurando associações para serviços</span><span class="sxs-lookup"><span data-stu-id="57170-142">Configuring Bindings for Services</span></span>](configuring-bindings-for-wcf-services.md)
- [<span data-ttu-id="57170-143">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="57170-143">Configuring System-Provided Bindings</span></span>](./feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="57170-144">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="57170-144">Configuring Services</span></span>](configuring-services.md)
- [<span data-ttu-id="57170-145">Configuração de serviços WCF</span><span class="sxs-lookup"><span data-stu-id="57170-145">Configuring WCF services</span></span>](configuring-services.md)
- [<span data-ttu-id="57170-146">Configurando serviços do WCF em código</span><span class="sxs-lookup"><span data-stu-id="57170-146">Configuring WCF Services in Code</span></span>](configuring-wcf-services-in-code.md)
