---
title: <authentication>do <serviceCertificate> elemento
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398223"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="a254f-102">\<authentication>do \<serviceCertificate> elemento</span><span class="sxs-lookup"><span data-stu-id="a254f-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="a254f-103">Especifica as configurações usadas pelo proxy do cliente para autenticar certificados de serviço que são obtidos usando a negociação SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="a254f-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="a254f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a254f-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a254f-105">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a254f-105">Attributes and Elements</span></span>  
 <span data-ttu-id="a254f-106">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a254f-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a254f-107">Atributos</span><span class="sxs-lookup"><span data-stu-id="a254f-107">Attributes</span></span>  
  
|<span data-ttu-id="a254f-108">Atributo</span><span class="sxs-lookup"><span data-stu-id="a254f-108">Attribute</span></span>|<span data-ttu-id="a254f-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a254f-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a254f-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="a254f-110">customCertificateValidatorType</span></span>|<span data-ttu-id="a254f-111">Cadeia de caracteres.</span><span class="sxs-lookup"><span data-stu-id="a254f-111">String.</span></span> <span data-ttu-id="a254f-112">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a254f-112">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="a254f-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a254f-113">certificateValidationMode</span></span>|<span data-ttu-id="a254f-114">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="a254f-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a254f-115">Se definido como `Custom` , um customCertificateValidator também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="a254f-115">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="a254f-116">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a254f-116">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="a254f-117">rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="a254f-117">revocationMode</span></span>|<span data-ttu-id="a254f-118">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="a254f-118">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="a254f-119">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="a254f-119">The default is `Online`.</span></span>|  
|<span data-ttu-id="a254f-120">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a254f-120">trustedStoreLocation</span></span>|<span data-ttu-id="a254f-121">Um dos dois locais de armazenamento do sistema: `LocalMachine` ou `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="a254f-121">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a254f-122">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a254f-122">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a254f-123">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="a254f-123">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="a254f-124">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a254f-124">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="a254f-125">Atributo customCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="a254f-125">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="a254f-126">Valor</span><span class="sxs-lookup"><span data-stu-id="a254f-126">Value</span></span>|<span data-ttu-id="a254f-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="a254f-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a254f-128">String</span><span class="sxs-lookup"><span data-stu-id="a254f-128">String</span></span>|<span data-ttu-id="a254f-129">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="a254f-129">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a254f-130">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a254f-130">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a254f-131">Valor</span><span class="sxs-lookup"><span data-stu-id="a254f-131">Value</span></span>|<span data-ttu-id="a254f-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="a254f-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a254f-133">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a254f-133">Enumeration</span></span>|<span data-ttu-id="a254f-134">Um dos seguintes valores: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="a254f-134">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="a254f-135">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a254f-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a254f-136">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="a254f-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a254f-137">Valor</span><span class="sxs-lookup"><span data-stu-id="a254f-137">Value</span></span>|<span data-ttu-id="a254f-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="a254f-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a254f-139">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a254f-139">Enumeration</span></span>|<span data-ttu-id="a254f-140">Um dos seguintes valores: NOCHECK, online, offline.</span><span class="sxs-lookup"><span data-stu-id="a254f-140">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="a254f-141">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a254f-141">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a254f-142">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a254f-142">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a254f-143">Valor</span><span class="sxs-lookup"><span data-stu-id="a254f-143">Value</span></span>|<span data-ttu-id="a254f-144">Descrição</span><span class="sxs-lookup"><span data-stu-id="a254f-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a254f-145">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a254f-145">Enumeration</span></span>|<span data-ttu-id="a254f-146">Um dos seguintes valores: LocalMachine ou CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a254f-146">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="a254f-147">O padrão é CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a254f-147">The default is CurrentUser.</span></span> <span data-ttu-id="a254f-148">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado normalmente estará em LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="a254f-148">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="a254f-149">Se o aplicativo cliente estiver sendo executado em uma conta de usuário, o certificado normalmente será em CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="a254f-149">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a254f-150">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a254f-150">Child Elements</span></span>  
 <span data-ttu-id="a254f-151">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="a254f-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a254f-152">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a254f-152">Parent Elements</span></span>  
  
