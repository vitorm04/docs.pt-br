---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 3b58214a1fd7a50fb1a9ab3dfee0a14870f8a476
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32748962"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="ce992-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="ce992-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="ce992-103">Fornece um elemento de configuração de fluxo de trabalho que estabelece o nível de serviço a validade de uma transmissão, a mensagem ou o originador.</span><span class="sxs-lookup"><span data-stu-id="ce992-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator..</span></span>  
  
<span data-ttu-id="ce992-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ce992-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="ce992-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="ce992-105">\<behaviors></span></span>  
<span data-ttu-id="ce992-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ce992-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="ce992-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ce992-107">\<behavior></span></span>  
<span data-ttu-id="ce992-108">\<serviceAuthenticationManager ></span><span class="sxs-lookup"><span data-stu-id="ce992-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce992-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="ce992-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ce992-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="ce992-110">Attributes and Elements</span></span>  
 <span data-ttu-id="ce992-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="ce992-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ce992-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="ce992-112">Attributes</span></span>  
  
|<span data-ttu-id="ce992-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="ce992-113">Attribute</span></span>|<span data-ttu-id="ce992-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce992-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ce992-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="ce992-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="ce992-116">Uma cadeia de caracteres que especifica o tipo de política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="ce992-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ce992-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="ce992-117">Child Elements</span></span>  
 <span data-ttu-id="ce992-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="ce992-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ce992-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="ce992-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ce992-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="ce992-120">Element</span></span>|<span data-ttu-id="ce992-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="ce992-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ce992-122">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="ce992-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="ce992-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="ce992-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ce992-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ce992-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
