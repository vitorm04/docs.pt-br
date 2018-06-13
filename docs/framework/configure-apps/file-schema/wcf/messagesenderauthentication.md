---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 9588ba191ef9f52cb81e52c0b8cf0b423fcaf1fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364340"
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="6a7f2-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="6a7f2-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="6a7f2-103">Especifica configurações de autenticação de certificado de ponto a ponto usado por um remetente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="6a7f2-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6a7f2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6a7f2-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="6a7f2-105">\<behaviors></span></span>  
<span data-ttu-id="6a7f2-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="6a7f2-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6a7f2-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="6a7f2-107">\<behavior></span></span>  
<span data-ttu-id="6a7f2-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="6a7f2-108">\<serviceCredentials></span></span>  
<span data-ttu-id="6a7f2-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="6a7f2-109">\<peer></span></span>  
<span data-ttu-id="6a7f2-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="6a7f2-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6a7f2-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6a7f2-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6a7f2-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="6a7f2-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6a7f2-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6a7f2-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="6a7f2-114">Attributes</span></span>  
  
|<span data-ttu-id="6a7f2-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="6a7f2-115">Attribute</span></span>|<span data-ttu-id="6a7f2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a7f2-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="6a7f2-117">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-117">Optional enumeration.</span></span> <span data-ttu-id="6a7f2-118">Especifica um dos cinco modos usados para validar credenciais.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="6a7f2-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="6a7f2-120">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="6a7f2-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-121">Optional string.</span></span> <span data-ttu-id="6a7f2-122">Especifica um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="6a7f2-123">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="6a7f2-124">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="6a7f2-125">Windows Communication Foundation (WCF) fornece um par de padrão de validador de certificado que verifica o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="6a7f2-126">Ele também verifica se o certificado se encadeia uma raiz válido.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="6a7f2-127">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="6a7f2-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-128">Optional enumeration.</span></span> <span data-ttu-id="6a7f2-129">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="6a7f2-130">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="6a7f2-131">O sistema verifica se o certificado de ponto a ponto não foi revogado por procurar na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="6a7f2-132">Essa verificação pode ser executada através da verificação online ou em uma lista de revogação em cache.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="6a7f2-133">Verificação de revogação pode ser desativado por configuração deste atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="6a7f2-134">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-134">Optional enumeration.</span></span> <span data-ttu-id="6a7f2-135">Especifica o local de armazenamento confiável em que o certificado de ponto a ponto é validado pelo sistema de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="6a7f2-136">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6a7f2-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="6a7f2-137">Child Elements</span></span>  
 <span data-ttu-id="6a7f2-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6a7f2-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="6a7f2-139">Parent Elements</span></span>  
  
|<span data-ttu-id="6a7f2-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="6a7f2-140">Element</span></span>|<span data-ttu-id="6a7f2-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="6a7f2-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6a7f2-142">\<par ></span><span class="sxs-lookup"><span data-stu-id="6a7f2-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="6a7f2-143">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6a7f2-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="6a7f2-144">Remarks</span></span>  
 <span data-ttu-id="6a7f2-145">Esse elemento deve ser configurado se você escolher autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="6a7f2-146">Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="6a7f2-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="6a7f2-147">Todas as mensagens, antes da entrega para o aplicativo, são verificados em relação a credencial de mensagem usando o validador especificado pelo `customCertificateValidatorType` atributos desse elemento.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="6a7f2-148">O validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="6a7f2-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6a7f2-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6a7f2-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="6a7f2-150">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="6a7f2-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="6a7f2-151">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="6a7f2-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="6a7f2-152">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="6a7f2-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="6a7f2-153">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="6a7f2-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="6a7f2-154">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="6a7f2-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
