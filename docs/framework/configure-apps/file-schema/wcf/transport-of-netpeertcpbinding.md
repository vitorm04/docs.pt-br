---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 837d01540fa63579877ab4085bd8034c78f2fbe0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69915571"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="75d68-102">\<> de transporte \<do NetPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="75d68-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="75d68-103">Especifica as configurações de segurança de nível de transporte ao usar o [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="75d68-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
 <span data-ttu-id="75d68-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="75d68-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="75d68-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="75d68-105">\<bindings></span></span>  
<span data-ttu-id="75d68-106">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="75d68-106">\<netPeerTcpBinding></span></span>  
<span data-ttu-id="75d68-107">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="75d68-107">\<binding></span></span>  
<span data-ttu-id="75d68-108">\<> de segurança</span><span class="sxs-lookup"><span data-stu-id="75d68-108">\<security></span></span>  
<span data-ttu-id="75d68-109">\<> de transporte</span><span class="sxs-lookup"><span data-stu-id="75d68-109">\<transport></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75d68-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="75d68-110">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="75d68-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="75d68-111">Attributes and Elements</span></span>  
 <span data-ttu-id="75d68-112">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="75d68-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="75d68-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="75d68-113">Attributes</span></span>  
  
|<span data-ttu-id="75d68-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="75d68-114">Attribute</span></span>|<span data-ttu-id="75d68-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="75d68-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="75d68-116">CredentialType</span><span class="sxs-lookup"><span data-stu-id="75d68-116">credentialType</span></span>|<span data-ttu-id="75d68-117">Opcional.</span><span class="sxs-lookup"><span data-stu-id="75d68-117">Optional.</span></span> <span data-ttu-id="75d68-118">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="75d68-118">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="75d68-119">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="75d68-119">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="75d68-120">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="75d68-120">credentialType Attribute</span></span>  
  
|<span data-ttu-id="75d68-121">Valor</span><span class="sxs-lookup"><span data-stu-id="75d68-121">Value</span></span>|<span data-ttu-id="75d68-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="75d68-122">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="75d68-123">Certificate</span><span class="sxs-lookup"><span data-stu-id="75d68-123">Certificate</span></span>|<span data-ttu-id="75d68-124">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="75d68-124">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="75d68-125">Senha</span><span class="sxs-lookup"><span data-stu-id="75d68-125">Password</span></span>|<span data-ttu-id="75d68-126">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="75d68-126">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="75d68-127">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="75d68-127">Child Elements</span></span>  
 <span data-ttu-id="75d68-128">Nenhum</span><span class="sxs-lookup"><span data-stu-id="75d68-128">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="75d68-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="75d68-129">Parent Elements</span></span>  
  
|<span data-ttu-id="75d68-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="75d68-130">Element</span></span>|<span data-ttu-id="75d68-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="75d68-131">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="75d68-132">\<security></span><span class="sxs-lookup"><span data-stu-id="75d68-132">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="75d68-133">Define as configurações de segurança para o [ \<> NetPeerTcpBinding](netpeertcpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="75d68-133">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75d68-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="75d68-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="75d68-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="75d68-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="75d68-136">Associações</span><span class="sxs-lookup"><span data-stu-id="75d68-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="75d68-137">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="75d68-137">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="75d68-138">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="75d68-138">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="75d68-139">\<binding></span><span class="sxs-lookup"><span data-stu-id="75d68-139">\<binding></span></span>](../../../misc/binding.md)
