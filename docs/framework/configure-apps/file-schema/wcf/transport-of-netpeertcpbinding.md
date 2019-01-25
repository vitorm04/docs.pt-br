---
title: '&lt;transporte&gt; de &lt;netPeerTcpBinding&gt;'
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: b929c97d0b5d9e021a71e4b88dd3d8a5f2f909a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54676998"
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="9548c-102">&lt;transporte&gt; de &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="9548c-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="9548c-103">Especifica as configurações de segurança em nível de transporte ao usar o [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9548c-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="9548c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9548c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9548c-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="9548c-105">\<bindings></span></span>  
<span data-ttu-id="9548c-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="9548c-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="9548c-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="9548c-107">\<binding></span></span>  
<span data-ttu-id="9548c-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="9548c-108">\<security></span></span>  
<span data-ttu-id="9548c-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="9548c-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9548c-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9548c-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9548c-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9548c-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9548c-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="9548c-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9548c-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="9548c-113">Attributes</span></span>  
  
|<span data-ttu-id="9548c-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="9548c-114">Attribute</span></span>|<span data-ttu-id="9548c-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="9548c-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9548c-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="9548c-116">credentialType</span></span>|<span data-ttu-id="9548c-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="9548c-117">Optional.</span></span> <span data-ttu-id="9548c-118">Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par.</span><span class="sxs-lookup"><span data-stu-id="9548c-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="9548c-119">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="9548c-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="9548c-120">credentialType atributo</span><span class="sxs-lookup"><span data-stu-id="9548c-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="9548c-121">Valor</span><span class="sxs-lookup"><span data-stu-id="9548c-121">Value</span></span>|<span data-ttu-id="9548c-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="9548c-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9548c-123">Certificado</span><span class="sxs-lookup"><span data-stu-id="9548c-123">Certificate</span></span>|<span data-ttu-id="9548c-124">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="9548c-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="9548c-125">Senha</span><span class="sxs-lookup"><span data-stu-id="9548c-125">Password</span></span>|<span data-ttu-id="9548c-126">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="9548c-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9548c-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9548c-127">Child Elements</span></span>  
 <span data-ttu-id="9548c-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9548c-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9548c-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9548c-129">Parent Elements</span></span>  
  
|<span data-ttu-id="9548c-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="9548c-130">Element</span></span>|<span data-ttu-id="9548c-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="9548c-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9548c-132">\<security></span><span class="sxs-lookup"><span data-stu-id="9548c-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="9548c-133">Define as configurações de segurança para o [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="9548c-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9548c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9548c-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="9548c-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9548c-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="9548c-136">Associações</span><span class="sxs-lookup"><span data-stu-id="9548c-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="9548c-137">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="9548c-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9548c-138">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="9548c-138">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9548c-139">\<binding></span><span class="sxs-lookup"><span data-stu-id="9548c-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
