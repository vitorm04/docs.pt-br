---
title: <serviceCertificate>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: a3013d0f7efd3014892cf6400447d708809c5fcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936337"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="41865-102">\<> de userCertificate do \<elemento > ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="41865-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="41865-103">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="41865-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="41865-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="41865-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="41865-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="41865-105">\<behaviors></span></span>  
<span data-ttu-id="41865-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="41865-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="41865-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="41865-107">\<behavior></span></span>  
<span data-ttu-id="41865-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="41865-108">\<clientCredentials></span></span>  
<span data-ttu-id="41865-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="41865-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41865-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41865-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41865-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41865-111">Attributes and Elements</span></span>  
 <span data-ttu-id="41865-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41865-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41865-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="41865-113">Attributes</span></span>  
 <span data-ttu-id="41865-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="41865-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41865-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41865-115">Child Elements</span></span>  
  
|<span data-ttu-id="41865-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="41865-116">Element</span></span>|<span data-ttu-id="41865-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="41865-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41865-118">\<defaultCertificate></span><span class="sxs-lookup"><span data-stu-id="41865-118">\<defaultCertificate></span></span>](defaultcertificate-element.md)|<span data-ttu-id="41865-119">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="41865-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="41865-120">\<scopedCertificates></span><span class="sxs-lookup"><span data-stu-id="41865-120">\<scopedCertificates></span></span>](scopedcertificates-element.md)|<span data-ttu-id="41865-121">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="41865-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="41865-122">Normalmente, essa coleção é usada para especificar os certificados de serviço para serviços de token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="41865-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="41865-123">\<authentication></span><span class="sxs-lookup"><span data-stu-id="41865-123">\<authentication></span></span>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="41865-124">Especifica comportamentos de autenticação para certificados de serviço usados por um cliente.</span><span class="sxs-lookup"><span data-stu-id="41865-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41865-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41865-125">Parent Elements</span></span>  
  
|<span data-ttu-id="41865-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="41865-126">Element</span></span>|<span data-ttu-id="41865-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="41865-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="41865-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="41865-128">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="41865-129">Especifica as credenciais usadas pelo cliente para se autenticar em um serviço.</span><span class="sxs-lookup"><span data-stu-id="41865-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41865-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="41865-130">Remarks</span></span>  
 <span data-ttu-id="41865-131">Esse elemento de configuração especifica as configurações usadas pelo cliente para validar o certificado apresentado pelo serviço usando a autenticação SSL.</span><span class="sxs-lookup"><span data-stu-id="41865-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="41865-132">Também contém um certificado para o serviço que é explicitamente configurado no cliente a ser usado para criptografar mensagens para o serviço usando a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="41865-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="41865-133">Os atributos do `serviceCertificate` elemento são idênticos aos atributos [ \<do > clientCertificate](clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="41865-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41865-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="41865-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="41865-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="41865-135">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="41865-136">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="41865-136">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="41865-137">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="41865-137">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="41865-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="41865-138">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
