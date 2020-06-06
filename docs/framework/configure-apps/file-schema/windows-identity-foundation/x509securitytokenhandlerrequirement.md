---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152444"
---
# \<x509SecurityTokenHandlerRequirement>
<span data-ttu-id="38fcf-101">Fornece a configuração opcional para a <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> classe ou classes derivadas.</span><span class="sxs-lookup"><span data-stu-id="38fcf-101">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509SecurityTokenHandlerRequirement>**  
  
## <a name="syntax"></a><span data-ttu-id="38fcf-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38fcf-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38fcf-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38fcf-103">Attributes and Elements</span></span>  
 <span data-ttu-id="38fcf-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38fcf-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38fcf-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="38fcf-105">Attributes</span></span>  
  
|<span data-ttu-id="38fcf-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="38fcf-106">Attribute</span></span>|<span data-ttu-id="38fcf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="38fcf-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38fcf-108">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="38fcf-108">certificateValidationMode</span></span>|<span data-ttu-id="38fcf-109">Um <xref:System.ServiceModel.Security.X509CertificateValidationMode> valor que especifica o modo de validação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="38fcf-109">An <xref:System.ServiceModel.Security.X509CertificateValidationMode> value that specifies the validation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="38fcf-110">O valor padrão é "PeerOrChainTrust".</span><span class="sxs-lookup"><span data-stu-id="38fcf-110">The default value is "PeerOrChainTrust".</span></span>|  
|<span data-ttu-id="38fcf-111">mapToWindows</span><span class="sxs-lookup"><span data-stu-id="38fcf-111">mapToWindows</span></span>|<span data-ttu-id="38fcf-112">Especifica se o manipulador de token deve mapear o token de validação para uma conta do Windows usando a declaração UPN de entrada.</span><span class="sxs-lookup"><span data-stu-id="38fcf-112">Specifies whether the token handler should map the validating token to a Windows account by using the incoming UPN claim.</span></span> <span data-ttu-id="38fcf-113">O padrão é "falso".</span><span class="sxs-lookup"><span data-stu-id="38fcf-113">The default is "false".</span></span>|  
|<span data-ttu-id="38fcf-114">rerevocationmode</span><span class="sxs-lookup"><span data-stu-id="38fcf-114">revocationMode</span></span>|<span data-ttu-id="38fcf-115">Um <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> valor que especifica o modo de revogação a ser usado para o certificado X. 509.</span><span class="sxs-lookup"><span data-stu-id="38fcf-115">An <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> value that specifies the revocation mode to use for the X.509 certificate.</span></span> <span data-ttu-id="38fcf-116">O valor padrão é "online".</span><span class="sxs-lookup"><span data-stu-id="38fcf-116">The default value is "Online".</span></span>|  
|<span data-ttu-id="38fcf-117">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="38fcf-117">trustedStoreLocation</span></span>|<span data-ttu-id="38fcf-118">Um <xref:System.Security.Cryptography.X509Certificates.StoreLocation> valor que especifica o repositório de certificados X. 509.</span><span class="sxs-lookup"><span data-stu-id="38fcf-118">A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> value that specifies the X.509 certificate store.</span></span> <span data-ttu-id="38fcf-119">O valor padrão é "LocalMachine".</span><span class="sxs-lookup"><span data-stu-id="38fcf-119">The default value is "LocalMachine".</span></span>|  
|<span data-ttu-id="38fcf-120">certificateValidator</span><span class="sxs-lookup"><span data-stu-id="38fcf-120">certificateValidator</span></span>|<span data-ttu-id="38fcf-121">Um tipo personalizado que deriva de <xref:System.IdentityModel.Selectors.X509CertificateValidator> .</span><span class="sxs-lookup"><span data-stu-id="38fcf-121">A custom type that derives from <xref:System.IdentityModel.Selectors.X509CertificateValidator>.</span></span> <span data-ttu-id="38fcf-122">Se o `certificateValidationMode` atributo for "Custom", uma instância desse tipo será usada para validação do certificado do emissor.</span><span class="sxs-lookup"><span data-stu-id="38fcf-122">If the `certificateValidationMode` attribute is "Custom", an instance of this type is used for issuer certificate validation.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38fcf-123">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38fcf-123">Child Elements</span></span>  
 <span data-ttu-id="38fcf-124">Nenhum</span><span class="sxs-lookup"><span data-stu-id="38fcf-124">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38fcf-125">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38fcf-125">Parent Elements</span></span>  
  
|<span data-ttu-id="38fcf-126">Elemento</span><span class="sxs-lookup"><span data-stu-id="38fcf-126">Element</span></span>|<span data-ttu-id="38fcf-127">Descrição</span><span class="sxs-lookup"><span data-stu-id="38fcf-127">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add.md)|<span data-ttu-id="38fcf-128">Adiciona o manipulador de token de segurança especificado à coleção de manipulador de token.</span><span class="sxs-lookup"><span data-stu-id="38fcf-128">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="38fcf-129">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38fcf-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
