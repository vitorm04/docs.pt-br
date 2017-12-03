---
title: '&lt;System. ServiceModel&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 16a3b9b361048344993fdc338544b6b0ceb95387
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltsystemservicemodelgt"></a><span data-ttu-id="d9c0c-102">&lt;System. ServiceModel&gt;</span><span class="sxs-lookup"><span data-stu-id="d9c0c-102">&lt;system.serviceModel&gt;</span></span>
<span data-ttu-id="d9c0c-103">Esta seção de configuração contém todas as [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] elementos de configuração do ServiceModel.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-103">This configuration section contains all the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9c0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d9c0c-104">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <behaviors>  
  </behaviors>  
  <bindings>  
  </bindings>  
  <client>  
  </client>  
  <comContracts>  
  </comContracts>  
  <commonBehaviors>  
  </commonBehaviors>  
  <diagnostics>  
  </diagnostics>  
  <extensions>  
  </extensions>
  <protocolMapping>
  </protocolMapping>
  <routing>
  </routing>  
  <serviceHostingEnvironment>  
  </serviceHostingEnvironment>  
  <services>  
  </services>
  <standardEndpoints>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d9c0c-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d9c0c-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d9c0c-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d9c0c-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d9c0c-107">Attributes</span></span>  
 <span data-ttu-id="d9c0c-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d9c0c-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d9c0c-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d9c0c-109">Child Elements</span></span>  
  
