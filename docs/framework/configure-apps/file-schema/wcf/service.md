---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c12f57d68de870123d92c8a101e2999c24bb988f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855024"
---
# \<service>
<span data-ttu-id="d471d-101">O `service` elemento contém as configurações para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="d471d-101">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="d471d-102">Ele também contém pontos de extremidade que expõem o serviço.</span><span class="sxs-lookup"><span data-stu-id="d471d-102">It also contains endpoints that expose the service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**  
  
## <a name="syntax"></a><span data-ttu-id="d471d-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d471d-103">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d471d-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d471d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="d471d-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d471d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d471d-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="d471d-106">Attributes</span></span>  
  
|<span data-ttu-id="d471d-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="d471d-107">Attribute</span></span>|<span data-ttu-id="d471d-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d471d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d471d-109">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="d471d-109">behaviorConfiguration</span></span>|<span data-ttu-id="d471d-110">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="d471d-110">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="d471d-111">O nome do comportamento deve estar no escopo no ponto em que o serviço é definido.</span><span class="sxs-lookup"><span data-stu-id="d471d-111">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="d471d-112">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="d471d-112">The default value is an empty string.</span></span>|  
|<span data-ttu-id="d471d-113">name</span><span class="sxs-lookup"><span data-stu-id="d471d-113">name</span></span>|<span data-ttu-id="d471d-114">Atributo de cadeia de caracteres necessário que especifica o tipo de serviço a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="d471d-114">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="d471d-115">Essa configuração deve ser igual a um tipo válido.</span><span class="sxs-lookup"><span data-stu-id="d471d-115">This setting must equate to a valid type.</span></span> <span data-ttu-id="d471d-116">O formato deve ser`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="d471d-116">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d471d-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d471d-117">Child Elements</span></span>  
  
|<span data-ttu-id="d471d-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="d471d-118">Element</span></span>|<span data-ttu-id="d471d-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="d471d-119">Description</span></span>|  
|-------------|-----------------|  
|[\<endpoint>](endpoint-element.md)|<span data-ttu-id="d471d-120">Uma coleção de `endpoint` elementos que expõe este serviço.</span><span class="sxs-lookup"><span data-stu-id="d471d-120">A collection of `endpoint` elements that expose this service.</span></span>|  
|[\<host>](host.md)|<span data-ttu-id="d471d-121">Especifica o host dessa instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="d471d-121">Specifies the host of this service instance.</span></span> <span data-ttu-id="d471d-122">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HostElement> .</span><span class="sxs-lookup"><span data-stu-id="d471d-122">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d471d-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d471d-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d471d-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="d471d-124">Element</span></span>|<span data-ttu-id="d471d-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="d471d-125">Description</span></span>|  
|-------------|-----------------|  
|[\<services>](services.md)|<span data-ttu-id="d471d-126">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="d471d-126">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d471d-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="d471d-127">Remarks</span></span>  
 <span data-ttu-id="d471d-128">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d471d-128">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="d471d-129">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="d471d-129">An assembly can contain any number of services.</span></span> <span data-ttu-id="d471d-130">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="d471d-130">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="d471d-131">Esta seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="d471d-131">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="d471d-132">O `behaviorConfiguration` elemento também é opcional.</span><span class="sxs-lookup"><span data-stu-id="d471d-132">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="d471d-133">Ele identifica o comportamento usado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="d471d-133">It identifies the behavior the service uses.</span></span> <span data-ttu-id="d471d-134">O comportamento especificado neste atributo deve ser vinculado a um comportamento no escopo no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="d471d-134">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="d471d-135">Cada serviço expõe um ou mais pontos de extremidade, que tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="d471d-135">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="d471d-136">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="d471d-136">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="d471d-137">A associação é vinculada aos pontos de extremidade por meio da combinação dos atributos `name` e `bindingConfiguration` .</span><span class="sxs-lookup"><span data-stu-id="d471d-137">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="d471d-138">O `name` atributo descreve a seção em que a associação é definida.</span><span class="sxs-lookup"><span data-stu-id="d471d-138">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="d471d-139">O `bindingConfiguration` atributo define qual configuração dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="d471d-139">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="d471d-140">Uma seção de associação pode definir várias configurações.</span><span class="sxs-lookup"><span data-stu-id="d471d-140">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d471d-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d471d-141">Example</span></span>  
 <span data-ttu-id="d471d-142">Este é um exemplo de uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="d471d-142">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"
         name="HelloWorld">
  <endpoint address="/HelloWorld2/"
            name="test"
            bindingNamespace="http://www.cohowinery.com/"
            binding="basicHttpBinding"
            contract="IHelloWorld" />
</service>
```  
  
## <a name="see-also"></a><span data-ttu-id="d471d-143">Confira também</span><span class="sxs-lookup"><span data-stu-id="d471d-143">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="d471d-144">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="d471d-144">Configuring Services</span></span>](../../../wcf/configuring-services.md)
