---
title: <authentication>do <serviceCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: d770ba1f9a0a18c927b3a4bf6d4141286e3a380c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919991"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="7ba72-102">\<> de autenticação \<do elemento > de certificado</span><span class="sxs-lookup"><span data-stu-id="7ba72-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="7ba72-103">Especifica as configurações usadas pelo proxy do cliente para autenticar certificados de serviço que são obtidos usando a negociação SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="7ba72-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="7ba72-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7ba72-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ba72-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="7ba72-105">\<behaviors></span></span>  
<span data-ttu-id="7ba72-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="7ba72-106">endpointBehaviors section</span></span>  
<span data-ttu-id="7ba72-107">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="7ba72-107">\<behavior></span></span>  
<span data-ttu-id="7ba72-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="7ba72-108">\<clientCredentials></span></span>  
<span data-ttu-id="7ba72-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="7ba72-109">\<serviceCertificate></span></span>  
<span data-ttu-id="7ba72-110">\<> de autenticação</span><span class="sxs-lookup"><span data-stu-id="7ba72-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ba72-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ba72-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ba72-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7ba72-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7ba72-113">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="7ba72-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ba72-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="7ba72-114">Attributes</span></span>  
  
|<span data-ttu-id="7ba72-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="7ba72-115">Attribute</span></span>|<span data-ttu-id="7ba72-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba72-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7ba72-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="7ba72-117">customCertificateValidatorType</span></span>|<span data-ttu-id="7ba72-118">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="7ba72-118">String.</span></span> <span data-ttu-id="7ba72-119">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="7ba72-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="7ba72-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7ba72-120">certificateValidationMode</span></span>|<span data-ttu-id="7ba72-121">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="7ba72-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="7ba72-122">Se definido como `Custom`, um customCertificateValidator também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="7ba72-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="7ba72-123">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7ba72-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="7ba72-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7ba72-124">revocationMode</span></span>|<span data-ttu-id="7ba72-125">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="7ba72-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="7ba72-126">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="7ba72-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="7ba72-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7ba72-127">trustedStoreLocation</span></span>|<span data-ttu-id="7ba72-128">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="7ba72-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7ba72-129">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7ba72-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="7ba72-130">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="7ba72-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="7ba72-131">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7ba72-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="7ba72-132">Atributo customCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="7ba72-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="7ba72-133">Valor</span><span class="sxs-lookup"><span data-stu-id="7ba72-133">Value</span></span>|<span data-ttu-id="7ba72-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba72-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ba72-135">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="7ba72-135">String</span></span>|<span data-ttu-id="7ba72-136">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="7ba72-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="7ba72-137">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7ba72-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="7ba72-138">Valor</span><span class="sxs-lookup"><span data-stu-id="7ba72-138">Value</span></span>|<span data-ttu-id="7ba72-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba72-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ba72-140">Enumeração</span><span class="sxs-lookup"><span data-stu-id="7ba72-140">Enumeration</span></span>|<span data-ttu-id="7ba72-141">Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="7ba72-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="7ba72-142">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7ba72-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="7ba72-143">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="7ba72-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="7ba72-144">Valor</span><span class="sxs-lookup"><span data-stu-id="7ba72-144">Value</span></span>|<span data-ttu-id="7ba72-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba72-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ba72-146">Enumeração</span><span class="sxs-lookup"><span data-stu-id="7ba72-146">Enumeration</span></span>|<span data-ttu-id="7ba72-147">Um dos seguintes valores: NOCHECK, online, offline.</span><span class="sxs-lookup"><span data-stu-id="7ba72-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="7ba72-148">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7ba72-148">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="7ba72-149">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7ba72-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="7ba72-150">Valor</span><span class="sxs-lookup"><span data-stu-id="7ba72-150">Value</span></span>|<span data-ttu-id="7ba72-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba72-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7ba72-152">Enumeração</span><span class="sxs-lookup"><span data-stu-id="7ba72-152">Enumeration</span></span>|<span data-ttu-id="7ba72-153">Um dos seguintes valores: LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7ba72-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="7ba72-154">O padrão é CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7ba72-154">The default is CurrentUser.</span></span> <span data-ttu-id="7ba72-155">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado normalmente estará em LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="7ba72-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="7ba72-156">Se o aplicativo cliente estiver sendo executado em uma conta de usuário, o certificado normalmente será em CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7ba72-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7ba72-157">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7ba72-157">Child Elements</span></span>  
 <span data-ttu-id="7ba72-158">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="7ba72-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7ba72-159">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7ba72-159">Parent Elements</span></span>  
  
