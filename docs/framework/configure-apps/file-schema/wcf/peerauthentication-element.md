---
title: Elemento <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 6e9fd69af5bce4da0bb14442cddcbecd536535f3
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55277713"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="5ee6c-102">\<peerAuthentication > elemento</span><span class="sxs-lookup"><span data-stu-id="5ee6c-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="5ee6c-103">Especifica as opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="5ee6c-104">Para obter mais informações sobre a programação de peer-to-peer, consulte [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="5ee6c-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="5ee6c-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="5ee6c-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="5ee6c-106">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="5ee6c-106">\<behaviors></span></span>  
<span data-ttu-id="5ee6c-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="5ee6c-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="5ee6c-108">\<behavior></span><span class="sxs-lookup"><span data-stu-id="5ee6c-108">\<behavior></span></span>  
<span data-ttu-id="5ee6c-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="5ee6c-109">\<clientCredentials></span></span>  
<span data-ttu-id="5ee6c-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="5ee6c-110">\<peer></span></span>  
<span data-ttu-id="5ee6c-111">\<peerAuthentication ></span><span class="sxs-lookup"><span data-stu-id="5ee6c-111">\<PeerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ee6c-112">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ee6c-112">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ee6c-113">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ee6c-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5ee6c-114">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ee6c-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ee6c-115">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ee6c-115">Attributes</span></span>  
  
|<span data-ttu-id="5ee6c-116">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ee6c-116">Attribute</span></span>|<span data-ttu-id="5ee6c-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee6c-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="5ee6c-118">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-118">Optional string.</span></span> <span data-ttu-id="5ee6c-119">Um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="5ee6c-120">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certifcateValidationMode`|<span data-ttu-id="5ee6c-121">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-121">Optional enumeration.</span></span> <span data-ttu-id="5ee6c-122">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="5ee6c-123">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="5ee6c-124">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-124">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="5ee6c-125">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-125">Optional enumeration.</span></span> <span data-ttu-id="5ee6c-126">Um dos modos usados para verificar por listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="5ee6c-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="5ee6c-127">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-127">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="5ee6c-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-128">Optional enumeration.</span></span> <span data-ttu-id="5ee6c-129">Um dos locais de armazenamento de sistema de dois: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="5ee6c-130">Esse valor é usado quando um certificado de serviço é negociado ao cliente.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="5ee6c-131">Validação é executada em relação a **pessoas confiáveis** armazenar no local de repositório especificado.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="5ee6c-132">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="5ee6c-133">customCertificateValidatorType atributo</span><span class="sxs-lookup"><span data-stu-id="5ee6c-133">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="5ee6c-134">Valor</span><span class="sxs-lookup"><span data-stu-id="5ee6c-134">Value</span></span>|<span data-ttu-id="5ee6c-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee6c-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ee6c-136">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="5ee6c-136">String</span></span>|<span data-ttu-id="5ee6c-137">Especifica o nome do tipo e assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-137">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="5ee6c-138">No mínimo, um nome de namespace e tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-138">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="5ee6c-139">Incluem informações opcionais: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-139">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="5ee6c-140">certificateValidationMode atributo</span><span class="sxs-lookup"><span data-stu-id="5ee6c-140">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="5ee6c-141">Valor</span><span class="sxs-lookup"><span data-stu-id="5ee6c-141">Value</span></span>|<span data-ttu-id="5ee6c-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee6c-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ee6c-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="5ee6c-143">Enumeration</span></span>|<span data-ttu-id="5ee6c-144">Um dos seguintes valores: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-144">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="5ee6c-145">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="5ee6c-146">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="5ee6c-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="5ee6c-147">revocationMode atributo</span><span class="sxs-lookup"><span data-stu-id="5ee6c-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="5ee6c-148">Valor</span><span class="sxs-lookup"><span data-stu-id="5ee6c-148">Value</span></span>|<span data-ttu-id="5ee6c-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee6c-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ee6c-150">Enumeração</span><span class="sxs-lookup"><span data-stu-id="5ee6c-150">Enumeration</span></span>|<span data-ttu-id="5ee6c-151">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="5ee6c-152">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="5ee6c-153">Para obter mais informações, consulte [trabalhando com certificados](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="5ee6c-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="5ee6c-154">trustedStoreLocation atributo</span><span class="sxs-lookup"><span data-stu-id="5ee6c-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="5ee6c-155">Valor</span><span class="sxs-lookup"><span data-stu-id="5ee6c-155">Value</span></span>|<span data-ttu-id="5ee6c-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee6c-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="5ee6c-157">Enumeração</span><span class="sxs-lookup"><span data-stu-id="5ee6c-157">Enumeration</span></span>|<span data-ttu-id="5ee6c-158">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="5ee6c-159">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="5ee6c-160">Se o aplicativo cliente é executado sob uma conta do sistema, o certificado está normalmente abaixo `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="5ee6c-161">Se o aplicativo cliente está em execução em uma conta de usuário, o certificado é normalmente em `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ee6c-162">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ee6c-162">Child Elements</span></span>  
 <span data-ttu-id="5ee6c-163">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-163">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ee6c-164">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ee6c-164">Parent Elements</span></span>  
  
|<span data-ttu-id="5ee6c-165">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ee6c-165">Element</span></span>|<span data-ttu-id="5ee6c-166">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ee6c-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5ee6c-167">\<peer></span><span class="sxs-lookup"><span data-stu-id="5ee6c-167">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="5ee6c-168">Especifica uma credencial usada para autenticar o cliente para um serviço de ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-168">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ee6c-169">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ee6c-169">Remarks</span></span>  
 <span data-ttu-id="5ee6c-170">O `<authentication>` elemento corresponde ao <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-170">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="5ee6c-171">Esse elemento Especifica um validador, que é invocado durante a autenticação de vizinho para vizinhos na malha.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-171">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="5ee6c-172">Quando um novo par tenta estabelecer uma conexão de vizinho, ele passa seu próprio credencial para o par está respondendo.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-172">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="5ee6c-173">O validador do Respondente é invocado para verificar se a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-173">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="5ee6c-174">Sempre que uma conexão ponto a ponto é estabelecida na malha, os pontos são autenticados mutuamente, validadores de significado em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-174">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ee6c-175">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ee6c-175">Example</span></span>  
 <span data-ttu-id="5ee6c-176">O código a seguir define o modo de validação de certificado `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="5ee6c-176">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ee6c-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5ee6c-177">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="5ee6c-178">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="5ee6c-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="5ee6c-179">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="5ee6c-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- [<span data-ttu-id="5ee6c-180">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="5ee6c-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)
- [<span data-ttu-id="5ee6c-181">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="5ee6c-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)
- [<span data-ttu-id="5ee6c-182">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="5ee6c-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
