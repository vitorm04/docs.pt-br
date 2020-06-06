---
title: <peerAuthentication>
ms.date: 03/30/2017
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
ms.openlocfilehash: 118159617a7f4c27ecc5e8fe077c28cfefac8537
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397613"
---
# \<peerAuthentication>
<span data-ttu-id="f7936-101">Especifica as configurações de autenticação para um certificado par usado por um nó par.</span><span class="sxs-lookup"><span data-stu-id="f7936-101">Specifies authentication settings for a peer certificate used by a peer node.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<peerAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="f7936-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7936-102">Syntax</span></span>  
  
```xml  
<peerAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                    certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                    revocationMode="NoCheck/Online/Offline"
                    trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7936-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f7936-103">Attributes and Elements</span></span>  
 <span data-ttu-id="f7936-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f7936-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7936-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7936-105">Attributes</span></span>  
  
|<span data-ttu-id="f7936-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="f7936-106">Attribute</span></span>|<span data-ttu-id="f7936-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7936-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="f7936-108">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="f7936-108">Optional enumeration.</span></span> <span data-ttu-id="f7936-109">Especifica um dos três modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="f7936-109">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="f7936-110">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="f7936-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="f7936-111">Se definido como `Custom` , um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="f7936-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="f7936-112">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="f7936-112">Optional string.</span></span> <span data-ttu-id="f7936-113">Especifica um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="f7936-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="f7936-114">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="f7936-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="f7936-115">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="f7936-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="f7936-116">O Windows Communication Foundation (WCF) fornece um validador de certificado par padrão que verifica o certificado de mesmo nível no repositório de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f7936-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="f7936-117">Ele também verifica se o certificado se encadeia em uma raiz válida.</span><span class="sxs-lookup"><span data-stu-id="f7936-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="f7936-118">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="f7936-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="f7936-119">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="f7936-119">Optional enumeration.</span></span> <span data-ttu-id="f7936-120">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="f7936-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="f7936-121">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="f7936-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="f7936-122">O sistema verifica se o certificado de mesmo nível não foi revogado ao procurá-lo na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="f7936-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="f7936-123">Essa verificação pode ser executada marcando-se online ou em uma lista de revogação armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="f7936-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="f7936-124">A verificação de revogação pode ser desativada definindo esse atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="f7936-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="f7936-125">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="f7936-125">Optional enumeration.</span></span> <span data-ttu-id="f7936-126">Especifica o local de repositório confiável em que o certificado par é validado pelo sistema de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="f7936-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="f7936-127">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="f7936-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7936-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f7936-128">Child Elements</span></span>  
 <span data-ttu-id="f7936-129">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="f7936-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7936-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f7936-130">Parent Elements</span></span>  
  
|<span data-ttu-id="f7936-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7936-131">Element</span></span>|<span data-ttu-id="f7936-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7936-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="f7936-133">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="f7936-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f7936-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="f7936-134">Remarks</span></span>  
 <span data-ttu-id="f7936-135">O `<authentication>` elemento corresponde à <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> classe.</span><span class="sxs-lookup"><span data-stu-id="f7936-135">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> class.</span></span> <span data-ttu-id="f7936-136">Esse elemento especifica um validador, que é invocado durante a autenticação de vizinho para vizinho na malha.</span><span class="sxs-lookup"><span data-stu-id="f7936-136">This element specifies a validator, which is invoked during neighbor-to-neighbor authentication in the mesh.</span></span> <span data-ttu-id="f7936-137">Quando um novo par tenta estabelecer uma conexão vizinha, ele passa sua própria credencial para o par de resposta.</span><span class="sxs-lookup"><span data-stu-id="f7936-137">When a new peer tries to establish a neighbor connection, it passes its own credential to the responding peer.</span></span> <span data-ttu-id="f7936-138">O validador do respondente é chamado para verificar a credencial da parte remota.</span><span class="sxs-lookup"><span data-stu-id="f7936-138">The validator of the responder is invoked to verify the credential of the remote party.</span></span> <span data-ttu-id="f7936-139">Sempre que uma conexão de mesmo nível é estabelecida na malha, ambos os pares são mutuamente autenticados, o que significa que os validadores em ambas as extremidades são invocados.</span><span class="sxs-lookup"><span data-stu-id="f7936-139">Whenever a peer connection is established in the mesh, both peers are mutually authenticated, meaning validators on both ends are invoked.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7936-140">Confira também</span><span class="sxs-lookup"><span data-stu-id="f7936-140">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="f7936-141">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="f7936-141">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="f7936-142">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="f7936-142">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="f7936-143">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f7936-143">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="f7936-144">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="f7936-144">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="f7936-145">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="f7936-145">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
