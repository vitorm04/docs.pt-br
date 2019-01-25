---
title: elemento &lt;messageSenderAuthentication&gt;
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 9b5155e579973555db1fefb6b22bd6c1ff38ea70
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54579895"
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="10fcb-102">elemento &lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="10fcb-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="10fcb-103">Especifica opções de autenticação para remetentes de mensagens ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="10fcb-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="10fcb-104">Para obter mais informações sobre a programação de peer-to-peer, consulte [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="10fcb-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="10fcb-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="10fcb-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="10fcb-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="10fcb-106">\<behaviors></span></span>  
<span data-ttu-id="10fcb-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="10fcb-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="10fcb-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="10fcb-108">\<behavior></span></span>  
<span data-ttu-id="10fcb-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="10fcb-109">\<clientCredentials></span></span>  
<span data-ttu-id="10fcb-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="10fcb-110">\<peer></span></span>  
<span data-ttu-id="10fcb-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="10fcb-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="10fcb-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="10fcb-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="10fcb-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="10fcb-113">Attributes and Elements</span></span>  
 <span data-ttu-id="10fcb-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="10fcb-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="10fcb-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="10fcb-115">Attributes</span></span>  
  
|<span data-ttu-id="10fcb-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="10fcb-116">Attribute</span></span>|<span data-ttu-id="10fcb-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fcb-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="10fcb-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="10fcb-118">customCertificateValidatorType</span></span>|<span data-ttu-id="10fcb-119">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="10fcb-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="10fcb-120">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="10fcb-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="10fcb-121">certifcateValidationMode</span></span>|<span data-ttu-id="10fcb-122">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="10fcb-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="10fcb-123">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="10fcb-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="10fcb-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="10fcb-124">revocationMode</span></span>|<span data-ttu-id="10fcb-125">Um dos modos usados para verificar por listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="10fcb-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="10fcb-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="10fcb-126">trustedStoreLocation</span></span>|<span data-ttu-id="10fcb-127">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="10fcb-128">Esse valor é usado quando um certificado de serviço é negociado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="10fcb-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="10fcb-129">Validação é executada em relação a **pessoas confiáveis** armazenar no local de repositório especificado.</span><span class="sxs-lookup"><span data-stu-id="10fcb-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="10fcb-130">customCertificateValidatorType atributo</span><span class="sxs-lookup"><span data-stu-id="10fcb-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="10fcb-131">Valor</span><span class="sxs-lookup"><span data-stu-id="10fcb-131">Value</span></span>|<span data-ttu-id="10fcb-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fcb-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10fcb-133">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="10fcb-133">String</span></span>|<span data-ttu-id="10fcb-134">Opcional.</span><span class="sxs-lookup"><span data-stu-id="10fcb-134">Optional.</span></span> <span data-ttu-id="10fcb-135">Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="10fcb-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="10fcb-136">No mínimo, um nome de namespace e tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="10fcb-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="10fcb-137">Incluem informações opcionais: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="10fcb-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="10fcb-138">certificateValidationMode atributo</span><span class="sxs-lookup"><span data-stu-id="10fcb-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="10fcb-139">Valor</span><span class="sxs-lookup"><span data-stu-id="10fcb-139">Value</span></span>|<span data-ttu-id="10fcb-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fcb-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10fcb-141">Enumeração</span><span class="sxs-lookup"><span data-stu-id="10fcb-141">Enumeration</span></span>|<span data-ttu-id="10fcb-142">Opcional.</span><span class="sxs-lookup"><span data-stu-id="10fcb-142">Optional.</span></span> <span data-ttu-id="10fcb-143">Um dos seguintes valores: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="10fcb-144">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="10fcb-145">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="10fcb-146">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="10fcb-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="10fcb-147">revocationMode atributo</span><span class="sxs-lookup"><span data-stu-id="10fcb-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="10fcb-148">Valor</span><span class="sxs-lookup"><span data-stu-id="10fcb-148">Value</span></span>|<span data-ttu-id="10fcb-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fcb-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10fcb-150">Enumeração</span><span class="sxs-lookup"><span data-stu-id="10fcb-150">Enumeration</span></span>|<span data-ttu-id="10fcb-151">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="10fcb-152">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="10fcb-153">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="10fcb-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="10fcb-154">trustedStoreLocation atributo</span><span class="sxs-lookup"><span data-stu-id="10fcb-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="10fcb-155">Valor</span><span class="sxs-lookup"><span data-stu-id="10fcb-155">Value</span></span>|<span data-ttu-id="10fcb-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fcb-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="10fcb-157">Enumeração</span><span class="sxs-lookup"><span data-stu-id="10fcb-157">Enumeration</span></span>|<span data-ttu-id="10fcb-158">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="10fcb-159">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="10fcb-160">Se o aplicativo cliente é executado sob uma conta do sistema, o certificado está normalmente abaixo `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="10fcb-161">Se o aplicativo cliente está em execução em uma conta de usuário, o certificado é normalmente em `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="10fcb-162">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="10fcb-163">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="10fcb-163">Child Elements</span></span>  
 <span data-ttu-id="10fcb-164">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="10fcb-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="10fcb-165">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="10fcb-165">Parent Elements</span></span>  
  
|<span data-ttu-id="10fcb-166">Elemento</span><span class="sxs-lookup"><span data-stu-id="10fcb-166">Element</span></span>|<span data-ttu-id="10fcb-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="10fcb-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="10fcb-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="10fcb-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="10fcb-169">Especifica uma credencial usada para autenticar o cliente para um serviço de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="10fcb-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10fcb-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="10fcb-170">Remarks</span></span>  
 <span data-ttu-id="10fcb-171">Esse elemento deve ser configurado, se for escolhida a autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="10fcb-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="10fcb-172">Para os canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="10fcb-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="10fcb-173">Todas as mensagens, antes da entrega para o aplicativo, são verificados em relação a credencial de mensagem usando o validador especificado pelo `customCertificateValidatorType` atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="10fcb-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="10fcb-174">O validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="10fcb-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="10fcb-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="10fcb-175">Example</span></span>  
 <span data-ttu-id="10fcb-176">O código a seguir define o modo de validação do remetente de mensagem para `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="10fcb-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="10fcb-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="10fcb-177">See also</span></span>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="10fcb-178">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="10fcb-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="10fcb-179">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="10fcb-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="10fcb-180">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="10fcb-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="10fcb-181">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="10fcb-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="10fcb-182">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="10fcb-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
