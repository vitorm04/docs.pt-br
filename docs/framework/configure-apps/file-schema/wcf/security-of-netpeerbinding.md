---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: be5ebacec466caf8d8a77bf552f42da1861e77a1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936623"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="48460-102">\<> de segurança \<do netpeerbinding ></span><span class="sxs-lookup"><span data-stu-id="48460-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="48460-103">Define as configurações de segurança do [ \<> NetPeerTcpBinding](netpeertcpbinding.md), incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="48460-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
 <span data-ttu-id="48460-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="48460-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="48460-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="48460-105">\<bindings></span></span>  
<span data-ttu-id="48460-106">\<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="48460-106">\<netPeerBinding></span></span>  
<span data-ttu-id="48460-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="48460-107">\<binding></span></span>  
<span data-ttu-id="48460-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="48460-108">\<security></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48460-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48460-109">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="48460-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="48460-110">Attributes and Elements</span></span>  
 <span data-ttu-id="48460-111">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="48460-111">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="48460-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="48460-112">Attributes</span></span>  
  
|<span data-ttu-id="48460-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="48460-113">Attribute</span></span>|<span data-ttu-id="48460-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="48460-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="48460-115">modo</span><span class="sxs-lookup"><span data-stu-id="48460-115">mode</span></span>|<span data-ttu-id="48460-116">Opcional.</span><span class="sxs-lookup"><span data-stu-id="48460-116">Optional.</span></span> <span data-ttu-id="48460-117">Especifica o tipo de segurança usado por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="48460-117">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="48460-118">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="48460-118">The default value is `Message`.</span></span> <span data-ttu-id="48460-119">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="48460-119">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="48460-120">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="48460-120">mode Attribute</span></span>  
  
|<span data-ttu-id="48460-121">Valor</span><span class="sxs-lookup"><span data-stu-id="48460-121">Value</span></span>|<span data-ttu-id="48460-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="48460-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="48460-123">Mensagem</span><span class="sxs-lookup"><span data-stu-id="48460-123">Message</span></span>|<span data-ttu-id="48460-124">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="48460-124">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="48460-125">Nenhum</span><span class="sxs-lookup"><span data-stu-id="48460-125">None</span></span>|<span data-ttu-id="48460-126">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="48460-126">Security is disabled.</span></span>|  
|<span data-ttu-id="48460-127">Porta</span><span class="sxs-lookup"><span data-stu-id="48460-127">Transport</span></span>|<span data-ttu-id="48460-128">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="48460-128">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="48460-129">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="48460-129">TransportWithMessageCredential</span></span>|<span data-ttu-id="48460-130">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="48460-130">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="48460-131">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="48460-131">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="48460-132">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="48460-132">Child Elements</span></span>  
  
|<span data-ttu-id="48460-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="48460-133">Element</span></span>|<span data-ttu-id="48460-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="48460-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48460-135">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="48460-135">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="48460-136">Define o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="48460-136">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="48460-137">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="48460-137">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="48460-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="48460-138">Parent Elements</span></span>  
  
|<span data-ttu-id="48460-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="48460-139">Element</span></span>|<span data-ttu-id="48460-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="48460-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="48460-141">\<binding></span><span class="sxs-lookup"><span data-stu-id="48460-141">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="48460-142">Define todos os recursos de associação do [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="48460-142">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48460-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="48460-143">Remarks</span></span>  
 <span data-ttu-id="48460-144">A segurança pode ser específica de mensagens ou de transporte.</span><span class="sxs-lookup"><span data-stu-id="48460-144">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48460-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48460-145">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="48460-146">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="48460-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="48460-147">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="48460-147">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="48460-148">Associações</span><span class="sxs-lookup"><span data-stu-id="48460-148">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="48460-149">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="48460-149">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="48460-150">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="48460-150">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="48460-151">\<binding></span><span class="sxs-lookup"><span data-stu-id="48460-151">\<binding></span></span>](../../../misc/binding.md)
