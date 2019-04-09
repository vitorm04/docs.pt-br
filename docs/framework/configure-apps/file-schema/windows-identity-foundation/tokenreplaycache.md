---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1567c669b5e682a7a771d7bedc95a8effa474e36
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113380"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="37589-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="37589-101">\<tokenReplayCache></span></span>
<span data-ttu-id="37589-102">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="37589-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="37589-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="37589-103">\<system.identityModel></span></span>  
<span data-ttu-id="37589-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="37589-104">\<identityConfiguration></span></span>  
<span data-ttu-id="37589-105">\<caches></span><span class="sxs-lookup"><span data-stu-id="37589-105">\<caches></span></span>  
<span data-ttu-id="37589-106">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="37589-106">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37589-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="37589-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="37589-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="37589-108">Attributes and Elements</span></span>  
 <span data-ttu-id="37589-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="37589-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="37589-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="37589-110">Attributes</span></span>  
  
|<span data-ttu-id="37589-111">Atributo</span><span class="sxs-lookup"><span data-stu-id="37589-111">Attribute</span></span>|<span data-ttu-id="37589-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="37589-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="37589-113">tipo</span><span class="sxs-lookup"><span data-stu-id="37589-113">type</span></span>|<span data-ttu-id="37589-114">Um tipo que deriva de <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="37589-114">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="37589-115">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="37589-115">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="37589-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="37589-116">Child Elements</span></span>  
 <span data-ttu-id="37589-117">Nenhum</span><span class="sxs-lookup"><span data-stu-id="37589-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="37589-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="37589-118">Parent Elements</span></span>  
  
|<span data-ttu-id="37589-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="37589-119">Element</span></span>|<span data-ttu-id="37589-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="37589-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="37589-121">\<caches></span><span class="sxs-lookup"><span data-stu-id="37589-121">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="37589-122">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="37589-122">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37589-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="37589-123">Remarks</span></span>  
 <span data-ttu-id="37589-124">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="37589-124">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="37589-125">Detecção de reprodução de token é habilitada pela [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) elemento, que também especifica a hora de expiração máximo de tokens.</span><span class="sxs-lookup"><span data-stu-id="37589-125">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37589-126">Exemplo</span><span class="sxs-lookup"><span data-stu-id="37589-126">Example</span></span>  
 <span data-ttu-id="37589-127">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="37589-127">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="37589-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37589-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="37589-129">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="37589-129">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
