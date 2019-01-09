---
title: '&lt;serviceCertificate&gt; de elemento &lt;clientCredentials&gt;'
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 82fb39f15ea0dbf38d9c9b41d7fbdd50daebb823
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54151976"
---
# <a name="ltservicecertificategt-of-ltclientcredentialsgt-element"></a><span data-ttu-id="341be-102">&lt;serviceCertificate&gt; de elemento &lt;clientCredentials&gt;</span><span class="sxs-lookup"><span data-stu-id="341be-102">&lt;serviceCertificate&gt; of &lt;clientCredentials&gt; Element</span></span>
<span data-ttu-id="341be-103">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="341be-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
 <span data-ttu-id="341be-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="341be-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="341be-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="341be-105">\<behaviors></span></span>  
<span data-ttu-id="341be-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="341be-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="341be-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="341be-107">\<behavior></span></span>  
<span data-ttu-id="341be-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="341be-108">\<clientCredentials></span></span>  
<span data-ttu-id="341be-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="341be-109">\<serviceCertificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="341be-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="341be-110">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="341be-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="341be-111">Attributes and Elements</span></span>  
 <span data-ttu-id="341be-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="341be-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="341be-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="341be-113">Attributes</span></span>  
 <span data-ttu-id="341be-114">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="341be-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="341be-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="341be-115">Child Elements</span></span>  
  
|<span data-ttu-id="341be-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="341be-116">Element</span></span>|<span data-ttu-id="341be-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="341be-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="341be-118">\<defaultCertificate ></span><span class="sxs-lookup"><span data-stu-id="341be-118">\<defaultCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultcertificate-element.md)|<span data-ttu-id="341be-119">Especifica um certificado X.509 a ser usado quando um serviço ou STS não fornece um através de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="341be-119">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[<span data-ttu-id="341be-120">\<scopedCertificates ></span><span class="sxs-lookup"><span data-stu-id="341be-120">\<scopedCertificates></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopedcertificates-element.md)|<span data-ttu-id="341be-121">Representa uma coleção de certificados X.509 fornecidos por serviços específicos (escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="341be-121">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="341be-122">Essa coleção é normalmente usada para especificar os certificados de serviço para serviços de Token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="341be-122">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[<span data-ttu-id="341be-123">\<authentication></span><span class="sxs-lookup"><span data-stu-id="341be-123">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-servicecertificate-element.md)|<span data-ttu-id="341be-124">Especifica os comportamentos de autenticação para certificados de serviço usados por um cliente.</span><span class="sxs-lookup"><span data-stu-id="341be-124">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="341be-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="341be-125">Parent Elements</span></span>  
  
|<span data-ttu-id="341be-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="341be-126">Element</span></span>|<span data-ttu-id="341be-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="341be-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="341be-128">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="341be-128">\<clientCredentials></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|<span data-ttu-id="341be-129">Especifica as credenciais usadas pelo cliente para se autenticar em um serviço.</span><span class="sxs-lookup"><span data-stu-id="341be-129">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="341be-130">Comentários</span><span class="sxs-lookup"><span data-stu-id="341be-130">Remarks</span></span>  
 <span data-ttu-id="341be-131">Este elemento de configuração especifica as configurações usadas pelo cliente para validar o certificado apresentado pelo serviço usando a autenticação SSL.</span><span class="sxs-lookup"><span data-stu-id="341be-131">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="341be-132">Também contém um certificado para o serviço que é explicitamente configurado no cliente a ser usado para criptografar mensagens para o serviço usando a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="341be-132">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="341be-133">Os atributos do `serviceCertificate` elemento são idênticos aos atributos do [ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span><span class="sxs-lookup"><span data-stu-id="341be-133">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="341be-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="341be-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 [<span data-ttu-id="341be-135">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="341be-135">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="341be-136">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="341be-136">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="341be-137">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="341be-137">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="341be-138">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="341be-138">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
