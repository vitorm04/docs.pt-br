---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 6e8267f170dbb26381564be7b66df5f617156885
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790436"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="44afa-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="44afa-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="44afa-102">Fornece configuração opcional para o <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="44afa-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="44afa-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="44afa-103">\<system.identityModel></span></span>  
<span data-ttu-id="44afa-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="44afa-104">\<identityConfiguration></span></span>  
<span data-ttu-id="44afa-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="44afa-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="44afa-106">\<add></span><span class="sxs-lookup"><span data-stu-id="44afa-106">\<add></span></span>  
<span data-ttu-id="44afa-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="44afa-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44afa-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44afa-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44afa-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="44afa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="44afa-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="44afa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44afa-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="44afa-111">Attributes</span></span>  
  
|<span data-ttu-id="44afa-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="44afa-112">Attribute</span></span>|<span data-ttu-id="44afa-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="44afa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44afa-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="44afa-114">certificateValidationMode</span></span>|<span data-ttu-id="44afa-115">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="44afa-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="44afa-116">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="44afa-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="44afa-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="44afa-117">mapToWindows</span></span>|<span data-ttu-id="44afa-118">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração de UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="44afa-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="44afa-119">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="44afa-119">The default is "false".</span></span>|  
|<span data-ttu-id="44afa-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="44afa-120">revocationMode</span></span>|<span data-ttu-id="44afa-121">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação para usar o certificado x. 509.</span><span class="sxs-lookup"><span data-stu-id="44afa-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="44afa-122">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="44afa-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="44afa-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="44afa-123">trustedStoreLocation</span></span>|<span data-ttu-id="44afa-124">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados x. 509.</span><span class="sxs-lookup"><span data-stu-id="44afa-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="44afa-125">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="44afa-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="44afa-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="44afa-126">certificateValidator</span></span>|<span data-ttu-id="44afa-127">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="44afa-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="44afa-128">Se o `certificateValidationMode` atributo é "Custom", uma instância desse tipo é usada para validação de certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="44afa-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44afa-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="44afa-129">Child Elements</span></span>  
 <span data-ttu-id="44afa-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="44afa-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44afa-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="44afa-131">Parent Elements</span></span>  
  
|<span data-ttu-id="44afa-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="44afa-132">Element</span></span>|<span data-ttu-id="44afa-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="44afa-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="44afa-134">\<add></span><span class="sxs-lookup"><span data-stu-id="44afa-134">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="44afa-135">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="44afa-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="44afa-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="44afa-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
