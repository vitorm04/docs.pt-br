---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: cab7572518a7a6dc26f8bbcf67cd424fa1c01085
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251896"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="b1e83-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="b1e83-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="b1e83-102">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="b1e83-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="b1e83-103">Representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="b1e83-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="b1e83-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b1e83-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b1e83-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b1e83-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b1e83-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b1e83-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b1e83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="b1e83-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="b1e83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="b1e83-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="b1e83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> samlSecurityTokenRequirement**</span><span class="sxs-lookup"><span data-stu-id="b1e83-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1e83-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b1e83-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1e83-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="b1e83-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b1e83-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="b1e83-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1e83-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="b1e83-113">Attributes</span></span>  
  
|<span data-ttu-id="b1e83-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="b1e83-114">Attribute</span></span>|<span data-ttu-id="b1e83-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1e83-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b1e83-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="b1e83-116">mapToWindows</span></span>|<span data-ttu-id="b1e83-117">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="b1e83-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="b1e83-118">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="b1e83-118">The default is "false".</span></span>|  
|<span data-ttu-id="b1e83-119">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="b1e83-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="b1e83-120">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1e83-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b1e83-121">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="b1e83-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="b1e83-122">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="b1e83-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="b1e83-123">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1e83-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="b1e83-124">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="b1e83-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="b1e83-125">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="b1e83-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="b1e83-126">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="b1e83-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="b1e83-127">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="b1e83-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="b1e83-128">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="b1e83-128">issuerCertificateValidator</span></span>|<span data-ttu-id="b1e83-129">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="b1e83-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="b1e83-130">Se o `issuerCertificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="b1e83-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1e83-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="b1e83-131">Child Elements</span></span>  
  
|<span data-ttu-id="b1e83-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1e83-132">Element</span></span>|<span data-ttu-id="b1e83-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1e83-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1e83-134">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="b1e83-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="b1e83-135">Define o tipo de declaração que especifica <xref:System.Security.Principal.IIdentity.Name%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="b1e83-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="b1e83-136">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="b1e83-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="b1e83-137">Especifica o tipo de declaração que define as declarações de tipo de função na <xref:System.Security.Claims.ClaimsIdentity> coleção de objetos retornada <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> pelo método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="b1e83-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b1e83-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="b1e83-138">Parent Elements</span></span>  
  
|<span data-ttu-id="b1e83-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="b1e83-139">Element</span></span>|<span data-ttu-id="b1e83-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="b1e83-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b1e83-141">\<add></span><span class="sxs-lookup"><span data-stu-id="b1e83-141">\<add></span></span>](add.md)|<span data-ttu-id="b1e83-142">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="b1e83-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1e83-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="b1e83-143">Remarks</span></span>  
 <span data-ttu-id="b1e83-144">O `<samlSecurityTokenRequirement>` elemento é representado <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> pela classe no modelo de objeto e é usado para configurar a `SamlSecurityTokenRequirement` Propriedade em um <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou um <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="b1e83-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b1e83-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b1e83-145">Example</span></span>  
  
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
