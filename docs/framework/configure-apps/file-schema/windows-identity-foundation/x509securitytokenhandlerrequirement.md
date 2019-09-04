---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 76eeea635fd65486a1c16bea15a49018876dae99
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251688"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="f7143-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="f7143-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="f7143-102">Fornece a configuração opcional para <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="f7143-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="f7143-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f7143-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f7143-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="f7143-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="f7143-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="f7143-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="f7143-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="f7143-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="f7143-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Adicionar >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="f7143-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="f7143-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> x509SecurityTokenHandlerRequirement**</span><span class="sxs-lookup"><span data-stu-id="f7143-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7143-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f7143-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7143-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="f7143-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f7143-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="f7143-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7143-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="f7143-112">Attributes</span></span>  
  
|<span data-ttu-id="f7143-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="f7143-113">Attribute</span></span>|<span data-ttu-id="f7143-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7143-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f7143-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="f7143-115">certificateValidationMode</span></span>|<span data-ttu-id="f7143-116">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="f7143-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f7143-117">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="f7143-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="f7143-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="f7143-118">mapToWindows</span></span>|<span data-ttu-id="f7143-119">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="f7143-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="f7143-120">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="f7143-120">The default is "false".</span></span>|  
|<span data-ttu-id="f7143-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="f7143-121">revocationMode</span></span>|<span data-ttu-id="f7143-122">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="f7143-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="f7143-123">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="f7143-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="f7143-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="f7143-124">trustedStoreLocation</span></span>|<span data-ttu-id="f7143-125">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="f7143-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="f7143-126">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="f7143-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="f7143-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="f7143-127">certificateValidator</span></span>|<span data-ttu-id="f7143-128">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="f7143-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="f7143-129">Se o `certificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="f7143-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7143-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="f7143-130">Child Elements</span></span>  
 <span data-ttu-id="f7143-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="f7143-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f7143-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="f7143-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f7143-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="f7143-133">Element</span></span>|<span data-ttu-id="f7143-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="f7143-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7143-135">\<add></span><span class="sxs-lookup"><span data-stu-id="f7143-135">\<add></span></span>](add.md)|<span data-ttu-id="f7143-136">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="f7143-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f7143-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f7143-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
