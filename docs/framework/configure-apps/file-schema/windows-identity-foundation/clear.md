---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252039"
---
# <a name="clear"></a><span data-ttu-id="00534-101">\<clear></span><span class="sxs-lookup"><span data-stu-id="00534-101">\<clear></span></span>
<span data-ttu-id="00534-102">Limpa todos os manipuladores de token de segurança da coleção de manipuladores de tokens atual.</span><span class="sxs-lookup"><span data-stu-id="00534-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
<span data-ttu-id="00534-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="00534-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="00534-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="00534-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="00534-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> identityConfiguration**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="00534-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="00534-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> securityTokenHandlers**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="00534-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="00534-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<limpar >**</span><span class="sxs-lookup"><span data-stu-id="00534-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00534-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="00534-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="00534-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="00534-109">Attributes and Elements</span></span>  
 <span data-ttu-id="00534-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="00534-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="00534-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="00534-111">Attributes</span></span>  
 <span data-ttu-id="00534-112">Nenhum</span><span class="sxs-lookup"><span data-stu-id="00534-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="00534-113">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="00534-113">Child Elements</span></span>  
 <span data-ttu-id="00534-114">Nenhum</span><span class="sxs-lookup"><span data-stu-id="00534-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="00534-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="00534-115">Parent Elements</span></span>  
  
|<span data-ttu-id="00534-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="00534-116">Element</span></span>|<span data-ttu-id="00534-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="00534-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="00534-118">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="00534-118">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="00534-119">Especifica uma coleção de manipuladores de token de segurança que são registrados com o ponto de extremidade.</span><span class="sxs-lookup"><span data-stu-id="00534-119">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
