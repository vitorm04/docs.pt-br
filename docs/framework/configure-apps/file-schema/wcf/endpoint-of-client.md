---
title: <endpoint> de <client>
ms.date: 03/30/2017
ms.assetid: de6238ae-bbf8-48e9-a1b5-e24c0bea8afa
ms.openlocfilehash: f1ffbc1e8efac70523d7f631c8cf9ba9a1622bfc
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855322"
---
# <a name="endpoint-of-client"></a><span data-ttu-id="be88f-102">\<> de ponto \<de extremidade do cliente ></span><span class="sxs-lookup"><span data-stu-id="be88f-102">\<endpoint> of \<client></span></span>
<span data-ttu-id="be88f-103">Especifica o contrato, a associação e as propriedades de endereço do ponto de extremidade do canal, que é usado pelos clientes para se conectar a pontos de extremidades de serviço no servidor.</span><span class="sxs-lookup"><span data-stu-id="be88f-103">Specifies contract, binding, and address properties of the channel endpoint, which is used by clients to connect to service endpoints on the server.</span></span>  
  
<span data-ttu-id="be88f-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="be88f-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="be88f-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="be88f-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="be88f-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> do cliente**](client.md)</span><span class="sxs-lookup"><span data-stu-id="be88f-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)</span></span>\
<span data-ttu-id="be88f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> do ponto de extremidade**</span><span class="sxs-lookup"><span data-stu-id="be88f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<endpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be88f-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="be88f-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="be88f-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="be88f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="be88f-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="be88f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="be88f-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="be88f-111">Attributes</span></span>  
  
