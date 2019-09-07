---
title: Elemento <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400089"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="1e75b-102">\<Elemento de > peerAuthentication</span><span class="sxs-lookup"><span data-stu-id="1e75b-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="1e75b-103">Especifica opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="1e75b-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="1e75b-104">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="1e75b-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="1e75b-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="1e75b-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="1e75b-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="1e75b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="1e75b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="1e75b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="1e75b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> par**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="1e75b-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="1e75b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> peerAuthentication**</span><span class="sxs-lookup"><span data-stu-id="1e75b-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e75b-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1e75b-113">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e75b-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1e75b-114">Attributes and Elements</span></span>  
 <span data-ttu-id="1e75b-115">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e75b-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e75b-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="1e75b-116">Attributes</span></span>  
  
|<span data-ttu-id="1e75b-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="1e75b-117">Attribute</span></span>|<span data-ttu-id="1e75b-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e75b-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="1e75b-119">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="1e75b-119">Optional string.</span></span> <span data-ttu-id="1e75b-120">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="1e75b-120">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="1e75b-121">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-121">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="1e75b-122">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="1e75b-122">Optional enumeration.</span></span> <span data-ttu-id="1e75b-123">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="1e75b-123">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="1e75b-124">Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="1e75b-124">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="1e75b-125">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-125">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="1e75b-126">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="1e75b-126">Optional enumeration.</span></span> <span data-ttu-id="1e75b-127">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="1e75b-127">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="1e75b-128">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-128">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="1e75b-129">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="1e75b-129">Optional enumeration.</span></span> <span data-ttu-id="1e75b-130">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="1e75b-130">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1e75b-131">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="1e75b-131">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="1e75b-132">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="1e75b-132">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="1e75b-133">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-133">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="1e75b-134">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="1e75b-134">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="1e75b-135">Valor</span><span class="sxs-lookup"><span data-stu-id="1e75b-135">Value</span></span>|<span data-ttu-id="1e75b-136">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e75b-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e75b-137">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="1e75b-137">String</span></span>|<span data-ttu-id="1e75b-138">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="1e75b-138">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="1e75b-139">No mínimo, um namespace e um nome de tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="1e75b-139">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="1e75b-140">As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="1e75b-140">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="1e75b-141">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="1e75b-141">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="1e75b-142">Valor</span><span class="sxs-lookup"><span data-stu-id="1e75b-142">Value</span></span>|<span data-ttu-id="1e75b-143">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e75b-143">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e75b-144">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1e75b-144">Enumeration</span></span>|<span data-ttu-id="1e75b-145">Um dos seguintes valores: `None` `ChainTrust`, `PeerTrust`,, `Custom`,. `PeerOrChainTrust`</span><span class="sxs-lookup"><span data-stu-id="1e75b-145">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="1e75b-146">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-146">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="1e75b-147">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1e75b-147">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="1e75b-148">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="1e75b-148">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="1e75b-149">Valor</span><span class="sxs-lookup"><span data-stu-id="1e75b-149">Value</span></span>|<span data-ttu-id="1e75b-150">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e75b-150">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e75b-151">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1e75b-151">Enumeration</span></span>|<span data-ttu-id="1e75b-152">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-152">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="1e75b-153">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-153">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="1e75b-154">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="1e75b-154">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="1e75b-155">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="1e75b-155">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="1e75b-156">Valor</span><span class="sxs-lookup"><span data-stu-id="1e75b-156">Value</span></span>|<span data-ttu-id="1e75b-157">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e75b-157">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="1e75b-158">Enumeração</span><span class="sxs-lookup"><span data-stu-id="1e75b-158">Enumeration</span></span>|<span data-ttu-id="1e75b-159">Um dos seguintes valores: `LocalMachine` ou. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="1e75b-159">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="1e75b-160">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="1e75b-160">The default is `CurrentUser`.</span></span> <span data-ttu-id="1e75b-161">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente `LocalMachine`estará abaixo de.</span><span class="sxs-lookup"><span data-stu-id="1e75b-161">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="1e75b-162">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente `CurrentUser`estará em.</span><span class="sxs-lookup"><span data-stu-id="1e75b-162">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e75b-163">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1e75b-163">Child Elements</span></span>  
 <span data-ttu-id="1e75b-164">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1e75b-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1e75b-165">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1e75b-165">Parent Elements</span></span>  
  
|<span data-ttu-id="1e75b-166">Elemento</span><span class="sxs-lookup"><span data-stu-id="1e75b-166">Element</span></span>|<span data-ttu-id="1e75b-167">Descrição</span><span class="sxs-lookup"><span data-stu-id="1e75b-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1e75b-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="1e75b-168">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="1e75b-169">Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="1e75b-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1e75b-170">Comentários</span><span class="sxs-lookup"><span data-stu-id="1e75b-170">Remarks</span></span>  
 <span data-ttu-id="1e75b-171">O `<authentication>` elemento corresponde <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> à classe.</span><span class="sxs-lookup"><span data-stu-id="1e75b-171">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="1e75b-172">Esse elemento especifica um validador, que é invocado durante a autenticação de vizinho para vizinho na malha.</span><span class="sxs-lookup"><span data-stu-id="1e75b-172">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="1e75b-173">Quando um novo par tenta estabelecer uma conexão vizinha, ele passa sua própria credencial para o par de resposta.</span><span class="sxs-lookup"><span data-stu-id="1e75b-173">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="1e75b-174">O validador do respondente é chamado para verificar a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="1e75b-174">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="1e75b-175">Sempre que uma conexão de mesmo nível é estabelecida na malha, ambos os pares são mutuamente autenticados, o que significa que os validadores em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="1e75b-175">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1e75b-176">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1e75b-176">Example</span></span>  
 <span data-ttu-id="1e75b-177">O código a seguir define o modo de validação `PeerOrChainTrust`de certificado como.</span><span class="sxs-lookup"><span data-stu-id="1e75b-177">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1e75b-178">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1e75b-178">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="1e75b-179">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="1e75b-179">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="1e75b-180">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="1e75b-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="1e75b-181">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e75b-181">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="1e75b-182">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="1e75b-182">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="1e75b-183">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="1e75b-183">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
