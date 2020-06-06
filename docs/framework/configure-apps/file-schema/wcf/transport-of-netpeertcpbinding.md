---
title: <transport> de <netPeerTcpBinding>
ms.date: 03/30/2017
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
ms.openlocfilehash: 49b31a889d192d190125214e89ba09305114eb7f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73735979"
---
# <a name="transport-of-netpeertcpbinding"></a><span data-ttu-id="0f7f0-102">\<transport> de \<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="0f7f0-102">\<transport> of \<netPeerTcpBinding></span></span>
<span data-ttu-id="0f7f0-103">Especifica as configurações de segurança de nível de transporte ao usar o [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0f7f0-103">Specifies settings for transport level security when using the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netPeerTcpBinding>**](netpeertcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-netpeerbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transport>**  
  
## <a name="syntax"></a><span data-ttu-id="0f7f0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f7f0-104">Syntax</span></span>  
  
```xml  
<netPeerTcpBinding>
  <binding>
    <security>
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f7f0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0f7f0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0f7f0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="0f7f0-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f7f0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f7f0-107">Attributes</span></span>  
  
|<span data-ttu-id="0f7f0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0f7f0-108">Attribute</span></span>|<span data-ttu-id="0f7f0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f7f0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f7f0-110">credentialType</span><span class="sxs-lookup"><span data-stu-id="0f7f0-110">credentialType</span></span>|<span data-ttu-id="0f7f0-111">Opcional.</span><span class="sxs-lookup"><span data-stu-id="0f7f0-111">Optional.</span></span> <span data-ttu-id="0f7f0-112">Especifica o tipo de credenciais usadas para verificar as mensagens enviadas com o transporte de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="0f7f0-112">Specifies the type of credentials used to verify messages sent with the peer transport.</span></span> <span data-ttu-id="0f7f0-113">Esse atributo é do tipo <xref:System.ServiceModel.PeerTransportCredentialType> .</span><span class="sxs-lookup"><span data-stu-id="0f7f0-113">This attribute is of type <xref:System.ServiceModel.PeerTransportCredentialType>.</span></span>|  
  
## <a name="credentialtype-attribute"></a><span data-ttu-id="0f7f0-114">Atributo CredentialType</span><span class="sxs-lookup"><span data-stu-id="0f7f0-114">credentialType Attribute</span></span>  
  
|<span data-ttu-id="0f7f0-115">Valor</span><span class="sxs-lookup"><span data-stu-id="0f7f0-115">Value</span></span>|<span data-ttu-id="0f7f0-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f7f0-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f7f0-117">Certificado</span><span class="sxs-lookup"><span data-stu-id="0f7f0-117">Certificate</span></span>|<span data-ttu-id="0f7f0-118">A autenticação do transporte de canal par requer um certificado X509.</span><span class="sxs-lookup"><span data-stu-id="0f7f0-118">Authentication of the peer channel transport requires an X509 certificate.</span></span>|  
|<span data-ttu-id="0f7f0-119">Senha</span><span class="sxs-lookup"><span data-stu-id="0f7f0-119">Password</span></span>|<span data-ttu-id="0f7f0-120">A autenticação do transporte de canal par requer uma senha correta.</span><span class="sxs-lookup"><span data-stu-id="0f7f0-120">Authentication of the peer channel transport requires a correct password.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f7f0-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0f7f0-121">Child Elements</span></span>  
 <span data-ttu-id="0f7f0-122">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0f7f0-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f7f0-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0f7f0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0f7f0-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f7f0-124">Element</span></span>|<span data-ttu-id="0f7f0-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f7f0-125">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="0f7f0-126">Define as configurações de segurança para o [\<netPeerTcpBinding>](netpeertcpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="0f7f0-126">Defines the security settings for the [\<netPeerTcpBinding>](netpeertcpbinding.md).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0f7f0-127">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f7f0-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>
- <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>
- <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>
- <xref:System.ServiceModel.PeerTransportSecuritySettings>
- [<span data-ttu-id="0f7f0-128">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0f7f0-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="0f7f0-129">Associações</span><span class="sxs-lookup"><span data-stu-id="0f7f0-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0f7f0-130">Configurando associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="0f7f0-130">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="0f7f0-131">Usando associações para configurar serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="0f7f0-131">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
