---
title: <endpoint> de <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855322"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="98ea8-102">\<endpoint> de \<client></span><span class="sxs-lookup"><span data-stu-id="98ea8-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="98ea8-103">Especifica o contrato, a associação e as propriedades de endereço do ponto de extremidade do canal, que é usado pelos clientes para se conectar a pontos de extremidades de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="98ea8-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="98ea8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="98ea8-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98ea8-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="98ea8-105">Attributes and Elements</span></span>  
 <span data-ttu-id="98ea8-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="98ea8-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98ea8-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="98ea8-107">Attributes</span></span>  
  
|<span data-ttu-id="98ea8-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="98ea8-108">Attribute</span></span>|<span data-ttu-id="98ea8-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="98ea8-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="98ea8-110">address</span><span class="sxs-lookup"><span data-stu-id="98ea8-110">address</span></span>|<span data-ttu-id="98ea8-111">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="98ea8-111">Required string attribute.</span></span><br /><br /> <span data-ttu-id="98ea8-112">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="98ea8-112">Specifies the address of the endpoint.</span></span> <span data-ttu-id="98ea8-113">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="98ea8-113">The default is an empty string.</span></span> <span data-ttu-id="98ea8-114">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="98ea8-114">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="98ea8-115">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="98ea8-115">behaviorConfiguration</span></span>|<span data-ttu-id="98ea8-116">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="98ea8-116">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="98ea8-117">O nome do comportamento deve estar no escopo no ponto em que o serviço é definido.</span><span class="sxs-lookup"><span data-stu-id="98ea8-117">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="98ea8-118">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="98ea8-118">The default is an empty string.</span></span>|  
|<span data-ttu-id="98ea8-119">associação</span><span class="sxs-lookup"><span data-stu-id="98ea8-119">binding</span></span>|<span data-ttu-id="98ea8-120">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="98ea8-120">Required string attribute.</span></span><br /><br /> <span data-ttu-id="98ea8-121">Uma cadeia de caracteres que indica o tipo de associação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="98ea8-121">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="98ea8-122">O tipo deve ter uma seção de configuração registrada para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="98ea8-122">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="98ea8-123">O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo da associação.</span><span class="sxs-lookup"><span data-stu-id="98ea8-123">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="98ea8-124">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="98ea8-124">bindingConfiguration</span></span>|<span data-ttu-id="98ea8-125">Opcional.</span><span class="sxs-lookup"><span data-stu-id="98ea8-125">Optional.</span></span> <span data-ttu-id="98ea8-126">Uma cadeia de caracteres que contém o nome da configuração de associação a ser usada quando o ponto de extremidade é instanciado.</span><span class="sxs-lookup"><span data-stu-id="98ea8-126">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="98ea8-127">A configuração de associação deve estar no escopo no ponto em que o ponto de extremidade é definido.</span><span class="sxs-lookup"><span data-stu-id="98ea8-127">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="98ea8-128">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="98ea8-128">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="98ea8-129">Esse atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="98ea8-129">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="98ea8-130">Defina esse atributo se você estiver tentando usar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="98ea8-130">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="98ea8-131">Caso contrário, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="98ea8-131">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="98ea8-132">contrato</span><span class="sxs-lookup"><span data-stu-id="98ea8-132">contract</span></span>|<span data-ttu-id="98ea8-133">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="98ea8-133">Required string attribute.</span></span><br /><br /> <span data-ttu-id="98ea8-134">Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="98ea8-134">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="98ea8-135">O assembly deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="98ea8-135">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="98ea8-136">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="98ea8-136">endpointConfiguration</span></span>|<span data-ttu-id="98ea8-137">Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é definido pelo `kind` atributo, que faz referência às informações de configuração adicionais desse ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="98ea8-137">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="98ea8-138">O mesmo nome deve ser definido na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="98ea8-138">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="98ea8-139">kind</span><span class="sxs-lookup"><span data-stu-id="98ea8-139">kind</span></span>|<span data-ttu-id="98ea8-140">Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado.</span><span class="sxs-lookup"><span data-stu-id="98ea8-140">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="98ea8-141">O tipo deve ser registrado na `<extensions>` seção ou em Machine. config. Se nada for especificado, um ponto de extremidade de canal comum será criado.</span><span class="sxs-lookup"><span data-stu-id="98ea8-141">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="98ea8-142">name</span><span class="sxs-lookup"><span data-stu-id="98ea8-142">name</span></span>|<span data-ttu-id="98ea8-143">Atributo de cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="98ea8-143">Optional string attribute.</span></span> <span data-ttu-id="98ea8-144">Esse atributo identifica exclusivamente um ponto de extremidade para um determinado contrato.</span><span class="sxs-lookup"><span data-stu-id="98ea8-144">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="98ea8-145">Você pode definir vários clientes para um determinado tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="98ea8-145">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="98ea8-146">Cada definição deve ser diferenciada por um nome de configuração exclusivo.</span><span class="sxs-lookup"><span data-stu-id="98ea8-146">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="98ea8-147">Se esse atributo for omitido, o ponto de extremidade correspondente será usado como o ponto de extremidade padrão associado ao tipo de contrato especificado.</span><span class="sxs-lookup"><span data-stu-id="98ea8-147">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="98ea8-148">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="98ea8-148">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="98ea8-149">O `name` atributo de uma associação é usado para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="98ea8-149">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98ea8-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="98ea8-150">Child Elements</span></span>  
  
|<span data-ttu-id="98ea8-151">Elemento</span><span class="sxs-lookup"><span data-stu-id="98ea8-151">Element</span></span>|<span data-ttu-id="98ea8-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="98ea8-152">Description</span></span>|  
|-------------|-----------------|  
|[\<headers>](headers.md)|<span data-ttu-id="98ea8-153">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="98ea8-153">A collection of address headers.</span></span>|  
|[\<identity>](identity.md)|<span data-ttu-id="98ea8-154">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="98ea8-154">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="98ea8-155">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="98ea8-155">Parent Elements</span></span>  
  
|<span data-ttu-id="98ea8-156">Elemento</span><span class="sxs-lookup"><span data-stu-id="98ea8-156">Element</span></span>|<span data-ttu-id="98ea8-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="98ea8-157">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="98ea8-158">Uma seção de configuração que define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="98ea8-158">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="98ea8-159">Exemplo</span><span class="sxs-lookup"><span data-stu-id="98ea8-159">Example</span></span>  
 <span data-ttu-id="98ea8-160">Este é um exemplo de uma configuração de ponto de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="98ea8-160">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="98ea8-161">Confira também</span><span class="sxs-lookup"><span data-stu-id="98ea8-161">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="98ea8-162">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="98ea8-162">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="98ea8-163">Clientes</span><span class="sxs-lookup"><span data-stu-id="98ea8-163">Clients</span></span>](../../../wcf/feature-details/clients.md)
