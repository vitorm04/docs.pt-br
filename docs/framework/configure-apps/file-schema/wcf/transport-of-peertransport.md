---
title: <transport> de <peerTransport>
ms.date: 03/30/2017
ms.assetid: d7116240-845c-4b6f-b203-262de6b597ef
ms.openlocfilehash: 3b2c7716727f58abb81bf4d58b13189ac170cf7c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399297"
---
# <a name="transport-of-peertransport"></a><span data-ttu-id="5170b-102">\<> de transporte \<do peerTransport ></span><span class="sxs-lookup"><span data-stu-id="5170b-102">\<transport> of \<peerTransport></span></span>
<span data-ttu-id="5170b-103">Especifica o tipo de transporte para mensagens protegidas enviadas por pares configurados com essa associação.</span><span class="sxs-lookup"><span data-stu-id="5170b-103">Specifies the transport type for secured messages sent by peers configured with this binding.</span></span>  
  
<span data-ttu-id="5170b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5170b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5170b-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5170b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5170b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="5170b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="5170b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="5170b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="5170b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**</span><span class="sxs-lookup"><span data-stu-id="5170b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="5170b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> peerTransport**](peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="5170b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peerTransport>**](peertransport.md)</span></span>\
<span data-ttu-id="5170b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de segurança**](security-of-peertransport.md)</span><span class="sxs-lookup"><span data-stu-id="5170b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-peertransport.md)</span></span>\
<span data-ttu-id="5170b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de transporte**</span><span class="sxs-lookup"><span data-stu-id="5170b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5170b-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5170b-112">Syntax</span></span>  
  
```xml  
<security>
  <transport credentialType="Certificate/Password" />
</security>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5170b-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5170b-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5170b-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="5170b-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5170b-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5170b-115">Attributes</span></span>  
  
|<span data-ttu-id="5170b-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5170b-116">Attribute</span></span>|<span data-ttu-id="5170b-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5170b-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5170b-118">CredentialType</span><span class="sxs-lookup"><span data-stu-id="5170b-118">credentialType</span></span>|<span data-ttu-id="5170b-119">Opcional.</span><span class="sxs-lookup"><span data-stu-id="5170b-119">Optional.</span></span> <span data-ttu-id="5170b-120">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="5170b-120">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="5170b-121">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType>.</span><span class="sxs-lookup"><span data-stu-id="5170b-121">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="5170b-122">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="5170b-122">credentialType Attribute</span></span>  
  
|<span data-ttu-id="5170b-123">Valor</span><span class="sxs-lookup"><span data-stu-id="5170b-123">Value</span></span>|<span data-ttu-id="5170b-124">Descrição</span><span class="sxs-lookup"><span data-stu-id="5170b-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5170b-125">Certificate</span><span class="sxs-lookup"><span data-stu-id="5170b-125">Certificate</span></span>|<span data-ttu-id="5170b-126">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="5170b-126">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="5170b-127">Senha</span><span class="sxs-lookup"><span data-stu-id="5170b-127">Password</span></span>|<span data-ttu-id="5170b-128">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="5170b-128">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5170b-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5170b-129">Child Elements</span></span>  
 <span data-ttu-id="5170b-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5170b-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5170b-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5170b-131">Parent Elements</span></span>  
  
|<span data-ttu-id="5170b-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="5170b-132">Element</span></span>|<span data-ttu-id="5170b-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="5170b-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5170b-134">\<security></span><span class="sxs-lookup"><span data-stu-id="5170b-134">\<security></span></span>](security-of-peertransport.md)|<span data-ttu-id="5170b-135">Define as configurações de segurança para um transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="5170b-135">Defines the security settings for a peer transport.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5170b-136">Comentários</span><span class="sxs-lookup"><span data-stu-id="5170b-136">Remarks</span></span>  
 <span data-ttu-id="5170b-137">Esse elemento será definido somente se o atributo mode do [ \<> de segurança](security-of-peertransport.md) for definido `Transport` como `TransportWithMessageCredential`ou.</span><span class="sxs-lookup"><span data-stu-id="5170b-137">This element is set only if the mode attribute of [\<security>](security-of-peertransport.md) is set to `Transport` or `TransportWithMessageCredential`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5170b-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5170b-138">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="5170b-139">Segurança de transporte</span><span class="sxs-lookup"><span data-stu-id="5170b-139">Transport Security</span></span>](../../../wcf/feature-details/transport-security.md)
- [<span data-ttu-id="5170b-140">Transportes</span><span class="sxs-lookup"><span data-stu-id="5170b-140">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="5170b-141">Escolhendo um transporte</span><span class="sxs-lookup"><span data-stu-id="5170b-141">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="5170b-142">Associações</span><span class="sxs-lookup"><span data-stu-id="5170b-142">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="5170b-143">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="5170b-143">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="5170b-144">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="5170b-144">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="5170b-145">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="5170b-145">\<customBinding></span></span>](custombinding.md)
