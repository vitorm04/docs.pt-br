---
title: Elemento <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 09094c00b8faa28c37e202112251fee7cb4580be
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934015"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="43712-102">\<Elemento de > peerAuthentication</span><span class="sxs-lookup"><span data-stu-id="43712-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="43712-103">Especifica opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="43712-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="43712-104">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="43712-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="43712-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="43712-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="43712-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="43712-106">\<behaviors></span></span>  
<span data-ttu-id="43712-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="43712-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="43712-108">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="43712-108">\<behavior></span></span>  
<span data-ttu-id="43712-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="43712-109">\<clientCredentials></span></span>  
<span data-ttu-id="43712-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="43712-110">\<peer></span></span>  
<span data-ttu-id="43712-111">\<> PeerAuthentication</span><span class="sxs-lookup"><span data-stu-id="43712-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43712-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="43712-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="43712-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="43712-113">Attributes and Elements</span></span>  
 <span data-ttu-id="43712-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="43712-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="43712-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="43712-115">Attributes</span></span>  
  
|<span data-ttu-id="43712-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="43712-116">Attribute</span></span>|<span data-ttu-id="43712-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="43712-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="43712-118">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="43712-118">Optional string.</span></span> <span data-ttu-id="43712-119">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="43712-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="43712-120">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="43712-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="43712-121">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="43712-121">Optional enumeration.</span></span> <span data-ttu-id="43712-122">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="43712-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="43712-123">Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="43712-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="43712-124">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="43712-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="43712-125">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="43712-125">Optional enumeration.</span></span> <span data-ttu-id="43712-126">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="43712-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="43712-127">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="43712-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="43712-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="43712-128">Optional enumeration.</span></span> <span data-ttu-id="43712-129">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="43712-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="43712-130">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="43712-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="43712-131">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="43712-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="43712-132">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="43712-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="43712-133">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="43712-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="43712-134">Valor</span><span class="sxs-lookup"><span data-stu-id="43712-134">Value</span></span>|<span data-ttu-id="43712-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="43712-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43712-136">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="43712-136">String</span></span>|<span data-ttu-id="43712-137">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="43712-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="43712-138">No mínimo, um namespace e um nome de tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="43712-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="43712-139">As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="43712-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="43712-140">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="43712-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="43712-141">Valor</span><span class="sxs-lookup"><span data-stu-id="43712-141">Value</span></span>|<span data-ttu-id="43712-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="43712-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43712-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="43712-143">Enumeration</span></span>|<span data-ttu-id="43712-144">Um dos seguintes valores: `None` `ChainTrust`, `PeerTrust`,, `Custom`,. `PeerOrChainTrust`</span><span class="sxs-lookup"><span data-stu-id="43712-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="43712-145">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="43712-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="43712-146">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="43712-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="43712-147">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="43712-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="43712-148">Valor</span><span class="sxs-lookup"><span data-stu-id="43712-148">Value</span></span>|<span data-ttu-id="43712-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="43712-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43712-150">Enumeração</span><span class="sxs-lookup"><span data-stu-id="43712-150">Enumeration</span></span>|<span data-ttu-id="43712-151">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="43712-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="43712-152">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="43712-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="43712-153">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="43712-153">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="43712-154">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="43712-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="43712-155">Valor</span><span class="sxs-lookup"><span data-stu-id="43712-155">Value</span></span>|<span data-ttu-id="43712-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="43712-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="43712-157">Enumeração</span><span class="sxs-lookup"><span data-stu-id="43712-157">Enumeration</span></span>|<span data-ttu-id="43712-158">Um dos seguintes valores: `LocalMachine` ou. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="43712-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="43712-159">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="43712-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="43712-160">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente `LocalMachine`estará abaixo de.</span><span class="sxs-lookup"><span data-stu-id="43712-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="43712-161">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente `CurrentUser`estará em.</span><span class="sxs-lookup"><span data-stu-id="43712-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="43712-162">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="43712-162">Child Elements</span></span>  
 <span data-ttu-id="43712-163">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="43712-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="43712-164">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="43712-164">Parent Elements</span></span>  
  
|<span data-ttu-id="43712-165">Elemento</span><span class="sxs-lookup"><span data-stu-id="43712-165">Element</span></span>|<span data-ttu-id="43712-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="43712-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="43712-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="43712-167">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="43712-168">Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="43712-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43712-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="43712-169">Remarks</span></span>  
 <span data-ttu-id="43712-170">O `<authentication>` elemento corresponde <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> à classe.</span><span class="sxs-lookup"><span data-stu-id="43712-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="43712-171">Esse elemento especifica um validador, que é invocado durante a autenticação de vizinho para vizinho na malha.</span><span class="sxs-lookup"><span data-stu-id="43712-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="43712-172">Quando um novo par tenta estabelecer uma conexão vizinha, ele passa sua própria credencial para o par de resposta.</span><span class="sxs-lookup"><span data-stu-id="43712-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="43712-173">O validador do respondente é chamado para verificar a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="43712-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="43712-174">Sempre que uma conexão de mesmo nível é estabelecida na malha, ambos os pares são mutuamente autenticados, o que significa que os validadores em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="43712-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43712-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43712-175">Example</span></span>  
 <span data-ttu-id="43712-176">O código a seguir define o modo de validação `PeerOrChainTrust`de certificado como.</span><span class="sxs-lookup"><span data-stu-id="43712-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <peerAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="43712-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43712-177">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="43712-178">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="43712-178">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="43712-179">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="43712-179">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="43712-180">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="43712-180">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="43712-181">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="43712-181">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="43712-182">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="43712-182">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
