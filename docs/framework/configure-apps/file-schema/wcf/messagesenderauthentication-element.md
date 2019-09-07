---
title: Elemento <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397783"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="bf7d5-102">\<elemento de > messageSenderAuthentication</span><span class="sxs-lookup"><span data-stu-id="bf7d5-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="bf7d5-103">Especifica opções de autenticação para remetentes de mensagens ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="bf7d5-104">Para obter mais informações sobre a programação ponto a ponto, consulte [rede ponto a ponto](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="bf7d5-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
<span data-ttu-id="bf7d5-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bf7d5-106">&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-106">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bf7d5-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bf7d5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> endpointBehaviors**](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="bf7d5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="bf7d5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<clientCredentials >** ](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="bf7d5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> par**](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="bf7d5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="bf7d5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> messageSenderAuthentication**</span><span class="sxs-lookup"><span data-stu-id="bf7d5-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf7d5-113">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bf7d5-113">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bf7d5-114">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="bf7d5-114">Attributes and Elements</span></span>  
 <span data-ttu-id="bf7d5-115">As seções a seguir descrevem atributos, elementos filho e elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf7d5-115">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bf7d5-116">Atributos</span><span class="sxs-lookup"><span data-stu-id="bf7d5-116">Attributes</span></span>  
  
|<span data-ttu-id="bf7d5-117">Atributo</span><span class="sxs-lookup"><span data-stu-id="bf7d5-117">Attribute</span></span>|<span data-ttu-id="bf7d5-118">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf7d5-118">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="bf7d5-119">Um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="bf7d5-120">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="bf7d5-121">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="bf7d5-122">Se definido como `Custom`, um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-122">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="bf7d5-123">Um dos modos usados para verificar se há listas de certificados revogados (CRL).</span><span class="sxs-lookup"><span data-stu-id="bf7d5-123">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="bf7d5-124">Um dos dois locais de armazenamento do sistema `LocalMachine` : `CurrentUser`ou.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-124">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="bf7d5-125">Esse valor é usado quando um certificado de serviço é negociado para o cliente.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-125">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="bf7d5-126">A validação é executada no repositório de **pessoas confiáveis** no local de armazenamento especificado.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-126">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="bf7d5-127">Atributo customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="bf7d5-127">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="bf7d5-128">Valor</span><span class="sxs-lookup"><span data-stu-id="bf7d5-128">Value</span></span>|<span data-ttu-id="bf7d5-129">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf7d5-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf7d5-130">Cadeia de Caracteres</span><span class="sxs-lookup"><span data-stu-id="bf7d5-130">String</span></span>|<span data-ttu-id="bf7d5-131">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-131">Optional.</span></span> <span data-ttu-id="bf7d5-132">Especifica o nome do tipo e o assembly e outros dados usados para localizar o tipo.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-132">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="bf7d5-133">No mínimo, um namespace e um nome de tipo são necessários.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-133">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="bf7d5-134">As informações opcionais incluem: nome do assembly, número de versão, cultura e token de chave pública.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-134">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="bf7d5-135">Atributo certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="bf7d5-135">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="bf7d5-136">Valor</span><span class="sxs-lookup"><span data-stu-id="bf7d5-136">Value</span></span>|<span data-ttu-id="bf7d5-137">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf7d5-137">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf7d5-138">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bf7d5-138">Enumeration</span></span>|<span data-ttu-id="bf7d5-139">Opcional.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-139">Optional.</span></span> <span data-ttu-id="bf7d5-140">Um dos seguintes valores: `None` `ChainTrust`, `PeerTrust`,, `Custom`,. `PeerOrChainTrust`</span><span class="sxs-lookup"><span data-stu-id="bf7d5-140">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="bf7d5-141">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-141">The default is `ChainTrust`.</span></span> <span data-ttu-id="bf7d5-142">O padrão é `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-142">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="bf7d5-143">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="bf7d5-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="bf7d5-144">Atributo rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="bf7d5-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="bf7d5-145">Valor</span><span class="sxs-lookup"><span data-stu-id="bf7d5-145">Value</span></span>|<span data-ttu-id="bf7d5-146">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf7d5-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf7d5-147">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bf7d5-147">Enumeration</span></span>|<span data-ttu-id="bf7d5-148">Um dos seguintes valores: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-148">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="bf7d5-149">O padrão é `Online`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-149">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="bf7d5-150">Para obter mais informações, consulte [trabalhando com certificados](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="bf7d5-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="bf7d5-151">Atributo trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="bf7d5-151">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="bf7d5-152">Valor</span><span class="sxs-lookup"><span data-stu-id="bf7d5-152">Value</span></span>|<span data-ttu-id="bf7d5-153">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf7d5-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="bf7d5-154">Enumeração</span><span class="sxs-lookup"><span data-stu-id="bf7d5-154">Enumeration</span></span>|<span data-ttu-id="bf7d5-155">Um dos seguintes valores: `LocalMachine` ou. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="bf7d5-155">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="bf7d5-156">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-156">The default is `CurrentUser`.</span></span> <span data-ttu-id="bf7d5-157">Se o aplicativo cliente estiver sendo executado em uma conta do sistema, o certificado geralmente `LocalMachine`estará abaixo de.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-157">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="bf7d5-158">Se o aplicativo cliente estiver sendo executado sob uma conta de usuário, o certificado normalmente `CurrentUser`estará em.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-158">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="bf7d5-159">O padrão é `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-159">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bf7d5-160">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="bf7d5-160">Child Elements</span></span>  
 <span data-ttu-id="bf7d5-161">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-161">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bf7d5-162">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="bf7d5-162">Parent Elements</span></span>  
  
|<span data-ttu-id="bf7d5-163">Elemento</span><span class="sxs-lookup"><span data-stu-id="bf7d5-163">Element</span></span>|<span data-ttu-id="bf7d5-164">Descrição</span><span class="sxs-lookup"><span data-stu-id="bf7d5-164">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bf7d5-165">\<peer></span><span class="sxs-lookup"><span data-stu-id="bf7d5-165">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="bf7d5-166">Especifica uma credencial usada para autenticar o cliente para um serviço de mesmo nível.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-166">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf7d5-167">Comentários</span><span class="sxs-lookup"><span data-stu-id="bf7d5-167">Remarks</span></span>  
 <span data-ttu-id="bf7d5-168">Esse elemento deve ser configurado se a autenticação de mensagem for escolhida.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-168">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="bf7d5-169">Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="bf7d5-169">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="bf7d5-170">Todas as mensagens, antes de serem entregues ao aplicativo, são verificadas em relação à credencial da mensagem `customCertificateValidatorType` usando o validador especificado pelo atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-170">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="bf7d5-171">O Validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-171">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bf7d5-172">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bf7d5-172">Example</span></span>  
 <span data-ttu-id="bf7d5-173">O código a seguir define o modo de validação do `PeerOrChainTrust`remetente da mensagem como.</span><span class="sxs-lookup"><span data-stu-id="bf7d5-173">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bf7d5-174">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bf7d5-174">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="bf7d5-175">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="bf7d5-175">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="bf7d5-176">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="bf7d5-176">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="bf7d5-177">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bf7d5-177">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="bf7d5-178">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="bf7d5-178">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="bf7d5-179">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="bf7d5-179">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
