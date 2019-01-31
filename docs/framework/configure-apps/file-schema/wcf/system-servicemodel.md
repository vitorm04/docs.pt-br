---
title: <system.serviceModel>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 7b0c91bafc14dee0d298a5cd31dc674f5002466a
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55274190"
---
# <a name="systemservicemodel"></a><span data-ttu-id="7c658-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7c658-102">\<system.serviceModel></span></span>
<span data-ttu-id="7c658-103">Esta seção de configuração contém todos os elementos de configuração de ServiceModel do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="7c658-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c658-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7c658-104">Syntax</span></span>  
  
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
  <tracking>
  </tracking>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7c658-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7c658-105">Attributes and Elements</span></span>  
 <span data-ttu-id="7c658-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7c658-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7c658-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="7c658-107">Attributes</span></span>  
 <span data-ttu-id="7c658-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7c658-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7c658-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7c658-109">Child Elements</span></span>  
  
|<span data-ttu-id="7c658-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c658-110">Element</span></span>|<span data-ttu-id="7c658-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c658-111">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7c658-112">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="7c658-112">\<behaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)|<span data-ttu-id="7c658-113">Esta seção define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="7c658-113">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7c658-114">Cada coleção define elementos de comportamento consumidos pelos pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7c658-114">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="7c658-115">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="7c658-115">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="7c658-116">\<bindings></span><span class="sxs-lookup"><span data-stu-id="7c658-116">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="7c658-117">Esta seção contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7c658-117">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="7c658-118">Cada entrada é identificada por seu exclusivo `name`.</span><span class="sxs-lookup"><span data-stu-id="7c658-118">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="7c658-119">Serviços usam associações vinculando-as usando o `name`.</span><span class="sxs-lookup"><span data-stu-id="7c658-119">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="7c658-120">\<client></span><span class="sxs-lookup"><span data-stu-id="7c658-120">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="7c658-121">Esta seção contém uma lista de pontos de extremidade de que um cliente usa para se conectar a um serviço.</span><span class="sxs-lookup"><span data-stu-id="7c658-121">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="7c658-122">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="7c658-122">\<comContracts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/comcontracts.md)|<span data-ttu-id="7c658-123">Esta seção define os contratos COM habilitado para a interoperabilidade do WCF e do COM.</span><span class="sxs-lookup"><span data-stu-id="7c658-123">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="7c658-124">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="7c658-124">\<commonBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md)|<span data-ttu-id="7c658-125">Esta seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="7c658-125">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="7c658-126">Ele define duas coleções filhas nomeadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="7c658-126">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="7c658-127">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7c658-127">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="7c658-128">Se um comportamento é definido em ambos `<commonBehaviors>` e `<behaviors>` seções, o comportamento no \<comportamentos > seção é dada preferência.</span><span class="sxs-lookup"><span data-stu-id="7c658-128">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="7c658-129">\<diagnóstico ></span><span class="sxs-lookup"><span data-stu-id="7c658-129">\<diagnostics></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|<span data-ttu-id="7c658-130">Esta seção contém as configurações para os recursos de diagnóstico do WCF.</span><span class="sxs-lookup"><span data-stu-id="7c658-130">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="7c658-131">O usuário pode habilitar/desabilitar o rastreamento, contadores de desempenho e o provedor WMI e pode adicionar filtros de mensagem personalizada.</span><span class="sxs-lookup"><span data-stu-id="7c658-131">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="7c658-132">\<extensions></span><span class="sxs-lookup"><span data-stu-id="7c658-132">\<extensions></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/extensions-section.md)|<span data-ttu-id="7c658-133">Esta seção contém uma coleção de extensões, que permitem que o usuário crie associações definidas pelo usuário, comportamentos e outros aspectos de extensões.</span><span class="sxs-lookup"><span data-stu-id="7c658-133">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="7c658-134">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="7c658-134">\<protocolMapping></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/protocolmapping.md)|<span data-ttu-id="7c658-135">Esta seção define um conjunto padrão de mapeamento de protocolo entre esquemas de protocolo de transporte (por exemplo, http, NET. TCP, NET. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="7c658-135">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="7c658-136">\<routing></span><span class="sxs-lookup"><span data-stu-id="7c658-136">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="7c658-137">Esta seção define um conjunto de filtros de roteamento, que determinam o tipo do Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usada ao avaliar mensagens recebidas, bem como roteamento de tabelas que definem os pontos de extremidade de destino para enviar mensagens para quando um corresponde ao filtro.</span><span class="sxs-lookup"><span data-stu-id="7c658-137">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="7c658-138">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="7c658-138">\<serviceHostingEnvironment></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|<span data-ttu-id="7c658-139">Esta seção define que tipo de serviço do ambiente de hospedagem cria uma instância para um transporte particular.</span><span class="sxs-lookup"><span data-stu-id="7c658-139">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="7c658-140">Se esta seção está vazia, o tipo padrão é usado.</span><span class="sxs-lookup"><span data-stu-id="7c658-140">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="7c658-141">\<services></span><span class="sxs-lookup"><span data-stu-id="7c658-141">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="7c658-142">A seção contém uma coleção de serviços.</span><span class="sxs-lookup"><span data-stu-id="7c658-142">The section contains a collection of services.</span></span> <span data-ttu-id="7c658-143">Para cada serviço definido no assembly, esse elemento contém um `service` elemento que especifica configurações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="7c658-143">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="7c658-144">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="7c658-144">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="7c658-145">Esta seção define uma coleção de pontos de extremidade padrão que são pontos de extremidade pré-configurados reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="7c658-145">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="7c658-146">Um ponto de extremidade padrão terá um ou mais do endereço, associação e atributos de contrato definido como um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="7c658-146">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="7c658-147">Por exemplo, o ponto de extremidade de descoberta o contrato é fixo.</span><span class="sxs-lookup"><span data-stu-id="7c658-147">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="7c658-148">Você também pode usar pontos de extremidade padrão para estender o ponto de extremidade de serviço com novas propriedades semelhantes à definição de ligações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="7c658-148">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="7c658-149">\<tracking></span><span class="sxs-lookup"><span data-stu-id="7c658-149">\<tracking></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/tracking-of-wcf.md)|<span data-ttu-id="7c658-150">Esta seção define as configurações de rastreamento para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7c658-150">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7c658-151">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7c658-151">Parent Elements</span></span>  
  
