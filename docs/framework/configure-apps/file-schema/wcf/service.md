---
title: '&lt;Serviço&gt;'
ms.date: 03/30/2017
ms.assetid: 13123dd6-c4a9-4a04-a984-df184b851788
ms.openlocfilehash: a73e4699e0998338f09e1ed0504f5b1cfd73b225
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicegt"></a><span data-ttu-id="476cf-102">&lt;Serviço&gt;</span><span class="sxs-lookup"><span data-stu-id="476cf-102">&lt;service&gt;</span></span>
<span data-ttu-id="476cf-103">O `service` elemento contém as configurações para um serviço do Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="476cf-103">The `service` element contains the settings for a Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="476cf-104">Ele também contém pontos de extremidade que expõem o serviço.</span><span class="sxs-lookup"><span data-stu-id="476cf-104">It also contains endpoints that expose the service.</span></span>  
  
 <span data-ttu-id="476cf-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="476cf-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="476cf-106">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="476cf-106">\<services></span></span>  
<span data-ttu-id="476cf-107">\<serviço ></span><span class="sxs-lookup"><span data-stu-id="476cf-107">\<service></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="476cf-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="476cf-108">Syntax</span></span>  
  
```xml  
<service behaviorConfiguration=String"  
        name="String"  
</service>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="476cf-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="476cf-109">Attributes and Elements</span></span>  
 <span data-ttu-id="476cf-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="476cf-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="476cf-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="476cf-111">Attributes</span></span>  
  
|<span data-ttu-id="476cf-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="476cf-112">Attribute</span></span>|<span data-ttu-id="476cf-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="476cf-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="476cf-114">behaviorConfiguration</span><span class="sxs-lookup"><span data-stu-id="476cf-114">behaviorConfiguration</span></span>|<span data-ttu-id="476cf-115">Uma cadeia de caracteres que contém o nome do comportamento do comportamento a ser usado para instanciar o serviço.</span><span class="sxs-lookup"><span data-stu-id="476cf-115">A string that contains the behavior name of the behavior to be used to instantiate the service.</span></span> <span data-ttu-id="476cf-116">O nome do comportamento deve estar no escopo no ponto em que o serviço está definido.</span><span class="sxs-lookup"><span data-stu-id="476cf-116">The behavior name must be in scope at the point the service is defined.</span></span> <span data-ttu-id="476cf-117">O valor padrão é uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="476cf-117">The default value is an empty string.</span></span>|  
|<span data-ttu-id="476cf-118">name</span><span class="sxs-lookup"><span data-stu-id="476cf-118">name</span></span>|<span data-ttu-id="476cf-119">Necessário um atributo de cadeia de caracteres que especifica o tipo de serviço a ser instanciado.</span><span class="sxs-lookup"><span data-stu-id="476cf-119">Required String attribute that specifies the type of the service to be instantiated.</span></span> <span data-ttu-id="476cf-120">Essa configuração deve serão iguais a um tipo válido.</span><span class="sxs-lookup"><span data-stu-id="476cf-120">This setting must equate to a valid type.</span></span> <span data-ttu-id="476cf-121">O formato deve ser `Namespace.Class.`</span><span class="sxs-lookup"><span data-stu-id="476cf-121">The format should be `Namespace.Class.`</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="476cf-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="476cf-122">Child Elements</span></span>  
  
|<span data-ttu-id="476cf-123">Elemento</span><span class="sxs-lookup"><span data-stu-id="476cf-123">Element</span></span>|<span data-ttu-id="476cf-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="476cf-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="476cf-125">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="476cf-125">\<endpoint></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpoint-element.md)|<span data-ttu-id="476cf-126">Uma coleção de `endpoint` elementos que expõem este serviço.</span><span class="sxs-lookup"><span data-stu-id="476cf-126">A collection of `endpoint` elements that expose this service.</span></span>|  
|[<span data-ttu-id="476cf-127">\<host ></span><span class="sxs-lookup"><span data-stu-id="476cf-127">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="476cf-128">Especifica o host desta instância de serviço.</span><span class="sxs-lookup"><span data-stu-id="476cf-128">Specifies the host of this service instance.</span></span> <span data-ttu-id="476cf-129">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.HostElement>.</span><span class="sxs-lookup"><span data-stu-id="476cf-129">This element is of type <xref:System.ServiceModel.Configuration.HostElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="476cf-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="476cf-130">Parent Elements</span></span>  
  
|<span data-ttu-id="476cf-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="476cf-131">Element</span></span>|<span data-ttu-id="476cf-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="476cf-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="476cf-133">\<Serviços ></span><span class="sxs-lookup"><span data-stu-id="476cf-133">\<services></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md)|<span data-ttu-id="476cf-134">O elemento raiz de todos os elementos de configuração do WCF.</span><span class="sxs-lookup"><span data-stu-id="476cf-134">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="476cf-135">Comentários</span><span class="sxs-lookup"><span data-stu-id="476cf-135">Remarks</span></span>  
 <span data-ttu-id="476cf-136">Os serviços são definidos no `services` seção do arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="476cf-136">Services are defined in the `services` section of the configuration file.</span></span> <span data-ttu-id="476cf-137">Um assembly pode conter qualquer número de serviços.</span><span class="sxs-lookup"><span data-stu-id="476cf-137">An assembly can contain any number of services.</span></span> <span data-ttu-id="476cf-138">Cada serviço tem seu próprio `service` seção de configuração.</span><span class="sxs-lookup"><span data-stu-id="476cf-138">Each service has its own `service` configuration section.</span></span> <span data-ttu-id="476cf-139">Esta seção e seu conteúdo definem o contrato de serviço, o comportamento e os pontos de extremidade do serviço em questão.</span><span class="sxs-lookup"><span data-stu-id="476cf-139">This section and its content define the service contract, behavior, and endpoints of the particular service.</span></span>  
  
 <span data-ttu-id="476cf-140">O `behaviorConfiguration` elemento também é opcional.</span><span class="sxs-lookup"><span data-stu-id="476cf-140">The `behaviorConfiguration` element is also optional.</span></span> <span data-ttu-id="476cf-141">Ele identifica o comportamento de serviço usa.</span><span class="sxs-lookup"><span data-stu-id="476cf-141">It identifies the behavior the service uses.</span></span> <span data-ttu-id="476cf-142">O comportamento especificado neste atributo deve vincular a um comportamento no escopo no mesmo arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="476cf-142">The behavior specified in this attribute must link to a behavior in scope in the same configuration file.</span></span>  
  
 <span data-ttu-id="476cf-143">Cada serviço expõe um ou mais pontos de extremidade, que tem seu próprio endereço e associação.</span><span class="sxs-lookup"><span data-stu-id="476cf-143">Each service exposes one or more endpoints, which has its own address and binding.</span></span> <span data-ttu-id="476cf-144">Todas as associações usadas no arquivo de configuração devem ser definidas no escopo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="476cf-144">All bindings used within the configuration file must be defined in the scope of the file.</span></span> <span data-ttu-id="476cf-145">Associação são vinculados aos pontos de extremidade pela combinação dos atributos `name` e `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="476cf-145">Binding are linked to endpoints through the combination of the attributes `name` and `bindingConfiguration`.</span></span> <span data-ttu-id="476cf-146">O `name` atributo descreve a seção a associação é definida no.</span><span class="sxs-lookup"><span data-stu-id="476cf-146">The `name` attribute describes the section the binding is defined in.</span></span> <span data-ttu-id="476cf-147">O `bindingConfiguration` atributo define qual configuração dentro da seção de associação é usada.</span><span class="sxs-lookup"><span data-stu-id="476cf-147">The `bindingConfiguration` attribute defines which configuration within the binding section is used.</span></span> <span data-ttu-id="476cf-148">Uma seção de associação pode definir várias configurações.</span><span class="sxs-lookup"><span data-stu-id="476cf-148">A binding section can define several configurations.</span></span>  
  
## <a name="example"></a><span data-ttu-id="476cf-149">Exemplo</span><span class="sxs-lookup"><span data-stu-id="476cf-149">Example</span></span>  
 <span data-ttu-id="476cf-150">Este é um exemplo de uma configuração de serviço.</span><span class="sxs-lookup"><span data-stu-id="476cf-150">This is an example of a service configuration.</span></span>  
  
```xml  
<service behaviorConfiguration="testChannelBehavior"   
     name="HelloWorld">  
     <endpoint   
        address="/HelloWorld2/"  
        name="test"  
        bindingNamespace="http://www.cohowinery.com/"  
        binding="basicHttpBinding"  
        contract="IHelloWorld" />  
</service>  
```  
  
## <a name="see-also"></a><span data-ttu-id="476cf-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="476cf-151">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceElement>  
 [<span data-ttu-id="476cf-152">Configurando serviços</span><span class="sxs-lookup"><span data-stu-id="476cf-152">Configuring Services</span></span>](../../../../../docs/framework/wcf/configuring-services.md)
