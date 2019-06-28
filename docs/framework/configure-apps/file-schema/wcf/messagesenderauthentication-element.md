---
title: Elemento <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423119"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="8cac9-102">\<messageSenderAuthentication > elemento</span><span class="sxs-lookup"><span data-stu-id="8cac9-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="8cac9-103">Especifica opções de autenticação para remetentes de mensagens ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="8cac9-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="8cac9-104">Para obter mais informações sobre a programação de peer-to-peer, consulte [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="8cac9-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="8cac9-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8cac9-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="8cac9-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="8cac9-106">\<behaviors></span></span>  
<span data-ttu-id="8cac9-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="8cac9-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="8cac9-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="8cac9-108">\<behavior></span></span>  
<span data-ttu-id="8cac9-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="8cac9-109">\<clientCredentials></span></span>  
<span data-ttu-id="8cac9-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="8cac9-110">\<peer></span></span>  
<span data-ttu-id="8cac9-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="8cac9-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cac9-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8cac9-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cac9-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8cac9-113">Attributes and Elements</span></span>  
 <span data-ttu-id="8cac9-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="8cac9-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cac9-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="8cac9-115">Attributes</span></span>  
  
|<span data-ttu-id="8cac9-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="8cac9-116">Attribute</span></span>|<span data-ttu-id="8cac9-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cac9-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="8cac9-118">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="8cac9-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="8cac9-119">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="8cac9-120">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="8cac9-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="8cac9-121">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="8cac9-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="8cac9-122">Um dos modos usados para verificar por listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="8cac9-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="8cac9-123">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="8cac9-124">Esse valor é usado quando um certificado de serviço é negociado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="8cac9-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="8cac9-125">Validação é executada em relação a **pessoas confiáveis** armazenar no local de repositório especificado.</span><span class="sxs-lookup"><span data-stu-id="8cac9-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="8cac9-126">customCertificateValidatorType atributo</span><span class="sxs-lookup"><span data-stu-id="8cac9-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="8cac9-127">Valor</span><span class="sxs-lookup"><span data-stu-id="8cac9-127">Value</span></span>|<span data-ttu-id="8cac9-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cac9-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cac9-129">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="8cac9-129">String</span></span>|<span data-ttu-id="8cac9-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8cac9-130">Optional.</span></span> <span data-ttu-id="8cac9-131">Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="8cac9-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="8cac9-132">No mínimo, um nome de namespace e tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="8cac9-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="8cac9-133">Incluem informações opcionais: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="8cac9-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="8cac9-134">certificateValidationMode atributo</span><span class="sxs-lookup"><span data-stu-id="8cac9-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="8cac9-135">Valor</span><span class="sxs-lookup"><span data-stu-id="8cac9-135">Value</span></span>|<span data-ttu-id="8cac9-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cac9-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cac9-137">Enumeração</span><span class="sxs-lookup"><span data-stu-id="8cac9-137">Enumeration</span></span>|<span data-ttu-id="8cac9-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="8cac9-138">Optional.</span></span> <span data-ttu-id="8cac9-139">Um dos seguintes valores: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="8cac9-140">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="8cac9-141">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="8cac9-142">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8cac9-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="8cac9-143">revocationMode atributo</span><span class="sxs-lookup"><span data-stu-id="8cac9-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="8cac9-144">Valor</span><span class="sxs-lookup"><span data-stu-id="8cac9-144">Value</span></span>|<span data-ttu-id="8cac9-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cac9-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cac9-146">Enumeração</span><span class="sxs-lookup"><span data-stu-id="8cac9-146">Enumeration</span></span>|<span data-ttu-id="8cac9-147">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="8cac9-148">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="8cac9-149">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="8cac9-149">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="8cac9-150">trustedStoreLocation atributo</span><span class="sxs-lookup"><span data-stu-id="8cac9-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="8cac9-151">Valor</span><span class="sxs-lookup"><span data-stu-id="8cac9-151">Value</span></span>|<span data-ttu-id="8cac9-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cac9-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8cac9-153">Enumeração</span><span class="sxs-lookup"><span data-stu-id="8cac9-153">Enumeration</span></span>|<span data-ttu-id="8cac9-154">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="8cac9-155">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="8cac9-156">Se o aplicativo cliente é executado sob uma conta do sistema, o certificado está normalmente abaixo `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="8cac9-157">Se o aplicativo cliente está em execução em uma conta de usuário, o certificado é normalmente em `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="8cac9-158">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8cac9-159">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8cac9-159">Child Elements</span></span>  
 <span data-ttu-id="8cac9-160">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="8cac9-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8cac9-161">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8cac9-161">Parent Elements</span></span>  
  
|<span data-ttu-id="8cac9-162">Elemento</span><span class="sxs-lookup"><span data-stu-id="8cac9-162">Element</span></span>|<span data-ttu-id="8cac9-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="8cac9-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cac9-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="8cac9-164">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="8cac9-165">Especifica uma credencial usada para autenticar o cliente para um serviço de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="8cac9-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8cac9-166">Comentários</span><span class="sxs-lookup"><span data-stu-id="8cac9-166">Remarks</span></span>  
 <span data-ttu-id="8cac9-167">Esse elemento deve ser configurado, se for escolhida a autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="8cac9-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="8cac9-168">Para os canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="8cac9-168">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="8cac9-169">Todas as mensagens, antes da entrega para o aplicativo, são verificados em relação a credencial de mensagem usando o validador especificado pelo `customCertificateValidatorType` atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="8cac9-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="8cac9-170">O validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="8cac9-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8cac9-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8cac9-171">Example</span></span>  
 <span data-ttu-id="8cac9-172">O código a seguir define o modo de validação do remetente de mensagem para `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="8cac9-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8cac9-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8cac9-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="8cac9-174">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="8cac9-174">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="8cac9-175">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="8cac9-175">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="8cac9-176">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8cac9-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="8cac9-177">[Autenticação personalizada de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="8cac9-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="8cac9-178">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="8cac9-178">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
