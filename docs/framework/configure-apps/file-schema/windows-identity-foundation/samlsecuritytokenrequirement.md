---
title: <samlSecurityTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 09202d12-88d3-49cc-953b-703bcc1690eb
author: BrucePerlerMS
ms.openlocfilehash: df259398beb242ea95efb248d6b5140b38ca3c45
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942489"
---
# <a name="samlsecuritytokenrequirement"></a><span data-ttu-id="8831b-101">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="8831b-101">\<samlSecurityTokenRequirement></span></span>
<span data-ttu-id="8831b-102">Fornece a configuração para <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> a classe, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> a classe ou uma classe derivada de qualquer uma dessas classes.</span><span class="sxs-lookup"><span data-stu-id="8831b-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span> <span data-ttu-id="8831b-103">Representado pela <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> classe.</span><span class="sxs-lookup"><span data-stu-id="8831b-103">Represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class.</span></span>  
  
 <span data-ttu-id="8831b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8831b-104">\<system.identityModel></span></span>  
<span data-ttu-id="8831b-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8831b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8831b-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8831b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8831b-107">\<add></span><span class="sxs-lookup"><span data-stu-id="8831b-107">\<add></span></span>  
<span data-ttu-id="8831b-108">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="8831b-108">\<samlSecurityTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8831b-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8831b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8831b-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="8831b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8831b-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="8831b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8831b-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="8831b-112">Attributes</span></span>  
  
|<span data-ttu-id="8831b-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="8831b-113">Attribute</span></span>|<span data-ttu-id="8831b-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="8831b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8831b-115">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="8831b-115">mapToWindows</span></span>|<span data-ttu-id="8831b-116">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="8831b-116">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="8831b-117">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="8831b-117">The default is "false".</span></span>|  
|<span data-ttu-id="8831b-118">issuerCertificateRevocationMode</span><span class="sxs-lookup"><span data-stu-id="8831b-118">issuerCertificateRevocationMode</span></span>|<span data-ttu-id="8831b-119">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="8831b-119">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="8831b-120">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="8831b-120">The default value is "Online".</span></span>|  
|<span data-ttu-id="8831b-121">issuerCertificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="8831b-121">issuerCertificateValidationMode</span></span>|<span data-ttu-id="8831b-122">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="8831b-122">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="8831b-123">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="8831b-123">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="8831b-124">issuerCertificateTrustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="8831b-124">issuerCertificateTrustedStoreLocation</span></span>|<span data-ttu-id="8831b-125">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="8831b-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="8831b-126">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="8831b-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="8831b-127">issuerCertificateValidator</span><span class="sxs-lookup"><span data-stu-id="8831b-127">issuerCertificateValidator</span></span>|<span data-ttu-id="8831b-128">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="8831b-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="8831b-129">Se o `issuerCertificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="8831b-129">If the `issuerCertificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8831b-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="8831b-130">Child Elements</span></span>  
  
|<span data-ttu-id="8831b-131">Elemento</span><span class="sxs-lookup"><span data-stu-id="8831b-131">Element</span></span>|<span data-ttu-id="8831b-132">Descrição</span><span class="sxs-lookup"><span data-stu-id="8831b-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8831b-133">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="8831b-133">\<nameClaimType></span></span>](nameclaimtype.md)|<span data-ttu-id="8831b-134">Define o tipo de declaração que especifica <xref:System.Security.Principal.IIdentity.Name%2A> a propriedade.</span><span class="sxs-lookup"><span data-stu-id="8831b-134">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span>|  
|[<span data-ttu-id="8831b-135">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="8831b-135">\<roleClaimType></span></span>](roleclaimtype.md)|<span data-ttu-id="8831b-136">Especifica o tipo de declaração que define as declarações de tipo de função na <xref:System.Security.Claims.ClaimsIdentity> coleção de objetos retornada <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> pelo método do manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="8831b-136">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8831b-137">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="8831b-137">Parent Elements</span></span>  
  
|<span data-ttu-id="8831b-138">Elemento</span><span class="sxs-lookup"><span data-stu-id="8831b-138">Element</span></span>|<span data-ttu-id="8831b-139">Descrição</span><span class="sxs-lookup"><span data-stu-id="8831b-139">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8831b-140">\<add></span><span class="sxs-lookup"><span data-stu-id="8831b-140">\<add></span></span>](add.md)|<span data-ttu-id="8831b-141">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="8831b-141">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8831b-142">Comentários</span><span class="sxs-lookup"><span data-stu-id="8831b-142">Remarks</span></span>  
 <span data-ttu-id="8831b-143">O `<samlSecurityTokenRequirement>` elemento é representado <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> pela classe no modelo de objeto e é usado para configurar a `SamlSecurityTokenRequirement` Propriedade em um <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> ou um <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="8831b-143">The `<samlSecurityTokenRequirement>` element is represented by the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> class in the object model and is used to configure the `SamlSecurityTokenRequirement` property on a <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> or a <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8831b-144">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8831b-144">Example</span></span>  
  
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
