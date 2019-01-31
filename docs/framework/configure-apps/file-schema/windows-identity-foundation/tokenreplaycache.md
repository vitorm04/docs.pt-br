---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: dfa6c0d84582d55595f00f149adfdcaa9d554d6b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271940"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="9bd86-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="9bd86-101">\<tokenReplayCache></span></span>
<span data-ttu-id="9bd86-102">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9bd86-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="9bd86-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9bd86-103">\<system.identityModel></span></span>  
<span data-ttu-id="9bd86-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9bd86-104">\<identityConfiguration></span></span>  
<span data-ttu-id="9bd86-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="9bd86-105">\<caches></span></span>  
<span data-ttu-id="9bd86-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="9bd86-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9bd86-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9bd86-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9bd86-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="9bd86-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9bd86-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="9bd86-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9bd86-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="9bd86-110">Attributes</span></span>  
  
|<span data-ttu-id="9bd86-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="9bd86-111">Attribute</span></span>|<span data-ttu-id="9bd86-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bd86-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9bd86-113">tipo</span><span class="sxs-lookup"><span data-stu-id="9bd86-113">type</span></span>|<span data-ttu-id="9bd86-114">Um tipo que deriva de <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="9bd86-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="9bd86-115">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="9bd86-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="9bd86-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="9bd86-116">Child Elements</span></span>  
 <span data-ttu-id="9bd86-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="9bd86-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9bd86-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="9bd86-118">Parent Elements</span></span>  
  
|<span data-ttu-id="9bd86-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="9bd86-119">Element</span></span>|<span data-ttu-id="9bd86-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="9bd86-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9bd86-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="9bd86-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="9bd86-122">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="9bd86-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bd86-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd86-123">Remarks</span></span>  
 <span data-ttu-id="9bd86-124">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="9bd86-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="9bd86-125">Detecção de reprodução de token é habilitada pela [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) elemento, que também especifica a hora de expiração máximo de tokens.</span><span class="sxs-lookup"><span data-stu-id="9bd86-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9bd86-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd86-126">Example</span></span>  
 <span data-ttu-id="9bd86-127">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="9bd86-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9bd86-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd86-128">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="9bd86-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="9bd86-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
