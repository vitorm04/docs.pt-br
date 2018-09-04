---
title: '&lt;messageSenderAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: 8a3beb42d1064e6c6629014369628248b4cd5c8d
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43553791"
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="fea48-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="fea48-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="fea48-103">Especifica as configurações de autenticação de certificado par usado por um remetente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="fea48-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="fea48-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fea48-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fea48-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="fea48-105">\<behaviors></span></span>  
<span data-ttu-id="fea48-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fea48-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fea48-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="fea48-107">\<behavior></span></span>  
<span data-ttu-id="fea48-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fea48-108">\<serviceCredentials></span></span>  
<span data-ttu-id="fea48-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="fea48-109">\<peer></span></span>  
<span data-ttu-id="fea48-110">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="fea48-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fea48-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fea48-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fea48-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fea48-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fea48-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fea48-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fea48-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="fea48-114">Attributes</span></span>  
  
|<span data-ttu-id="fea48-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="fea48-115">Attribute</span></span>|<span data-ttu-id="fea48-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fea48-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="fea48-117">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fea48-117">Optional enumeration.</span></span> <span data-ttu-id="fea48-118">Especifica um dos cinco modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="fea48-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="fea48-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="fea48-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="fea48-120">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="fea48-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="fea48-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="fea48-121">Optional string.</span></span> <span data-ttu-id="fea48-122">Especifica um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="fea48-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="fea48-123">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="fea48-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="fea48-124">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="fea48-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="fea48-125">Windows Communication Foundation (WCF) oferece um par de padrão de validador de certificado que verifica se o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="fea48-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="fea48-126">Ela também verifica se o certificado encadeia-se a uma raiz válida.</span><span class="sxs-lookup"><span data-stu-id="fea48-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="fea48-127">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="fea48-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="fea48-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fea48-128">Optional enumeration.</span></span> <span data-ttu-id="fea48-129">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="fea48-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="fea48-130">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="fea48-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="fea48-131">O sistema verifica o certificado par não foi revogado por procurando na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="fea48-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="fea48-132">Essa verificação pode ser executada, verificando online ou em uma lista de revogação em cache.</span><span class="sxs-lookup"><span data-stu-id="fea48-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="fea48-133">Verificação de revogação pode ser desativado, definindo este atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="fea48-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="fea48-134">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fea48-134">Optional enumeration.</span></span> <span data-ttu-id="fea48-135">Especifica o local de repositório confiável em que o certificado par é validado pelo sistema de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="fea48-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="fea48-136">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="fea48-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fea48-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fea48-137">Child Elements</span></span>  
 <span data-ttu-id="fea48-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fea48-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fea48-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fea48-139">Parent Elements</span></span>  
  
|<span data-ttu-id="fea48-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="fea48-140">Element</span></span>|<span data-ttu-id="fea48-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="fea48-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fea48-142">\<par ></span><span class="sxs-lookup"><span data-stu-id="fea48-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="fea48-143">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="fea48-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fea48-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="fea48-144">Remarks</span></span>  
 <span data-ttu-id="fea48-145">Esse elemento deve ser configurado, se for escolhida a autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fea48-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="fea48-146">Para os canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="fea48-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="fea48-147">Todas as mensagens, antes da entrega para o aplicativo, são verificados em relação a credencial de mensagem usando o validador especificado pelo `customCertificateValidatorType` atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="fea48-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="fea48-148">O validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="fea48-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fea48-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fea48-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="fea48-150">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="fea48-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="fea48-151">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="fea48-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="fea48-152">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="fea48-152">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="fea48-153">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="fea48-153">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="fea48-154">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="fea48-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
