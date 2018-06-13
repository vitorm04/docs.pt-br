---
title: '&lt;autenticação&gt; de elemento &lt;clientCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: ccc184f63428fd4a12b9047c0bcf4416e87f24d2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750473"
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="b687b-102">&lt;autenticação&gt; de elemento &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="b687b-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="b687b-103">Especifica os comportamentos de autenticação para certificados de cliente usados por um serviço.</span><span class="sxs-lookup"><span data-stu-id="b687b-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="b687b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b687b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b687b-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b687b-105">\<behaviors></span></span>  
<span data-ttu-id="b687b-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="b687b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="b687b-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="b687b-107">\<behavior></span></span>  
<span data-ttu-id="b687b-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="b687b-108">\<serviceCredentials></span></span>  
<span data-ttu-id="b687b-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="b687b-109">\<clientCertificate></span></span>  
<span data-ttu-id="b687b-110">\<autenticação ></span><span class="sxs-lookup"><span data-stu-id="b687b-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b687b-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b687b-111">Syntax</span></span>  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b687b-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b687b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="b687b-113">As seções a seguir descrevem os elementos pai de atributos e elementos filho</span><span class="sxs-lookup"><span data-stu-id="b687b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b687b-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="b687b-114">Attributes</span></span>  
  
|<span data-ttu-id="b687b-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="b687b-115">Attribute</span></span>|<span data-ttu-id="b687b-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="b687b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b687b-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="b687b-117">customCertificateValidatorType</span></span>|<span data-ttu-id="b687b-118">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="b687b-118">Optional string.</span></span> <span data-ttu-id="b687b-119">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="b687b-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="b687b-120">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b687b-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="b687b-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b687b-121">certificateValidationMode</span></span>|<span data-ttu-id="b687b-122">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="b687b-122">Optional enumeration.</span></span> <span data-ttu-id="b687b-123">Especifica um dos modos usados para validar credenciais.</span><span class="sxs-lookup"><span data-stu-id="b687b-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="b687b-124">Esse atributo é do <xref:System.ServiceModel.Security.X509CertificateValidationMode> tipo.</span><span class="sxs-lookup"><span data-stu-id="b687b-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="b687b-125">Se definido como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="b687b-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="b687b-126">O padrão é <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b687b-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="b687b-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="b687b-127">includeWindowsGroups</span></span>|<span data-ttu-id="b687b-128">Booleano opcional.</span><span class="sxs-lookup"><span data-stu-id="b687b-128">Optional Boolean.</span></span> <span data-ttu-id="b687b-129">Especifica se os grupos do Windows são incluídos no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="b687b-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="b687b-130">A configuração desse atributo `true` tem um impacto no desempenho, já que resulta em uma expansão de grupo completo.</span><span class="sxs-lookup"><span data-stu-id="b687b-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="b687b-131">Defina este atributo como `false` se você não precisa estabelecer a lista de grupos de um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="b687b-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="b687b-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="b687b-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="b687b-133">Booliano.</span><span class="sxs-lookup"><span data-stu-id="b687b-133">Boolean.</span></span> <span data-ttu-id="b687b-134">Especifica se o cliente pode ser mapeado para uma identidade do Windows usando o certificado.</span><span class="sxs-lookup"><span data-stu-id="b687b-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="b687b-135">Active Directory deve ser habilitado para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="b687b-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="b687b-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="b687b-136">revocationMode</span></span>|<span data-ttu-id="b687b-137">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="b687b-137">Optional enumeration.</span></span> <span data-ttu-id="b687b-138">Um dos modos usados para verificar por listas de certificados revogados (RCL).</span><span class="sxs-lookup"><span data-stu-id="b687b-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="b687b-139">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="b687b-139">The default is `Online`.</span></span> <span data-ttu-id="b687b-140">Esse valor é ignorado ao usar a segurança de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="b687b-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="b687b-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b687b-141">trustedStoreLocation</span></span>|<span data-ttu-id="b687b-142">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="b687b-142">Optional enumeration.</span></span> <span data-ttu-id="b687b-143">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b687b-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b687b-144">Esse valor é usado quando um certificado de serviço é negociado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b687b-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="b687b-145">A validação é executada em relação a **pessoas confiáveis** armazenar no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="b687b-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="b687b-146">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b687b-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="b687b-147">customCertificateValidatorType atributo</span><span class="sxs-lookup"><span data-stu-id="b687b-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="b687b-148">Valor</span><span class="sxs-lookup"><span data-stu-id="b687b-148">Value</span></span>|<span data-ttu-id="b687b-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="b687b-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b687b-150">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b687b-150">String</span></span>|<span data-ttu-id="b687b-151">Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="b687b-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="b687b-152">certificateValidationMode atributo</span><span class="sxs-lookup"><span data-stu-id="b687b-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="b687b-153">Valor</span><span class="sxs-lookup"><span data-stu-id="b687b-153">Value</span></span>|<span data-ttu-id="b687b-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="b687b-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b687b-155">Enumeração</span><span class="sxs-lookup"><span data-stu-id="b687b-155">Enumeration</span></span>|<span data-ttu-id="b687b-156">Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, personalizado.</span><span class="sxs-lookup"><span data-stu-id="b687b-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="b687b-157">Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b687b-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="b687b-158">revocationMode atributo</span><span class="sxs-lookup"><span data-stu-id="b687b-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="b687b-159">Valor</span><span class="sxs-lookup"><span data-stu-id="b687b-159">Value</span></span>|<span data-ttu-id="b687b-160">Descrição</span><span class="sxs-lookup"><span data-stu-id="b687b-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b687b-161">Enumeração</span><span class="sxs-lookup"><span data-stu-id="b687b-161">Enumeration</span></span>|<span data-ttu-id="b687b-162">Um dos seguintes valores: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="b687b-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="b687b-163">Para obter mais informações, consulte [trabalhar com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b687b-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="b687b-164">trustedStoreLocation atributo</span><span class="sxs-lookup"><span data-stu-id="b687b-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="b687b-165">Valor</span><span class="sxs-lookup"><span data-stu-id="b687b-165">Value</span></span>|<span data-ttu-id="b687b-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="b687b-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b687b-167">Enumeração</span><span class="sxs-lookup"><span data-stu-id="b687b-167">Enumeration</span></span>|<span data-ttu-id="b687b-168">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b687b-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b687b-169">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b687b-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="b687b-170">Se o aplicativo cliente é executado sob uma conta de sistema, o certificado é geralmente em `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="b687b-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="b687b-171">Se o aplicativo cliente é executado sob uma conta de usuário, o certificado é geralmente em `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b687b-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b687b-172">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b687b-172">Child Elements</span></span>  
 <span data-ttu-id="b687b-173">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b687b-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b687b-174">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b687b-174">Parent Elements</span></span>  
  
