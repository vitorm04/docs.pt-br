---
title: '&lt;tokenReplayCache&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
caps.latest.revision: "8"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: f388369d4dc2e590473ad98189ade70b77551b10
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaycachegt"></a><span data-ttu-id="38105-102">&lt;tokenReplayCache&gt;</span><span class="sxs-lookup"><span data-stu-id="38105-102">&lt;tokenReplayCache&gt;</span></span>
<span data-ttu-id="38105-103">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="38105-103">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
 <span data-ttu-id="38105-104">\<System. IdentityModel ></span><span class="sxs-lookup"><span data-stu-id="38105-104">\<system.identityModel></span></span>  
<span data-ttu-id="38105-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="38105-105">\<identityConfiguration></span></span>  
<span data-ttu-id="38105-106">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="38105-106">\<caches></span></span>  
<span data-ttu-id="38105-107">\<tokenReplayCache ></span><span class="sxs-lookup"><span data-stu-id="38105-107">\<tokenReplayCache></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38105-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38105-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38105-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="38105-109">Attributes and Elements</span></span>  
 <span data-ttu-id="38105-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="38105-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38105-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="38105-111">Attributes</span></span>  
  
|<span data-ttu-id="38105-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="38105-112">Attribute</span></span>|<span data-ttu-id="38105-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="38105-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38105-114">tipo</span><span class="sxs-lookup"><span data-stu-id="38105-114">type</span></span>|<span data-ttu-id="38105-115">Um tipo que deriva de <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="38105-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="38105-116">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="38105-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="38105-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="38105-117">Child Elements</span></span>  
 <span data-ttu-id="38105-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="38105-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38105-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="38105-119">Parent Elements</span></span>  
  
|<span data-ttu-id="38105-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="38105-120">Element</span></span>|<span data-ttu-id="38105-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="38105-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="38105-122">\<armazena em cache ></span><span class="sxs-lookup"><span data-stu-id="38105-122">\<caches></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|<span data-ttu-id="38105-123">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="38105-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38105-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="38105-124">Remarks</span></span>  
 <span data-ttu-id="38105-125">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="38105-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="38105-126">Detecção de reprodução de token é habilitada pelo [ \<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) elemento, que também especifica o tempo máximo de expiração de tokens.</span><span class="sxs-lookup"><span data-stu-id="38105-126">Token replay detection is enabled by the [\<tokenReplayDetection>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38105-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="38105-127">Example</span></span>  
 <span data-ttu-id="38105-128">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="38105-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="38105-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38105-129">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.TokenReplayCache>  
 [<span data-ttu-id="38105-130">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="38105-130">\<tokenReplayDetection></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)
