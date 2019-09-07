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
ms.openlocfilehash: 2125ce00b0e23f2e93ff251549f9c1276892b16b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399449"
---
# <a name="systemservicemodel"></a><span data-ttu-id="3a23b-102">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3a23b-102">\<system.serviceModel></span></span>
<span data-ttu-id="3a23b-103">Esta seção de configuração contém todos os elementos de configuração de ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3a23b-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

<span data-ttu-id="3a23b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3a23b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3a23b-105">&nbsp;&nbsp; **\<> de System. serviceModel**</span><span class="sxs-lookup"><span data-stu-id="3a23b-105">&nbsp;&nbsp;**\<system.serviceModel>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a23b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a23b-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3a23b-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3a23b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="3a23b-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3a23b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3a23b-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="3a23b-109">Attributes</span></span>  
 <span data-ttu-id="3a23b-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="3a23b-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3a23b-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3a23b-111">Child Elements</span></span>  
  
|<span data-ttu-id="3a23b-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a23b-112">Element</span></span>|<span data-ttu-id="3a23b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a23b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3a23b-114">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3a23b-114">\<behaviors></span></span>](behaviors.md)|<span data-ttu-id="3a23b-115">Esta seção define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3a23b-115">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3a23b-116">Cada coleção define elementos de comportamento consumidos por pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3a23b-116">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="3a23b-117">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="3a23b-117">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[<span data-ttu-id="3a23b-118">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3a23b-118">\<bindings></span></span>](bindings.md)|<span data-ttu-id="3a23b-119">Esta seção contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="3a23b-119">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="3a23b-120">Cada entrada é identificada por seu `name`exclusivo.</span><span class="sxs-lookup"><span data-stu-id="3a23b-120">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="3a23b-121">Os serviços usam associações vinculando-os usando `name`o.</span><span class="sxs-lookup"><span data-stu-id="3a23b-121">Services use bindings by linking them using the `name`.</span></span>|  
|[<span data-ttu-id="3a23b-122">\<client></span><span class="sxs-lookup"><span data-stu-id="3a23b-122">\<client></span></span>](client.md)|<span data-ttu-id="3a23b-123">Esta seção contém uma lista de pontos de extremidade que um cliente usa para se conectar a um serviço.</span><span class="sxs-lookup"><span data-stu-id="3a23b-123">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[<span data-ttu-id="3a23b-124">\<comContracts></span><span class="sxs-lookup"><span data-stu-id="3a23b-124">\<comContracts></span></span>](comcontracts.md)|<span data-ttu-id="3a23b-125">Esta seção define contratos COM habilitados para WCF e interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="3a23b-125">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[<span data-ttu-id="3a23b-126">\<commonBehaviors></span><span class="sxs-lookup"><span data-stu-id="3a23b-126">\<commonBehaviors></span></span>](commonbehaviors.md)|<span data-ttu-id="3a23b-127">Esta seção só pode ser definida no arquivo Machine. config.</span><span class="sxs-lookup"><span data-stu-id="3a23b-127">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="3a23b-128">Ele define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors`.</span><span class="sxs-lookup"><span data-stu-id="3a23b-128">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="3a23b-129">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="3a23b-129">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="3a23b-130">Se um comportamento for definido em ambas `<commonBehaviors>` as `<behaviors>` seções e \<, o comportamento na seção comportamentos > será dada preferência.</span><span class="sxs-lookup"><span data-stu-id="3a23b-130">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[<span data-ttu-id="3a23b-131">\<> de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="3a23b-131">\<diagnostics></span></span>](diagnostics.md)|<span data-ttu-id="3a23b-132">Esta seção contém configurações para os recursos de diagnóstico do WCF.</span><span class="sxs-lookup"><span data-stu-id="3a23b-132">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="3a23b-133">O usuário pode habilitar/desabilitar rastreamento, contadores de desempenho e o provedor WMI e pode adicionar filtros de mensagem personalizados.</span><span class="sxs-lookup"><span data-stu-id="3a23b-133">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[<span data-ttu-id="3a23b-134">\<extensions></span><span class="sxs-lookup"><span data-stu-id="3a23b-134">\<extensions></span></span>](extensions-section.md)|<span data-ttu-id="3a23b-135">Esta seção contém uma coleção de extensões, que permitem ao usuário criar associações definidas pelo usuário, comportamentos e outros aspectos das extensões.</span><span class="sxs-lookup"><span data-stu-id="3a23b-135">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[<span data-ttu-id="3a23b-136">\<protocolMapping></span><span class="sxs-lookup"><span data-stu-id="3a23b-136">\<protocolMapping></span></span>](protocolmapping.md)|<span data-ttu-id="3a23b-137">Esta seção define um conjunto de mapeamento de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="3a23b-137">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[<span data-ttu-id="3a23b-138">\<routing></span><span class="sxs-lookup"><span data-stu-id="3a23b-138">\<routing></span></span>](routing.md)|<span data-ttu-id="3a23b-139">Esta seção define um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (<xref:System.ServiceModel.Dispatcher.MessageFilter> WCF) a ser usado ao avaliar mensagens recebidas, bem como tabelas de roteamento que definem os pontos de extremidade de destino para envio de mensagens quando um correspondências de filtro.</span><span class="sxs-lookup"><span data-stu-id="3a23b-139">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[<span data-ttu-id="3a23b-140">\<serviceHostingEnvironment></span><span class="sxs-lookup"><span data-stu-id="3a23b-140">\<serviceHostingEnvironment></span></span>](servicehostingenvironment.md)|<span data-ttu-id="3a23b-141">Esta seção define o tipo que o ambiente de Hospedagem de serviço instancia para um determinado transporte.</span><span class="sxs-lookup"><span data-stu-id="3a23b-141">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="3a23b-142">Se esta seção estiver vazia, o tipo padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="3a23b-142">If this section is empty, the default type is used.</span></span>|  
|[<span data-ttu-id="3a23b-143">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="3a23b-143">\<services></span></span>](services.md)|<span data-ttu-id="3a23b-144">A seção contém uma coleção de serviços.</span><span class="sxs-lookup"><span data-stu-id="3a23b-144">The section contains a collection of services.</span></span> <span data-ttu-id="3a23b-145">Para cada serviço definido no assembly, esse elemento contém um `service` elemento que especifica as configurações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="3a23b-145">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[<span data-ttu-id="3a23b-146">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="3a23b-146">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="3a23b-147">Esta seção define uma coleção de pontos de extremidade padrão, que são pontos de extremidade pré-configurados reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="3a23b-147">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="3a23b-148">Um ponto de extremidade padrão terá um ou mais dos atributos de endereço, associação e contrato definidos como um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="3a23b-148">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="3a23b-149">Por exemplo, no ponto de extremidade de descoberta, o contrato é fixo.</span><span class="sxs-lookup"><span data-stu-id="3a23b-149">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="3a23b-150">Você também pode usar pontos de extremidade padrão para estender o ponto final de serviço com novas propriedades semelhantes à definição de associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="3a23b-150">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[<span data-ttu-id="3a23b-151">\<tracking></span><span class="sxs-lookup"><span data-stu-id="3a23b-151">\<tracking></span></span>](tracking-of-wcf.md)|<span data-ttu-id="3a23b-152">Esta seção define as configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3a23b-152">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3a23b-153">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3a23b-153">Parent Elements</span></span>  
  
|<span data-ttu-id="3a23b-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="3a23b-154">Element</span></span>|<span data-ttu-id="3a23b-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a23b-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="3a23b-156">\<configuration></span><span class="sxs-lookup"><span data-stu-id="3a23b-156">\<configuration></span></span>|<span data-ttu-id="3a23b-157">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="3a23b-157">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3a23b-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="3a23b-158">Remarks</span></span>  
 <span data-ttu-id="3a23b-159">O WCF não adiciona elementos às seções de configuração de outros produtos.</span><span class="sxs-lookup"><span data-stu-id="3a23b-159">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="3a23b-160">Os serviços WCF são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a23b-160">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="3a23b-161">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="3a23b-161">An assembly can contain any number of services.</span></span> <span data-ttu-id="3a23b-162">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="3a23b-162">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="3a23b-163">A seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="3a23b-163">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="3a23b-164">Somente um atributo de `name` serviço é necessário.</span><span class="sxs-lookup"><span data-stu-id="3a23b-164">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="3a23b-165">Por padrão, o nome de um serviço descreve o tipo CLR subjacente usado para implementar um serviço; no entanto, você pode alterar a propriedade ConfigurationName em um <xref:System.ServiceModel.ServiceContractAttribute> para substituir o requisito de tipo CLR.</span><span class="sxs-lookup"><span data-stu-id="3a23b-165">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="3a23b-166">O atributo `behaviorConfiguration` é opcional.</span><span class="sxs-lookup"><span data-stu-id="3a23b-166">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="3a23b-167">Ele identifica o comportamento do serviço usado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="3a23b-167">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="3a23b-168">O comportamento especificado por esse atributo deve ser vinculado a um comportamento de serviço definido no escopo do mesmo arquivo de configuração (ou seja, o mesmo arquivo ou um arquivo pai).</span><span class="sxs-lookup"><span data-stu-id="3a23b-168">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="3a23b-169">Cada serviço expõe um ou mais pontos de extremidade definidos em um `endpoint` elemento.</span><span class="sxs-lookup"><span data-stu-id="3a23b-169">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="3a23b-170">Cada ponto de extremidade tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="3a23b-170">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="3a23b-171">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="3a23b-171">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="3a23b-172">As associações são vinculadas a pontos de extremidade por meio da combinação dos `name` atributos `bindingConfiguration`e.</span><span class="sxs-lookup"><span data-stu-id="3a23b-172">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="3a23b-173">O `binding` atributo define em qual seção a associação é definida.</span><span class="sxs-lookup"><span data-stu-id="3a23b-173">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="3a23b-174">O `bindingConfiguration` atributo define qual associação configurada dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="3a23b-174">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="3a23b-175">Uma seção de associação pode definir várias associações configuradas.</span><span class="sxs-lookup"><span data-stu-id="3a23b-175">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a23b-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3a23b-176">Example</span></span>  
 <span data-ttu-id="3a23b-177">Este é um exemplo de um arquivo de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="3a23b-177">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3a23b-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a23b-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
