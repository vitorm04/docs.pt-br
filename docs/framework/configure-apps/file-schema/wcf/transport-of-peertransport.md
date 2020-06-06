---
title: <transport> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399297"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="eeced-102">\<transport> de \<peerTransport></span><span class="sxs-lookup"><span data-stu-id="eeced-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="eeced-103">Especifica o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="eeced-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="eeced-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eeced-104">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eeced-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eeced-105">Attributes and Elements</span></span>  
 <span data-ttu-id="eeced-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="eeced-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eeced-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="eeced-107">Attributes</span></span>  
  
|<span data-ttu-id="eeced-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="eeced-108">Attribute</span></span>|<span data-ttu-id="eeced-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="eeced-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eeced-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="eeced-110">credentialType</span></span>|<span data-ttu-id="eeced-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="eeced-111">Optional.</span></span> <span data-ttu-id="eeced-112">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="eeced-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="eeced-113">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="eeced-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="eeced-114">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="eeced-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="eeced-115">Valor</span><span class="sxs-lookup"><span data-stu-id="eeced-115">Value</span></span>|<span data-ttu-id="eeced-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="eeced-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="eeced-117">Certificado</span><span class="sxs-lookup"><span data-stu-id="eeced-117">Certificate</span></span>|<span data-ttu-id="eeced-118">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="eeced-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="eeced-119">Senha</span><span class="sxs-lookup"><span data-stu-id="eeced-119">Password</span></span>|<span data-ttu-id="eeced-120">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="eeced-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eeced-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eeced-121">Child Elements</span></span>  
 <span data-ttu-id="eeced-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="eeced-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eeced-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eeced-123">Parent Elements</span></span>  
  
|<span data-ttu-id="eeced-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="eeced-124">Element</span></span>|<span data-ttu-id="eeced-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="eeced-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-peertransport.md)|<span data-ttu-id="eeced-126">Define as configurações de segurança para um transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="eeced-126">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eeced-127">Comentários</span><span class="sxs-lookup"><span data-stu-id="eeced-127">Remarks</span></span>  
 <span data-ttu-id="eeced-128">Esse elemento será definido somente se o atributo mode de [\<security>](security-of-peertransport.md) for definido como `Transport` ou `TransportWithMessageCredential` .</span><span class="sxs-lookup"><span data-stu-id="eeced-128">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eeced-129">Confira também</span><span class="sxs-lookup"><span data-stu-id="eeced-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="eeced-130">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="eeced-130">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="eeced-131">Transportes</span><span class="sxs-lookup"><span data-stu-id="eeced-131">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="eeced-132">Selecionando um transporte</span><span class="sxs-lookup"><span data-stu-id="eeced-132">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="eeced-133">Associações</span><span class="sxs-lookup"><span data-stu-id="eeced-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="eeced-134">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="eeced-134">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="eeced-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="eeced-135">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
