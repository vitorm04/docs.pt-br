---
title: <service>
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: c12f57d68de870123d92c8a101e2999c24bb988f
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855024"
---
# <a name="service"></a><span data-ttu-id="789f7-101">\<> de serviço</span><span class="sxs-lookup"><span data-stu-id="789f7-101">\<service></span></span>
<span data-ttu-id="789f7-102">O `service` elemento contém as configurações para um serviço Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="789f7-102">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="789f7-103">Ele também contém pontos de extremidade que expõem o serviço.</span><span class="sxs-lookup"><span data-stu-id="789f7-103">It also contains endpoints that expose the service.</span></span>  
  
<span data-ttu-id="789f7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="789f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="789f7-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="789f7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="789f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Serviços >** ](services.md)</span><span class="sxs-lookup"><span data-stu-id="789f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<services>**](services.md)</span></span>\
<span data-ttu-id="789f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de serviço**</span><span class="sxs-lookup"><span data-stu-id="789f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<service>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="789f7-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="789f7-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration="String"
         name="String">
</service>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="789f7-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="789f7-109">Attributes and Elements</span></span>  
 <span data-ttu-id="789f7-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="789f7-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="789f7-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="789f7-111">Attributes</span></span>  
  
|<span data-ttu-id="789f7-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="789f7-112">Attribute</span></span>|<span data-ttu-id="789f7-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="789f7-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="789f7-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="789f7-114">behaviorConfiguration</span></span>|<span data-ttu-id="789f7-115">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="789f7-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="789f7-116">O nome do comportamento deve estar no escopo no ponto em que o serviço é definido.</span><span class="sxs-lookup"><span data-stu-id="789f7-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="789f7-117">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="789f7-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="789f7-118">name</span><span class="sxs-lookup"><span data-stu-id="789f7-118">name</span></span>|<span data-ttu-id="789f7-119">Atributo de cadeia de caracteres necessário que especifica o tipo de serviço a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="789f7-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="789f7-120">Essa configuração deve ser igual a um tipo válido.</span><span class="sxs-lookup"><span data-stu-id="789f7-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="789f7-121">O formato deve ser`Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="789f7-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="789f7-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="789f7-122">Child Elements</span></span>  
  
|<span data-ttu-id="789f7-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="789f7-123">Element</span></span>|<span data-ttu-id="789f7-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="789f7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="789f7-125">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="789f7-125">\<endpoint></span></span>](endpoint-element.md)|<span data-ttu-id="789f7-126">Uma coleção de `endpoint` elementos que expõe este serviço.</span><span class="sxs-lookup"><span data-stu-id="789f7-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="789f7-127">\<host></span><span class="sxs-lookup"><span data-stu-id="789f7-127">\<host></span></span>](host.md)|<span data-ttu-id="789f7-128">Especifica o host dessa instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="789f7-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="789f7-129">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="789f7-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="789f7-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="789f7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="789f7-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="789f7-131">Element</span></span>|<span data-ttu-id="789f7-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="789f7-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="789f7-133">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="789f7-133">\<services></span></span>](services.md)|<span data-ttu-id="789f7-134">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="789f7-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="789f7-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="789f7-135">Remarks</span></span>  
 <span data-ttu-id="789f7-136">Os serviços são definidos na `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="789f7-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="789f7-137">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="789f7-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="789f7-138">Cada serviço tem sua própria `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="789f7-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="789f7-139">Esta seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço específico.</span><span class="sxs-lookup"><span data-stu-id="789f7-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="789f7-140">O `behaviorConfiguration` elemento também é opcional.</span><span class="sxs-lookup"><span data-stu-id="789f7-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="789f7-141">Ele identifica o comportamento usado pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="789f7-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="789f7-142">O comportamento especificado neste atributo deve ser vinculado a um comportamento no escopo no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="789f7-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="789f7-143">Cada serviço expõe um ou mais pontos de extremidade, que tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="789f7-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="789f7-144">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="789f7-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="789f7-145">A associação é vinculada aos pontos de extremidade por meio da combinação `name` dos `bindingConfiguration`atributos e.</span><span class="sxs-lookup"><span data-stu-id="789f7-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="789f7-146">O `name` atributo descreve a seção em que a associação é definida.</span><span class="sxs-lookup"><span data-stu-id="789f7-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="789f7-147">O `bindingConfiguration` atributo define qual configuração dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="789f7-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="789f7-148">Uma seção de associação pode definir várias configurações.</span><span class="sxs-lookup"><span data-stu-id="789f7-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="789f7-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="789f7-149">Example</span></span>  
 <span data-ttu-id="789f7-150">Este é um exemplo de uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="789f7-150">This is an example of a service configuration.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="789f7-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="789f7-151">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceElement>
- [<span data-ttu-id="789f7-152">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="789f7-152">Configuring Services</span></span>](../../../wcf/configuring-services.md)
