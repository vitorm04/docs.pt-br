---
title: <security> de <netPeerBinding>
ms.date: 03/30/2017
ms.assetid: 1ef40d8c-f903-4426-9b08-da81462766d8
ms.openlocfilehash: 3d1ac85073c44f683fe0c054737c5ec7ed1cbf52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738666"
---
# <a name="security-of-netpeerbinding"></a><span data-ttu-id="09db1-102">\<security> de \<netPeerBinding></span><span class="sxs-lookup"><span data-stu-id="09db1-102">\<security> of \<netPeerBinding></span></span>
<span data-ttu-id="09db1-103">Define as configurações de segurança do [\<netPeerTcpBinding>](netpeertcpbinding.md) , incluindo o tipo de autenticação usado e a segurança usada para o transporte de mensagens.</span><span class="sxs-lookup"><span data-stu-id="09db1-103">Defines the security settings of the [\<netPeerTcpBinding>](netpeertcpbinding.md), including the type of authentication used and the security used for the message transport.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<security>**  
  
## <a name="syntax"></a><span data-ttu-id="09db1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09db1-104">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding>
    <security mode="Message/None/Transport//TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="09db1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="09db1-105">Attributes and Elements</span></span>  
 <span data-ttu-id="09db1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="09db1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="09db1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="09db1-107">Attributes</span></span>  
  
|<span data-ttu-id="09db1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="09db1-108">Attribute</span></span>|<span data-ttu-id="09db1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="09db1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="09db1-110">mode</span><span class="sxs-lookup"><span data-stu-id="09db1-110">mode</span></span>|<span data-ttu-id="09db1-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="09db1-111">Optional.</span></span> <span data-ttu-id="09db1-112">Especifica o tipo de segurança usado por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="09db1-112">Specifies the type of security used by peers configured with this binding.</span></span> <span data-ttu-id="09db1-113">O valor padrão é `Message`.</span><span class="sxs-lookup"><span data-stu-id="09db1-113">The default value is `Message`.</span></span> <span data-ttu-id="09db1-114">Esse atributo é do tipo <xref:System.ServiceModel.SecurityMode> .</span><span class="sxs-lookup"><span data-stu-id="09db1-114">This attribute is of type <xref:System.ServiceModel.SecurityMode>.</span></span>|  
  
## <a name="mode-attribute"></a><span data-ttu-id="09db1-115">Atributo de modo</span><span class="sxs-lookup"><span data-stu-id="09db1-115">mode Attribute</span></span>  
  
|<span data-ttu-id="09db1-116">Valor</span><span class="sxs-lookup"><span data-stu-id="09db1-116">Value</span></span>|<span data-ttu-id="09db1-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="09db1-117">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="09db1-118">Mensagem</span><span class="sxs-lookup"><span data-stu-id="09db1-118">Message</span></span>|<span data-ttu-id="09db1-119">A segurança SOAP fornece autenticação, integridade e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="09db1-119">SOAP security provides authentication, integrity and confidentiality.</span></span>|  
|<span data-ttu-id="09db1-120">Nenhum</span><span class="sxs-lookup"><span data-stu-id="09db1-120">None</span></span>|<span data-ttu-id="09db1-121">A segurança é desabilitada.</span><span class="sxs-lookup"><span data-stu-id="09db1-121">Security is disabled.</span></span>|  
|<span data-ttu-id="09db1-122">Transport</span><span class="sxs-lookup"><span data-stu-id="09db1-122">Transport</span></span>|<span data-ttu-id="09db1-123">A proteção é fornecida usando HTTPS.</span><span class="sxs-lookup"><span data-stu-id="09db1-123">Security is provided using HTTPS.</span></span>|  
|<span data-ttu-id="09db1-124">TransportWithMessageCredential</span><span class="sxs-lookup"><span data-stu-id="09db1-124">TransportWithMessageCredential</span></span>|<span data-ttu-id="09db1-125">O HTTPS fornece autenticação e confidencialidade.</span><span class="sxs-lookup"><span data-stu-id="09db1-125">HTTPS provides authentication and confidentiality.</span></span> <span data-ttu-id="09db1-126">As mensagens SOAP fornecem tipos de credenciais avançados.</span><span class="sxs-lookup"><span data-stu-id="09db1-126">SOAP messages provide rich credential types.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="09db1-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="09db1-127">Child Elements</span></span>  
  
|<span data-ttu-id="09db1-128">Elemento</span><span class="sxs-lookup"><span data-stu-id="09db1-128">Element</span></span>|<span data-ttu-id="09db1-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="09db1-129">Description</span></span>|  
|-------------|-----------------|  
|[\<transport>](transport-of-netpeertcpbinding.md)|<span data-ttu-id="09db1-130">Define o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="09db1-130">Defines the transport type for secured messages sent by peers configured with this binding.</span></span> <span data-ttu-id="09db1-131">Esse elemento é do tipo <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="09db1-131">This element is of type <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="09db1-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="09db1-132">Parent Elements</span></span>  
  
|<span data-ttu-id="09db1-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="09db1-133">Element</span></span>|<span data-ttu-id="09db1-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="09db1-134">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="09db1-135">Define todos os recursos de associação do [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="09db1-135">Defines all binding capabilities of the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="09db1-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="09db1-136">Remarks</span></span>  
 <span data-ttu-id="09db1-137">A segurança pode ser específica de mensagens ou de transporte.</span><span class="sxs-lookup"><span data-stu-id="09db1-137">Security can be either message- or transport-specific.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09db1-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="09db1-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerSecurityElement>
- <xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.PeerSecuritySettings>
- [<span data-ttu-id="09db1-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="09db1-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="09db1-140">Selecionando um tipo de credencial</span><span class="sxs-lookup"><span data-stu-id="09db1-140">Selecting a Credential Type</span></span>](../../../wcf/feature-details/selecting-a-credential-type.md)
- [<span data-ttu-id="09db1-141">Associações</span><span class="sxs-lookup"><span data-stu-id="09db1-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="09db1-142">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="09db1-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="09db1-143">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="09db1-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
