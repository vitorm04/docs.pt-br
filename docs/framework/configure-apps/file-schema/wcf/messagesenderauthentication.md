---
title: <messageSenderAuthentication>
ms.date: 03/30/2017
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
ms.openlocfilehash: c6183a8d27d56c7199b815ccb31b06f983a51b33
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398395"
---
# \<messageSenderAuthentication>
<span data-ttu-id="7bfec-101">Especifica as configurações de autenticação para o certificado par usado por um remetente de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7bfec-101">Specifies authentication settings for peer certificate used by a message sender.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="7bfec-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bfec-102">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bfec-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7bfec-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7bfec-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7bfec-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bfec-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="7bfec-105">Attributes</span></span>  
  
|<span data-ttu-id="7bfec-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="7bfec-106">Attribute</span></span>|<span data-ttu-id="7bfec-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bfec-107">Description</span></span>|  
|---------------|-----------------|  
|`certificateValidationMode`|<span data-ttu-id="7bfec-108">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="7bfec-108">Optional enumeration.</span></span> <span data-ttu-id="7bfec-109">Especifica um dos cinco modos usados para validar as credenciais.</span><span class="sxs-lookup"><span data-stu-id="7bfec-109">Specifies one of five modes used to validate credentials.</span></span> <span data-ttu-id="7bfec-110">Esse atributo é do tipo <xref:System.ServiceModel.Security.X509CertificateValidationMode> .</span><span class="sxs-lookup"><span data-stu-id="7bfec-110">This attribute is of type <xref:System.ServiceModel.Security.X509CertificateValidationMode>.</span></span> <span data-ttu-id="7bfec-111">Se definido como `Custom` , um `customCertificateValidator` também deverá ser fornecido.</span><span class="sxs-lookup"><span data-stu-id="7bfec-111">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`customCertificateValidatorType`|<span data-ttu-id="7bfec-112">Cadeia de caracteres opcional.</span><span class="sxs-lookup"><span data-stu-id="7bfec-112">Optional string.</span></span> <span data-ttu-id="7bfec-113">Especifica um tipo e um assembly usados para validar um tipo personalizado.</span><span class="sxs-lookup"><span data-stu-id="7bfec-113">Specifies a type and assembly used to validate a custom type.</span></span> <span data-ttu-id="7bfec-114">Esse atributo deve ser definido quando `certificateValidationMode` é definido como `Custom` .</span><span class="sxs-lookup"><span data-stu-id="7bfec-114">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span> <span data-ttu-id="7bfec-115">Esse atributo é do tipo <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="7bfec-115">This attribute is of type <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="7bfec-116">O Windows Communication Foundation (WCF) fornece um validador de certificado par padrão que verifica o certificado de mesmo nível no repositório de pessoas confiáveis.</span><span class="sxs-lookup"><span data-stu-id="7bfec-116">Windows Communication Foundation (WCF) provides a default peer certificate validator that verifies the peer certificate against the trusted people store.</span></span> <span data-ttu-id="7bfec-117">Ele também verifica se o certificado se encadeia em uma raiz válida.</span><span class="sxs-lookup"><span data-stu-id="7bfec-117">It also verifies that the certificate chains up to a valid root.</span></span> <span data-ttu-id="7bfec-118">Você pode implementar um validador personalizado para especificar um comportamento diferente e usar esse atributo para apontar para o validador personalizado.</span><span class="sxs-lookup"><span data-stu-id="7bfec-118">You can implement a custom validator to specify a different behavior and use this attribute to point to the custom validator.</span></span>|  
|`revocationMode`|<span data-ttu-id="7bfec-119">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="7bfec-119">Optional enumeration.</span></span> <span data-ttu-id="7bfec-120">Especifica o modo de revogação de certificado.</span><span class="sxs-lookup"><span data-stu-id="7bfec-120">Specifies the certificate revocation mode.</span></span> <span data-ttu-id="7bfec-121">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> .</span><span class="sxs-lookup"><span data-stu-id="7bfec-121">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>.</span></span> <span data-ttu-id="7bfec-122">O sistema verifica se o certificado de mesmo nível não foi revogado ao procurá-lo na lista de certificados revogados.</span><span class="sxs-lookup"><span data-stu-id="7bfec-122">The system verifies that the peer certificate has not been revoked by looking it up in the revoked certificate list.</span></span> <span data-ttu-id="7bfec-123">Essa verificação pode ser executada marcando-se online ou em uma lista de revogação armazenada em cache.</span><span class="sxs-lookup"><span data-stu-id="7bfec-123">This check can be performed either by checking online or against a cached revocation list.</span></span> <span data-ttu-id="7bfec-124">A verificação de revogação pode ser desativada definindo esse atributo como NoCheck.</span><span class="sxs-lookup"><span data-stu-id="7bfec-124">Revocation checking can be turned off by setting this attribute to NoCheck.</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="7bfec-125">Enumeração opcional.</span><span class="sxs-lookup"><span data-stu-id="7bfec-125">Optional enumeration.</span></span> <span data-ttu-id="7bfec-126">Especifica o local de repositório confiável em que o certificado par é validado pelo sistema de segurança do WCF.</span><span class="sxs-lookup"><span data-stu-id="7bfec-126">Specifies the trusted store location where the peer certificate is validated by the WCF security system.</span></span> <span data-ttu-id="7bfec-127">Esse atributo é do tipo <xref:System.Security.Cryptography.X509Certificates.StoreLocation> .</span><span class="sxs-lookup"><span data-stu-id="7bfec-127">This attribute is of type <xref:System.Security.Cryptography.X509Certificates.StoreLocation>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bfec-128">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7bfec-128">Child Elements</span></span>  
 <span data-ttu-id="7bfec-129">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="7bfec-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bfec-130">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7bfec-130">Parent Elements</span></span>  
  