|<span data-ttu-id="7c658-152">Elemento</span><span class="sxs-lookup"><span data-stu-id="7c658-152">Element</span></span>|<span data-ttu-id="7c658-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="7c658-153">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7c658-154">\<configuration></span><span class="sxs-lookup"><span data-stu-id="7c658-154">\<configuration></span></span>|<span data-ttu-id="7c658-155">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="7c658-155">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c658-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="7c658-156">Remarks</span></span>  
 <span data-ttu-id="7c658-157">WCF não adiciona elementos para as seções de configuração de outros produtos.</span><span class="sxs-lookup"><span data-stu-id="7c658-157">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="7c658-158">Os serviços do WCF são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="7c658-158">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="7c658-159">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="7c658-159">An assembly can contain any number of services.</span></span> <span data-ttu-id="7c658-160">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="7c658-160">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="7c658-161">A seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="7c658-161">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="7c658-162">Somente o de um serviço `name` atributo é necessário.</span><span class="sxs-lookup"><span data-stu-id="7c658-162">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="7c658-163">Por padrão, o nome do serviço descreve o tipo CLR subjacente usado para implementar um serviço; No entanto, você pode alterar a propriedade ConfigurationName em um <xref:System.ServiceModel.ServiceContractAttribute> para substituir o requisito de tipo CLR.</span><span class="sxs-lookup"><span data-stu-id="7c658-163">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="7c658-164">O atributo `behaviorConfiguration` é opcional.</span><span class="sxs-lookup"><span data-stu-id="7c658-164">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="7c658-165">Ele identifica o comportamento de serviço usado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="7c658-165">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="7c658-166">O comportamento especificado por este atributo deve vincular a um comportamento de serviço definido no escopo do mesmo arquivo de configuração (ou seja, o mesmo arquivo ou um arquivo pai).</span><span class="sxs-lookup"><span data-stu-id="7c658-166">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="7c658-167">Cada serviço expõe um ou mais pontos de extremidade definido em um `endpoint` elemento.</span><span class="sxs-lookup"><span data-stu-id="7c658-167">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="7c658-168">Cada ponto de extremidade tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="7c658-168">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="7c658-169">Todas as ligações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="7c658-169">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="7c658-170">Associações são vinculadas aos pontos de extremidade por meio da combinação dos atributos `name` e `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="7c658-170">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="7c658-171">O `binding` atributo define em qual seção a associação é definida.</span><span class="sxs-lookup"><span data-stu-id="7c658-171">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="7c658-172">O `bindingConfiguration` atributo define qual associação configurada dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="7c658-172">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="7c658-173">Uma seção de associação pode definir várias associações configuradas.</span><span class="sxs-lookup"><span data-stu-id="7c658-173">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c658-174">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7c658-174">Example</span></span>  
 <span data-ttu-id="7c658-175">Este é um exemplo de um arquivo de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="7c658-175">This is an example of a WCF configuration file.</span></span>  
  
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
    <diagnostics wmiProviderEnabled="false"
                 performanceCountersEnabled="false"
                 tracingEnabled="false">
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
  
## <a name="see-also"></a><span data-ttu-id="7c658-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c658-176">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
