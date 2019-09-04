---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251778"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="eef53-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="eef53-101">\<tokenReplayCache></span></span>
<span data-ttu-id="eef53-102">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="eef53-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="eef53-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="eef53-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="eef53-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="eef53-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="eef53-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="eef53-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="eef53-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<caches >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="eef53-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="eef53-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> tokenReplayCache**</span><span class="sxs-lookup"><span data-stu-id="eef53-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eef53-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="eef53-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eef53-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="eef53-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eef53-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="eef53-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eef53-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="eef53-111">Attributes</span></span>  
  
|<span data-ttu-id="eef53-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="eef53-112">Attribute</span></span>|<span data-ttu-id="eef53-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="eef53-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="eef53-114">tipo</span><span class="sxs-lookup"><span data-stu-id="eef53-114">type</span></span>|<span data-ttu-id="eef53-115">Um tipo que deriva da <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="eef53-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="eef53-116">Para obter mais informações sobre como especificar um personalizado `type`, consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="eef53-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="eef53-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="eef53-117">Child Elements</span></span>  
 <span data-ttu-id="eef53-118">Nenhum</span><span class="sxs-lookup"><span data-stu-id="eef53-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eef53-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="eef53-119">Parent Elements</span></span>  
  
|<span data-ttu-id="eef53-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="eef53-120">Element</span></span>|<span data-ttu-id="eef53-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="eef53-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="eef53-122">\<caches></span><span class="sxs-lookup"><span data-stu-id="eef53-122">\<caches></span></span>](caches.md)|<span data-ttu-id="eef53-123">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="eef53-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eef53-124">Comentários</span><span class="sxs-lookup"><span data-stu-id="eef53-124">Remarks</span></span>  
 <span data-ttu-id="eef53-125">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="eef53-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="eef53-126">A detecção de reprodução de token é habilitada pelo elemento de [ \<> tokenReplayDetection](tokenreplaydetection.md) , que também especifica o tempo de expiração máximo para tokens.</span><span class="sxs-lookup"><span data-stu-id="eef53-126">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="eef53-127">Exemplo</span><span class="sxs-lookup"><span data-stu-id="eef53-127">Example</span></span>  
 <span data-ttu-id="eef53-128">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="eef53-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="eef53-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="eef53-129">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="eef53-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="eef53-130">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