|<span data-ttu-id="7bfec-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="7bfec-131">Element</span></span>|<span data-ttu-id="7bfec-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bfec-132">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-servicecredentials.md)|<span data-ttu-id="7bfec-133">Especifica as credenciais atuais para um nó par.</span><span class="sxs-lookup"><span data-stu-id="7bfec-133">Specifies the current credentials for a peer node.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bfec-134">Comentários</span><span class="sxs-lookup"><span data-stu-id="7bfec-134">Remarks</span></span>  
 <span data-ttu-id="7bfec-135">Esse elemento deve ser configurado se a autenticação de mensagem for escolhida.</span><span class="sxs-lookup"><span data-stu-id="7bfec-135">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="7bfec-136">Para canais de saída, cada mensagem é assinada usando o certificado fornecido pelo [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="7bfec-136">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="7bfec-137">Todas as mensagens, antes de serem entregues ao aplicativo, são verificadas em relação à credencial da mensagem usando o validador especificado pelo `customCertificateValidatorType` atributo desse elemento.</span><span class="sxs-lookup"><span data-stu-id="7bfec-137">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="7bfec-138">O Validador pode aceitar ou rejeitar a credencial.</span><span class="sxs-lookup"><span data-stu-id="7bfec-138">The validator can either accept or reject the credential.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bfec-139">Confira também</span><span class="sxs-lookup"><span data-stu-id="7bfec-139">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- [<span data-ttu-id="7bfec-140">Trabalhando com certificados</span><span class="sxs-lookup"><span data-stu-id="7bfec-140">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7bfec-141">Rede ponto a ponto</span><span class="sxs-lookup"><span data-stu-id="7bfec-141">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="7bfec-142">[Autenticação de mensagem de canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7bfec-142">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="7bfec-143">[Autenticação personalizada do canal par](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7bfec-143">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="7bfec-144">Protegendo aplicativos de canal par</span><span class="sxs-lookup"><span data-stu-id="7bfec-144">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
