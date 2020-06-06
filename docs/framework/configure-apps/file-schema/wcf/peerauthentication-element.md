---
title: Elemento <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
ms.openlocfilehash: 4c29c84a2cc56a890c8273e410ba31b5f3900732
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400089"
---
# <a name="peerauthentication-element"></a><span data-ttu-id="fe494-102">Elemento \<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="fe494-102">\<peerAuthentication> Element</span></span>
<span data-ttu-id="fe494-103">Especifica opções de autenticação para clientes ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="fe494-103">Specifies authentication options for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="fe494-104">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="fe494-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="fe494-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fe494-105">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe494-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fe494-106">Attributes and Elements</span></span>  
 <span data-ttu-id="fe494-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="fe494-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe494-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="fe494-108">Attributes</span></span>  
  
|<span data-ttu-id="fe494-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="fe494-109">Attribute</span></span>|<span data-ttu-id="fe494-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe494-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="fe494-111">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="fe494-111">Optional string.</span></span> <span data-ttu-id="fe494-112">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="fe494-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="fe494-113">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="fe494-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="fe494-114">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fe494-114">Optional enumeration.</span></span> <span data-ttu-id="fe494-115">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="fe494-115">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="fe494-116">Se definido como `Custom` , um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="fe494-116">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="fe494-117">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="fe494-117">The default is `ChainTrust`.</span></span>|  
|`revocationMode`|<span data-ttu-id="fe494-118">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fe494-118">Optional enumeration.</span></span> <span data-ttu-id="fe494-119">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="fe494-119">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="fe494-120">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="fe494-120">The default is `Online`.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="fe494-121">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fe494-121">Optional enumeration.</span></span> <span data-ttu-id="fe494-122">Um dos dois locais de armazenamento do sistema: `LocalMachine` ou `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="fe494-122">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="fe494-123">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="fe494-123">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="fe494-124">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="fe494-124">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="fe494-125">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fe494-125">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="fe494-126">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="fe494-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="fe494-127">Valor</span><span class="sxs-lookup"><span data-stu-id="fe494-127">Value</span></span>|<span data-ttu-id="fe494-128">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe494-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe494-129">String</span><span class="sxs-lookup"><span data-stu-id="fe494-129">String</span></span>|<span data-ttu-id="fe494-130">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="fe494-130">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="fe494-131">No mínimo, um namespace e um nome de tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="fe494-131">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="fe494-132">As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="fe494-132">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="fe494-133">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="fe494-133">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="fe494-134">Valor</span><span class="sxs-lookup"><span data-stu-id="fe494-134">Value</span></span>|<span data-ttu-id="fe494-135">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe494-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe494-136">Enumeração</span><span class="sxs-lookup"><span data-stu-id="fe494-136">Enumeration</span></span>|<span data-ttu-id="fe494-137">Um dos seguintes valores:,,, `None` `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="fe494-137">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="fe494-138">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="fe494-138">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="fe494-139">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fe494-139">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="fe494-140">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="fe494-140">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="fe494-141">Valor</span><span class="sxs-lookup"><span data-stu-id="fe494-141">Value</span></span>|<span data-ttu-id="fe494-142">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe494-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe494-143">Enumeração</span><span class="sxs-lookup"><span data-stu-id="fe494-143">Enumeration</span></span>|<span data-ttu-id="fe494-144">Um dos seguintes valores: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="fe494-144">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="fe494-145">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="fe494-145">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="fe494-146">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="fe494-146">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="fe494-147">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="fe494-147">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="fe494-148">Valor</span><span class="sxs-lookup"><span data-stu-id="fe494-148">Value</span></span>|<span data-ttu-id="fe494-149">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe494-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="fe494-150">Enumeração</span><span class="sxs-lookup"><span data-stu-id="fe494-150">Enumeration</span></span>|<span data-ttu-id="fe494-151">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fe494-151">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="fe494-152">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="fe494-152">The default is `CurrentUser`.</span></span> <span data-ttu-id="fe494-153">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente estará abaixo de `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="fe494-153">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="fe494-154">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente estará em `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="fe494-154">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe494-155">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fe494-155">Child Elements</span></span>  
 <span data-ttu-id="fe494-156">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="fe494-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fe494-157">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fe494-157">Parent Elements</span></span>  
  
|<span data-ttu-id="fe494-158">Elemento</span><span class="sxs-lookup"><span data-stu-id="fe494-158">Element</span></span>|<span data-ttu-id="fe494-159">Descrição</span><span class="sxs-lookup"><span data-stu-id="fe494-159">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="fe494-160">Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="fe494-160">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe494-161">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe494-161">Remarks</span></span>  
 <span data-ttu-id="fe494-162">O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="fe494-162">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="fe494-163">Esse elemento especifica um validador, que é invocado durante a autenticação de vizinho para vizinho na malha.</span><span class="sxs-lookup"><span data-stu-id="fe494-163">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="fe494-164">Quando um novo par tenta estabelecer uma conexão vizinha, ele passa sua própria credencial para o par de resposta.</span><span class="sxs-lookup"><span data-stu-id="fe494-164">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="fe494-165">O validador do respondente é chamado para verificar a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="fe494-165">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="fe494-166">Sempre que uma conexão de mesmo nível é estabelecida na malha, ambos os pares são mutuamente autenticados, o que significa que os validadores em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="fe494-166">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe494-167">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe494-167">Example</span></span>  
 <span data-ttu-id="fe494-168">O código a seguir define o modo de validação de certificado como `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="fe494-168">The following code sets the certificate validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe494-169">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe494-169">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="fe494-170">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="fe494-170">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="fe494-171">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="fe494-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="fe494-172">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fe494-172">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="fe494-173">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="fe494-173">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="fe494-174">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="fe494-174">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