|<span data-ttu-id="be88f-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="be88f-112">Attribute</span></span>|<span data-ttu-id="be88f-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="be88f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="be88f-114">endereço</span><span class="sxs-lookup"><span data-stu-id="be88f-114">address</span></span>|<span data-ttu-id="be88f-115">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="be88f-115">Required string attribute.</span></span><br /><br /> <span data-ttu-id="be88f-116">Especifica o endereço do ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="be88f-116">Specifies the address of the endpoint.</span></span> <span data-ttu-id="be88f-117">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="be88f-117">The default is an empty string.</span></span> <span data-ttu-id="be88f-118">O endereço deve ser um URI absoluto.</span><span class="sxs-lookup"><span data-stu-id="be88f-118">The address must be an absolute URI.</span></span>|  
|<span data-ttu-id="be88f-119">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="be88f-119">behaviorConfiguration</span></span>|<span data-ttu-id="be88f-120">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="be88f-120">A string that contains the behavior name of the behavior to be used to instantiate the endpoint.</span></span> <span data-ttu-id="be88f-121">O nome do comportamento deve estar no escopo no ponto em que o serviço é definido.</span><span class="sxs-lookup"><span data-stu-id="be88f-121">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="be88f-122">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="be88f-122">The default is an empty string.</span></span>|  
|<span data-ttu-id="be88f-123">associação</span><span class="sxs-lookup"><span data-stu-id="be88f-123">binding</span></span>|<span data-ttu-id="be88f-124">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="be88f-124">Required string attribute.</span></span><br /><br /> <span data-ttu-id="be88f-125">Uma cadeia de caracteres que indica o tipo de associação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="be88f-125">A string that indicates the type of binding to use.</span></span> <span data-ttu-id="be88f-126">O tipo deve ter uma seção de configuração registrada para ser referenciado.</span><span class="sxs-lookup"><span data-stu-id="be88f-126">The type must have a registered configuration section in order to be referenced.</span></span> <span data-ttu-id="be88f-127">O tipo é registrado pelo nome da seção, em vez de pelo nome do tipo da associação.</span><span class="sxs-lookup"><span data-stu-id="be88f-127">The type is registered by section name, instead of by the type name of the binding.</span></span>|  
|<span data-ttu-id="be88f-128">bindingConfiguration</span><span class="sxs-lookup"><span data-stu-id="be88f-128">bindingConfiguration</span></span>|<span data-ttu-id="be88f-129">Opcional.</span><span class="sxs-lookup"><span data-stu-id="be88f-129">Optional.</span></span> <span data-ttu-id="be88f-130">Uma cadeia de caracteres que contém o nome da configuração de associação a ser usada quando o ponto de extremidade é instanciado.</span><span class="sxs-lookup"><span data-stu-id="be88f-130">A string that contains the name of the binding configuration to be used when the endpoint is instantiated.</span></span> <span data-ttu-id="be88f-131">A configuração de associação deve estar no escopo no ponto em que o ponto de extremidade é definido.</span><span class="sxs-lookup"><span data-stu-id="be88f-131">The binding configuration must be in scope at the point the endpoint is defined.</span></span> <span data-ttu-id="be88f-132">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="be88f-132">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="be88f-133">Esse atributo é usado em conjunto com `binding` para fazer referência a uma configuração de associação específica no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="be88f-133">This attribute is used in conjunction with `binding` to reference a specific binding configuration in the configuration file.</span></span> <span data-ttu-id="be88f-134">Defina esse atributo se você estiver tentando usar uma associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="be88f-134">Set this attribute if you are attempting to use a custom binding.</span></span> <span data-ttu-id="be88f-135">Caso contrário, uma exceção pode ser lançada.</span><span class="sxs-lookup"><span data-stu-id="be88f-135">Otherwise, an exception may be thrown.</span></span>|  
|<span data-ttu-id="be88f-136">contrato</span><span class="sxs-lookup"><span data-stu-id="be88f-136">contract</span></span>|<span data-ttu-id="be88f-137">Atributo de cadeia de caracteres obrigatório.</span><span class="sxs-lookup"><span data-stu-id="be88f-137">Required string attribute.</span></span><br /><br /> <span data-ttu-id="be88f-138">Uma cadeia de caracteres que indica qual contrato este ponto de extremidade está expondo.</span><span class="sxs-lookup"><span data-stu-id="be88f-138">A string that indicates which contract this endpoint is exposing.</span></span> <span data-ttu-id="be88f-139">O assembly deve implementar o tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="be88f-139">The assembly must implement the contract type.</span></span>|  
|<span data-ttu-id="be88f-140">endpointConfiguration</span><span class="sxs-lookup"><span data-stu-id="be88f-140">endpointConfiguration</span></span>|<span data-ttu-id="be88f-141">Uma cadeia de caracteres que especifica o nome do ponto de extremidade padrão que é `kind` definido pelo atributo, que faz referência às informações de configuração adicionais desse ponto de extremidade padrão.</span><span class="sxs-lookup"><span data-stu-id="be88f-141">A string that specifies the name of the standard endpoint that is set by the `kind` attribute, which references to the additional configuration information of this standard endpoint.</span></span> <span data-ttu-id="be88f-142">O mesmo nome deve ser definido na `<standardEndpoints>` seção.</span><span class="sxs-lookup"><span data-stu-id="be88f-142">The same name must be defined in the `<standardEndpoints>` section.</span></span>|  
|<span data-ttu-id="be88f-143">Quase</span><span class="sxs-lookup"><span data-stu-id="be88f-143">kind</span></span>|<span data-ttu-id="be88f-144">Uma cadeia de caracteres que especifica o tipo de ponto de extremidade padrão aplicado.</span><span class="sxs-lookup"><span data-stu-id="be88f-144">A string that specifies the type of standard endpoint applied.</span></span> <span data-ttu-id="be88f-145">O tipo deve ser registrado na seção `<extensions>` ou em machine.config. Se nada for especificado, um ponto de extremidade de canal comum será criado.</span><span class="sxs-lookup"><span data-stu-id="be88f-145">The type must be registered in the `<extensions>` section or in machine.config. If nothing is specified, a common channel endpoint is created.</span></span>|  
|<span data-ttu-id="be88f-146">name</span><span class="sxs-lookup"><span data-stu-id="be88f-146">name</span></span>|<span data-ttu-id="be88f-147">Atributo de cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="be88f-147">Optional string attribute.</span></span> <span data-ttu-id="be88f-148">Esse atributo identifica exclusivamente um ponto de extremidade para um determinado contrato.</span><span class="sxs-lookup"><span data-stu-id="be88f-148">This attribute uniquely identifies an endpoint for a given contract.</span></span> <span data-ttu-id="be88f-149">Você pode definir vários clientes para um determinado tipo de contrato.</span><span class="sxs-lookup"><span data-stu-id="be88f-149">You can define multiple clients for a given Contract type.</span></span> <span data-ttu-id="be88f-150">Cada definição deve ser diferenciada por um nome de configuração exclusivo.</span><span class="sxs-lookup"><span data-stu-id="be88f-150">Each definition must be differentiated by a unique configuration name.</span></span> <span data-ttu-id="be88f-151">Se esse atributo for omitido, o ponto de extremidade correspondente será usado como o ponto de extremidade padrão associado ao tipo de contrato especificado.</span><span class="sxs-lookup"><span data-stu-id="be88f-151">If this attribute is omitted, the corresponding endpoint is used as the default endpoint associated with the specified Contract type.</span></span> <span data-ttu-id="be88f-152">O padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="be88f-152">The default is an empty string.</span></span><br /><br /> <span data-ttu-id="be88f-153">O `name` atributo de uma associação é usado para exportação de definição por meio de WSDL.</span><span class="sxs-lookup"><span data-stu-id="be88f-153">The `name` attribute of a binding is used for definition export through WSDL.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="be88f-154">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="be88f-154">Child Elements</span></span>  
  
