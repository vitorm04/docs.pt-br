---
title: <authentication>do <clientCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 99084f6b7afbdd8586ee706cd6ec44b349d81ff2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398261"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="0f1e0-102">\<authentication>do \<clientCertificate> elemento</span><span class="sxs-lookup"><span data-stu-id="0f1e0-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="0f1e0-103">Especifica comportamentos de autenticação para certificados de cliente usados por um serviço.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="0f1e0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f1e0-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f1e0-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0f1e0-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0f1e0-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="0f1e0-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f1e0-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f1e0-107">Attributes</span></span>  
  
|<span data-ttu-id="0f1e0-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="0f1e0-108">Attribute</span></span>|<span data-ttu-id="0f1e0-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1e0-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f1e0-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="0f1e0-110">customCertificateValidatorType</span></span>|<span data-ttu-id="0f1e0-111">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-111">Optional string.</span></span> <span data-ttu-id="0f1e0-112">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="0f1e0-113">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="0f1e0-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="0f1e0-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0f1e0-114">certificateValidationMode</span></span>|<span data-ttu-id="0f1e0-115">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-115">Optional enumeration.</span></span> <span data-ttu-id="0f1e0-116">Especifica um dos modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-116">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="0f1e0-117">Esse atributo é do <xref:System.ServiceModel.Security.X509CertificateValidationMode> tipo.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-117">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="0f1e0-118">Se definido como <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> , um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-118">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="0f1e0-119">O padrão é <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-119">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="0f1e0-120">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="0f1e0-120">includeWindowsGroups</span></span>|<span data-ttu-id="0f1e0-121">Booliano opcional.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-121">Optional Boolean.</span></span> <span data-ttu-id="0f1e0-122">Especifica se os grupos do Windows estão incluídos no contexto de segurança.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-122">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="0f1e0-123">Definir esse atributo como `true` tem um impacto no desempenho, pois ele resulta em uma expansão de grupo completa.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-123">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="0f1e0-124">Defina esse atributo como `false` se você não precisar estabelecer a lista de grupos aos quais um usuário pertence.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-124">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="0f1e0-125">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="0f1e0-125">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="0f1e0-126">Booliano.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-126">Boolean.</span></span> <span data-ttu-id="0f1e0-127">Especifica se o cliente pode ser mapeado para uma identidade do Windows usando o certificado.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-127">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="0f1e0-128">Active Directory deve estar habilitado para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-128">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="0f1e0-129">rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="0f1e0-129">revocationMode</span></span>|<span data-ttu-id="0f1e0-130">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-130">Optional enumeration.</span></span> <span data-ttu-id="0f1e0-131">Um dos modos usados para verificar as listas de certificados revogados (RCL).</span><span class="sxs-lookup"><span data-stu-id="0f1e0-131">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="0f1e0-132">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-132">The default is `Online`.</span></span> <span data-ttu-id="0f1e0-133">Esse valor é ignorado ao usar a segurança de transporte HTTP.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-133">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="0f1e0-134">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0f1e0-134">trustedStoreLocation</span></span>|<span data-ttu-id="0f1e0-135">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-135">Optional enumeration.</span></span> <span data-ttu-id="0f1e0-136">Um dos dois locais de armazenamento do sistema: `LocalMachine` ou `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="0f1e0-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="0f1e0-137">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-137">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="0f1e0-138">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-138">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="0f1e0-139">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-139">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="0f1e0-140">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="0f1e0-140">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="0f1e0-141">Valor</span><span class="sxs-lookup"><span data-stu-id="0f1e0-141">Value</span></span>|<span data-ttu-id="0f1e0-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1e0-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f1e0-143">String</span><span class="sxs-lookup"><span data-stu-id="0f1e0-143">String</span></span>|<span data-ttu-id="0f1e0-144">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-144">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="0f1e0-145">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0f1e0-145">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="0f1e0-146">Valor</span><span class="sxs-lookup"><span data-stu-id="0f1e0-146">Value</span></span>|<span data-ttu-id="0f1e0-147">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1e0-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f1e0-148">Enumeração</span><span class="sxs-lookup"><span data-stu-id="0f1e0-148">Enumeration</span></span>|<span data-ttu-id="0f1e0-149">Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-149">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="0f1e0-150">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0f1e0-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="0f1e0-151">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="0f1e0-151">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="0f1e0-152">Valor</span><span class="sxs-lookup"><span data-stu-id="0f1e0-152">Value</span></span>|<span data-ttu-id="0f1e0-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1e0-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f1e0-154">Enumeração</span><span class="sxs-lookup"><span data-stu-id="0f1e0-154">Enumeration</span></span>|<span data-ttu-id="0f1e0-155">Um dos seguintes valores: NOCHECK, online, offline.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-155">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="0f1e0-156">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="0f1e0-156">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="0f1e0-157">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0f1e0-157">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="0f1e0-158">Valor</span><span class="sxs-lookup"><span data-stu-id="0f1e0-158">Value</span></span>|<span data-ttu-id="0f1e0-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1e0-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="0f1e0-160">Enumeração</span><span class="sxs-lookup"><span data-stu-id="0f1e0-160">Enumeration</span></span>|<span data-ttu-id="0f1e0-161">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-161">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="0f1e0-162">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-162">The default is `CurrentUser`.</span></span> <span data-ttu-id="0f1e0-163">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente estará abaixo de `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="0f1e0-163">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="0f1e0-164">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente estará em `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="0f1e0-164">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f1e0-165">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0f1e0-165">Child Elements</span></span>  
 <span data-ttu-id="0f1e0-166">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-166">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f1e0-167">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0f1e0-167">Parent Elements</span></span>  
  