|<span data-ttu-id="b687b-175">Elemento</span><span class="sxs-lookup"><span data-stu-id="b687b-175">Element</span></span>|<span data-ttu-id="b687b-176">Descrição</span><span class="sxs-lookup"><span data-stu-id="b687b-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b687b-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="b687b-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="b687b-178">Define um certificado x. 509 usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="b687b-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b687b-179">Comentários</span><span class="sxs-lookup"><span data-stu-id="b687b-179">Remarks</span></span>  
 <span data-ttu-id="b687b-180">O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="b687b-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="b687b-181">Ele permite que você personalize como os clientes são autenticados.</span><span class="sxs-lookup"><span data-stu-id="b687b-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="b687b-182">Você pode definir o `certificateValidationMode` atributo `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, ou `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b687b-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="b687b-183">Por padrão, o nível é definido como `ChainTrust`, que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados terminam em um *autoridade raiz* na parte superior da cadeia.</span><span class="sxs-lookup"><span data-stu-id="b687b-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="b687b-184">Este é o modo mais seguro.</span><span class="sxs-lookup"><span data-stu-id="b687b-184">This is the most secure mode.</span></span> <span data-ttu-id="b687b-185">Você também pode definir o valor `PeerOrChainTrust`, que especifica que os certificados emitidos por conta própria (confiança ponto a ponto) são aceitos, bem como certificados que estão em uma cadeia confiável.</span><span class="sxs-lookup"><span data-stu-id="b687b-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="b687b-186">Esse valor é usado durante o desenvolvimento e depuração clientes e serviços, pois os certificados emitidos por conta própria não precisam ser adquiridos de uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="b687b-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="b687b-187">Ao implantar um cliente, use o `ChainTrust` valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="b687b-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="b687b-188">Você também pode definir o valor `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b687b-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="b687b-189">Quando definido como o `Custom` valor, você também deve definir o `customCertificateValidatorType` de atributo para um assembly e o tipo usado para validar o certificado.</span><span class="sxs-lookup"><span data-stu-id="b687b-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="b687b-190">Para criar seu próprios validador personalizado, você deve herdar de abstrata <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe.</span><span class="sxs-lookup"><span data-stu-id="b687b-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="b687b-191">Para obter mais informações, consulte [como: criar um serviço que utiliza um validador de certificado personalizado](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="b687b-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b687b-192">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b687b-192">Example</span></span>  
 <span data-ttu-id="b687b-193">O código a seguir especifica um certificado x. 509 e um tipo de validação personalizada no `<authentication>` elemento.</span><span class="sxs-lookup"><span data-stu-id="b687b-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
         storeLocation="CurrentUser"   
         storeName="TrustedPeople"  
         x509FindType="FindByIssuerName" />  
   <authentication customCertificateValidatorType="MyTypes.Coho"  
    certificateValidationMode="Custom"   
    revocationMode="Offline"  
    includeWindowsGroups="false"   
    mapClientCertificateToWindowsAccount="true" />  
  </clientCertificate>  
 </behavior>  
</serviceBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b687b-194">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b687b-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="b687b-195">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="b687b-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="b687b-196">Como criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="b687b-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="b687b-197">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="b687b-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
