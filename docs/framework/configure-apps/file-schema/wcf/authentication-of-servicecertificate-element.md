---
title: "&lt;autenticação&gt; do elemento &lt;serviceCertificate&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cb2f567b47f66b378cc6e0a5d5e96441ea65c1ac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a><span data-ttu-id="6f55b-102">&lt;autenticação&gt; do elemento &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="6f55b-102">&lt;authentication&gt; of &lt;serviceCertificate&gt; Element</span></span>
<span data-ttu-id="6f55b-103">Especifica as configurações usadas pelo proxy do cliente para autenticar certificados de serviço que são obtidos usando negociação SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="6f55b-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="6f55b-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="6f55b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6f55b-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="6f55b-105">\<behaviors></span></span>  
<span data-ttu-id="6f55b-106">seção endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="6f55b-106">endpointBehaviors section</span></span>  
<span data-ttu-id="6f55b-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="6f55b-107">\<behavior></span></span>  
<span data-ttu-id="6f55b-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="6f55b-108">\<clientCredentials></span></span>  
<span data-ttu-id="6f55b-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="6f55b-109">\<serviceCertificate></span></span>  
<span data-ttu-id="6f55b-110">\<autenticação ></span><span class="sxs-lookup"><span data-stu-id="6f55b-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f55b-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f55b-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f55b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6f55b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6f55b-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f55b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f55b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6f55b-114">Attributes</span></span>  
  
|<span data-ttu-id="6f55b-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="6f55b-115">Attribute</span></span>|<span data-ttu-id="6f55b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f55b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6f55b-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="6f55b-117">customCertificateValidatorType</span></span>|<span data-ttu-id="6f55b-118">Cadeia.</span><span class="sxs-lookup"><span data-stu-id="6f55b-118">String.</span></span> <span data-ttu-id="6f55b-119">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6f55b-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="6f55b-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="6f55b-120">certificateValidationMode</span></span>|<span data-ttu-id="6f55b-121">Especifica um dos três modos usados para validar credenciais.</span><span class="sxs-lookup"><span data-stu-id="6f55b-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6f55b-122">Se definido como `Custom`, em seguida, customCertificateValidator também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="6f55b-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="6f55b-123">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6f55b-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="6f55b-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="6f55b-124">revocationMode</span></span>|<span data-ttu-id="6f55b-125">Um dos modos usados para verificar por listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="6f55b-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="6f55b-126">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="6f55b-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="6f55b-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6f55b-127">trustedStoreLocation</span></span>|<span data-ttu-id="6f55b-128">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6f55b-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6f55b-129">Esse valor é usado quando um certificado de serviço é negociado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="6f55b-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="6f55b-130">A validação é executada em relação a **pessoas confiáveis** armazenar no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="6f55b-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="6f55b-131">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6f55b-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="6f55b-132">customCertificateValidator atributo</span><span class="sxs-lookup"><span data-stu-id="6f55b-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="6f55b-133">Valor</span><span class="sxs-lookup"><span data-stu-id="6f55b-133">Value</span></span>|<span data-ttu-id="6f55b-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f55b-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f55b-135">Cadeia de caracteres</span><span class="sxs-lookup"><span data-stu-id="6f55b-135">String</span></span>|<span data-ttu-id="6f55b-136">Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="6f55b-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="6f55b-137">certificateValidationMode atributo</span><span class="sxs-lookup"><span data-stu-id="6f55b-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="6f55b-138">Valor</span><span class="sxs-lookup"><span data-stu-id="6f55b-138">Value</span></span>|<span data-ttu-id="6f55b-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f55b-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f55b-140">Enumeração</span><span class="sxs-lookup"><span data-stu-id="6f55b-140">Enumeration</span></span>|<span data-ttu-id="6f55b-141">Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, personalizado.</span><span class="sxs-lookup"><span data-stu-id="6f55b-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="6f55b-142">Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6f55b-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="6f55b-143">revocationMode atributo</span><span class="sxs-lookup"><span data-stu-id="6f55b-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="6f55b-144">Valor</span><span class="sxs-lookup"><span data-stu-id="6f55b-144">Value</span></span>|<span data-ttu-id="6f55b-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f55b-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f55b-146">Enumeração</span><span class="sxs-lookup"><span data-stu-id="6f55b-146">Enumeration</span></span>|<span data-ttu-id="6f55b-147">Um dos seguintes valores: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="6f55b-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="6f55b-148">Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6f55b-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="6f55b-149">trustedStoreLocation atributo</span><span class="sxs-lookup"><span data-stu-id="6f55b-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="6f55b-150">Valor</span><span class="sxs-lookup"><span data-stu-id="6f55b-150">Value</span></span>|<span data-ttu-id="6f55b-151">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f55b-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6f55b-152">Enumeração</span><span class="sxs-lookup"><span data-stu-id="6f55b-152">Enumeration</span></span>|<span data-ttu-id="6f55b-153">Um dos valores seguintes: LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6f55b-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="6f55b-154">O padrão é CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6f55b-154">The default is CurrentUser.</span></span> <span data-ttu-id="6f55b-155">Se o aplicativo cliente é executado sob uma conta de sistema, em seguida, o certificado é geralmente em LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="6f55b-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="6f55b-156">Se o aplicativo cliente é executado sob uma conta de usuário, em seguida, o certificado é geralmente em CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6f55b-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f55b-157">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6f55b-157">Child Elements</span></span>  
 <span data-ttu-id="6f55b-158">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6f55b-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f55b-159">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6f55b-159">Parent Elements</span></span>  
  
