---
title: '&lt;segurança&gt; de &lt;netPeerBinding&gt;'
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
author: BrucePerlerMS
ms.openlocfilehash: 1d7ffaf72e34b700f4702b2e531afbf7e842de09
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2018
ms.locfileid: "48844560"
---
# <a name="ltsecuritygt-of-ltnetpeerbindinggt"></a><span data-ttu-id="c3910-102">&lt;segurança&gt; de &lt;netPeerBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="c3910-102">&lt;security&gt; of &lt;netPeerBinding&gt;</span></span>
<span data-ttu-id="c3910-103">Define as configurações de segurança de [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="c3910-103">Defines the security settings of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="c3910-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c3910-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c3910-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c3910-105">\<bindings></span></span>  
<span data-ttu-id="c3910-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="c3910-106">\<netPeerBinding></span></span>  
<span data-ttu-id="c3910-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c3910-107">\<binding></span></span>  
<span data-ttu-id="c3910-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="c3910-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3910-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c3910-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>  
    <binding>  
        <security mode="Message/None/Transport//TransportWithMessageCredential">  
            <transport credentialType="Certificate/Password" />  
        </security>  
    </binding>  
</netPeerBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c3910-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c3910-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c3910-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="c3910-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c3910-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c3910-112">Attributes</span></span>  
  
|<span data-ttu-id="c3910-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c3910-113">Attribute</span></span>|<span data-ttu-id="c3910-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3910-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c3910-115">modo</span><span class="sxs-lookup"><span data-stu-id="c3910-115">mode</span></span>|<span data-ttu-id="c3910-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="c3910-116">Optional.</span></span> <span data-ttu-id="c3910-117">Especifica o tipo de segurança usado por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c3910-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="c3910-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="c3910-118">The default value is `Message`.</span></span> <span data-ttu-id="c3910-119">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="c3910-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="c3910-120">modo de atributo</span><span class="sxs-lookup"><span data-stu-id="c3910-120">mode Attribute</span></span>  
  
|<span data-ttu-id="c3910-121">Valor</span><span class="sxs-lookup"><span data-stu-id="c3910-121">Value</span></span>|<span data-ttu-id="c3910-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3910-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c3910-123">Mensagem</span><span class="sxs-lookup"><span data-stu-id="c3910-123">Message</span></span>|<span data-ttu-id="c3910-124">Segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="c3910-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="c3910-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c3910-125">None</span></span>|<span data-ttu-id="c3910-126">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="c3910-126">Security is disabled.</span></span>|  
|<span data-ttu-id="c3910-127">Transporte</span><span class="sxs-lookup"><span data-stu-id="c3910-127">Transport</span></span>|<span data-ttu-id="c3910-128">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="c3910-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="c3910-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="c3910-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="c3910-130">HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="c3910-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="c3910-131">As mensagens SOAP fornecem tipos de credencial avançados.</span><span class="sxs-lookup"><span data-stu-id="c3910-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c3910-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c3910-132">Child Elements</span></span>  
  
|<span data-ttu-id="c3910-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3910-133">Element</span></span>|<span data-ttu-id="c3910-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3910-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3910-135">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="c3910-135">\<transport></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-netpeertcpbinding.md)|<span data-ttu-id="c3910-136">Define o tipo de transporte para mensagens protegidas enviadas pelos pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="c3910-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="c3910-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="c3910-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c3910-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c3910-138">Parent Elements</span></span>  
  
|<span data-ttu-id="c3910-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="c3910-139">Element</span></span>|<span data-ttu-id="c3910-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="c3910-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c3910-141">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c3910-141">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c3910-142">Define todos os recursos de associação do [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="c3910-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3910-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="c3910-143">Remarks</span></span>  
 <span data-ttu-id="c3910-144">Segurança pode ser qualquer um dos específicos de mensagem ou de transporte.</span><span class="sxs-lookup"><span data-stu-id="c3910-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3910-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3910-145">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>  
 <xref:System.ServiceModel.PeerSecuritySettings>  
 [<span data-ttu-id="c3910-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c3910-146">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="c3910-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="c3910-147">Selecting a Credential Type</span></span>](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [<span data-ttu-id="c3910-148">Associações</span><span class="sxs-lookup"><span data-stu-id="c3910-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="c3910-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c3910-149">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="c3910-150">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="c3910-150">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [<span data-ttu-id="c3910-151">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c3910-151">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
