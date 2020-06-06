---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152626"
---
# \<samlSecurityTokenRequirement>
<span data-ttu-id="b3dd5-101">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="b3dd5-102">Representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="b3dd5-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3dd5-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement
            issuerCertificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
            issuerCertificateRevocationMode="NoCheck||Offline||Online"  
            issuerCertificateTrustedStoreLocation="CurrentLocation||LocalMachine"  
            issuerCertificateValidator="Namespace.Class Assembly"  
            mapToWindows=xs:boolean  
          <nameClaimType value=xs:string />  
          <roleClaimType value=xs:string />  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b3dd5-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b3dd5-104">Attributes and Elements</span></span>  
 <span data-ttu-id="b3dd5-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b3dd5-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="b3dd5-106">Attributes</span></span>  
  
|<span data-ttu-id="b3dd5-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="b3dd5-107">Attribute</span></span>|<span data-ttu-id="b3dd5-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3dd5-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b3dd5-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="b3dd5-109">mapToWindows</span></span>|<span data-ttu-id="b3dd5-110">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="b3dd5-111">O padrão é "falso".</span><span class="sxs-lookup"><span data-stu-id="b3dd5-111">The default is "false".</span></span>|  
|<span data-ttu-id="b3dd5-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="b3dd5-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="b3dd5-113">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b3dd5-114">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="b3dd5-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="b3dd5-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b3dd5-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="b3dd5-116">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b3dd5-117">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="b3dd5-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="b3dd5-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b3dd5-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="b3dd5-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="b3dd5-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="b3dd5-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="b3dd5-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="b3dd5-121">issuerCertificateValidator</span></span>|<span data-ttu-id="b3dd5-122">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="b3dd5-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="b3dd5-123">Se o `issuerCertificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b3dd5-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b3dd5-124">Child Elements</span></span>  
  
|<span data-ttu-id="b3dd5-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="b3dd5-125">Element</span></span>|<span data-ttu-id="b3dd5-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3dd5-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="b3dd5-127">Define o tipo de declaração que especifica a <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="b3dd5-128">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornada pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b3dd5-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b3dd5-129">Parent Elements</span></span>  
  
|<span data-ttu-id="b3dd5-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="b3dd5-130">Element</span></span>|<span data-ttu-id="b3dd5-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="b3dd5-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="b3dd5-132">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="b3dd5-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3dd5-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3dd5-133">Remarks</span></span>  
 <span data-ttu-id="b3dd5-134">O `<samlSecurityTokenRequirement>` elemento é representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe no modelo de objeto e é usado para configurar a `SamlSecurityTokenRequirement` propriedade em um <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou um <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="b3dd5-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3dd5-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b3dd5-135">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement issuerCertificateValidationMode="PeerOrChainTrust"  
                                  issuerCertificateRevocationMode="Online"  
                                  issuerCertificateTrustedStoreLocation="LocalMachine"  
                                  mapToWindows="false">  
  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```
