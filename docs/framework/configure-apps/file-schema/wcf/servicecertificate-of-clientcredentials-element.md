---
title: <serviceCertificate>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399679"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="5f0ac-102">\<> de userCertificate do \<elemento > ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="5f0ac-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="5f0ac-103">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
<span data-ttu-id="5f0ac-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5f0ac-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5f0ac-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5f0ac-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5f0ac-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5f0ac-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5f0ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5f0ac-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="5f0ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5f0ac-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="5f0ac-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="5f0ac-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="5f0ac-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de certificados**</span><span class="sxs-lookup"><span data-stu-id="5f0ac-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0ac-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5f0ac-111">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5f0ac-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5f0ac-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5f0ac-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5f0ac-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="5f0ac-114">Attributes</span></span>  
 <span data-ttu-id="5f0ac-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="5f0ac-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5f0ac-116">Child Elements</span></span>  
  
|<span data-ttu-id="5f0ac-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f0ac-117">Element</span></span>|<span data-ttu-id="5f0ac-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f0ac-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f0ac-119">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="5f0ac-119">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="5f0ac-120">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-120">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="5f0ac-121">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="5f0ac-121">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="5f0ac-122">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-122">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="5f0ac-123">Normalmente, essa coleção é usada para especificar os certificados de serviço para serviços de token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-123">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="5f0ac-124">\<authentication></span><span class="sxs-lookup"><span data-stu-id="5f0ac-124">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="5f0ac-125">Especifica comportamentos de autenticação para certificados de serviço usados por um cliente.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-125">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5f0ac-126">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5f0ac-126">Parent Elements</span></span>  
  
|<span data-ttu-id="5f0ac-127">Elemento</span><span class="sxs-lookup"><span data-stu-id="5f0ac-127">Element</span></span>|<span data-ttu-id="5f0ac-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="5f0ac-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5f0ac-129">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5f0ac-129">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="5f0ac-130">Especifica as credenciais usadas pelo cliente para se autenticar em um serviço.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-130">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f0ac-131">Comentários</span><span class="sxs-lookup"><span data-stu-id="5f0ac-131">Remarks</span></span>  
 <span data-ttu-id="5f0ac-132">Esse elemento de configuração especifica as configurações usadas pelo cliente para validar o certificado apresentado pelo serviço usando a autenticação SSL.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-132">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="5f0ac-133">Também contém um certificado para o serviço que é explicitamente configurado no cliente a ser usado para criptografar mensagens para o serviço usando a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5f0ac-133">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="5f0ac-134">Os atributos do `serviceCertificate` elemento são idênticos aos atributos [ \<do > clientCertificate](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="5f0ac-134">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0ac-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5f0ac-135">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="5f0ac-136">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="5f0ac-136">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="5f0ac-137">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="5f0ac-137">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="5f0ac-138">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="5f0ac-138">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5f0ac-139">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="5f0ac-139">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
