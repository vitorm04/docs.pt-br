---
title: '&lt;transporte&gt; de &lt;netPeerTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 181e6a9458754934d6b3b27a31c2cf2dd3455f52
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a><span data-ttu-id="a61af-102">&lt;transporte&gt; de &lt;netPeerTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="a61af-102">&lt;transport&gt; of &lt;netPeerTcpBinding&gt;</span></span>
<span data-ttu-id="a61af-103">Especifica as configurações de segurança em nível de transporte ao usar o [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a61af-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="a61af-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="a61af-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="a61af-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="a61af-105">\<bindings></span></span>  
<span data-ttu-id="a61af-106">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="a61af-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="a61af-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="a61af-107">\<binding></span></span>  
<span data-ttu-id="a61af-108">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="a61af-108">\<security></span></span>  
<span data-ttu-id="a61af-109">\<transporte ></span><span class="sxs-lookup"><span data-stu-id="a61af-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a61af-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a61af-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a61af-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a61af-111">Attributes and Elements</span></span>  
 <span data-ttu-id="a61af-112">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="a61af-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a61af-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="a61af-113">Attributes</span></span>  
  
|<span data-ttu-id="a61af-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="a61af-114">Attribute</span></span>|<span data-ttu-id="a61af-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="a61af-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a61af-116">credentialType</span><span class="sxs-lookup"><span data-stu-id="a61af-116">credentialType</span></span>|<span data-ttu-id="a61af-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a61af-117">Optional.</span></span> <span data-ttu-id="a61af-118">Especifica o tipo de credenciais usado para verificar as mensagens enviadas com o transporte de par.</span><span class="sxs-lookup"><span data-stu-id="a61af-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="a61af-119">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="a61af-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="a61af-120">credentialType atributo</span><span class="sxs-lookup"><span data-stu-id="a61af-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="a61af-121">Valor</span><span class="sxs-lookup"><span data-stu-id="a61af-121">Value</span></span>|<span data-ttu-id="a61af-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="a61af-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a61af-123">certificado</span><span class="sxs-lookup"><span data-stu-id="a61af-123">Certificate</span></span>|<span data-ttu-id="a61af-124">Requer a autenticação do transporte de canal par X509 certificado.</span><span class="sxs-lookup"><span data-stu-id="a61af-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="a61af-125">Senha</span><span class="sxs-lookup"><span data-stu-id="a61af-125">Password</span></span>|<span data-ttu-id="a61af-126">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="a61af-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a61af-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a61af-127">Child Elements</span></span>  
 <span data-ttu-id="a61af-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="a61af-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a61af-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a61af-129">Parent Elements</span></span>  
  
|<span data-ttu-id="a61af-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="a61af-130">Element</span></span>|<span data-ttu-id="a61af-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="a61af-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a61af-132">\<segurança ></span><span class="sxs-lookup"><span data-stu-id="a61af-132">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="a61af-133">Define as configurações de segurança para o [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="a61af-133">Defines the security settings for the [\<netPeerTcpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a61af-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a61af-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [<span data-ttu-id="a61af-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a61af-135">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 <span data-ttu-id="a61af-136">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="a61af-136">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="a61af-137">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="a61af-137">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="a61af-138">Usando associações para configurar clientes e serviços do Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="a61af-138">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="a61af-139">\<associação ></span><span class="sxs-lookup"><span data-stu-id="a61af-139">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
