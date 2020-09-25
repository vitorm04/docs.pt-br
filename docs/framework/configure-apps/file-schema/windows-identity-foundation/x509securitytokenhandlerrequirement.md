---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: a6a8185297e1345de9fa20c7d4d0dffbdcd8620f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91185386"
---
# \<x509SecurityTokenHandlerRequirement>

<span data-ttu-id="eedcc-101">Fornece a configuração opcional para a <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="eedcc-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="eedcc-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eedcc-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eedcc-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eedcc-103">Attributes and Elements</span></span>  

 <span data-ttu-id="eedcc-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eedcc-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eedcc-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="eedcc-105">Attributes</span></span>  
  
|<span data-ttu-id="eedcc-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="eedcc-106">Attribute</span></span>|<span data-ttu-id="eedcc-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="eedcc-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eedcc-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="eedcc-108">certificateValidationMode</span></span>|<span data-ttu-id="eedcc-109">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="eedcc-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="eedcc-110">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="eedcc-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="eedcc-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="eedcc-111">mapToWindows</span></span>|<span data-ttu-id="eedcc-112">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="eedcc-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="eedcc-113">O padrão é "falso".</span><span class="sxs-lookup"><span data-stu-id="eedcc-113">The default is "false".</span></span>|  
|<span data-ttu-id="eedcc-114">rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="eedcc-114">revocationMode</span></span>|<span data-ttu-id="eedcc-115">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="eedcc-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="eedcc-116">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="eedcc-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="eedcc-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="eedcc-117">trustedStoreLocation</span></span>|<span data-ttu-id="eedcc-118">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="eedcc-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="eedcc-119">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="eedcc-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="eedcc-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="eedcc-120">certificateValidator</span></span>|<span data-ttu-id="eedcc-121">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="eedcc-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="eedcc-122">Se o `certificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="eedcc-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eedcc-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eedcc-123">Child Elements</span></span>  

 <span data-ttu-id="eedcc-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="eedcc-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eedcc-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eedcc-125">Parent Elements</span></span>  
  
|<span data-ttu-id="eedcc-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="eedcc-126">Element</span></span>|<span data-ttu-id="eedcc-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="eedcc-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="eedcc-128">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="eedcc-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="eedcc-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eedcc-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
