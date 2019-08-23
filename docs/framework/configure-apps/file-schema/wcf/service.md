---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: 69f3c70514fc2bcab1b4ef6a45036de98d1af7b7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936519"
---
# <a name="service"></a><span data-ttu-id="b1a16-101">\<> de serviço</span><span class="sxs-lookup"><span data-stu-id="b1a16-101">\<service></span></span>
<span data-ttu-id="b1a16-102">O `service` elemento contém as configurações para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b1a16-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="b1a16-103">Ele também contém pontos de extremidade que expõem o serviço.</span><span class="sxs-lookup"><span data-stu-id="b1a16-103">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="b1a16-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b1a16-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b1a16-105">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="b1a16-105">\<services></span></span>  
<span data-ttu-id="b1a16-106">\<> de serviço</span><span class="sxs-lookup"><span data-stu-id="b1a16-106">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1a16-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1a16-107">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1a16-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1a16-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b1a16-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1a16-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1a16-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1a16-110">Attributes</span></span>  
  
|<span data-ttu-id="b1a16-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="b1a16-111">Attribute</span></span>|<span data-ttu-id="b1a16-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1a16-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1a16-113">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="b1a16-113">behaviorConfiguration</span></span>|<span data-ttu-id="b1a16-114">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="b1a16-114">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="b1a16-115">O nome do comportamento deve estar no escopo no ponto em que o serviço é definido.</span><span class="sxs-lookup"><span data-stu-id="b1a16-115">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="b1a16-116">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="b1a16-116">The default value is an empty string.</span></span>|  
|<span data-ttu-id="b1a16-117">name</span><span class="sxs-lookup"><span data-stu-id="b1a16-117">name</span></span>|<span data-ttu-id="b1a16-118">Atributo de cadeia de caracteres necessário que especifica o tipo de serviço a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="b1a16-118">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="b1a16-119">Essa configuração deve ser igual a um tipo válido.</span><span class="sxs-lookup"><span data-stu-id="b1a16-119">This setting must equate to a valid type.</span></span> <span data-ttu-id="b1a16-120">O formato deve ser`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="b1a16-120">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1a16-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1a16-121">Child Elements</span></span>  
  
|<span data-ttu-id="b1a16-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1a16-122">Element</span></span>|<span data-ttu-id="b1a16-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1a16-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1a16-124">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="b1a16-124">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="b1a16-125">Uma coleção de `endpoint` elementos que expõe este serviço.</span><span class="sxs-lookup"><span data-stu-id="b1a16-125">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="b1a16-126">\<host></span><span class="sxs-lookup"><span data-stu-id="b1a16-126">\<host></span></span>](host.md)|<span data-ttu-id="b1a16-127">Especifica o host dessa instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="b1a16-127">Specifies the host of this service instance.</span></span> <span data-ttu-id="b1a16-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="b1a16-128">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1a16-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1a16-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b1a16-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1a16-130">Element</span></span>|<span data-ttu-id="b1a16-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1a16-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1a16-132">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="b1a16-132">\<services></span></span>](services.md)|<span data-ttu-id="b1a16-133">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="b1a16-133">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1a16-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1a16-134">Remarks</span></span>  
 <span data-ttu-id="b1a16-135">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1a16-135">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="b1a16-136">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="b1a16-136">An assembly can contain any number of services.</span></span> <span data-ttu-id="b1a16-137">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1a16-137">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="b1a16-138">Esta seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="b1a16-138">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="b1a16-139">O `behaviorConfiguration` elemento também é opcional.</span><span class="sxs-lookup"><span data-stu-id="b1a16-139">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="b1a16-140">Ele identifica o comportamento usado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="b1a16-140">It identifies the behavior the service uses.</span></span> <span data-ttu-id="b1a16-141">O comportamento especificado neste atributo deve ser vinculado a um comportamento no escopo no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="b1a16-141">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="b1a16-142">Cada serviço expõe um ou mais pontos de extremidade, que tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="b1a16-142">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="b1a16-143">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="b1a16-143">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="b1a16-144">A associação é vinculada aos pontos de extremidade por meio da combinação `name` dos `bindingConfiguration`atributos e.</span><span class="sxs-lookup"><span data-stu-id="b1a16-144">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="b1a16-145">O `name` atributo descreve a seção em que a associação é definida.</span><span class="sxs-lookup"><span data-stu-id="b1a16-145">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="b1a16-146">O `bindingConfiguration` atributo define qual configuração dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="b1a16-146">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="b1a16-147">Uma seção de associação pode definir várias configurações.</span><span class="sxs-lookup"><span data-stu-id="b1a16-147">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1a16-148">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1a16-148">Example</span></span>  
 <span data-ttu-id="b1a16-149">Este é um exemplo de uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="b1a16-149">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b1a16-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b1a16-150">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="b1a16-151">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="b1a16-151">Configuring Services</span></span>](../../../wcf/configuring-services.md)
