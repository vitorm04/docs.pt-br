---
title: '&lt;tokenReplayCache&gt;'
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 1e89afc5764dbdb86e87d2307425299dff57c686
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54525139"
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="13407-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="13407-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="13407-103">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="13407-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="13407-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="13407-104">\<system.identityModel></span></span>  
<span data-ttu-id="13407-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="13407-105">\<identityConfiguration></span></span>  
<span data-ttu-id="13407-106">\<caches></span><span class="sxs-lookup"><span data-stu-id="13407-106">\<caches></span></span>  
<span data-ttu-id="13407-107">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="13407-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13407-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13407-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13407-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="13407-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13407-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="13407-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13407-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="13407-111">Attributes</span></span>  
  
|<span data-ttu-id="13407-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="13407-112">Attribute</span></span>|<span data-ttu-id="13407-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="13407-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="13407-114">tipo</span><span class="sxs-lookup"><span data-stu-id="13407-114">type</span></span>|<span data-ttu-id="13407-115">Um tipo que deriva de <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="13407-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="13407-116">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="13407-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="13407-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="13407-117">Child Elements</span></span>  
 <span data-ttu-id="13407-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="13407-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13407-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="13407-119">Parent Elements</span></span>  
  
|<span data-ttu-id="13407-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="13407-120">Element</span></span>|<span data-ttu-id="13407-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="13407-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13407-122">\<caches></span><span class="sxs-lookup"><span data-stu-id="13407-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="13407-123">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="13407-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="13407-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="13407-124">Remarks</span></span>  
 <span data-ttu-id="13407-125">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="13407-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="13407-126">Detecção de reprodução de token é habilitada pela [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) elemento, que também especifica a hora de expiração máximo de tokens.</span><span class="sxs-lookup"><span data-stu-id="13407-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13407-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="13407-127">Example</span></span>  
 <span data-ttu-id="13407-128">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="13407-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13407-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13407-129">See also</span></span>
- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="13407-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="13407-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