|<span data-ttu-id="be88f-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="be88f-155">Element</span></span>|<span data-ttu-id="be88f-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="be88f-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be88f-157">\<headers></span><span class="sxs-lookup"><span data-stu-id="be88f-157">\<headers></span></span>](headers.md)|<span data-ttu-id="be88f-158">Uma coleção de cabeçalhos de endereço.</span><span class="sxs-lookup"><span data-stu-id="be88f-158">A collection of address headers.</span></span>|  
|[<span data-ttu-id="be88f-159">\<identity></span><span class="sxs-lookup"><span data-stu-id="be88f-159">\<identity></span></span>](identity.md)|<span data-ttu-id="be88f-160">Uma identidade que permite a autenticação de um ponto de extremidade por outros pontos de extremidades que trocam mensagens com ele.</span><span class="sxs-lookup"><span data-stu-id="be88f-160">An identity that enables the authentication of an endpoint by other endpoints exchanging messages with it.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="be88f-161">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="be88f-161">Parent Elements</span></span>  
  
|<span data-ttu-id="be88f-162">Elemento</span><span class="sxs-lookup"><span data-stu-id="be88f-162">Element</span></span>|<span data-ttu-id="be88f-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="be88f-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="be88f-164">\<client></span><span class="sxs-lookup"><span data-stu-id="be88f-164">\<client></span></span>](client.md)|<span data-ttu-id="be88f-165">Uma seção de configuração que define uma lista de pontos de extremidade aos quais um cliente pode se conectar.</span><span class="sxs-lookup"><span data-stu-id="be88f-165">A configuration section that defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="be88f-166">Exemplo</span><span class="sxs-lookup"><span data-stu-id="be88f-166">Example</span></span>  
 <span data-ttu-id="be88f-167">Este é um exemplo de uma configuração de ponto de extremidade de canal.</span><span class="sxs-lookup"><span data-stu-id="be88f-167">This is an example of a channel endpoint configuration.</span></span>  
  
```xml  
<endpoint address="/HelloWorld/"
          bindingConfiguration="usingDefaults"
          name="MyBinding"
          binding="customBinding"
          contract="HelloWorld">
</endpoint>
```  
  
## <a name="see-also"></a><span data-ttu-id="be88f-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="be88f-168">See also</span></span>

- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- <xref:System.ServiceModel.Configuration.ClientSection>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElementCollection>
- <xref:System.ServiceModel.Configuration.ClientSection.Endpoints%2A>
- <xref:System.ServiceModel.Configuration.ChannelEndpointElement>
- [<span data-ttu-id="be88f-169">Configuração de cliente do WCF</span><span class="sxs-lookup"><span data-stu-id="be88f-169">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="be88f-170">Clientes</span><span class="sxs-lookup"><span data-stu-id="be88f-170">Clients</span></span>](../../../wcf/feature-details/clients.md)