|<span data-ttu-id="d9c0c-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9c0c-110">Element</span></span>|<span data-ttu-id="d9c0c-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9c0c-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d9c0c-112">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="d9c0c-113">Esta seção define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d9c0c-114">Cada coleção define elementos de comportamento consumidos pelos pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="d9c0c-115">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="d9c0c-116">\<associações ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="d9c0c-117">Esta seção contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="d9c0c-118">Cada entrada é identificada pelo seu exclusivo `name`.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="d9c0c-119">Serviços usar associações vinculando-as usando o `name`.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="d9c0c-120">\<cliente ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="d9c0c-121">Esta seção contém uma lista de pontos de extremidade de que um cliente usa para se conectar a um serviço.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="d9c0c-122">\<comContracts ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="d9c0c-123">Esta seção define os contratos COM habilitado para interoperabilidade COM e o WCF.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="d9c0c-124">\<commonBehaviors ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="d9c0c-125">Esta seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="d9c0c-126">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="d9c0c-127">Cada coleção define elementos de comportamento consumidos por todos os [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] pontos de extremidade e serviços no computador respectivamente.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-127">Each collection defines behavior elements consumed by all [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="d9c0c-128">Se um comportamento é definido em `<commonBehaviors>` e `<behaviors>` seções, o comportamento de \<comportamentos > seção tem preferência.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="d9c0c-129">\<Extensões ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-129">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="d9c0c-130">Esta seção contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-130">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="d9c0c-131">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-131">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="d9c0c-132">Esta seção contém as configurações para os recursos de diagnóstico do WCF.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="d9c0c-133">O usuário pode ativar/desativar o rastreamento, contadores de desempenho e o provedor WMI e pode adicionar filtros de mensagem personalizada.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="d9c0c-134">\<protocolMapping ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="d9c0c-135">Esta seção define um conjunto de mapeamento de padrão de protocolo entre esquemas de protocolo de transporte (por exemplo, http, net.tcp, NET. pipe, etc.) e as associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="d9c0c-136">\<roteamento ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="d9c0c-137">Esta seção define um conjunto de filtros de roteamento, que determinam o tipo de [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como o roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens para quando houver correspondência de filtro.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-137">This section defines a set of routing filters, which determine the type of [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="d9c0c-138">\<serviceHostingEnvironment ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="d9c0c-139">Esta seção define o tipo de serviço instancia do ambiente de hospedagem para um determinado transporte.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="d9c0c-140">Se esta seção está vazia, o tipo padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="d9c0c-141">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="d9c0c-142">A seção contém uma coleção de serviços.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-142">The section contains a collection of services.</span></span> <span data-ttu-id="d9c0c-143">Para cada serviço definido no assembly, esse elemento contém um `service` elemento para especificar configurações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="d9c0c-144">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="d9c0c-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="d9c0c-145">Esta seção define uma coleção de pontos de extremidade padrão, que são pontos de extremidade pré-configurados reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="d9c0c-146">Um ponto de extremidade padrão terá um ou mais do endereço, associação e os atributos do contrato definido como um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="d9c0c-147">Por exemplo, no ponto de extremidade de descoberta do contrato é fixo.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="d9c0c-148">Você também pode usar pontos de extremidade padrão para estender o ponto de extremidade de serviço com novas propriedades semelhantes para definir associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d9c0c-149">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d9c0c-149">Parent Elements</span></span>  
  
|<span data-ttu-id="d9c0c-150">Elemento</span><span class="sxs-lookup"><span data-stu-id="d9c0c-150">Element</span></span>|<span data-ttu-id="d9c0c-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="d9c0c-151">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d9c0c-152">\<configuration></span><span class="sxs-lookup"><span data-stu-id="d9c0c-152">\<configuration></span></span>|<span data-ttu-id="d9c0c-153">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-153">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9c0c-154">Comentários</span><span class="sxs-lookup"><span data-stu-id="d9c0c-154">Remarks</span></span>  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="d9c0c-155">Não adicione elementos para as seções de configuração de outros produtos.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-155"> does not add elements to the configuration sections of other products.</span></span>  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]<span data-ttu-id="d9c0c-156">os serviços são definidos no `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-156"> services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="d9c0c-157">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-157">An assembly can contain any number of services.</span></span> <span data-ttu-id="d9c0c-158">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-158">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="d9c0c-159">A seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-159">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="d9c0c-160">Do somente um serviço `name` atributo é necessário.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-160">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="d9c0c-161">Por padrão, o nome do serviço descreve o tipo CLR subjacente usado para implementar um serviço; No entanto, você pode alterar a propriedade ConfigurationName em um <xref:System.ServiceModel.ServiceContractAttribute> para substituir o requisito de tipo CLR.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-161">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="d9c0c-162">O atributo `behaviorConfiguration` é opcional.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-162">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="d9c0c-163">Ele identifica o comportamento de serviço usado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-163">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="d9c0c-164">O comportamento especificado por esse atributo deve vincular a um comportamento de serviço definido no escopo do mesmo arquivo de configuração (ou seja, o mesmo arquivo ou um arquivo pai).</span><span class="sxs-lookup"><span data-stu-id="d9c0c-164">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="d9c0c-165">Cada serviço expõe um ou mais pontos de extremidade definidos em um `endpoint` elemento.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-165">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="d9c0c-166">Cada ponto de extremidade tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-166">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="d9c0c-167">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-167">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="d9c0c-168">Associações são vinculadas aos pontos de extremidade pela combinação dos atributos `name` e `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-168">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="d9c0c-169">O `binding` atributo define na seção a associação está definida.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-169">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="d9c0c-170">O `bindingConfiguration` atributo define qual associação configurada na seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-170">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="d9c0c-171">Uma seção de associação pode definir várias associações configuradas.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-171">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9c0c-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d9c0c-172">Example</span></span>  
 <span data-ttu-id="d9c0c-173">Este é um exemplo de um arquivo de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="d9c0c-173">This is an example of a WCF configuration file.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <behaviors>  
           <!-- List of Behaviors -->  
        </behaviors>  
        <client>  
           <!-- List of Endpoints -->  
        </client>  
        <diagnostics wmiProviderEnabled="false" performanceCountersEnabled="false" tracingEnabled="false">  
        </diagnostics>  
        <serviceHostingEnvironment>  
           <!-- List of entries -->  
        </serviceHostingEnvironment>  
        <comContracts>  
           <!-- List of COM+ Contracts -->  
        </comContracts>          
        <services>  
           <!-- List of Services -->  
        </services>  
        <bindings>  
           <!-- List of Bindings -->  
        </bindings>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d9c0c-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9c0c-174">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
