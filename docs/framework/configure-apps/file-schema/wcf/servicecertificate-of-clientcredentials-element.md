---
title: <serviceCertificate>do <clientCredentials> elemento
ms.date: 03/30/2017
ms.assetid: e50c0ac5-f0df-4c90-b54b-fc602c1f84ea
ms.openlocfilehash: 4c7489a171bdd5cb4b747ca99f1b7ff6dd65517b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399679"
---
# <a name="servicecertificate-of-clientcredentials-element"></a><span data-ttu-id="6c464-102">\<serviceCertificate>do \<clientCredentials> elemento</span><span class="sxs-lookup"><span data-stu-id="6c464-102">\<serviceCertificate> of \<clientCredentials> Element</span></span>
<span data-ttu-id="6c464-103">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="6c464-103">Specifies a certificate to use when authenticating a service to the client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceCertificate>**  
  
## <a name="syntax"></a><span data-ttu-id="6c464-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6c464-104">Syntax</span></span>  
  
```xml  
<serviceCertificate />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6c464-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6c464-105">Attributes and Elements</span></span>  
 <span data-ttu-id="6c464-106">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6c464-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6c464-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="6c464-107">Attributes</span></span>  
 <span data-ttu-id="6c464-108">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="6c464-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="6c464-109">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6c464-109">Child Elements</span></span>  
  
|<span data-ttu-id="6c464-110">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c464-110">Element</span></span>|<span data-ttu-id="6c464-111">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c464-111">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultCertificate>](defaultcertificate-element.md)|<span data-ttu-id="6c464-112">Especifica um certificado X. 509 a ser usado quando um serviço ou STS não fornecer um por meio de um protocolo de negociação.</span><span class="sxs-lookup"><span data-stu-id="6c464-112">Specifies an X.509 certificate to be used when a service or STS does not provide one via a negotiation protocol.</span></span>|  
|[\<scopedCertificates>](scopedcertificates-element.md)|<span data-ttu-id="6c464-113">Representa uma coleção de certificados X. 509 fornecidos por serviços específicos (com escopo) para autenticação.</span><span class="sxs-lookup"><span data-stu-id="6c464-113">Represents a collection of X.509 certificates provided by specific services (scoped) for authentication.</span></span> <span data-ttu-id="6c464-114">Normalmente, essa coleção é usada para especificar os certificados de serviço para serviços de token de segurança em um cenário federado.</span><span class="sxs-lookup"><span data-stu-id="6c464-114">This collection is typically used to specify the service certificates for Security Token Services in a federated scenario.</span></span>|  
|[\<authentication>](authentication-of-servicecertificate-element.md)|<span data-ttu-id="6c464-115">Especifica comportamentos de autenticação para certificados de serviço usados por um cliente.</span><span class="sxs-lookup"><span data-stu-id="6c464-115">Specifies authentication behaviors for service certificates used by a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6c464-116">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6c464-116">Parent Elements</span></span>  
  
|<span data-ttu-id="6c464-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="6c464-117">Element</span></span>|<span data-ttu-id="6c464-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="6c464-118">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="6c464-119">Especifica as credenciais usadas pelo cliente para se autenticar em um serviço.</span><span class="sxs-lookup"><span data-stu-id="6c464-119">Specifies the credentials used by the client to authenticate itself to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6c464-120">Comentários</span><span class="sxs-lookup"><span data-stu-id="6c464-120">Remarks</span></span>  
 <span data-ttu-id="6c464-121">Esse elemento de configuração especifica as configurações usadas pelo cliente para validar o certificado apresentado pelo serviço usando a autenticação SSL.</span><span class="sxs-lookup"><span data-stu-id="6c464-121">This configuration element specifies the settings used by the client to validate the certificate presented by the service using SSL authentication.</span></span> <span data-ttu-id="6c464-122">Também contém um certificado para o serviço que é explicitamente configurado no cliente a ser usado para criptografar mensagens para o serviço usando a segurança de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6c464-122">It also contains any certificate for the service that is explicitly configured on the client to use for encrypting messages to the service using message security.</span></span>  
  
 <span data-ttu-id="6c464-123">Os atributos do `serviceCertificate` elemento são idênticos aos atributos do [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md) .</span><span class="sxs-lookup"><span data-stu-id="6c464-123">The attributes of the `serviceCertificate` element are identical to the attributes of the [\<clientCertificate>](clientcertificate-of-clientcredentials-element.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c464-124">Confira também</span><span class="sxs-lookup"><span data-stu-id="6c464-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.ServiceCertificate%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>
- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- [<span data-ttu-id="6c464-125">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="6c464-125">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6c464-126">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="6c464-126">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="6c464-127">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="6c464-127">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6c464-128">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6c464-128">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
