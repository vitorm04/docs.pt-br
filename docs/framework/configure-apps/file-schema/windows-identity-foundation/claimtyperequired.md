---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: a86265ba3963ebc8bea880befbcf80345529116d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91203846"
---
# \<claimTypeRequired>

<span data-ttu-id="06ccb-101">Especifica o conjunto de declarações necessárias para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="06ccb-101">Specifies the set of required claims for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**  
  
## <a name="syntax"></a><span data-ttu-id="06ccb-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="06ccb-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="06ccb-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="06ccb-103">Attributes and Elements</span></span>  

 <span data-ttu-id="06ccb-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="06ccb-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="06ccb-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="06ccb-105">Attributes</span></span>  

 <span data-ttu-id="06ccb-106">Nenhum</span><span class="sxs-lookup"><span data-stu-id="06ccb-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="06ccb-107">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="06ccb-107">Child Elements</span></span>  
  
|<span data-ttu-id="06ccb-108">Elemento</span><span class="sxs-lookup"><span data-stu-id="06ccb-108">Element</span></span>|<span data-ttu-id="06ccb-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="06ccb-109">Description</span></span>|  
|-------------|-----------------|  
|[\<claimType>](claimtype.md)|<span data-ttu-id="06ccb-110">Especifica uma única declaração opcional ou necessária para tokens de segurança de entrada.</span><span class="sxs-lookup"><span data-stu-id="06ccb-110">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="06ccb-111">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="06ccb-111">Parent Elements</span></span>  
  
|<span data-ttu-id="06ccb-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="06ccb-112">Element</span></span>|<span data-ttu-id="06ccb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="06ccb-113">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="06ccb-114">Especifica as configurações de identidade de nível de serviço.</span><span class="sxs-lookup"><span data-stu-id="06ccb-114">Specifies service-level identity settings.</span></span>|
