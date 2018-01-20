---
title: "&lt;segurança&gt; de &lt;netNamedPipeBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb3cb022-637e-49fd-92e8-6766038affa7
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 3a018c502aead84eb6936001acb5bc24c59188f8
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltsecuritygt-of-ltnetnamedpipebindinggt"></a><span data-ttu-id="f1147-102">&lt;segurança&gt; de &lt;netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="f1147-102">&lt;security&gt; of &lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="f1147-103">Define as configurações de segurança para uma associação.</span><span class="sxs-lookup"><span data-stu-id="f1147-103">Defines the security settings for a binding.</span></span>  
  
 <span data-ttu-id="f1147-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1147-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1147-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f1147-105">\<bindings></span></span>  
<span data-ttu-id="f1147-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="f1147-106">\<netNamedPipeBinding></span></span>  
<span data-ttu-id="f1147-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="f1147-107">\<binding></span></span>  
<span data-ttu-id="f1147-108">\<security></span><span class="sxs-lookup"><span data-stu-id="f1147-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1147-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1147-109">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
      <binding>  
            <security mode="None/Transport">  
                        <transport protectionLevel="None/Sign/EncryptAndSign" />  
            </security>  
      </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1147-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f1147-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f1147-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f1147-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1147-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f1147-112">Attributes</span></span>  
  
|<span data-ttu-id="f1147-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f1147-113">Attribute</span></span>|<span data-ttu-id="f1147-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1147-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f1147-115">modo</span><span class="sxs-lookup"><span data-stu-id="f1147-115">mode</span></span>|<span data-ttu-id="f1147-116">Especifica o tipo de segurança que é aplicada a esta associação.</span><span class="sxs-lookup"><span data-stu-id="f1147-116">Specifies the type of security that is applied to this binding.</span></span> <span data-ttu-id="f1147-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="f1147-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f1147-118">-Nenhum: Isso desabilita a segurança.</span><span class="sxs-lookup"><span data-stu-id="f1147-118">-   None: This disables security.</span></span><br /><span data-ttu-id="f1147-119">-Transporte: Segurança é fornecida usando a segurança de transporte com base subjacente.</span><span class="sxs-lookup"><span data-stu-id="f1147-119">-   Transport: Security is provided using underlying transport based security.</span></span> <span data-ttu-id="f1147-120">É possível controlar o nível de proteção com esse modo.</span><span class="sxs-lookup"><span data-stu-id="f1147-120">It is possible to control the protection level with this mode.</span></span><br /><span data-ttu-id="f1147-121">-O valor padrão é o transporte.</span><span class="sxs-lookup"><span data-stu-id="f1147-121">-   The default value is Transport.</span></span> <span data-ttu-id="f1147-122">Esse atributo é do tipo <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="f1147-122">This attribute is of type <xref:System.ServiceModel.NetNamedPipeSecurityMode>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1147-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f1147-123">Child Elements</span></span>  
  
|<span data-ttu-id="f1147-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1147-124">Element</span></span>|<span data-ttu-id="f1147-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1147-125">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1147-126">transporte</span><span class="sxs-lookup"><span data-stu-id="f1147-126">transport</span></span>|<span data-ttu-id="f1147-127">Define as configurações de segurança para o transporte.</span><span class="sxs-lookup"><span data-stu-id="f1147-127">Defines the security settings for the transport.</span></span> <span data-ttu-id="f1147-128">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="f1147-128">This element is of type <xref:System.ServiceModel.Configuration.NamedPipeTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f1147-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f1147-129">Parent Elements</span></span>  
  
|<span data-ttu-id="f1147-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="f1147-130">Element</span></span>|<span data-ttu-id="f1147-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="f1147-131">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f1147-132">associação</span><span class="sxs-lookup"><span data-stu-id="f1147-132">binding</span></span>|<span data-ttu-id="f1147-133">O elemento de associação do [ \<netNamedPipeBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span><span class="sxs-lookup"><span data-stu-id="f1147-133">The binding element of the [\<netNamedPipeBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1147-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1147-134">See Also</span></span>  
 <xref:System.ServiceModel.NetNamedPipeSecurity>  
 <xref:System.ServiceModel.NetNamedPipeBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeSecurityElement>  
 [<span data-ttu-id="f1147-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="f1147-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="f1147-136">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="f1147-136">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="f1147-137">Associações</span><span class="sxs-lookup"><span data-stu-id="f1147-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="f1147-138">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="f1147-138">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="f1147-139">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="f1147-139">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="f1147-140">\<binding></span><span class="sxs-lookup"><span data-stu-id="f1147-140">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
