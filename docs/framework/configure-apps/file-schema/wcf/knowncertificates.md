---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400330"
---
# \<knownCertificates>
<span data-ttu-id="3c664-101">Representa uma coleção de certificados X. 509 que são fornecidos para autenticar credenciais de segurança emitidas de um serviço de token de segurança (STS).</span><span class="sxs-lookup"><span data-stu-id="3c664-101">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="3c664-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3c664-102">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3c664-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3c664-103">Attributes and Elements</span></span>  
 <span data-ttu-id="3c664-104">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c664-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3c664-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="3c664-105">Attributes</span></span>  
 <span data-ttu-id="3c664-106">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="3c664-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3c664-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3c664-107">Child Elements</span></span>  
  
|<span data-ttu-id="3c664-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c664-108">Element</span></span>|<span data-ttu-id="3c664-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c664-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="3c664-110">Adiciona um certificado X. 509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="3c664-110">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3c664-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3c664-111">Parent Elements</span></span>  
  
|<span data-ttu-id="3c664-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="3c664-112">Element</span></span>|<span data-ttu-id="3c664-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3c664-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="3c664-114">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="3c664-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3c664-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="3c664-115">Remarks</span></span>  
 <span data-ttu-id="3c664-116">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="3c664-116">The issued token scenario has three stages.</span></span> <span data-ttu-id="3c664-117">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="3c664-117">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="3c664-118">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="3c664-118">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="3c664-119">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="3c664-119">The client then returns to the service with the token.</span></span> <span data-ttu-id="3c664-120">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="3c664-120">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="3c664-121">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="3c664-121">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="3c664-122">O [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) elemento é o repositório para qualquer certificado de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="3c664-122">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="3c664-123">Para adicionar certificados, use o [ \<knownCertificates> elemento](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="3c664-123">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="3c664-124">Insira um [\<add>](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="3c664-124">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="3c664-125">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="3c664-125">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="3c664-126">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="3c664-126">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="3c664-127">Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de configuração, consulte [como configurar credenciais em um serviço de Federação](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="3c664-127">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="3c664-128">Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="3c664-128">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="3c664-129">Para obter um exemplo que mostra como preencher a coleção na configuração, consulte [\<add>](add-of-knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="3c664-129">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c664-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="3c664-130">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="3c664-131">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="3c664-131">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3c664-132">Como configurar credenciais em um serviço de federação</span><span class="sxs-lookup"><span data-stu-id="3c664-132">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="3c664-133">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="3c664-133">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3c664-134">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="3c664-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="3c664-135">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="3c664-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
