---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 543c57d6b2dba1ff5934b49e0e219cf2e5cad153
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91170019"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="0a19d-102">\<security> de \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="0a19d-102">\<security> of \<netPeerBinding></span></span>

<span data-ttu-id="0a19d-103">Define as configurações de segurança do [\<netPeerTcpBinding>](netpeertcpbinding.md) , incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="0a19d-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="0a19d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0a19d-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a19d-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0a19d-105">Attributes and Elements</span></span>  

 <span data-ttu-id="0a19d-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a19d-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a19d-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0a19d-107">Attributes</span></span>  
  
|<span data-ttu-id="0a19d-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0a19d-108">Attribute</span></span>|<span data-ttu-id="0a19d-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a19d-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a19d-110">mode</span><span class="sxs-lookup"><span data-stu-id="0a19d-110">mode</span></span>|<span data-ttu-id="0a19d-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="0a19d-111">Optional.</span></span> <span data-ttu-id="0a19d-112">Especifica o tipo de segurança usado por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="0a19d-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="0a19d-113">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="0a19d-113">The default value is `Message`.</span></span> <span data-ttu-id="0a19d-114">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="0a19d-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="0a19d-115">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="0a19d-115">mode Attribute</span></span>  
  
|<span data-ttu-id="0a19d-116">Valor</span><span class="sxs-lookup"><span data-stu-id="0a19d-116">Value</span></span>|<span data-ttu-id="0a19d-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a19d-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0a19d-118">Mensagem</span><span class="sxs-lookup"><span data-stu-id="0a19d-118">Message</span></span>|<span data-ttu-id="0a19d-119">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="0a19d-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="0a19d-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0a19d-120">None</span></span>|<span data-ttu-id="0a19d-121">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="0a19d-121">Security is disabled.</span></span>|  
|<span data-ttu-id="0a19d-122">Transport</span><span class="sxs-lookup"><span data-stu-id="0a19d-122">Transport</span></span>|<span data-ttu-id="0a19d-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="0a19d-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="0a19d-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="0a19d-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="0a19d-125">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="0a19d-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="0a19d-126">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="0a19d-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a19d-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0a19d-127">Child Elements</span></span>  
  
|<span data-ttu-id="0a19d-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a19d-128">Element</span></span>|<span data-ttu-id="0a19d-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a19d-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="0a19d-130">Define o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="0a19d-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="0a19d-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="0a19d-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0a19d-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0a19d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="0a19d-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="0a19d-133">Element</span></span>|<span data-ttu-id="0a19d-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="0a19d-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="0a19d-135">Define todos os recursos de associação do [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0a19d-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a19d-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="0a19d-136">Remarks</span></span>  

 <span data-ttu-id="0a19d-137">A segurança pode ser específica de mensagens ou de transporte.</span><span class="sxs-lookup"><span data-stu-id="0a19d-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a19d-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="0a19d-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="0a19d-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0a19d-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0a19d-140">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="0a19d-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="0a19d-141">Associações</span><span class="sxs-lookup"><span data-stu-id="0a19d-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0a19d-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="0a19d-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0a19d-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0a19d-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
