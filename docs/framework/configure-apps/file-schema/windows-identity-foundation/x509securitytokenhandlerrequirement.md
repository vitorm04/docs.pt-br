---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 2851820460a34d62175929b48ad57914df557059
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945179"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="0e543-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="0e543-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="0e543-102">Fornece a configuração opcional para <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> a classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="0e543-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="0e543-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0e543-103">\<system.identityModel></span></span>  
<span data-ttu-id="0e543-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0e543-104">\<identityConfiguration></span></span>  
<span data-ttu-id="0e543-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0e543-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0e543-106">\<add></span><span class="sxs-lookup"><span data-stu-id="0e543-106">\<add></span></span>  
<span data-ttu-id="0e543-107">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="0e543-107">\<x509SecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e543-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0e543-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0e543-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0e543-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0e543-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0e543-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0e543-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0e543-111">Attributes</span></span>  
  
|<span data-ttu-id="0e543-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0e543-112">Attribute</span></span>|<span data-ttu-id="0e543-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e543-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0e543-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="0e543-114">certificateValidationMode</span></span>|<span data-ttu-id="0e543-115">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="0e543-115">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0e543-116">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="0e543-116">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="0e543-117">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="0e543-117">mapToWindows</span></span>|<span data-ttu-id="0e543-118">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="0e543-118">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="0e543-119">O padrão é "false".</span><span class="sxs-lookup"><span data-stu-id="0e543-119">The default is "false".</span></span>|  
|<span data-ttu-id="0e543-120">revocationMode</span><span class="sxs-lookup"><span data-stu-id="0e543-120">revocationMode</span></span>|<span data-ttu-id="0e543-121">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="0e543-121">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="0e543-122">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="0e543-122">The default value is "Online".</span></span>|  
|<span data-ttu-id="0e543-123">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="0e543-123">trustedStoreLocation</span></span>|<span data-ttu-id="0e543-124">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="0e543-124">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="0e543-125">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="0e543-125">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="0e543-126">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="0e543-126">certificateValidator</span></span>|<span data-ttu-id="0e543-127">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span><span class="sxs-lookup"><span data-stu-id="0e543-127">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="0e543-128">Se o `certificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="0e543-128">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0e543-129">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0e543-129">Child Elements</span></span>  
 <span data-ttu-id="0e543-130">Nenhum</span><span class="sxs-lookup"><span data-stu-id="0e543-130">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0e543-131">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0e543-131">Parent Elements</span></span>  
  
|<span data-ttu-id="0e543-132">Elemento</span><span class="sxs-lookup"><span data-stu-id="0e543-132">Element</span></span>|<span data-ttu-id="0e543-133">Descrição</span><span class="sxs-lookup"><span data-stu-id="0e543-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0e543-134">\<add></span><span class="sxs-lookup"><span data-stu-id="0e543-134">\<add></span></span>](add.md)|<span data-ttu-id="0e543-135">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="0e543-135">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0e543-136">Exemplo</span><span class="sxs-lookup"><span data-stu-id="0e543-136">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"   
                                         certificateValidationMode="PeerOrChainTrust"   
                                         revocationMode="Online"   
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
