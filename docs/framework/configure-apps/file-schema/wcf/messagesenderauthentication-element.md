---
title: '<messageSenderAuthentication> Elemento '
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 410fffd541926b9a2e75c04d26a2a1e08a262939
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59135051"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="b8815-102">\<messageSenderAuthentication > elemento</span><span class="sxs-lookup"><span data-stu-id="b8815-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="b8815-103">Especifica opções de autenticação para remetentes de mensagens ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="b8815-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="b8815-104">Para obter mais informações sobre a programação de peer-to-peer, consulte [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="b8815-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="b8815-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b8815-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="b8815-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="b8815-106">\<behaviors></span></span>  
<span data-ttu-id="b8815-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="b8815-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="b8815-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="b8815-108">\<behavior></span></span>  
<span data-ttu-id="b8815-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="b8815-109">\<clientCredentials></span></span>  
<span data-ttu-id="b8815-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="b8815-110">\<peer></span></span>  
<span data-ttu-id="b8815-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="b8815-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8815-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8815-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8815-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b8815-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b8815-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="b8815-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8815-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="b8815-115">Attributes</span></span>  
  
|<span data-ttu-id="b8815-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="b8815-116">Attribute</span></span>|<span data-ttu-id="b8815-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8815-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8815-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="b8815-118">customCertificateValidatorType</span></span>|<span data-ttu-id="b8815-119">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="b8815-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="b8815-120">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b8815-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="b8815-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b8815-121">certifcateValidationMode</span></span>|<span data-ttu-id="b8815-122">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="b8815-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="b8815-123">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="b8815-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="b8815-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="b8815-124">revocationMode</span></span>|<span data-ttu-id="b8815-125">Um dos modos usados para verificar por listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="b8815-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="b8815-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b8815-126">trustedStoreLocation</span></span>|<span data-ttu-id="b8815-127">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b8815-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b8815-128">Esse valor é usado quando um certificado de serviço é negociado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="b8815-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="b8815-129">Validação é executada em relação a **pessoas confiáveis** armazenar no local de repositório especificado.</span><span class="sxs-lookup"><span data-stu-id="b8815-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="b8815-130">customCertificateValidatorType atributo</span><span class="sxs-lookup"><span data-stu-id="b8815-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="b8815-131">Valor</span><span class="sxs-lookup"><span data-stu-id="b8815-131">Value</span></span>|<span data-ttu-id="b8815-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8815-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8815-133">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="b8815-133">String</span></span>|<span data-ttu-id="b8815-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8815-134">Optional.</span></span> <span data-ttu-id="b8815-135">Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="b8815-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="b8815-136">No mínimo, um nome de namespace e tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="b8815-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="b8815-137">Incluem informações opcionais: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="b8815-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="b8815-138">certificateValidationMode atributo</span><span class="sxs-lookup"><span data-stu-id="b8815-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="b8815-139">Valor</span><span class="sxs-lookup"><span data-stu-id="b8815-139">Value</span></span>|<span data-ttu-id="b8815-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8815-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8815-141">Enumeração</span><span class="sxs-lookup"><span data-stu-id="b8815-141">Enumeration</span></span>|<span data-ttu-id="b8815-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="b8815-142">Optional.</span></span> <span data-ttu-id="b8815-143">Um dos seguintes valores: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="b8815-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="b8815-144">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b8815-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="b8815-145">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b8815-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="b8815-146">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b8815-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="b8815-147">revocationMode atributo</span><span class="sxs-lookup"><span data-stu-id="b8815-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="b8815-148">Valor</span><span class="sxs-lookup"><span data-stu-id="b8815-148">Value</span></span>|<span data-ttu-id="b8815-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8815-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8815-150">Enumeração</span><span class="sxs-lookup"><span data-stu-id="b8815-150">Enumeration</span></span>|<span data-ttu-id="b8815-151">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="b8815-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="b8815-152">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="b8815-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="b8815-153">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="b8815-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="b8815-154">trustedStoreLocation atributo</span><span class="sxs-lookup"><span data-stu-id="b8815-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="b8815-155">Valor</span><span class="sxs-lookup"><span data-stu-id="b8815-155">Value</span></span>|<span data-ttu-id="b8815-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8815-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="b8815-157">Enumeração</span><span class="sxs-lookup"><span data-stu-id="b8815-157">Enumeration</span></span>|<span data-ttu-id="b8815-158">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b8815-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="b8815-159">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b8815-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="b8815-160">Se o aplicativo cliente é executado sob uma conta do sistema, o certificado está normalmente abaixo `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="b8815-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="b8815-161">Se o aplicativo cliente está em execução em uma conta de usuário, o certificado é normalmente em `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b8815-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="b8815-162">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="b8815-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8815-163">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b8815-163">Child Elements</span></span>  
 <span data-ttu-id="b8815-164">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="b8815-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8815-165">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b8815-165">Parent Elements</span></span>  
  
|<span data-ttu-id="b8815-166">Elemento</span><span class="sxs-lookup"><span data-stu-id="b8815-166">Element</span></span>|<span data-ttu-id="b8815-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="b8815-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8815-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="b8815-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="b8815-169">Especifica uma credencial usada para autenticar o cliente para um serviço de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="b8815-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8815-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8815-170">Remarks</span></span>  
 <span data-ttu-id="b8815-171">Esse elemento deve ser configurado, se for escolhida a autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="b8815-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="b8815-172">Para os canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="b8815-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="b8815-173">Todas as mensagens, antes da entrega para o aplicativo, são verificados em relação a credencial de mensagem usando o validador especificado pelo `customCertificateValidatorType` atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="b8815-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="b8815-174">O validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="b8815-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8815-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b8815-175">Example</span></span>  
 <span data-ttu-id="b8815-176">O código a seguir define o modo de validação do remetente de mensagem para `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="b8815-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="b8815-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8815-177">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="b8815-178">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="b8815-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="b8815-179">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="b8815-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="b8815-180">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="b8815-180">Peer Channel Message Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))
- [<span data-ttu-id="b8815-181">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="b8815-181">Peer Channel Custom Authentication</span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))
- [<span data-ttu-id="b8815-182">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="b8815-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
