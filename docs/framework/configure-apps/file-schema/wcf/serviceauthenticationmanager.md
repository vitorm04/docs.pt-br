---
title: '&lt;serviceAuthenticationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: fd04b10c0ac0bef4087daa1012a1b8bd3a5880e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54493632"
---
# <a name="ltserviceauthenticationmanagergt"></a><span data-ttu-id="e6b14-102">&lt;serviceAuthenticationManager&gt;</span><span class="sxs-lookup"><span data-stu-id="e6b14-102">&lt;serviceAuthenticationManager&gt;</span></span>
<span data-ttu-id="e6b14-103">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="e6b14-103">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="e6b14-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6b14-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6b14-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="e6b14-105">\<behaviors></span></span>  
<span data-ttu-id="e6b14-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="e6b14-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="e6b14-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e6b14-107">\<behavior></span></span>  
<span data-ttu-id="e6b14-108">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="e6b14-108">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6b14-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6b14-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6b14-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="e6b14-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e6b14-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="e6b14-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6b14-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="e6b14-112">Attributes</span></span>  
  
|<span data-ttu-id="e6b14-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="e6b14-113">Attribute</span></span>|<span data-ttu-id="e6b14-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6b14-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6b14-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="e6b14-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="e6b14-116">Uma cadeia de caracteres que especifica o tipo de política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="e6b14-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6b14-117">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="e6b14-117">Child Elements</span></span>  
 <span data-ttu-id="e6b14-118">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="e6b14-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6b14-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="e6b14-119">Parent Elements</span></span>  
  
|<span data-ttu-id="e6b14-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="e6b14-120">Element</span></span>|<span data-ttu-id="e6b14-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6b14-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6b14-122">\<behavior></span><span class="sxs-lookup"><span data-stu-id="e6b14-122">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="e6b14-123">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="e6b14-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6b14-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6b14-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
