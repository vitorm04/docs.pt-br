---
title: '&lt;segurança&gt; de &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 45000554226fcde753041fca283bfc8b1eeba5ce
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541763"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="ff88e-102">&lt;segurança&gt; de &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="ff88e-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="ff88e-103">Define as configurações de segurança de [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="ff88e-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="ff88e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ff88e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ff88e-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="ff88e-105">\<bindings></span></span>  
<span data-ttu-id="ff88e-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="ff88e-106">\<netPeerBinding></span></span>  
<span data-ttu-id="ff88e-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ff88e-107">\<binding></span></span>  
<span data-ttu-id="ff88e-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="ff88e-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff88e-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ff88e-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ff88e-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ff88e-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ff88e-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff88e-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ff88e-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ff88e-112">Attributes</span></span>  
  
|<span data-ttu-id="ff88e-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ff88e-113">Attribute</span></span>|<span data-ttu-id="ff88e-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff88e-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ff88e-115">modo</span><span class="sxs-lookup"><span data-stu-id="ff88e-115">mode</span></span>|<span data-ttu-id="ff88e-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="ff88e-116">Optional.</span></span> <span data-ttu-id="ff88e-117">Especifica o tipo de segurança usado por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="ff88e-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="ff88e-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="ff88e-118">The default value is `Message`.</span></span> <span data-ttu-id="ff88e-119">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="ff88e-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="ff88e-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="ff88e-120">mode Attribute</span></span>  
  
|<span data-ttu-id="ff88e-121">Valor</span><span class="sxs-lookup"><span data-stu-id="ff88e-121">Value</span></span>|<span data-ttu-id="ff88e-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff88e-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="ff88e-123">Mensagem</span><span class="sxs-lookup"><span data-stu-id="ff88e-123">Message</span></span>|<span data-ttu-id="ff88e-124">Segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="ff88e-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="ff88e-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ff88e-125">None</span></span>|<span data-ttu-id="ff88e-126">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="ff88e-126">Security is disabled.</span></span>|  
|<span data-ttu-id="ff88e-127">Transporte</span><span class="sxs-lookup"><span data-stu-id="ff88e-127">Transport</span></span>|<span data-ttu-id="ff88e-128">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="ff88e-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="ff88e-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="ff88e-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="ff88e-130">HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="ff88e-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="ff88e-131">As mensagens SOAP fornecem tipos de credencial avançados.</span><span class="sxs-lookup"><span data-stu-id="ff88e-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ff88e-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ff88e-132">Child Elements</span></span>  
  
|<span data-ttu-id="ff88e-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff88e-133">Element</span></span>|<span data-ttu-id="ff88e-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff88e-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff88e-135">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="ff88e-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="ff88e-136">Define o tipo de transporte para mensagens protegidas enviadas pelos pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="ff88e-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="ff88e-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="ff88e-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ff88e-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ff88e-138">Parent Elements</span></span>  
  
|<span data-ttu-id="ff88e-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="ff88e-139">Element</span></span>|<span data-ttu-id="ff88e-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="ff88e-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ff88e-141">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ff88e-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="ff88e-142">Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="ff88e-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff88e-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="ff88e-143">Remarks</span></span>  
 <span data-ttu-id="ff88e-144">Segurança pode ser qualquer um dos específicos de mensagem ou de transporte.</span><span class="sxs-lookup"><span data-stu-id="ff88e-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff88e-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ff88e-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="ff88e-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="ff88e-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="ff88e-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="ff88e-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="ff88e-148">Associações</span><span class="sxs-lookup"><span data-stu-id="ff88e-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="ff88e-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="ff88e-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="ff88e-150">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="ff88e-150">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](https://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="ff88e-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="ff88e-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