|<span data-ttu-id="7ba72-160">Elemento</span><span class="sxs-lookup"><span data-stu-id="7ba72-160">Element</span></span>|<span data-ttu-id="7ba72-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="7ba72-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ba72-162">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="7ba72-162">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="7ba72-163">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="7ba72-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ba72-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ba72-164">Remarks</span></span>  
 <span data-ttu-id="7ba72-165">O `certificateValidationMode` atributo desse elemento de configuração especifica o nível de confiança usado para autenticar certificados.</span><span class="sxs-lookup"><span data-stu-id="7ba72-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="7ba72-166">Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que termina em uma autoridade de certificação confiável na parte superior da cadeia.</span><span class="sxs-lookup"><span data-stu-id="7ba72-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="7ba72-167">Esse é o modo mais seguro.</span><span class="sxs-lookup"><span data-stu-id="7ba72-167">This is the most secure mode.</span></span> <span data-ttu-id="7ba72-168">Você também pode definir o valor como `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (peer Trust) são aceitos, bem como certificados que estão em uma cadeia confiável.</span><span class="sxs-lookup"><span data-stu-id="7ba72-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="7ba72-169">Esse valor é usado ao desenvolver e depurar clientes e serviços porque certificados emitidos por conta própria não precisam ser comprados de uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="7ba72-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="7ba72-170">Ao implantar um cliente, use o `ChainTrust` valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="7ba72-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="7ba72-171">Você também pode definir o valor para `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="7ba72-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="7ba72-172">Para usar o valor `Custom`, você também deverá definir o atributo `customCertificateValidator` para um assembly e um tipo usados para validar o certificado.</span><span class="sxs-lookup"><span data-stu-id="7ba72-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="7ba72-173">Para criar seu próprio validador personalizado, você deve herdar da classe abstrata X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="7ba72-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="7ba72-174">Para obter mais informações, confira [Como: Crie um serviço que empregue um validador](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)de certificado personalizado.</span><span class="sxs-lookup"><span data-stu-id="7ba72-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="7ba72-175">O `revocationMode` atributo especifica como os certificados são verificados para revogação.</span><span class="sxs-lookup"><span data-stu-id="7ba72-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="7ba72-176">O padrão é `online` que indica que os certificados serão verificados automaticamente para revogação.</span><span class="sxs-lookup"><span data-stu-id="7ba72-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="7ba72-177">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7ba72-177">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7ba72-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ba72-178">Example</span></span>  
 <span data-ttu-id="7ba72-179">O exemplo a seguir executa duas tarefas.</span><span class="sxs-lookup"><span data-stu-id="7ba72-179">The following example does two tasks.</span></span> <span data-ttu-id="7ba72-180">Ele especifica primeiro um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome de `www.contoso.com` domínio está sobre o protocolo http.</span><span class="sxs-lookup"><span data-stu-id="7ba72-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="7ba72-181">Em segundo lugar, ele especifica o modo de revogação e o local de armazenamento usados durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="7ba72-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7ba72-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7ba72-182">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="7ba72-183">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="7ba72-183">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7ba72-184">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="7ba72-184">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7ba72-185">Como: Criar um serviço que empregue um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="7ba72-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="7ba72-186">\<authentication></span><span class="sxs-lookup"><span data-stu-id="7ba72-186">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="7ba72-187">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="7ba72-187">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7ba72-188">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="7ba72-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
