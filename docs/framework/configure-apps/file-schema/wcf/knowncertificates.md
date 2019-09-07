---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400330"
---
# <a name="knowncertificates"></a><span data-ttu-id="b4d6f-101">\<knownCertificates></span><span class="sxs-lookup"><span data-stu-id="b4d6f-101">\<knownCertificates></span></span>
<span data-ttu-id="b4d6f-102">Representa uma coleção de certificados X. 509 que são fornecidos para autenticar credenciais de segurança emitidas de um serviço de token de segurança (STS).</span><span class="sxs-lookup"><span data-stu-id="b4d6f-102">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
<span data-ttu-id="b4d6f-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b4d6f-104">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="b4d6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="b4d6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="b4d6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="b4d6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCredentials >** ](servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)</span></span>\
<span data-ttu-id="b4d6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> issuedTokenAuthentication**](issuedtokenauthentication-of-servicecredentials.md)</span><span class="sxs-lookup"><span data-stu-id="b4d6f-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)</span></span>\
<span data-ttu-id="b4d6f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> knownCertificates**</span><span class="sxs-lookup"><span data-stu-id="b4d6f-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4d6f-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b4d6f-111">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b4d6f-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b4d6f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b4d6f-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="b4d6f-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b4d6f-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b4d6f-114">Attributes</span></span>  
 <span data-ttu-id="b4d6f-115">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b4d6f-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b4d6f-116">Child Elements</span></span>  
  
|<span data-ttu-id="b4d6f-117">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4d6f-117">Element</span></span>|<span data-ttu-id="b4d6f-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4d6f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4d6f-119">\<add></span><span class="sxs-lookup"><span data-stu-id="b4d6f-119">\<add></span></span>](add-of-knowncertificates.md)|<span data-ttu-id="b4d6f-120">Adiciona um certificado X. 509 à coleção.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b4d6f-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b4d6f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="b4d6f-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="b4d6f-122">Element</span></span>|<span data-ttu-id="b4d6f-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="b4d6f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b4d6f-124">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="b4d6f-124">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="b4d6f-125">Especifica um token emitido como uma credencial de serviço.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d6f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b4d6f-126">Remarks</span></span>  
 <span data-ttu-id="b4d6f-127">O cenário de token emitido tem três estágios.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="b4d6f-128">No primeiro estágio, um cliente que tenta acessar um serviço é chamado de um *serviço de token seguro*.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="b4d6f-129">O serviço de token seguro autentica o cliente e subsequentemente emite um token do cliente, normalmente um token SAML (Security Assertion Markup Language).</span><span class="sxs-lookup"><span data-stu-id="b4d6f-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="b4d6f-130">O cliente retorna ao serviço com o token.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="b4d6f-131">O serviço examina o token de dados que permite que o serviço autentique o token e, portanto, o cliente.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="b4d6f-132">Para autenticar o token, o certificado que o serviço de token seguro usa deve ser conhecido pelo serviço.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="b4d6f-133">O elemento de [ \<> issuedTokenAuthentication](issuedtokenauthentication-of-servicecredentials.md) é o repositório para qualquer certificado de serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-133">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="b4d6f-134">Para adicionar certificados, use o [ \<elemento de > knownCertificates](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="b4d6f-134">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="b4d6f-135">Insira um [ \<> Adicionar](add-of-knowncertificates.md) para cada certificado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-135">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="b4d6f-136">Por padrão, os certificados devem ser obtidos de um serviço de token seguro.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="b4d6f-137">Esses certificados "conhecidos" garantem que somente clientes legítimos possam acessar um serviço.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="b4d6f-138">Para revisar as condições necessárias para um cliente ser autenticado por um serviço federado, bem como mais informações sobre como usar esse elemento de [configuração, consulte Como: Configure as credenciais em um](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)serviço de Federação.</span><span class="sxs-lookup"><span data-stu-id="b4d6f-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="b4d6f-139">Para obter mais informações sobre cenários federados, consulte [Federação e tokens emitidos](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="b4d6f-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="b4d6f-140">Para obter um exemplo que mostra como preencher a coleção na configuração, consulte [ \<Adicionar >](add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="b4d6f-140">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d6f-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b4d6f-141">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [<span data-ttu-id="b4d6f-142">\<add></span><span class="sxs-lookup"><span data-stu-id="b4d6f-142">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="b4d6f-143">\<issuedTokenAuthentication></span><span class="sxs-lookup"><span data-stu-id="b4d6f-143">\<issuedTokenAuthentication></span></span>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="b4d6f-144">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b4d6f-144">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="b4d6f-145">Como: Configurar credenciais em um Serviço de Federação</span><span class="sxs-lookup"><span data-stu-id="b4d6f-145">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="b4d6f-146">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="b4d6f-146">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b4d6f-147">Federação e tokens emitidos</span><span class="sxs-lookup"><span data-stu-id="b4d6f-147">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [<span data-ttu-id="b4d6f-148">\<add></span><span class="sxs-lookup"><span data-stu-id="b4d6f-148">\<add></span></span>](add-of-knowncertificates.md)
- [<span data-ttu-id="b4d6f-149">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="b4d6f-149">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
