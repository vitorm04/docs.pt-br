---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: d21a819f789b5be4bdf7ebf57b37a072e1d213ff
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206210"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="ea243-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="ea243-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="ea243-103">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ea243-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="ea243-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ea243-104">\<system.identityModel></span></span>  
<span data-ttu-id="ea243-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ea243-105">\<identityConfiguration></span></span>  
<span data-ttu-id="ea243-106">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="ea243-106">\<caches></span></span>  
<span data-ttu-id="ea243-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="ea243-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea243-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ea243-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea243-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ea243-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ea243-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ea243-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea243-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="ea243-111">Attributes</span></span>  
  
|<span data-ttu-id="ea243-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="ea243-112">Attribute</span></span>|<span data-ttu-id="ea243-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea243-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ea243-114">tipo</span><span class="sxs-lookup"><span data-stu-id="ea243-114">type</span></span>|<span data-ttu-id="ea243-115">Um tipo que deriva de <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="ea243-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="ea243-116">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="ea243-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="ea243-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ea243-117">Child Elements</span></span>  
 <span data-ttu-id="ea243-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="ea243-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ea243-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ea243-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ea243-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ea243-120">Element</span></span>|<span data-ttu-id="ea243-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ea243-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea243-122">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="ea243-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="ea243-123">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="ea243-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea243-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="ea243-124">Remarks</span></span>  
 <span data-ttu-id="ea243-125">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="ea243-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="ea243-126">Detecção de reprodução de token é habilitada pela [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) elemento, que também especifica a hora de expiração máximo de tokens.</span><span class="sxs-lookup"><span data-stu-id="ea243-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea243-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ea243-127">Example</span></span>  
 <span data-ttu-id="ea243-128">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="ea243-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ea243-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ea243-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="ea243-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="ea243-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
