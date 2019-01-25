---
title: '&lt;ponto de extremidade&gt; do &lt;cliente&gt;'
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: a7d95ee819c911d80178e38a37aeaccc5b1f1764
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54598298"
---
# <a name="ltendpointgt-of-ltclientgt"></a><span data-ttu-id="b022b-102">&lt;ponto de extremidade&gt; do &lt;cliente&gt;</span><span class="sxs-lookup"><span data-stu-id="b022b-102">&lt;endpoint&gt; of &lt;client&gt;</span></span>
<span data-ttu-id="b022b-103">Especifica o contrato, associação e propriedades de endereço do ponto de extremidade de canal, que é usado pelos clientes para se conectar aos pontos de extremidade de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="b022b-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
 <span data-ttu-id="b022b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b022b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b022b-105">\<client></span><span class="sxs-lookup"><span data-stu-id="b022b-105">\<client></span></span>  
<span data-ttu-id="b022b-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="b022b-106">\<endpoint></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b022b-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b022b-107">Syntax</span></span>  
  
```xml  
<endpoint address="String"
          behaviorConfiguration="String"
          binding="String"
          bindingConfiguration="String"
          contract="String"
          endpointConfiguration="String"
          kind="String"
          name="String">
</endpoint>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b022b-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b022b-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b022b-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b022b-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b022b-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b022b-110">Attributes</span></span>  
  
|<span data-ttu-id="b022b-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b022b-111">Attribute</span></span>|<span data-ttu-id="b022b-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b022b-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b022b-113">endereço</span><span class="sxs-lookup"><span data-stu-id="b022b-113">address</span></span>|<span data-ttu-id="b022b-114">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b022b-114">Required string attribute.</span></span><br /><br /> <span data-ttu-id="b022b-115">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b022b-115">Specifies the address of the endpoint.</span></span> <span data-ttu-id="b022b-116">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b022b-116">The default is an empty string.</span></span> <span data-ttu-id="b022b-117">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="b022b-117">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="b022b-118">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="b022b-118">behaviorConfiguration</span></span>|<span data-ttu-id="b022b-119">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="b022b-119">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="b022b-120">O nome deve estar no escopo no ponto em que o serviço está definido.</span><span class="sxs-lookup"><span data-stu-id="b022b-120">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="b022b-121">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b022b-121">The default is an empty string.</span></span>|  
|<span data-ttu-id="b022b-122">associação</span><span class="sxs-lookup"><span data-stu-id="b022b-122">binding</span></span>|<span data-ttu-id="b022b-123">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b022b-123">Required string attribute.</span></span><br /><br /> <span data-ttu-id="b022b-124">Uma cadeia de caracteres que indica o tipo de associação a ser usada.</span><span class="sxs-lookup"><span data-stu-id="b022b-124">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="b022b-125">O tipo deve ter uma seção de configuração registrado para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="b022b-125">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="b022b-126">O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo da associação.</span><span class="sxs-lookup"><span data-stu-id="b022b-126">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="b022b-127">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="b022b-127">bindingConfiguration</span></span>|<span data-ttu-id="b022b-128">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b022b-128">Optional.</span></span> <span data-ttu-id="b022b-129">Uma cadeia de caracteres que contém o nome da configuração de associação a ser usado quando o ponto de extremidade é instanciado.</span><span class="sxs-lookup"><span data-stu-id="b022b-129">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="b022b-130">A configuração de associação deve estar no escopo no ponto de que extremidade é definido.</span><span class="sxs-lookup"><span data-stu-id="b022b-130">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="b022b-131">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b022b-131">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="b022b-132">Esse atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b022b-132">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="b022b-133">Defina esse atributo, se você está tentando usar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="b022b-133">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="b022b-134">Caso contrário, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="b022b-134">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="b022b-135">contrato</span><span class="sxs-lookup"><span data-stu-id="b022b-135">contract</span></span>|<span data-ttu-id="b022b-136">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="b022b-136">Required string attribute.</span></span><br /><br /> <span data-ttu-id="b022b-137">Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="b022b-137">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="b022b-138">O assembly deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="b022b-138">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="b022b-139">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="b022b-139">endpointConfiguration</span></span>|<span data-ttu-id="b022b-140">Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, o que faz referência às informações de configuração adicionais deste ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="b022b-140">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="b022b-141">O mesmo nome deve ser definido no `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="b022b-141">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="b022b-142">Tipo</span><span class="sxs-lookup"><span data-stu-id="b022b-142">kind</span></span>|<span data-ttu-id="b022b-143">Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado.</span><span class="sxs-lookup"><span data-stu-id="b022b-143">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="b022b-144">O tipo deve ser registrado na seção `<extensions>` ou em machine.config. Se nada for especificado, um ponto de extremidade de canal comum será criado.</span><span class="sxs-lookup"><span data-stu-id="b022b-144">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="b022b-145">name</span><span class="sxs-lookup"><span data-stu-id="b022b-145">name</span></span>|<span data-ttu-id="b022b-146">Atributo de cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="b022b-146">Optional string attribute.</span></span> <span data-ttu-id="b022b-147">Este atributo identifica exclusivamente um ponto de extremidade para um determinado contrato.</span><span class="sxs-lookup"><span data-stu-id="b022b-147">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="b022b-148">Você pode definir vários clientes para um determinado tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="b022b-148">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="b022b-149">Cada definição deve ser diferenciada por um nome de configuração exclusivas.</span><span class="sxs-lookup"><span data-stu-id="b022b-149">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="b022b-150">Se esse atributo for omitido, o ponto de extremidade correspondente é usado como o ponto de extremidade padrão associado ao tipo de contrato especificado.</span><span class="sxs-lookup"><span data-stu-id="b022b-150">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="b022b-151">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b022b-151">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="b022b-152">O `name` atributo de uma associação é usado para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="b022b-152">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b022b-153">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b022b-153">Child Elements</span></span>  
  
|<span data-ttu-id="b022b-154">Elemento</span><span class="sxs-lookup"><span data-stu-id="b022b-154">Element</span></span>|<span data-ttu-id="b022b-155">Descrição</span><span class="sxs-lookup"><span data-stu-id="b022b-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b022b-156">\<headers></span><span class="sxs-lookup"><span data-stu-id="b022b-156">\<headers></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|<span data-ttu-id="b022b-157">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="b022b-157">A collection of address headers.</span></span>|  
|[<span data-ttu-id="b022b-158">\<identity></span><span class="sxs-lookup"><span data-stu-id="b022b-158">\<identity></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|<span data-ttu-id="b022b-159">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidade trocando mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="b022b-159">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b022b-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b022b-160">Parent Elements</span></span>  
  
|<span data-ttu-id="b022b-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="b022b-161">Element</span></span>|<span data-ttu-id="b022b-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="b022b-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b022b-163">\<client></span><span class="sxs-lookup"><span data-stu-id="b022b-163">\<client></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/client.md)|<span data-ttu-id="b022b-164">Uma seção de configuração que define uma lista de pontos de extremidade que um cliente pode se conectar ao.</span><span class="sxs-lookup"><span data-stu-id="b022b-164">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="b022b-165">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b022b-165">Example</span></span>  
 <span data-ttu-id="b022b-166">Este é um exemplo de uma configuração de ponto de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="b022b-166">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="b022b-167">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b022b-167">See also</span></span>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="b022b-168">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="b022b-168">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="b022b-169">Clientes</span><span class="sxs-lookup"><span data-stu-id="b022b-169">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
