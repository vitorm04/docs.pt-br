---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: b27f337189a7d0b66ffd38e032b5eb864e5094a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152626"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="39595-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="39595-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="39595-102">Fornece configuração <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> para <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe, a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="39595-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="39595-103">Representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="39595-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
<span data-ttu-id="39595-104">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="39595-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="39595-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="39595-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="39595-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="39595-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="39595-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="39595-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="39595-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="39595-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="39595-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span><span class="sxs-lookup"><span data-stu-id="39595-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<samlSecurityTokenRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39595-110">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39595-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39595-111">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39595-111">Attributes and Elements</span></span>  
 <span data-ttu-id="39595-112">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39595-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39595-113">Atributos</span><span class="sxs-lookup"><span data-stu-id="39595-113">Attributes</span></span>  
  
|<span data-ttu-id="39595-114">Atributo</span><span class="sxs-lookup"><span data-stu-id="39595-114">Attribute</span></span>|<span data-ttu-id="39595-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="39595-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39595-116">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="39595-116">mapToWindows</span></span>|<span data-ttu-id="39595-117">Especifica se o manipulador de tokens deve mapear o token de validação para uma conta do Windows usando a reclamação UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="39595-117">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="39595-118">O padrão é "falso".</span><span class="sxs-lookup"><span data-stu-id="39595-118">The default is "false".</span></span>|  
|<span data-ttu-id="39595-119">emissorCertificadoRevocaçãoMode</span><span class="sxs-lookup"><span data-stu-id="39595-119">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="39595-120">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="39595-120">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="39595-121">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="39595-121">The default value is "Online".</span></span>|  
|<span data-ttu-id="39595-122">emissorCertificadoValidaçãoMode</span><span class="sxs-lookup"><span data-stu-id="39595-122">issuerCertificateValidationMode</span></span>|<span data-ttu-id="39595-123">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="39595-123">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="39595-124">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="39595-124">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="39595-125">emissorRetercertificadoDeconfiançaLocalizaçãodeArmazenamento</span><span class="sxs-lookup"><span data-stu-id="39595-125">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="39595-126">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica a loja de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="39595-126">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="39595-127">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="39595-127">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="39595-128">emissorCertificadode certificado</span><span class="sxs-lookup"><span data-stu-id="39595-128">issuerCertificateValidator</span></span>|<span data-ttu-id="39595-129">Um tipo personalizado que <xref:System.IdentityModel.Selectors.X509CertificateValidator>deriva de .</span><span class="sxs-lookup"><span data-stu-id="39595-129">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="39595-130">Se `issuerCertificateValidationMode` o atributo for "Personalizado", uma instância desse tipo será usada para validação de certificado de emissor.</span><span class="sxs-lookup"><span data-stu-id="39595-130">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39595-131">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39595-131">Child Elements</span></span>  
  
|<span data-ttu-id="39595-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="39595-132">Element</span></span>|<span data-ttu-id="39595-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="39595-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39595-134">\<>de nameClaimType</span><span class="sxs-lookup"><span data-stu-id="39595-134">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="39595-135">Define o tipo de <xref:System.Security.Principal.IIdentity.Name%2A> solicitação que especifica a propriedade.</span><span class="sxs-lookup"><span data-stu-id="39595-135">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="39595-136">\<>roleClaimType</span><span class="sxs-lookup"><span data-stu-id="39595-136">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="39595-137">Especifica o tipo de solicitação que define as <xref:System.Security.Claims.ClaimsIdentity> reivindicações do <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> tipo de função na coleção de objetos retornados pelo método do manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="39595-137">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="39595-138">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39595-138">Parent Elements</span></span>  
  
|<span data-ttu-id="39595-139">Elemento</span><span class="sxs-lookup"><span data-stu-id="39595-139">Element</span></span>|<span data-ttu-id="39595-140">Descrição</span><span class="sxs-lookup"><span data-stu-id="39595-140">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39595-141">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="39595-141">\<add></span></span>](add.md)|<span data-ttu-id="39595-142">Adiciona o manipulador de token de segurança especificado à coleção do manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="39595-142">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="39595-143">Comentários</span><span class="sxs-lookup"><span data-stu-id="39595-143">Remarks</span></span>  
 <span data-ttu-id="39595-144">O `<samlSecurityTokenRequirement>` elemento é <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> representado pela classe no modelo do `SamlSecurityTokenRequirement` objeto e <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> é <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>usado para configurar a propriedade em um ou a .</span><span class="sxs-lookup"><span data-stu-id="39595-144">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="39595-145">Exemplo</span><span class="sxs-lookup"><span data-stu-id="39595-145">Example</span></span>  
  
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
