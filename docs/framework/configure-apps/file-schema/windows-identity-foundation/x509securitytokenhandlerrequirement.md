---
title: '&lt;x509SecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 66d4e0d6a121f807f5f372b3f39577b0bb3c4ca6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltx509securitytokenhandlerrequirementgt"></a><span data-ttu-id="d306d-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="d306d-102">&lt;x509SecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="d306d-103">Fornece configuração opcional para o <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="d306d-103">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="d306d-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="d306d-104">\<system.identityModel></span></span>  
<span data-ttu-id="d306d-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d306d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d306d-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d306d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d306d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="d306d-107">\<add></span></span>  
<span data-ttu-id="d306d-108">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d306d-108">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d306d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d306d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d306d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="d306d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="d306d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="d306d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d306d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="d306d-112">Attributes</span></span>  
  
|<span data-ttu-id="d306d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="d306d-113">Attribute</span></span>|<span data-ttu-id="d306d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="d306d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d306d-115">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="d306d-115">certificateValidationMode</span></span>|<span data-ttu-id="d306d-116">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d306d-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d306d-117">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="d306d-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="d306d-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="d306d-118">mapToWindows</span></span>|<span data-ttu-id="d306d-119">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração de UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="d306d-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="d306d-120">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="d306d-120">The default is "false".</span></span>|  
|<span data-ttu-id="d306d-121">revocationMode</span><span class="sxs-lookup"><span data-stu-id="d306d-121">revocationMode</span></span>|<span data-ttu-id="d306d-122">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="d306d-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="d306d-123">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="d306d-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="d306d-124">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="d306d-124">trustedStoreLocation</span></span>|<span data-ttu-id="d306d-125">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="d306d-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="d306d-126">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="d306d-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="d306d-127">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="d306d-127">certificateValidator</span></span>|<span data-ttu-id="d306d-128">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="d306d-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="d306d-129">Se o `certificateValidationMode` atributo é "Custom", uma instância desse tipo é usada para validação de certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="d306d-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d306d-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="d306d-130">Child Elements</span></span>  
 <span data-ttu-id="d306d-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="d306d-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d306d-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="d306d-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d306d-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="d306d-133">Element</span></span>|<span data-ttu-id="d306d-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="d306d-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d306d-135">\<add></span><span class="sxs-lookup"><span data-stu-id="d306d-135">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="d306d-136">Adiciona o manipulador de token de segurança especificados na coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="d306d-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d306d-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d306d-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