|<span data-ttu-id="6f55b-160">Elemento</span><span class="sxs-lookup"><span data-stu-id="6f55b-160">Element</span></span>|<span data-ttu-id="6f55b-161">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f55b-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f55b-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="6f55b-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="6f55b-163">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="6f55b-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f55b-164">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f55b-164">Remarks</span></span>  
 <span data-ttu-id="6f55b-165">O `certificateValidationMode` atributo desse elemento de configuração especifica o nível de confiança usado para autenticar certificados.</span><span class="sxs-lookup"><span data-stu-id="6f55b-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="6f55b-166">Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados terminam em uma autoridade de certificação confiável na parte superior da cadeia.</span><span class="sxs-lookup"><span data-stu-id="6f55b-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="6f55b-167">Este é o modo mais seguro.</span><span class="sxs-lookup"><span data-stu-id="6f55b-167">This is the most secure mode.</span></span> <span data-ttu-id="6f55b-168">Você também pode definir o valor `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (confiança ponto a ponto) são aceitos, bem como certificados que estão em uma cadeia confiável.</span><span class="sxs-lookup"><span data-stu-id="6f55b-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="6f55b-169">Esse valor é usado durante o desenvolvimento e depuração clientes e serviços, pois os certificados emitidos por conta própria não precisam ser adquiridos de uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="6f55b-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="6f55b-170">Ao implantar um cliente, use o `ChainTrust` valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="6f55b-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="6f55b-171">Você também pode definir o valor `Custom` ou `None`.</span><span class="sxs-lookup"><span data-stu-id="6f55b-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="6f55b-172">Para usar o valor `Custom`, você também deverá definir o atributo `customCertificateValidator` para um assembly e um tipo usados para validar o certificado.</span><span class="sxs-lookup"><span data-stu-id="6f55b-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="6f55b-173">Para criar seu próprios validador personalizado, você deve herdar da classe abstrata X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="6f55b-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="6f55b-174">Para obter mais informações, consulte [como: criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="6f55b-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="6f55b-175">O `revocationMode` atributo especifica como os certificados são verificados para revogação.</span><span class="sxs-lookup"><span data-stu-id="6f55b-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="6f55b-176">O padrão é `online` que indica que certificados serão verificados automaticamente para revogação.</span><span class="sxs-lookup"><span data-stu-id="6f55b-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="6f55b-177">Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6f55b-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6f55b-178">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6f55b-178">Example</span></span>  
 <span data-ttu-id="6f55b-179">O exemplo a seguir executa duas tarefas.</span><span class="sxs-lookup"><span data-stu-id="6f55b-179">The following example does two tasks.</span></span> <span data-ttu-id="6f55b-180">Especifica um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome de domínio é www.contoso.com através do protocolo HTTP pela primeira vez.</span><span class="sxs-lookup"><span data-stu-id="6f55b-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is www.contoso.com over the HTTP protocol.</span></span> <span data-ttu-id="6f55b-181">Em segundo lugar, ele especifica o local de modo e repositório de revogação usado durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="6f55b-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="6f55b-182">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f55b-182">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [<span data-ttu-id="6f55b-183">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="6f55b-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="6f55b-184">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="6f55b-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6f55b-185">Como: criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="6f55b-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="6f55b-186">\<autenticação ></span><span class="sxs-lookup"><span data-stu-id="6f55b-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 <span data-ttu-id="6f55b-187">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md) (Protegendo clientes)</span><span class="sxs-lookup"><span data-stu-id="6f55b-187">[Securing Clients](../../../../../docs/framework/wcf/securing-clients.md)</span></span>  
 [<span data-ttu-id="6f55b-188">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="6f55b-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
