---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 0996a98438dc344d96d640abced52ac99709adbf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936681"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="fc00e-102">\<> de segurança \<do NetNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="fc00e-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="fc00e-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="fc00e-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="fc00e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fc00e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fc00e-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="fc00e-105">\<bindings></span></span>  
<span data-ttu-id="fc00e-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="fc00e-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="fc00e-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="fc00e-107">\<binding></span></span>  
<span data-ttu-id="fc00e-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="fc00e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc00e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fc00e-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fc00e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fc00e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fc00e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fc00e-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fc00e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="fc00e-112">Attributes</span></span>  
  
|<span data-ttu-id="fc00e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="fc00e-113">Attribute</span></span>|<span data-ttu-id="fc00e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc00e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fc00e-115">modo</span><span class="sxs-lookup"><span data-stu-id="fc00e-115">mode</span></span>|<span data-ttu-id="fc00e-116">Especifica o tipo de segurança que é aplicado a essa associação.</span><span class="sxs-lookup"><span data-stu-id="fc00e-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="fc00e-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fc00e-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="fc00e-118">None Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="fc00e-118">-   None: This disables security.</span></span><br /><span data-ttu-id="fc00e-119">Porta A segurança é fornecida usando a segurança baseada em transporte subjacente.</span><span class="sxs-lookup"><span data-stu-id="fc00e-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="fc00e-120">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="fc00e-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="fc00e-121">-O valor padrão é transporte.</span><span class="sxs-lookup"><span data-stu-id="fc00e-121">-   The default value is Transport.</span></span> <span data-ttu-id="fc00e-122">Esse atributo é do tipo <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="fc00e-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fc00e-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fc00e-123">Child Elements</span></span>  
  
|<span data-ttu-id="fc00e-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc00e-124">Element</span></span>|<span data-ttu-id="fc00e-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc00e-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc00e-126">transporte</span><span class="sxs-lookup"><span data-stu-id="fc00e-126">transport</span></span>|<span data-ttu-id="fc00e-127">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="fc00e-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="fc00e-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="fc00e-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fc00e-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fc00e-129">Parent Elements</span></span>  
  
|<span data-ttu-id="fc00e-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="fc00e-130">Element</span></span>|<span data-ttu-id="fc00e-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="fc00e-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc00e-132">associação</span><span class="sxs-lookup"><span data-stu-id="fc00e-132">binding</span></span>|<span data-ttu-id="fc00e-133">O elemento Binding da [ \<> NetNamedPipeBinding](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="fc00e-133">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc00e-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc00e-134">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="fc00e-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="fc00e-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="fc00e-136">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="fc00e-136">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="fc00e-137">Associações</span><span class="sxs-lookup"><span data-stu-id="fc00e-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="fc00e-138">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="fc00e-138">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="fc00e-139">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="fc00e-139">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="fc00e-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="fc00e-140">\<binding></span></span>](../../../misc/binding.md)
