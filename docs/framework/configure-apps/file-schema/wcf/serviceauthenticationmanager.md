---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: 7708dd8a572dd24c2852410b1781fce2807efab9
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55263479"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="2289b-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="2289b-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="2289b-102">Fornece um elemento de configuração de fluxo de trabalho que estabelece, no nível de serviço, a validade de uma transmissão, mensagem ou originador.</span><span class="sxs-lookup"><span data-stu-id="2289b-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="2289b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2289b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2289b-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="2289b-104">\<behaviors></span></span>  
<span data-ttu-id="2289b-105">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2289b-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="2289b-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2289b-106">\<behavior></span></span>  
<span data-ttu-id="2289b-107">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="2289b-107">\<serviceAuthenticationManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2289b-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2289b-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2289b-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2289b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2289b-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2289b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2289b-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="2289b-111">Attributes</span></span>  
  
|<span data-ttu-id="2289b-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="2289b-112">Attribute</span></span>|<span data-ttu-id="2289b-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="2289b-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2289b-114">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="2289b-114">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="2289b-115">Uma cadeia de caracteres que especifica o tipo de política de autenticação para o comportamento atual.</span><span class="sxs-lookup"><span data-stu-id="2289b-115">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2289b-116">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2289b-116">Child Elements</span></span>  
 <span data-ttu-id="2289b-117">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2289b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2289b-118">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2289b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2289b-119">Elemento</span><span class="sxs-lookup"><span data-stu-id="2289b-119">Element</span></span>|<span data-ttu-id="2289b-120">Descrição</span><span class="sxs-lookup"><span data-stu-id="2289b-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2289b-121">\<behavior></span><span class="sxs-lookup"><span data-stu-id="2289b-121">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="2289b-122">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="2289b-122">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2289b-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2289b-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
