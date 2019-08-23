---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 65488c34931f6d7c424ece58a4855e746ea455bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69936423"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="dcf02-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="dcf02-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="dcf02-102">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="dcf02-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="dcf02-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dcf02-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="dcf02-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="dcf02-104">\<behaviors></span></span>  
<span data-ttu-id="dcf02-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="dcf02-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="dcf02-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dcf02-106">\<behavior></span></span>  
<span data-ttu-id="dcf02-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="dcf02-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf02-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="dcf02-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcf02-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="dcf02-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dcf02-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="dcf02-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcf02-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="dcf02-111">Attributes</span></span>  
  
|<span data-ttu-id="dcf02-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="dcf02-112">Attribute</span></span>|<span data-ttu-id="dcf02-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcf02-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcf02-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="dcf02-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="dcf02-115">Uma cadeia de caracteres que especifica o tipo da política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="dcf02-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcf02-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="dcf02-116">Child Elements</span></span>  
 <span data-ttu-id="dcf02-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="dcf02-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dcf02-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="dcf02-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dcf02-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="dcf02-119">Element</span></span>|<span data-ttu-id="dcf02-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="dcf02-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcf02-121">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="dcf02-121">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="dcf02-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="dcf02-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dcf02-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dcf02-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
