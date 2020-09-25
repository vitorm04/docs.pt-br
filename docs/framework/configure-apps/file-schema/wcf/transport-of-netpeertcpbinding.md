---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 5df47b1bfc149b524fc9b90eacffa832817f653c
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172860"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="379d1-102">\<transport> de \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="379d1-102">\<transport> of \<netPeerTcpBinding></span></span>

<span data-ttu-id="379d1-103">Especifica as configurações de segurança de nível de transporte ao usar o [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="379d1-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="379d1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="379d1-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="379d1-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="379d1-105">Attributes and Elements</span></span>  

 <span data-ttu-id="379d1-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="379d1-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="379d1-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="379d1-107">Attributes</span></span>  
  
|<span data-ttu-id="379d1-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="379d1-108">Attribute</span></span>|<span data-ttu-id="379d1-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="379d1-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="379d1-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="379d1-110">credentialType</span></span>|<span data-ttu-id="379d1-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="379d1-111">Optional.</span></span> <span data-ttu-id="379d1-112">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="379d1-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="379d1-113">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="379d1-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="379d1-114">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="379d1-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="379d1-115">Valor</span><span class="sxs-lookup"><span data-stu-id="379d1-115">Value</span></span>|<span data-ttu-id="379d1-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="379d1-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="379d1-117">Certificado</span><span class="sxs-lookup"><span data-stu-id="379d1-117">Certificate</span></span>|<span data-ttu-id="379d1-118">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="379d1-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="379d1-119">Senha</span><span class="sxs-lookup"><span data-stu-id="379d1-119">Password</span></span>|<span data-ttu-id="379d1-120">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="379d1-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="379d1-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="379d1-121">Child Elements</span></span>  

 <span data-ttu-id="379d1-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="379d1-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="379d1-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="379d1-123">Parent Elements</span></span>  
  
|<span data-ttu-id="379d1-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="379d1-124">Element</span></span>|<span data-ttu-id="379d1-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="379d1-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="379d1-126">Define as configurações de segurança para o [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="379d1-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="379d1-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="379d1-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="379d1-128">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="379d1-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="379d1-129">Associações</span><span class="sxs-lookup"><span data-stu-id="379d1-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="379d1-130">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="379d1-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="379d1-131">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="379d1-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
