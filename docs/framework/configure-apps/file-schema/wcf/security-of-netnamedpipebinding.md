---
title: <security> de <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
ms.openlocfilehash: 31ea31ce6880a770c966350cd931e487396c4d63
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736439"
---
# <a name="security-of-netnamedpipebinding"></a><span data-ttu-id="f75f7-102">\<> de segurança do \<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="f75f7-102">\<security> of \<netNamedPipeBinding></span></span>
<span data-ttu-id="f75f7-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="f75f7-103">Defines the security settings for a binding.</span></span>  
  
<span data-ttu-id="f75f7-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f75f7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f75f7-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f75f7-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f75f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="f75f7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f75f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netNamedPipeBinding >** ](netnamedpipebinding.md)</span><span class="sxs-lookup"><span data-stu-id="f75f7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netNamedPipeBinding>**](netnamedpipebinding.md)</span></span>\
<span data-ttu-id="f75f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="f75f7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f75f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="f75f7-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f75f7-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f75f7-110">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding>
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f75f7-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f75f7-111">Attributes and Elements</span></span>  
 <span data-ttu-id="f75f7-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f75f7-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f75f7-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="f75f7-113">Attributes</span></span>  
  
|<span data-ttu-id="f75f7-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="f75f7-114">Attribute</span></span>|<span data-ttu-id="f75f7-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="f75f7-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f75f7-116">modo</span><span class="sxs-lookup"><span data-stu-id="f75f7-116">mode</span></span>|<span data-ttu-id="f75f7-117">Especifica o tipo de segurança que é aplicado a essa associação.</span><span class="sxs-lookup"><span data-stu-id="f75f7-117">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="f75f7-118">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f75f7-118">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f75f7-119">-Nenhum: isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="f75f7-119">-   None: This disables security.</span></span><br /><span data-ttu-id="f75f7-120">-Transport: a segurança é fornecida usando a segurança baseada em transporte subjacente.</span><span class="sxs-lookup"><span data-stu-id="f75f7-120">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="f75f7-121">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="f75f7-121">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="f75f7-122">-O valor padrão é transporte.</span><span class="sxs-lookup"><span data-stu-id="f75f7-122">-   The default value is Transport.</span></span> <span data-ttu-id="f75f7-123">Este atributo é do tipo <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f75f7-123">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f75f7-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f75f7-124">Child Elements</span></span>  
  
|<span data-ttu-id="f75f7-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="f75f7-125">Element</span></span>|<span data-ttu-id="f75f7-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="f75f7-126">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f75f7-127">transporte</span><span class="sxs-lookup"><span data-stu-id="f75f7-127">transport</span></span>|<span data-ttu-id="f75f7-128">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="f75f7-128">Defines the security settings for the transport.</span></span> <span data-ttu-id="f75f7-129">Este elemento é do tipo <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f75f7-129">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f75f7-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f75f7-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f75f7-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="f75f7-131">Element</span></span>|<span data-ttu-id="f75f7-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="f75f7-132">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f75f7-133">associação</span><span class="sxs-lookup"><span data-stu-id="f75f7-133">binding</span></span>|<span data-ttu-id="f75f7-134">O elemento Binding do [\<netNamedPipeBinding >](netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="f75f7-134">The binding element of the [\<netNamedPipeBinding>](netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f75f7-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f75f7-135">See also</span></span>

- <xref:System.ServiceModel.NetNamedPipeSecurity>
- <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>
- [<span data-ttu-id="f75f7-136">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f75f7-136">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f75f7-137">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="f75f7-137">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="f75f7-138">Associações</span><span class="sxs-lookup"><span data-stu-id="f75f7-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f75f7-139">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f75f7-139">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f75f7-140">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f75f7-140">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f75f7-141">\<binding ></span><span class="sxs-lookup"><span data-stu-id="f75f7-141">\<binding></span></span>](bindings.md)
