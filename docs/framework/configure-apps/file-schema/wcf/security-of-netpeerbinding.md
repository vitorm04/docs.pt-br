---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73738666"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="70914-102">\<> de segurança do \<netpeerbinding ></span><span class="sxs-lookup"><span data-stu-id="70914-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="70914-103">Define as configurações de segurança do [\<netPeerTcpBinding >](netpeertcpbinding.md), incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="70914-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
<span data-ttu-id="70914-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="70914-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="70914-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="70914-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="70914-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="70914-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="70914-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netPeerTcpBinding >** ](netpeertcpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="70914-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)</span></span>\
<span data-ttu-id="70914-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="70914-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="70914-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**security >**</span><span class="sxs-lookup"><span data-stu-id="70914-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70914-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="70914-110">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70914-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="70914-111">Attributes and Elements</span></span>  
 <span data-ttu-id="70914-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="70914-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70914-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="70914-113">Attributes</span></span>  
  
|<span data-ttu-id="70914-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="70914-114">Attribute</span></span>|<span data-ttu-id="70914-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="70914-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="70914-116">modo</span><span class="sxs-lookup"><span data-stu-id="70914-116">mode</span></span>|<span data-ttu-id="70914-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="70914-117">Optional.</span></span> <span data-ttu-id="70914-118">Especifica o tipo de segurança usado por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="70914-118">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="70914-119">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="70914-119">The default value is `Message`.</span></span> <span data-ttu-id="70914-120">Este atributo é do tipo <xref:System.ServiceModel.SecurityMode>.</span><span class="sxs-lookup"><span data-stu-id="70914-120">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="70914-121">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="70914-121">mode Attribute</span></span>  
  
|<span data-ttu-id="70914-122">Valor</span><span class="sxs-lookup"><span data-stu-id="70914-122">Value</span></span>|<span data-ttu-id="70914-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="70914-123">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="70914-124">Mensagem</span><span class="sxs-lookup"><span data-stu-id="70914-124">Message</span></span>|<span data-ttu-id="70914-125">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="70914-125">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="70914-126">Nenhum</span><span class="sxs-lookup"><span data-stu-id="70914-126">None</span></span>|<span data-ttu-id="70914-127">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="70914-127">Security is disabled.</span></span>|  
|<span data-ttu-id="70914-128">Porta</span><span class="sxs-lookup"><span data-stu-id="70914-128">Transport</span></span>|<span data-ttu-id="70914-129">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="70914-129">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="70914-130">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="70914-130">TransportWithMessageCredential</span></span>|<span data-ttu-id="70914-131">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="70914-131">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="70914-132">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="70914-132">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="70914-133">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="70914-133">Child Elements</span></span>  
  
|<span data-ttu-id="70914-134">Elemento</span><span class="sxs-lookup"><span data-stu-id="70914-134">Element</span></span>|<span data-ttu-id="70914-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="70914-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70914-136">> de transporte de \<</span><span class="sxs-lookup"><span data-stu-id="70914-136">\<transport></span></span>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="70914-137">Define o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="70914-137">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="70914-138">Este elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="70914-138">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70914-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="70914-139">Parent Elements</span></span>  
  
|<span data-ttu-id="70914-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="70914-140">Element</span></span>|<span data-ttu-id="70914-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="70914-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="70914-142">\<binding ></span><span class="sxs-lookup"><span data-stu-id="70914-142">\<binding></span></span>](bindings.md)|<span data-ttu-id="70914-143">Define todos os recursos de associação do [\<netPeerTcpBinding >](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="70914-143">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70914-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="70914-144">Remarks</span></span>  
 <span data-ttu-id="70914-145">A segurança pode ser específica de mensagens ou de transporte.</span><span class="sxs-lookup"><span data-stu-id="70914-145">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70914-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="70914-146">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="70914-147">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="70914-147">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="70914-148">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="70914-148">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="70914-149">Associações</span><span class="sxs-lookup"><span data-stu-id="70914-149">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="70914-150">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="70914-150">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="70914-151">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="70914-151">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="70914-152">\<binding ></span><span class="sxs-lookup"><span data-stu-id="70914-152">\<binding></span></span>](bindings.md)
