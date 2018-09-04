---
title: '&lt;segurança&gt; de &lt;netNamedPipeBinding&gt;'
ms.date: 03/30/2017
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 0e5a22d6e517bc7a05f74089b7c8ece8c8a4bd39
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43558666"
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="e7e1b-102">&lt;segurança&gt; de &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="e7e1b-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="e7e1b-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="e7e1b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e7e1b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e7e1b-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="e7e1b-105">\<bindings></span></span>  
<span data-ttu-id="e7e1b-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="e7e1b-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="e7e1b-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="e7e1b-107">\<binding></span></span>  
<span data-ttu-id="e7e1b-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="e7e1b-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e7e1b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e7e1b-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e7e1b-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e7e1b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e7e1b-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e7e1b-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e7e1b-112">Attributes</span></span>  
  
|<span data-ttu-id="e7e1b-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e7e1b-113">Attribute</span></span>|<span data-ttu-id="e7e1b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7e1b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e7e1b-115">modo</span><span class="sxs-lookup"><span data-stu-id="e7e1b-115">mode</span></span>|<span data-ttu-id="e7e1b-116">Especifica o tipo de segurança que é aplicada a essa associação.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="e7e1b-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="e7e1b-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="e7e1b-118">-None: Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-118">-   None: This disables security.</span></span><br /><span data-ttu-id="e7e1b-119">-Transport: Segurança é fornecida usando a segurança de transporte com base subjacente.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="e7e1b-120">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="e7e1b-121">-O valor padrão é o transporte.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-121">-   The default value is Transport.</span></span> <span data-ttu-id="e7e1b-122">Esse atributo é do tipo <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e7e1b-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e7e1b-123">Child Elements</span></span>  
  
|<span data-ttu-id="e7e1b-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="e7e1b-124">Element</span></span>|<span data-ttu-id="e7e1b-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7e1b-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7e1b-126">transporte</span><span class="sxs-lookup"><span data-stu-id="e7e1b-126">transport</span></span>|<span data-ttu-id="e7e1b-127">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="e7e1b-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="e7e1b-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e7e1b-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e7e1b-129">Parent Elements</span></span>  
  
|<span data-ttu-id="e7e1b-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="e7e1b-130">Element</span></span>|<span data-ttu-id="e7e1b-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="e7e1b-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e7e1b-132">associação</span><span class="sxs-lookup"><span data-stu-id="e7e1b-132">binding</span></span>|<span data-ttu-id="e7e1b-133">O elemento de associação do [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="e7e1b-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e7e1b-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e7e1b-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="e7e1b-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="e7e1b-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="e7e1b-136">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="e7e1b-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="e7e1b-137">Associações</span><span class="sxs-lookup"><span data-stu-id="e7e1b-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="e7e1b-138">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="e7e1b-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="e7e1b-139">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="e7e1b-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="e7e1b-140">\<associação ></span><span class="sxs-lookup"><span data-stu-id="e7e1b-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
