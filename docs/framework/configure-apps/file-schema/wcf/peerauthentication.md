---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a900a1f3fc2e07cffe04833cc3c7d3ccd063e24a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="4a280-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="4a280-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="4a280-103">Especifica as configurações de autenticação para um certificado de ponto a ponto usado por um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4a280-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="4a280-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="4a280-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="4a280-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="4a280-105">\<behaviors></span></span>  
<span data-ttu-id="4a280-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="4a280-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="4a280-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="4a280-107">\<behavior></span></span>  
<span data-ttu-id="4a280-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="4a280-108">\<serviceCredentials></span></span>  
<span data-ttu-id="4a280-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="4a280-109">\<peer></span></span>  
<span data-ttu-id="4a280-110">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="4a280-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a280-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4a280-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4a280-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="4a280-112">Attributes and Elements</span></span>  
 <span data-ttu-id="4a280-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="4a280-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4a280-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="4a280-114">Attributes</span></span>  
  
|<span data-ttu-id="4a280-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="4a280-115">Attribute</span></span>|<span data-ttu-id="4a280-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a280-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="4a280-117">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="4a280-117">Optional enumeration.</span></span> <span data-ttu-id="4a280-118">Especifica um dos três modos usados para validar credenciais.</span><span class="sxs-lookup"><span data-stu-id="4a280-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="4a280-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="4a280-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="4a280-120">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="4a280-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="4a280-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="4a280-121">Optional string.</span></span> <span data-ttu-id="4a280-122">Especifica um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a280-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="4a280-123">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="4a280-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="4a280-124">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="4a280-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]<span data-ttu-id="4a280-125">Fornece um par de padrão de validador de certificado que verifica o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="4a280-125"> provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="4a280-126">Ele também verifica se o certificado se encadeia uma raiz válido.</span><span class="sxs-lookup"><span data-stu-id="4a280-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="4a280-127">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="4a280-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="4a280-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="4a280-128">Optional enumeration.</span></span> <span data-ttu-id="4a280-129">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="4a280-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="4a280-130">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="4a280-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="4a280-131">O sistema verifica se o certificado de ponto a ponto não foi revogado por procurar na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="4a280-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="4a280-132">Essa verificação pode ser executada através da verificação online ou em uma lista de revogação em cache.</span><span class="sxs-lookup"><span data-stu-id="4a280-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="4a280-133">Verificação de revogação pode ser desativado por configuração deste atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="4a280-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="4a280-134">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="4a280-134">Optional enumeration.</span></span> <span data-ttu-id="4a280-135">Especifica o local de armazenamento confiável em que o certificado de ponto a ponto é validado pelo [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sistema de segurança.</span><span class="sxs-lookup"><span data-stu-id="4a280-135">Specifies the trusted store location where the peer certificate is validated by the [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] security system.</span></span> <span data-ttu-id="4a280-136">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="4a280-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4a280-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="4a280-137">Child Elements</span></span>  
 <span data-ttu-id="4a280-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="4a280-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4a280-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="4a280-139">Parent Elements</span></span>  
  
|<span data-ttu-id="4a280-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="4a280-140">Element</span></span>|<span data-ttu-id="4a280-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="4a280-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4a280-142">\<peer></span><span class="sxs-lookup"><span data-stu-id="4a280-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="4a280-143">Especifica as credenciais atuais de um nó ponto a ponto.</span><span class="sxs-lookup"><span data-stu-id="4a280-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a280-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="4a280-144">Remarks</span></span>  
 <span data-ttu-id="4a280-145">O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="4a280-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="4a280-146">Este elemento Especifica um validador, que é invocado durante a autenticação de vizinho de vizinho na malha.</span><span class="sxs-lookup"><span data-stu-id="4a280-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="4a280-147">Quando um novo par tenta estabelecer uma conexão vizinha, ele passa suas próprias credenciais para o par está respondendo.</span><span class="sxs-lookup"><span data-stu-id="4a280-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="4a280-148">O validador do Respondente é invocado para verificar a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="4a280-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="4a280-149">Sempre que uma conexão ponto a ponto é estabelecida na malha, os pontos são autenticados mutuamente, validadores significado em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="4a280-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a280-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4a280-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="4a280-151">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="4a280-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="4a280-152">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="4a280-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="4a280-153">Autenticação de mensagens de canal par</span><span class="sxs-lookup"><span data-stu-id="4a280-153">Peer Channel Message Authentication</span></span>](http://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="4a280-154">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="4a280-154">Peer Channel Custom Authentication</span></span>](http://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="4a280-155">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="4a280-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
