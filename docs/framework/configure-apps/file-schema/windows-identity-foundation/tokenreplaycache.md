---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 5e695bb56b59da40ce9e83f9f4f77d0d22d0b40f
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91202416"
---
# \<tokenReplayCache>

<span data-ttu-id="5ec4d-101">Registra um cache de reprodução de token com um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="5ec4d-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5ec4d-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ec4d-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="5ec4d-103">Attributes and Elements</span></span>  

 <span data-ttu-id="5ec4d-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ec4d-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="5ec4d-105">Attributes</span></span>  
  
|<span data-ttu-id="5ec4d-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="5ec4d-106">Attribute</span></span>|<span data-ttu-id="5ec4d-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ec4d-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5ec4d-108">type</span><span class="sxs-lookup"><span data-stu-id="5ec4d-108">type</span></span>|<span data-ttu-id="5ec4d-109">Um tipo que deriva da <xref:System.IdentityModel.Tokens.TokenReplayCache> classe.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="5ec4d-110">Para obter mais informações sobre como especificar um personalizado `type` , consulte [referências de tipo personalizado].</span><span class="sxs-lookup"><span data-stu-id="5ec4d-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="5ec4d-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="5ec4d-111">Child Elements</span></span>  

 <span data-ttu-id="5ec4d-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="5ec4d-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ec4d-113">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="5ec4d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="5ec4d-114">Elemento</span><span class="sxs-lookup"><span data-stu-id="5ec4d-114">Element</span></span>|<span data-ttu-id="5ec4d-115">Descrição</span><span class="sxs-lookup"><span data-stu-id="5ec4d-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="5ec4d-116">Registra os caches usados por um serviço ou uma coleção de manipulador de token de segurança.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ec4d-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="5ec4d-117">Remarks</span></span>  

 <span data-ttu-id="5ec4d-118">O cache de reprodução de token é usado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="5ec4d-119">A detecção de reprodução de token é habilitada pelo [\<tokenReplayDetection>](tokenreplaydetection.md) elemento, que também especifica o tempo de expiração máximo para tokens.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ec4d-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5ec4d-120">Example</span></span>  

 <span data-ttu-id="5ec4d-121">O XML a seguir mostra a configuração de um cache personalizado para detectar tokens reproduzidos.</span><span class="sxs-lookup"><span data-stu-id="5ec4d-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5ec4d-122">Confira também</span><span class="sxs-lookup"><span data-stu-id="5ec4d-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