|<span data-ttu-id="0f1e0-168">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f1e0-168">Element</span></span>|<span data-ttu-id="0f1e0-169">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f1e0-169">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="0f1e0-170">Define um certificado X. 509 usado para autenticar um cliente para um serviço.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-170">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f1e0-171">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f1e0-171">Remarks</span></span>  
 <span data-ttu-id="0f1e0-172">O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-172">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="0f1e0-173">Ele permite que você personalize como os clientes são autenticados.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-173">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="0f1e0-174">Você pode definir o `certificateValidationMode` atributo como `None` ,,, `ChainTrust` `PeerOrChainTrust` `PeerTrust` ou `Custom` .</span><span class="sxs-lookup"><span data-stu-id="0f1e0-174">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="0f1e0-175">Por padrão, o nível é definido como `ChainTrust` , que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que terminam em uma *autoridade raiz* na parte superior da cadeia.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-175">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="0f1e0-176">Esse é o modo mais seguro.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-176">This is the most secure mode.</span></span> <span data-ttu-id="0f1e0-177">Você também pode definir o valor como `PeerOrChainTrust` , que especifica que os certificados emitidos por conta própria (peer Trust) são aceitos, bem como certificados que estão em uma cadeia confiável.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-177">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="0f1e0-178">Esse valor é usado ao desenvolver e depurar clientes e serviços porque certificados emitidos por conta própria não precisam ser comprados de uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-178">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="0f1e0-179">Ao implantar um cliente, use o `ChainTrust` valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-179">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="0f1e0-180">Você também pode definir o valor como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="0f1e0-180">You can also set the value to `Custom`.</span></span> <span data-ttu-id="0f1e0-181">Quando definido como o `Custom` valor, você também deve definir o `customCertificateValidatorType` atributo para um assembly e tipo usado para validar o certificado.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-181">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="0f1e0-182">Para criar seu próprio validador personalizado, você deve herdar da <xref:System.IdentityModel.Selectors.X509CertificateValidator> classe abstrata.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-182">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="0f1e0-183">Para obter mais informações, consulte [como: criar um serviço que emprega um validador de certificado personalizado](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="0f1e0-183">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0f1e0-184">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0f1e0-184">Example</span></span>  
 <span data-ttu-id="0f1e0-185">O código a seguir especifica um certificado X. 509 e um tipo de validação personalizado no `<authentication>` elemento.</span><span class="sxs-lookup"><span data-stu-id="0f1e0-185">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
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
  
## <a name="see-also"></a><span data-ttu-id="0f1e0-186">Confira também</span><span class="sxs-lookup"><span data-stu-id="0f1e0-186">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="0f1e0-187">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="0f1e0-187">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="0f1e0-188">Como criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="0f1e0-188">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="0f1e0-189">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="0f1e0-189">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
