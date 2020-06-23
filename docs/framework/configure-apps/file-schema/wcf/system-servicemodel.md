---
title: <system.serviceModel>
description: Saiba mais sobre os elementos de configuração do WCF ServiceModel, que permitem configurar aplicativos cliente e serviço WCF.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#system.ServiceModel
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.ServiceModel
helpviewer_keywords:
- <system.serviceModel> element
- system.serviceModel element
ms.assetid: 78519531-ad7a-40d3-b3e7-42f1103d8854
ms.openlocfilehash: 567cbd2cc07ee82e795daa067b9034b2b8dc1974
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85243952"
---
# \<system.serviceModel>
<span data-ttu-id="5c82d-103">Esta seção de configuração contém todos os elementos de configuração de ServiceModel Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5c82d-103">This configuration section contains all the Windows Communication Foundation (WCF) ServiceModel configuration elements.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.serviceModel>**  
  
## <a name="syntax"></a><span data-ttu-id="5c82d-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c82d-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c82d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5c82d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="5c82d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5c82d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c82d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="5c82d-107">Attributes</span></span>  
 <span data-ttu-id="5c82d-108">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5c82d-108">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5c82d-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5c82d-109">Child Elements</span></span>  
  
|<span data-ttu-id="5c82d-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c82d-110">Element</span></span>|<span data-ttu-id="5c82d-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c82d-111">Description</span></span>|  
|-------------|-----------------|  
|[\<behaviors>](behaviors.md)|<span data-ttu-id="5c82d-112">Esta seção define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="5c82d-112">This section defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="5c82d-113">Cada coleção define elementos de comportamento consumidos por pontos de extremidade e serviços, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5c82d-113">Each collection defines behavior elements consumed by endpoints and services respectively.</span></span> <span data-ttu-id="5c82d-114">Cada elemento do comportamento é identificado por seu exclusivo `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="5c82d-114">Each behavior element is identified by its unique `name` attribute.</span></span>|  
|[\<bindings>](bindings.md)|<span data-ttu-id="5c82d-115">Esta seção contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5c82d-115">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="5c82d-116">Cada entrada é identificada por seu exclusivo `name` .</span><span class="sxs-lookup"><span data-stu-id="5c82d-116">Each entry is identified by its unique `name`.</span></span> <span data-ttu-id="5c82d-117">Os serviços usam associações vinculando-os usando o `name` .</span><span class="sxs-lookup"><span data-stu-id="5c82d-117">Services use bindings by linking them using the `name`.</span></span>|  
|[\<client>](client.md)|<span data-ttu-id="5c82d-118">Esta seção contém uma lista de pontos de extremidade que um cliente usa para se conectar a um serviço.</span><span class="sxs-lookup"><span data-stu-id="5c82d-118">This section contains a list of endpoints a client uses to connect to a service.</span></span>|  
|[\<comContracts>](comcontracts.md)|<span data-ttu-id="5c82d-119">Esta seção define contratos COM habilitados para WCF e interoperabilidade COM.</span><span class="sxs-lookup"><span data-stu-id="5c82d-119">This section defines COM contracts enabled for WCF and COM interop.</span></span>|  
|[\<commonBehaviors>](commonbehaviors.md)|<span data-ttu-id="5c82d-120">Esta seção só pode ser definida no arquivo de machine.config.</span><span class="sxs-lookup"><span data-stu-id="5c82d-120">This section can only be defined in the machine.config file.</span></span> <span data-ttu-id="5c82d-121">Ele define duas coleções filho chamadas `endpointBehaviors` e `serviceBehaviors` .</span><span class="sxs-lookup"><span data-stu-id="5c82d-121">It defines two child collections named `endpointBehaviors` and `serviceBehaviors`.</span></span>  <span data-ttu-id="5c82d-122">Cada coleção define elementos de comportamento consumidos por todos os pontos de extremidade do WCF e serviços no computador, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5c82d-122">Each collection defines behavior elements consumed by all WCF endpoints and services on the machine respectively.</span></span>  <span data-ttu-id="5c82d-123">Se um comportamento for definido em ambas `<commonBehaviors>` as `<behaviors>` seções e, o comportamento na \<behaviors> seção terá preferência.</span><span class="sxs-lookup"><span data-stu-id="5c82d-123">If a behavior is defined in both `<commonBehaviors>` and `<behaviors>` sections, the behavior in the \<behaviors> section is given preference.</span></span>|  
|[\<diagnostics>](diagnostics.md)|<span data-ttu-id="5c82d-124">Esta seção contém configurações para os recursos de diagnóstico do WCF.</span><span class="sxs-lookup"><span data-stu-id="5c82d-124">This section contains settings for the diagnostics features of WCF.</span></span> <span data-ttu-id="5c82d-125">O usuário pode habilitar/desabilitar rastreamento, contadores de desempenho e o provedor WMI e pode adicionar filtros de mensagem personalizados.</span><span class="sxs-lookup"><span data-stu-id="5c82d-125">The user can enable/disable tracing, performance counters, and the WMI provider, and can add custom message filters.</span></span>|  
|[\<extensions>](extensions-section.md)|<span data-ttu-id="5c82d-126">Esta seção contém uma coleção de extensões, que permitem ao usuário criar associações definidas pelo usuário, comportamentos e outros aspectos das extensões.</span><span class="sxs-lookup"><span data-stu-id="5c82d-126">This section contains a collection of extensions, which enable the user to create user-defined bindings, behaviors, and other aspects of extensions.</span></span>|  
|[\<protocolMapping>](protocolmapping.md)|<span data-ttu-id="5c82d-127">Esta seção define um conjunto de mapeamento de protocolo padrão entre esquemas de protocolo de transporte (por exemplo, http, net. TCP, net. pipe, etc.) e associações do WCF.</span><span class="sxs-lookup"><span data-stu-id="5c82d-127">This section defines a set of default protocol mapping between transport protocol schemes (e.g., http, net.tcp, net.pipe, etc.) and WCF bindings.</span></span>|  
|[\<routing>](routing.md)|<span data-ttu-id="5c82d-128">Esta seção define um conjunto de filtros de roteamento, que determinam o tipo de Windows Communication Foundation (WCF) <xref:System.ServiceModel.Dispatcher.MessageFilter> a ser usado ao avaliar mensagens recebidas, bem como tabelas de roteamento que definem os pontos de extremidade de destino para envio de mensagens quando um filtro é correspondente.</span><span class="sxs-lookup"><span data-stu-id="5c82d-128">This section defines a set of routing filters, which determine the type of Windows Communication Foundation (WCF)<xref:System.ServiceModel.Dispatcher.MessageFilter> to be used when evaluating incoming messages, as well as routing tables that define the target endpoints to send messages to when a filter matches.</span></span>|  
|[\<serviceHostingEnvironment>](servicehostingenvironment.md)|<span data-ttu-id="5c82d-129">Esta seção define o tipo que o ambiente de Hospedagem de serviço instancia para um determinado transporte.</span><span class="sxs-lookup"><span data-stu-id="5c82d-129">This section defines what type the service hosting environment instantiates for a particular transport.</span></span> <span data-ttu-id="5c82d-130">Se esta seção estiver vazia, o tipo padrão será usado.</span><span class="sxs-lookup"><span data-stu-id="5c82d-130">If this section is empty, the default type is used.</span></span>|  
|[\<services>](services.md)|<span data-ttu-id="5c82d-131">A seção contém uma coleção de serviços.</span><span class="sxs-lookup"><span data-stu-id="5c82d-131">The section contains a collection of services.</span></span> <span data-ttu-id="5c82d-132">Para cada serviço definido no assembly, esse elemento contém um `service` elemento que especifica as configurações para o serviço.</span><span class="sxs-lookup"><span data-stu-id="5c82d-132">For each service defined in the assembly, this element contains a `service` element specifying settings for the service.</span></span>|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="5c82d-133">Esta seção define uma coleção de pontos de extremidade padrão, que são pontos de extremidade pré-configurados reutilizáveis.</span><span class="sxs-lookup"><span data-stu-id="5c82d-133">This section defines a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="5c82d-134">Um ponto de extremidade padrão terá um ou mais dos atributos de endereço, associação e contrato definidos como um valor fixo.</span><span class="sxs-lookup"><span data-stu-id="5c82d-134">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="5c82d-135">Por exemplo, no ponto de extremidade de descoberta, o contrato é fixo.</span><span class="sxs-lookup"><span data-stu-id="5c82d-135">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="5c82d-136">Você também pode usar pontos de extremidade padrão para estender o ponto final de serviço com novas propriedades semelhantes à definição de associações personalizadas.</span><span class="sxs-lookup"><span data-stu-id="5c82d-136">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>|
|[\<tracking>](tracking-of-wcf.md)|<span data-ttu-id="5c82d-137">Esta seção define as configurações de controle para um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="5c82d-137">This section defines tracking settings for a workflow service.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5c82d-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5c82d-138">Parent Elements</span></span>  
  
