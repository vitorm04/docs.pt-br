---
title: '&lt;peerAuthentication&gt;'
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: bb83d2badad609394a66246fc14c19a6602399e0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43399454"
---
# <a name="ltpeerauthenticationgt"></a><span data-ttu-id="fedea-102">&lt;peerAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="fedea-102">&lt;peerAuthentication&gt;</span></span>
<span data-ttu-id="fedea-103">Especifica as configurações de autenticação para um certificado de ponto a ponto usado por um nó par.</span><span class="sxs-lookup"><span data-stu-id="fedea-103">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
 <span data-ttu-id="fedea-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="fedea-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="fedea-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="fedea-105">\<behaviors></span></span>  
<span data-ttu-id="fedea-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="fedea-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="fedea-107">\<comportamento de ></span><span class="sxs-lookup"><span data-stu-id="fedea-107">\<behavior></span></span>  
<span data-ttu-id="fedea-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="fedea-108">\<serviceCredentials></span></span>  
<span data-ttu-id="fedea-109">\<par ></span><span class="sxs-lookup"><span data-stu-id="fedea-109">\<peer></span></span>  
<span data-ttu-id="fedea-110">\<peerAuthentication></span><span class="sxs-lookup"><span data-stu-id="fedea-110">\<peerAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fedea-111">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fedea-111">Syntax</span></span>  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fedea-112">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="fedea-112">Attributes and Elements</span></span>  
 <span data-ttu-id="fedea-113">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="fedea-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fedea-114">Atributos</span><span class="sxs-lookup"><span data-stu-id="fedea-114">Attributes</span></span>  
  
|<span data-ttu-id="fedea-115">Atributo</span><span class="sxs-lookup"><span data-stu-id="fedea-115">Attribute</span></span>|<span data-ttu-id="fedea-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="fedea-116">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="fedea-117">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fedea-117">Optional enumeration.</span></span> <span data-ttu-id="fedea-118">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="fedea-118">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="fedea-119">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span><span class="sxs-lookup"><span data-stu-id="fedea-119">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="fedea-120">Se definido como `Custom`, em seguida, um `customCertificateValidator` também deve ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="fedea-120">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="fedea-121">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="fedea-121">Optional string.</span></span> <span data-ttu-id="fedea-122">Especifica um tipo e assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="fedea-122">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="fedea-123">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom`.</span><span class="sxs-lookup"><span data-stu-id="fedea-123">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="fedea-124">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="fedea-124">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="fedea-125">Windows Communication Foundation (WCF) oferece um par de padrão de validador de certificado que verifica se o certificado de ponto a ponto em relação ao armazenamento de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="fedea-125">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="fedea-126">Ela também verifica se o certificado encadeia-se a uma raiz válida.</span><span class="sxs-lookup"><span data-stu-id="fedea-126">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="fedea-127">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="fedea-127">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="fedea-128">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fedea-128">Optional enumeration.</span></span> <span data-ttu-id="fedea-129">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="fedea-129">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="fedea-130">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span><span class="sxs-lookup"><span data-stu-id="fedea-130">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="fedea-131">O sistema verifica o certificado par não foi revogado por procurando na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="fedea-131">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="fedea-132">Essa verificação pode ser executada, verificando online ou em uma lista de revogação em cache.</span><span class="sxs-lookup"><span data-stu-id="fedea-132">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="fedea-133">Verificação de revogação pode ser desativado, definindo este atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="fedea-133">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="fedea-134">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="fedea-134">Optional enumeration.</span></span> <span data-ttu-id="fedea-135">Especifica o local de repositório confiável em que o certificado par é validado pelo sistema de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="fedea-135">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="fedea-136">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span><span class="sxs-lookup"><span data-stu-id="fedea-136">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fedea-137">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="fedea-137">Child Elements</span></span>  
 <span data-ttu-id="fedea-138">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="fedea-138">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fedea-139">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="fedea-139">Parent Elements</span></span>  
  
|<span data-ttu-id="fedea-140">Elemento</span><span class="sxs-lookup"><span data-stu-id="fedea-140">Element</span></span>|<span data-ttu-id="fedea-141">Descrição</span><span class="sxs-lookup"><span data-stu-id="fedea-141">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fedea-142">\<par ></span><span class="sxs-lookup"><span data-stu-id="fedea-142">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|<span data-ttu-id="fedea-143">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="fedea-143">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fedea-144">Comentários</span><span class="sxs-lookup"><span data-stu-id="fedea-144">Remarks</span></span>  
 <span data-ttu-id="fedea-145">O `<authentication>` elemento corresponde ao <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="fedea-145">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="fedea-146">Esse elemento Especifica um validador, que é invocado durante a autenticação de vizinho para vizinhos na malha.</span><span class="sxs-lookup"><span data-stu-id="fedea-146">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="fedea-147">Quando um novo par tenta estabelecer uma conexão de vizinho, ele passa seu próprio credencial para o par está respondendo.</span><span class="sxs-lookup"><span data-stu-id="fedea-147">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="fedea-148">O validador do Respondente é invocado para verificar se a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="fedea-148">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="fedea-149">Sempre que uma conexão ponto a ponto é estabelecida na malha, os pontos são autenticados mutuamente, validadores de significado em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="fedea-149">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fedea-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fedea-150">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="fedea-151">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="fedea-151">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="fedea-152">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="fedea-152">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="fedea-153">Autenticação de mensagem de canal par</span><span class="sxs-lookup"><span data-stu-id="fedea-153">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="fedea-154">Autenticação personalizada de canal par</span><span class="sxs-lookup"><span data-stu-id="fedea-154">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="fedea-155">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="fedea-155">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
