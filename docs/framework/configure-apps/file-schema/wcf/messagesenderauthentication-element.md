---
title: Elemento <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 1e63b6fa93e1abfa87c83da4b5d46f492c59b9bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931370"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="a89be-102">\<elemento de > messageSenderAuthentication</span><span class="sxs-lookup"><span data-stu-id="a89be-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="a89be-103">Especifica opções de autenticação para remetentes de mensagens ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="a89be-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="a89be-104">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="a89be-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="a89be-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="a89be-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="a89be-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="a89be-106">\<behaviors></span></span>  
<span data-ttu-id="a89be-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="a89be-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="a89be-108">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="a89be-108">\<behavior></span></span>  
<span data-ttu-id="a89be-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="a89be-109">\<clientCredentials></span></span>  
<span data-ttu-id="a89be-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="a89be-110">\<peer></span></span>  
<span data-ttu-id="a89be-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="a89be-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89be-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a89be-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a89be-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="a89be-113">Attributes and Elements</span></span>  
 <span data-ttu-id="a89be-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="a89be-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a89be-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="a89be-115">Attributes</span></span>  
  
|<span data-ttu-id="a89be-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="a89be-116">Attribute</span></span>|<span data-ttu-id="a89be-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89be-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="a89be-118">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="a89be-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="a89be-119">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="a89be-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="a89be-120">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="a89be-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="a89be-121">Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="a89be-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="a89be-122">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="a89be-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="a89be-123">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="a89be-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a89be-124">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="a89be-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="a89be-125">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="a89be-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="a89be-126">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="a89be-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="a89be-127">Valor</span><span class="sxs-lookup"><span data-stu-id="a89be-127">Value</span></span>|<span data-ttu-id="a89be-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89be-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a89be-129">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="a89be-129">String</span></span>|<span data-ttu-id="a89be-130">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a89be-130">Optional.</span></span> <span data-ttu-id="a89be-131">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="a89be-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="a89be-132">No mínimo, um namespace e um nome de tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="a89be-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="a89be-133">As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="a89be-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="a89be-134">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="a89be-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="a89be-135">Valor</span><span class="sxs-lookup"><span data-stu-id="a89be-135">Value</span></span>|<span data-ttu-id="a89be-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89be-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a89be-137">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a89be-137">Enumeration</span></span>|<span data-ttu-id="a89be-138">Opcional.</span><span class="sxs-lookup"><span data-stu-id="a89be-138">Optional.</span></span> <span data-ttu-id="a89be-139">Um dos seguintes valores: `None` `ChainTrust`, `PeerTrust`,, `Custom`,. `PeerOrChainTrust`</span><span class="sxs-lookup"><span data-stu-id="a89be-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="a89be-140">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a89be-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="a89be-141">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="a89be-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="a89be-142">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a89be-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="a89be-143">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="a89be-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="a89be-144">Valor</span><span class="sxs-lookup"><span data-stu-id="a89be-144">Value</span></span>|<span data-ttu-id="a89be-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89be-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a89be-146">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a89be-146">Enumeration</span></span>|<span data-ttu-id="a89be-147">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="a89be-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="a89be-148">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="a89be-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="a89be-149">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="a89be-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="a89be-150">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="a89be-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="a89be-151">Valor</span><span class="sxs-lookup"><span data-stu-id="a89be-151">Value</span></span>|<span data-ttu-id="a89be-152">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89be-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a89be-153">Enumeração</span><span class="sxs-lookup"><span data-stu-id="a89be-153">Enumeration</span></span>|<span data-ttu-id="a89be-154">Um dos seguintes valores: `LocalMachine` ou. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="a89be-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="a89be-155">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a89be-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="a89be-156">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente `LocalMachine`estará abaixo de.</span><span class="sxs-lookup"><span data-stu-id="a89be-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="a89be-157">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente `CurrentUser`estará em.</span><span class="sxs-lookup"><span data-stu-id="a89be-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="a89be-158">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="a89be-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a89be-159">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="a89be-159">Child Elements</span></span>  
 <span data-ttu-id="a89be-160">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="a89be-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a89be-161">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="a89be-161">Parent Elements</span></span>  
  
|<span data-ttu-id="a89be-162">Elemento</span><span class="sxs-lookup"><span data-stu-id="a89be-162">Element</span></span>|<span data-ttu-id="a89be-163">Descrição</span><span class="sxs-lookup"><span data-stu-id="a89be-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="a89be-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="a89be-164">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="a89be-165">Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="a89be-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a89be-166">Comentários</span><span class="sxs-lookup"><span data-stu-id="a89be-166">Remarks</span></span>  
 <span data-ttu-id="a89be-167">Esse elemento deve ser configurado se a autenticação de mensagem for escolhida.</span><span class="sxs-lookup"><span data-stu-id="a89be-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="a89be-168">Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="a89be-168">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="a89be-169">Todas as mensagens, antes de serem entregues ao aplicativo, são verificadas em relação à credencial da mensagem `customCertificateValidatorType` usando o validador especificado pelo atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="a89be-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="a89be-170">O Validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="a89be-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a89be-171">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a89be-171">Example</span></span>  
 <span data-ttu-id="a89be-172">O código a seguir define o modo de validação do `PeerOrChainTrust`remetente da mensagem como.</span><span class="sxs-lookup"><span data-stu-id="a89be-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a89be-173">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a89be-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="a89be-174">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="a89be-174">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="a89be-175">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="a89be-175">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="a89be-176">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a89be-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="a89be-177">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="a89be-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="a89be-178">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="a89be-178">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
