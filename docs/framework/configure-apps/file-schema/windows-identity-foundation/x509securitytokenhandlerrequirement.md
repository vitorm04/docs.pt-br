---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152444"
---
# <a name="x509securitytokenhandlerrequirement"></a><span data-ttu-id="7bbf7-101">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="7bbf7-101">\<x509SecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="7bbf7-102">Fornece configuração <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> opcional para as classes de classe ou derivadas.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-102">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="7bbf7-103">[**\<>de configuração**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7bbf7-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7bbf7-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="7bbf7-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="7bbf7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de configuração de identidade**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="7bbf7-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="7bbf7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de segurançaTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="7bbf7-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="7bbf7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<adicionar>**](add.md)</span><span class="sxs-lookup"><span data-stu-id="7bbf7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="7bbf7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span><span class="sxs-lookup"><span data-stu-id="7bbf7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bbf7-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7bbf7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7bbf7-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7bbf7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7bbf7-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7bbf7-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7bbf7-112">Attributes</span></span>  
  
|<span data-ttu-id="7bbf7-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="7bbf7-113">Attribute</span></span>|<span data-ttu-id="7bbf7-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bbf7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7bbf7-115">modo de validação de certificados</span><span class="sxs-lookup"><span data-stu-id="7bbf7-115">certificateValidationMode</span></span>|<span data-ttu-id="7bbf7-116">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-116">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7bbf7-117">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="7bbf7-117">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="7bbf7-118">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="7bbf7-118">mapToWindows</span></span>|<span data-ttu-id="7bbf7-119">Especifica se o manipulador de tokens deve mapear o token de validação para uma conta do Windows usando a reclamação UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-119">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="7bbf7-120">O padrão é "falso".</span><span class="sxs-lookup"><span data-stu-id="7bbf7-120">The default is "false".</span></span>|  
|<span data-ttu-id="7bbf7-121">Revocationmode</span><span class="sxs-lookup"><span data-stu-id="7bbf7-121">revocationMode</span></span>|<span data-ttu-id="7bbf7-122">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X.509.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-122">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="7bbf7-123">O valor padrão é "Online".</span><span class="sxs-lookup"><span data-stu-id="7bbf7-123">The default value is "Online".</span></span>|  
|<span data-ttu-id="7bbf7-124">trustedStoreLocalização</span><span class="sxs-lookup"><span data-stu-id="7bbf7-124">trustedStoreLocation</span></span>|<span data-ttu-id="7bbf7-125">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica a loja de certificados X.509.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-125">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="7bbf7-126">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="7bbf7-126">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="7bbf7-127">validador de certificado</span><span class="sxs-lookup"><span data-stu-id="7bbf7-127">certificateValidator</span></span>|<span data-ttu-id="7bbf7-128">Um tipo personalizado que <xref:System.IdentityModel.Selectors.X509CertificateValidator>deriva de .</span><span class="sxs-lookup"><span data-stu-id="7bbf7-128">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="7bbf7-129">Se `certificateValidationMode` o atributo for "Personalizado", uma instância desse tipo será usada para validação de certificado de emissor.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-129">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7bbf7-130">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7bbf7-130">Child Elements</span></span>  
 <span data-ttu-id="7bbf7-131">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7bbf7-131">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7bbf7-132">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7bbf7-132">Parent Elements</span></span>  
  
|<span data-ttu-id="7bbf7-133">Elemento</span><span class="sxs-lookup"><span data-stu-id="7bbf7-133">Element</span></span>|<span data-ttu-id="7bbf7-134">Descrição</span><span class="sxs-lookup"><span data-stu-id="7bbf7-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7bbf7-135">\<adicionar></span><span class="sxs-lookup"><span data-stu-id="7bbf7-135">\<add></span></span>](add.md)|<span data-ttu-id="7bbf7-136">Adiciona o manipulador de token de segurança especificado à coleção do manipulador de tokens.</span><span class="sxs-lookup"><span data-stu-id="7bbf7-136">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="7bbf7-137">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7bbf7-137">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
