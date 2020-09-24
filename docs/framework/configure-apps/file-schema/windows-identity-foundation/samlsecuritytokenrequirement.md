---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: f93ec0007b537e306a570b166eaa4cd2fe7f81e2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91157025"
---
# \<samlSecurityTokenRequirement>

<span data-ttu-id="85465-101">Fornece a configuração para a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> classe, a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="85465-101">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="85465-102">Representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="85465-102">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="85465-103">Syntax</span><span class="sxs-lookup"><span data-stu-id="85465-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85465-104">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="85465-104">Attributes and Elements</span></span>  

 <span data-ttu-id="85465-105">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="85465-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85465-106">Atributos</span><span class="sxs-lookup"><span data-stu-id="85465-106">Attributes</span></span>  
  
|<span data-ttu-id="85465-107">Atributo</span><span class="sxs-lookup"><span data-stu-id="85465-107">Attribute</span></span>|<span data-ttu-id="85465-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="85465-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85465-109">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="85465-109">mapToWindows</span></span>|<span data-ttu-id="85465-110">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="85465-110">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="85465-111">O padrão é "falso".</span><span class="sxs-lookup"><span data-stu-id="85465-111">The default is "false".</span></span>|  
|<span data-ttu-id="85465-112">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="85465-112">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="85465-113">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="85465-113">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85465-114">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="85465-114">The default value is "Online".</span></span>|  
|<span data-ttu-id="85465-115">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="85465-115">issuerCertificateValidationMode</span></span>|<span data-ttu-id="85465-116">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="85465-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="85465-117">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="85465-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="85465-118">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="85465-118">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="85465-119">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="85465-119">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="85465-120">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="85465-120">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="85465-121">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="85465-121">issuerCertificateValidator</span></span>|<span data-ttu-id="85465-122">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="85465-122">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="85465-123">Se o `issuerCertificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="85465-123">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85465-124">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="85465-124">Child Elements</span></span>  
  
|<span data-ttu-id="85465-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="85465-125">Element</span></span>|<span data-ttu-id="85465-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="85465-126">Description</span></span>|  
|-------------|-----------------|  
|[\<nameClaimType>](nameclaimtype.md)|<span data-ttu-id="85465-127">Define o tipo de declaração que especifica a <xref:System.Security.Principal.IIdentity.Name%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="85465-127">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[\<roleClaimType>](roleclaimtype.md)|<span data-ttu-id="85465-128">Especifica o tipo de declaração que define as declarações de tipo de função na coleção de <xref:System.Security.Claims.ClaimsIdentity> objetos retornada pelo <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="85465-128">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="85465-129">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="85465-129">Parent Elements</span></span>  
  
|<span data-ttu-id="85465-130">Elemento</span><span class="sxs-lookup"><span data-stu-id="85465-130">Element</span></span>|<span data-ttu-id="85465-131">Descrição</span><span class="sxs-lookup"><span data-stu-id="85465-131">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="85465-132">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="85465-132">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85465-133">Comentários</span><span class="sxs-lookup"><span data-stu-id="85465-133">Remarks</span></span>  

 <span data-ttu-id="85465-134">O `<samlSecurityTokenRequirement>` elemento é representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe no modelo de objeto e é usado para configurar a `SamlSecurityTokenRequirement` propriedade em um <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou um <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="85465-134">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85465-135">Exemplo</span><span class="sxs-lookup"><span data-stu-id="85465-135">Example</span></span>  
  
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
