---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 0940248364488bb38a329c5e461d72463c574e74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670372"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="68361-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="68361-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="68361-102">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="68361-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="68361-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="68361-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="68361-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="68361-104">\<behaviors></span></span>  
<span data-ttu-id="68361-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="68361-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="68361-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="68361-106">\<behavior></span></span>  
<span data-ttu-id="68361-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="68361-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68361-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68361-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68361-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="68361-109">Attributes and Elements</span></span>  
 <span data-ttu-id="68361-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="68361-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68361-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="68361-111">Attributes</span></span>  
  
|<span data-ttu-id="68361-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="68361-112">Attribute</span></span>|<span data-ttu-id="68361-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="68361-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68361-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="68361-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="68361-115">Uma cadeia de caracteres que especifica o tipo de política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="68361-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68361-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="68361-116">Child Elements</span></span>  
 <span data-ttu-id="68361-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="68361-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68361-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="68361-118">Parent Elements</span></span>  
  
|<span data-ttu-id="68361-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="68361-119">Element</span></span>|<span data-ttu-id="68361-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="68361-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68361-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="68361-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="68361-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="68361-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="68361-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="68361-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