|<span data-ttu-id="5c82d-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="5c82d-139">Element</span></span>|<span data-ttu-id="5c82d-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="5c82d-140">Description</span></span>|  
|-------------|-----------------|  
|\<configuration>|<span data-ttu-id="5c82d-141">O elemento raiz para todos os elementos de configuração em um arquivo de configuração do .NET.</span><span class="sxs-lookup"><span data-stu-id="5c82d-141">The root element for all configuration elements in a .NET configuration file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c82d-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="5c82d-142">Remarks</span></span>  
 <span data-ttu-id="5c82d-143">O WCF não adiciona elementos às seções de configuração de outros produtos.</span><span class="sxs-lookup"><span data-stu-id="5c82d-143">WCF does not add elements to the configuration sections of other products.</span></span>  
  
 <span data-ttu-id="5c82d-144">Os serviços WCF são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="5c82d-144">WCF services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="5c82d-145">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="5c82d-145">An assembly can contain any number of services.</span></span> <span data-ttu-id="5c82d-146">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="5c82d-146">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="5c82d-147">A seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="5c82d-147">The section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="5c82d-148">Somente um atributo de serviço `name` é necessário.</span><span class="sxs-lookup"><span data-stu-id="5c82d-148">Only a service's `name` attribute is required.</span></span>  <span data-ttu-id="5c82d-149">Por padrão, o nome de um serviço descreve o tipo CLR subjacente usado para implementar um serviço; no entanto, você pode alterar a propriedade ConfigurationName em um <xref:System.ServiceModel.ServiceContractAttribute> para substituir o requisito de tipo CLR.</span><span class="sxs-lookup"><span data-stu-id="5c82d-149">By default, a service's name describes the underlying CLR type used to implement a service; however, you may change the ConfigurationName property on a <xref:System.ServiceModel.ServiceContractAttribute> to override the CLR type requirement.</span></span>  
  
 <span data-ttu-id="5c82d-150">O atributo `behaviorConfiguration` é opcional.</span><span class="sxs-lookup"><span data-stu-id="5c82d-150">The `behaviorConfiguration` attribute is optional.</span></span> <span data-ttu-id="5c82d-151">Ele identifica o comportamento do serviço usado por um serviço.</span><span class="sxs-lookup"><span data-stu-id="5c82d-151">It identifies the service behavior used by a service.</span></span> <span data-ttu-id="5c82d-152">O comportamento especificado por esse atributo deve ser vinculado a um comportamento de serviço definido no escopo do mesmo arquivo de configuração (ou seja, o mesmo arquivo ou um arquivo pai).</span><span class="sxs-lookup"><span data-stu-id="5c82d-152">The behavior specified by this attribute must link to a service behavior defined in the scope of the same configuration file (i.e. the same file or a parent file).</span></span>  
  
 <span data-ttu-id="5c82d-153">Cada serviço expõe um ou mais pontos de extremidade definidos em um `endpoint` elemento.</span><span class="sxs-lookup"><span data-stu-id="5c82d-153">Each service exposes one or more endpoints defined in an `endpoint` element.</span></span> <span data-ttu-id="5c82d-154">Cada ponto de extremidade tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="5c82d-154">Each endpoint has its own address and binding.</span></span> <span data-ttu-id="5c82d-155">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="5c82d-155">All bindings used within the configuration file must be defined in the scope of the file.</span></span>  
  
 <span data-ttu-id="5c82d-156">As associações são vinculadas a pontos de extremidade por meio da combinação dos atributos `name` e `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="5c82d-156">Bindings are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="5c82d-157">O `binding` atributo define em qual seção a associação é definida.</span><span class="sxs-lookup"><span data-stu-id="5c82d-157">The `binding` attribute defines in which section the binding is defined.</span></span> <span data-ttu-id="5c82d-158">O `bindingConfiguration` atributo define qual associação configurada dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="5c82d-158">The `bindingConfiguration` attribute defines which configured binding within the binding section is used.</span></span> <span data-ttu-id="5c82d-159">Uma seção de associação pode definir várias associações configuradas.</span><span class="sxs-lookup"><span data-stu-id="5c82d-159">A binding section can define several configured bindings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5c82d-160">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5c82d-160">Example</span></span>  
 <span data-ttu-id="5c82d-161">Este é um exemplo de um arquivo de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="5c82d-161">This is an example of a WCF configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5c82d-162">Confira também</span><span class="sxs-lookup"><span data-stu-id="5c82d-162">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceModelSectionGroup>
