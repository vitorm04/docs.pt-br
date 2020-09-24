---
title: <transport> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 7328d67c4649010dce3e1c866238d1e0067e4990
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157064"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="d38f6-102">\<transport> de \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="d38f6-102">\<transport> of \<peerTransport></span></span>

<span data-ttu-id="d38f6-103">Especifica o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="d38f6-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="d38f6-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="d38f6-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d38f6-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d38f6-105">Attributes and Elements</span></span>  

 <span data-ttu-id="d38f6-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="d38f6-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d38f6-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="d38f6-107">Attributes</span></span>  
  
|<span data-ttu-id="d38f6-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="d38f6-108">Attribute</span></span>|<span data-ttu-id="d38f6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d38f6-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d38f6-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="d38f6-110">credentialType</span></span>|<span data-ttu-id="d38f6-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="d38f6-111">Optional.</span></span> <span data-ttu-id="d38f6-112">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="d38f6-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="d38f6-113">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="d38f6-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="d38f6-114">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="d38f6-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="d38f6-115">Valor</span><span class="sxs-lookup"><span data-stu-id="d38f6-115">Value</span></span>|<span data-ttu-id="d38f6-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="d38f6-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d38f6-117">Certificado</span><span class="sxs-lookup"><span data-stu-id="d38f6-117">Certificate</span></span>|<span data-ttu-id="d38f6-118">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="d38f6-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="d38f6-119">Senha</span><span class="sxs-lookup"><span data-stu-id="d38f6-119">Password</span></span>|<span data-ttu-id="d38f6-120">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="d38f6-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d38f6-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d38f6-121">Child Elements</span></span>  

 <span data-ttu-id="d38f6-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d38f6-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d38f6-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d38f6-123">Parent Elements</span></span>  
  
|<span data-ttu-id="d38f6-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="d38f6-124">Element</span></span>|<span data-ttu-id="d38f6-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="d38f6-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="d38f6-126">Define as configurações de segurança para um transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="d38f6-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d38f6-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="d38f6-127">Remarks</span></span>  

 <span data-ttu-id="d38f6-128">Esse elemento será definido somente se o atributo mode de [\<security>](security-of-peertransport.md) for definido como `Transport` ou `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="d38f6-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d38f6-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="d38f6-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="d38f6-130">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="d38f6-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="d38f6-131">Transportes</span><span class="sxs-lookup"><span data-stu-id="d38f6-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="d38f6-132">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="d38f6-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="d38f6-133">Associações</span><span class="sxs-lookup"><span data-stu-id="d38f6-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="d38f6-134">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="d38f6-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="d38f6-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="d38f6-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
