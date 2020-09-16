---
title: Elemento <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 3693b2b4c6b6cbc3705a25967aedc88e36291407
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90547005"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="19145-102">Elemento \<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="19145-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="19145-103">Especifica opções de autenticação para remetentes de mensagens ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="19145-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="19145-104">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="19145-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="19145-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="19145-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19145-106">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="19145-106">Attributes and Elements</span></span>  
 <span data-ttu-id="19145-107">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="19145-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19145-108">Atributos</span><span class="sxs-lookup"><span data-stu-id="19145-108">Attributes</span></span>  
  
|<span data-ttu-id="19145-109">Atributo</span><span class="sxs-lookup"><span data-stu-id="19145-109">Attribute</span></span>|<span data-ttu-id="19145-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="19145-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="19145-111">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="19145-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="19145-112">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="19145-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="19145-113">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="19145-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="19145-114">Se definido como `Custom` , um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="19145-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="19145-115">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="19145-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="19145-116">Um dos dois locais de armazenamento do sistema: `LocalMachine` ou `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="19145-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="19145-117">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="19145-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="19145-118">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="19145-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="19145-119">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="19145-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="19145-120">Valor</span><span class="sxs-lookup"><span data-stu-id="19145-120">Value</span></span>|<span data-ttu-id="19145-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="19145-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19145-122">String</span><span class="sxs-lookup"><span data-stu-id="19145-122">String</span></span>|<span data-ttu-id="19145-123">Opcional.</span><span class="sxs-lookup"><span data-stu-id="19145-123">Optional.</span></span> <span data-ttu-id="19145-124">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="19145-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="19145-125">No mínimo, um namespace e um nome de tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="19145-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="19145-126">As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="19145-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="19145-127">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="19145-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="19145-128">Valor</span><span class="sxs-lookup"><span data-stu-id="19145-128">Value</span></span>|<span data-ttu-id="19145-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="19145-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19145-130">Enumeração</span><span class="sxs-lookup"><span data-stu-id="19145-130">Enumeration</span></span>|<span data-ttu-id="19145-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="19145-131">Optional.</span></span> <span data-ttu-id="19145-132">Um dos seguintes valores:,,, `None` `PeerTrust` `ChainTrust` `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="19145-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="19145-133">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="19145-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="19145-134">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="19145-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="19145-135">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="19145-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="19145-136">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="19145-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="19145-137">Valor</span><span class="sxs-lookup"><span data-stu-id="19145-137">Value</span></span>|<span data-ttu-id="19145-138">Descrição</span><span class="sxs-lookup"><span data-stu-id="19145-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19145-139">Enumeração</span><span class="sxs-lookup"><span data-stu-id="19145-139">Enumeration</span></span>|<span data-ttu-id="19145-140">Um dos seguintes valores: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="19145-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="19145-141">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="19145-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="19145-142">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="19145-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="19145-143">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="19145-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="19145-144">Valor</span><span class="sxs-lookup"><span data-stu-id="19145-144">Value</span></span>|<span data-ttu-id="19145-145">Descrição</span><span class="sxs-lookup"><span data-stu-id="19145-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19145-146">Enumeração</span><span class="sxs-lookup"><span data-stu-id="19145-146">Enumeration</span></span>|<span data-ttu-id="19145-147">Um dos seguintes valores: `LocalMachine` ou `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="19145-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="19145-148">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="19145-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="19145-149">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente estará abaixo de `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="19145-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="19145-150">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente estará em `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="19145-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="19145-151">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="19145-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19145-152">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="19145-152">Child Elements</span></span>  
 <span data-ttu-id="19145-153">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="19145-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19145-154">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="19145-154">Parent Elements</span></span>  
  
|<span data-ttu-id="19145-155">Elemento</span><span class="sxs-lookup"><span data-stu-id="19145-155">Element</span></span>|<span data-ttu-id="19145-156">Descrição</span><span class="sxs-lookup"><span data-stu-id="19145-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="19145-157">Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="19145-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19145-158">Comentários</span><span class="sxs-lookup"><span data-stu-id="19145-158">Remarks</span></span>  
 <span data-ttu-id="19145-159">Esse elemento deve ser configurado se a autenticação de mensagem for escolhida.</span><span class="sxs-lookup"><span data-stu-id="19145-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="19145-160">Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="19145-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="19145-161">Todas as mensagens, antes de serem entregues ao aplicativo, são verificadas em relação à credencial da mensagem usando o validador especificado pelo `customCertificateValidatorType` atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="19145-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="19145-162">O Validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="19145-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19145-163">Exemplo</span><span class="sxs-lookup"><span data-stu-id="19145-163">Example</span></span>  
 <span data-ttu-id="19145-164">O código a seguir define o modo de validação do remetente da mensagem como `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="19145-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="19145-165">Confira também</span><span class="sxs-lookup"><span data-stu-id="19145-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="19145-166">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="19145-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="19145-167">Rede peer-to-peer</span><span class="sxs-lookup"><span data-stu-id="19145-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="19145-168">[Autenticação de mensagem de canal par](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="19145-168">[Peer Channel Message Authentication](/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="19145-169">[Autenticação personalizada do canal par](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="19145-169">[Peer Channel Custom Authentication](/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="19145-170">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="19145-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
