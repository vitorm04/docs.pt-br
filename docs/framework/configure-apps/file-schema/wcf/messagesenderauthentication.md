---
title: '&lt;messageSenderAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 428dbdc65a4f66e5632e4ded7d7ded0d10b7c9d2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltmessagesenderauthenticationgt"></a><span data-ttu-id="4edb4-102">&lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="4edb4-102">&lt;messageSenderAuthentication&gt;</span></span>
<span data-ttu-id="4edb4-103">Especifica configurações de autenticação de certificado de ponto a ponto usado por um remetente da mensagem.</span><span class="sxs-lookup"><span data-stu-id="4edb4-103">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
 <span data-ttu-id="4edb4-104">\<sistema. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4edb4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4edb4-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="4edb4-105">\<behaviors></span></span>  
<span data-ttu-id="4edb4-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4edb4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4edb4-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="4edb4-107">\<behavior></span></span>  
<span data-ttu-id="4edb4-108">\<serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="4edb4-108">\<serviceCredentials></span></span>  
<span data-ttu-id="4edb4-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="4edb4-109">\<peer></span></span>  
<span data-ttu-id="4edb4-110">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="4edb4-110">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4edb4-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4edb4-111">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4edb4-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4edb4-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4edb4-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4edb4-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4edb4-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4edb4-114">Attributes</span></span>  
  
|<span data-ttu-id="4edb4-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="4edb4-115">Attribute</span></span>|<span data-ttu-id="4edb4-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4edb4-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="4edb4-117">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="4edb4-117">Optional enumeration.</span></span> <span data-ttu-id="4edb4-118">Especifica um dos cinco modos usados para validar credenciais.</span><span class="sxs-lookup"><span data-stu-id="4edb4-118">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="4edb4-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="4edb4-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="4edb4-120">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="4edb4-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="4edb4-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="4edb4-121">Optional string.</span></span> <span data-ttu-id="4edb4-122">Especifica um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4edb4-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="4edb4-123">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="4edb4-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="4edb4-124">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="4edb4-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="4edb4-125">Fornece um par de padrão de validador de certificado que verifica o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4edb4-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="4edb4-126">Ele também verifica se o certificado se encadeia uma raiz válido.</span><span class="sxs-lookup"><span data-stu-id="4edb4-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="4edb4-127">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="4edb4-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="4edb4-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="4edb4-128">Optional enumeration.</span></span> <span data-ttu-id="4edb4-129">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="4edb4-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="4edb4-130">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="4edb4-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="4edb4-131">O sistema verifica se o certificado de ponto a ponto não foi revogado por procurar na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="4edb4-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="4edb4-132">Essa verificação pode ser executada através da verificação online ou em uma lista de revogação em cache.</span><span class="sxs-lookup"><span data-stu-id="4edb4-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="4edb4-133">Verificação de revogação pode ser desativado por configuração deste atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="4edb4-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="4edb4-134">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="4edb4-134">Optional enumeration.</span></span> <span data-ttu-id="4edb4-135">Especifica o local de armazenamento confiável em que o certificado de ponto a ponto é validado pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sistema de segurança.</span><span class="sxs-lookup"><span data-stu-id="4edb4-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="4edb4-136">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="4edb4-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4edb4-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4edb4-137">Child Elements</span></span>  
 <span data-ttu-id="4edb4-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4edb4-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4edb4-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4edb4-139">Parent Elements</span></span>  
  
|<span data-ttu-id="4edb4-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="4edb4-140">Element</span></span>|<span data-ttu-id="4edb4-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="4edb4-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4edb4-142">\<par ></span><span class="sxs-lookup"><span data-stu-id="4edb4-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="4edb4-143">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4edb4-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4edb4-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="4edb4-144">Remarks</span></span>  
 <span data-ttu-id="4edb4-145">Esse elemento deve ser configurado se você escolher autenticação de mensagem.</span><span class="sxs-lookup"><span data-stu-id="4edb4-145">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="4edb4-146">Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [ \<certificado >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="4edb4-146">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="4edb4-147">Todas as mensagens, antes da entrega para o aplicativo, são verificados em relação a credencial de mensagem usando o validador especificado pelo `customCertificateValidatorType` atributos desse elemento.</span><span class="sxs-lookup"><span data-stu-id="4edb4-147">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="4edb4-148">O validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="4edb4-148">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4edb4-149">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4edb4-149">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 [<span data-ttu-id="4edb4-150">Trabalhar com certificados</span><span class="sxs-lookup"><span data-stu-id="4edb4-150">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="4edb4-151">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="4edb4-151">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="4edb4-152">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="4edb4-152">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="4edb4-153">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="4edb4-153">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="4edb4-154">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="4edb4-154">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
