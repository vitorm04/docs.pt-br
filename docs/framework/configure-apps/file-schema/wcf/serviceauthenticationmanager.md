---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59192037"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="0eacb-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="0eacb-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="0eacb-102">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="0eacb-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="0eacb-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="0eacb-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="0eacb-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="0eacb-104">\<behaviors></span></span>  
<span data-ttu-id="0eacb-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="0eacb-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="0eacb-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="0eacb-106">\<behavior></span></span>  
<span data-ttu-id="0eacb-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="0eacb-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eacb-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0eacb-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0eacb-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0eacb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0eacb-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0eacb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0eacb-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0eacb-111">Attributes</span></span>  
  
|<span data-ttu-id="0eacb-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0eacb-112">Attribute</span></span>|<span data-ttu-id="0eacb-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0eacb-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0eacb-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="0eacb-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="0eacb-115">Uma cadeia de caracteres que especifica o tipo de política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="0eacb-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0eacb-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0eacb-116">Child Elements</span></span>  
 <span data-ttu-id="0eacb-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0eacb-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0eacb-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0eacb-118">Parent Elements</span></span>  
  
|<span data-ttu-id="0eacb-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="0eacb-119">Element</span></span>|<span data-ttu-id="0eacb-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="0eacb-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0eacb-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="0eacb-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="0eacb-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="0eacb-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0eacb-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0eacb-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