|<span data-ttu-id="a254f-153">Elemento</span><span class="sxs-lookup"><span data-stu-id="a254f-153">Element</span></span>|<span data-ttu-id="a254f-154">Descrição</span><span class="sxs-lookup"><span data-stu-id="a254f-154">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="a254f-155">Especifica um certificado a ser usado ao autenticar um serviço para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a254f-155">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a254f-156">Comentários</span><span class="sxs-lookup"><span data-stu-id="a254f-156">Remarks</span></span>  
 <span data-ttu-id="a254f-157">O `certificateValidationMode` atributo desse elemento de configuração especifica o nível de confiança usado para autenticar certificados.</span><span class="sxs-lookup"><span data-stu-id="a254f-157">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="a254f-158">Por padrão, o nível é definido como `ChainTrust` , que especifica que cada certificado deve ser encontrado em uma hierarquia de certificados que termina em uma autoridade de certificação confiável na parte superior da cadeia.</span><span class="sxs-lookup"><span data-stu-id="a254f-158">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="a254f-159">Esse é o modo mais seguro.</span><span class="sxs-lookup"><span data-stu-id="a254f-159">This is the most secure mode.</span></span> <span data-ttu-id="a254f-160">Você também pode definir o valor como `PeerOrChainTrust` , que especifica que os certificados emitidos por conta própria (peer Trust) são aceitos, bem como certificados que estão em uma cadeia confiável.</span><span class="sxs-lookup"><span data-stu-id="a254f-160">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="a254f-161">Esse valor é usado ao desenvolver e depurar clientes e serviços porque certificados emitidos por conta própria não precisam ser comprados de uma autoridade confiável.</span><span class="sxs-lookup"><span data-stu-id="a254f-161">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="a254f-162">Ao implantar um cliente, use o `ChainTrust` valor em vez disso.</span><span class="sxs-lookup"><span data-stu-id="a254f-162">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="a254f-163">Você também pode definir o valor para `Custom` ou `None` .</span><span class="sxs-lookup"><span data-stu-id="a254f-163">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="a254f-164">Para usar o valor `Custom`, você também deverá definir o atributo `customCertificateValidator` para um assembly e um tipo usados para validar o certificado.</span><span class="sxs-lookup"><span data-stu-id="a254f-164">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="a254f-165">Para criar seu próprio validador personalizado, você deve herdar da classe abstrata X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="a254f-165">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="a254f-166">Para obter mais informações, consulte [como: criar um serviço que emprega um validador de certificado personalizado](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="a254f-166">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="a254f-167">O `revocationMode` atributo especifica como os certificados são verificados para revogação.</span><span class="sxs-lookup"><span data-stu-id="a254f-167">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="a254f-168">O padrão é `online` que indica que os certificados serão verificados automaticamente para revogação.</span><span class="sxs-lookup"><span data-stu-id="a254f-168">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="a254f-169">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a254f-169">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a254f-170">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a254f-170">Example</span></span>  
 <span data-ttu-id="a254f-171">O exemplo a seguir executa duas tarefas.</span><span class="sxs-lookup"><span data-stu-id="a254f-171">The following example does two tasks.</span></span> <span data-ttu-id="a254f-172">Ele especifica primeiro um certificado de serviço para o cliente usar ao se comunicar com pontos de extremidade cujo nome de domínio está `www.contoso.com` sobre o protocolo http.</span><span class="sxs-lookup"><span data-stu-id="a254f-172">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="a254f-173">Em segundo lugar, ele especifica o modo de revogação e o local de armazenamento usados durante a autenticação.</span><span class="sxs-lookup"><span data-stu-id="a254f-173">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a254f-174">Confira também</span><span class="sxs-lookup"><span data-stu-id="a254f-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="a254f-175">Comportamentos de segurança</span><span class="sxs-lookup"><span data-stu-id="a254f-175">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="a254f-176">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a254f-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a254f-177">Como criar um serviço que utiliza um validador de certificado personalizado</span><span class="sxs-lookup"><span data-stu-id="a254f-177">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="a254f-178">Protegendo clientes</span><span class="sxs-lookup"><span data-stu-id="a254f-178">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="a254f-179">Protegendo serviços e clientes</span><span class="sxs-lookup"><span data-stu-id="a254f-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
