---
title: <authentication>do <serviceCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398223"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="a2789-102">\<> de autenticação \<do elemento > de certificado</span><span class="sxs-lookup"><span data-stu-id="a2789-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="a2789-103">Especifica as configurações usadas pelo proxy do cliente para autenticar certificados de serviço que são obtidos usando a negociação SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="a2789-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
<span data-ttu-id="a2789-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="a2789-105">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="a2789-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="a2789-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="a2789-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="a2789-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="a2789-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de certificados**](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="a2789-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="a2789-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de autenticação**</span><span class="sxs-lookup"><span data-stu-id="a2789-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2789-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a2789-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2789-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a2789-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a2789-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a2789-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2789-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a2789-115">Attributes</span></span>  
  
|<span data-ttu-id="a2789-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="a2789-116">Attribute</span></span>|<span data-ttu-id="a2789-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2789-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a2789-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="a2789-118">customCertificateValidatorType</span></span>|<span data-ttu-id="a2789-119">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="a2789-119">String.</span></span> <span data-ttu-id="a2789-120">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a2789-120">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="a2789-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a2789-121">certificateValidationMode</span></span>|<span data-ttu-id="a2789-122">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="a2789-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a2789-123">Se definido como `Custom`, um customCertificateValidator também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="a2789-123">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="a2789-124">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a2789-124">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="a2789-125">revocationMode</span><span class="sxs-lookup"><span data-stu-id="a2789-125">revocationMode</span></span>|<span data-ttu-id="a2789-126">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="a2789-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="a2789-127">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="a2789-127">The default is `Online`.</span></span>|  
|<span data-ttu-id="a2789-128">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a2789-128">trustedStoreLocation</span></span>|<span data-ttu-id="a2789-129">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="a2789-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a2789-130">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a2789-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a2789-131">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="a2789-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="a2789-132">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a2789-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="a2789-133">Atributo customCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="a2789-133">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="a2789-134">Valor</span><span class="sxs-lookup"><span data-stu-id="a2789-134">Value</span></span>|<span data-ttu-id="a2789-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2789-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a2789-136">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="a2789-136">String</span></span>|<span data-ttu-id="a2789-137">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="a2789-137">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a2789-138">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a2789-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a2789-139">Valor</span><span class="sxs-lookup"><span data-stu-id="a2789-139">Value</span></span>|<span data-ttu-id="a2789-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2789-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a2789-141">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a2789-141">Enumeration</span></span>|<span data-ttu-id="a2789-142">Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="a2789-142">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="a2789-143">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a2789-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a2789-144">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="a2789-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a2789-145">Valor</span><span class="sxs-lookup"><span data-stu-id="a2789-145">Value</span></span>|<span data-ttu-id="a2789-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2789-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a2789-147">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a2789-147">Enumeration</span></span>|<span data-ttu-id="a2789-148">Um dos seguintes valores: NOCHECK, online, offline.</span><span class="sxs-lookup"><span data-stu-id="a2789-148">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="a2789-149">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a2789-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a2789-150">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a2789-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a2789-151">Valor</span><span class="sxs-lookup"><span data-stu-id="a2789-151">Value</span></span>|<span data-ttu-id="a2789-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2789-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a2789-153">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a2789-153">Enumeration</span></span>|<span data-ttu-id="a2789-154">Um dos seguintes valores: LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a2789-154">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="a2789-155">O padrão é CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a2789-155">The default is CurrentUser.</span></span> <span data-ttu-id="a2789-156">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado normalmente estará em LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a2789-156">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="a2789-157">Se o aplicativo cliente estiver sendo executado em uma conta de usuário, o certificado normalmente será em CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a2789-157">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2789-158">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a2789-158">Child Elements</span></span>  
 <span data-ttu-id="a2789-159">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a2789-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2789-160">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a2789-160">Parent Elements</span></span>  
  
|<span data-ttu-id="a2789-161">Elemento</span><span class="sxs-lookup"><span data-stu-id="a2789-161">Element</span></span>|<span data-ttu-id="a2789-162">Descrição</span><span class="sxs-lookup"><span data-stu-id="a2789-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a2789-163">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="a2789-163">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a2789-164">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a2789-164">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2789-165">Comentários</span><span class="sxs-lookup"><span data-stu-id="a2789-165">Remarks</span></span>  
 <span data-ttu-id="a2789-166">O `certificateValidationMode` atributo desse elemento de configuração especifica o nível de confiança usado para autenticar certificados.</span><span class="sxs-lookup"><span data-stu-id="a2789-166">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="a2789-167">Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que termina em uma autoridade de certificação confiável na parte superior da cadeia.</span><span class="sxs-lookup"><span data-stu-id="a2789-167">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="a2789-168">Esse é o modo mais seguro.</span><span class="sxs-lookup"><span data-stu-id="a2789-168">This is the most secure mode.</span></span> <span data-ttu-id="a2789-169">Você também pode definir o valor como `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (peer Trust) são aceitos, bem como certificados que estão em uma cadeia confiável.</span><span class="sxs-lookup"><span data-stu-id="a2789-169">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="a2789-170">Esse valor é usado ao desenvolver e depurar clientes e serviços porque certificados emitidos por conta própria não precisam ser comprados de uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="a2789-170">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="a2789-171">Ao implantar um cliente, use o `ChainTrust` valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a2789-171">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="a2789-172">Você também pode definir o valor para `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="a2789-172">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="a2789-173">Para usar o valor `Custom`, você também deverá definir o atributo `customCertificateValidator` para um assembly e um tipo usados para validar o certificado.</span><span class="sxs-lookup"><span data-stu-id="a2789-173">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="a2789-174">Para criar seu próprio validador personalizado, você deve herdar da classe abstrata X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="a2789-174">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="a2789-175">Para obter mais informações, confira [Como: Crie um serviço que empregue um validador](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)de certificado personalizado.</span><span class="sxs-lookup"><span data-stu-id="a2789-175">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="a2789-176">O `revocationMode` atributo especifica como os certificados são verificados para revogação.</span><span class="sxs-lookup"><span data-stu-id="a2789-176">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="a2789-177">O padrão é `online` que indica que os certificados serão verificados automaticamente para revogação.</span><span class="sxs-lookup"><span data-stu-id="a2789-177">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="a2789-178">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a2789-178">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2789-179">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a2789-179">Example</span></span>  
 <span data-ttu-id="a2789-180">O exemplo a seguir executa duas tarefas.</span><span class="sxs-lookup"><span data-stu-id="a2789-180">The following example does two tasks.</span></span> <span data-ttu-id="a2789-181">Ele especifica primeiro um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome de `www.contoso.com` domínio está sobre o protocolo http.</span><span class="sxs-lookup"><span data-stu-id="a2789-181">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="a2789-182">Em segundo lugar, ele especifica o modo de revogação e o local de armazenamento usados durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="a2789-182">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="a2789-183">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2789-183">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="a2789-184">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="a2789-184">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a2789-185">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a2789-185">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a2789-186">Como: Criar um serviço que empregue um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="a2789-186">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="a2789-187">\<authentication></span><span class="sxs-lookup"><span data-stu-id="a2789-187">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="a2789-188">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="a2789-188">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a2789-189">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a2789-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
