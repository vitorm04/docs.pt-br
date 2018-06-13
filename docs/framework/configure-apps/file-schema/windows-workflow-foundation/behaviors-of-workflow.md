---
title: '&lt;comportamentos&gt; de fluxo de trabalho'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 762fd1ff0de7980848ac3921706f406932c7f35d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32767304"
---
# <a name="ltbehaviorsgt-of-workflow"></a><span data-ttu-id="c56cf-102">&lt;comportamentos&gt; de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="c56cf-102">&lt;behaviors&gt; of workflow</span></span>
<span data-ttu-id="c56cf-103">Esse elemento contém o **serviceBehaviors** coleção.</span><span class="sxs-lookup"><span data-stu-id="c56cf-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="c56cf-104">Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c56cf-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="c56cf-105">Cada elemento de comportamento é identificado por seu exclusivo **nome** atributo.</span><span class="sxs-lookup"><span data-stu-id="c56cf-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="c56cf-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c56cf-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c56cf-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c56cf-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c56cf-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c56cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c56cf-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c56cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c56cf-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="c56cf-110">Attributes</span></span>  
 <span data-ttu-id="c56cf-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="c56cf-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c56cf-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c56cf-112">Child Elements</span></span>  
  
|<span data-ttu-id="c56cf-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="c56cf-113">Element</span></span>|<span data-ttu-id="c56cf-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c56cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c56cf-115">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="c56cf-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="c56cf-116">Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="c56cf-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c56cf-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c56cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c56cf-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="c56cf-118">Element</span></span>|<span data-ttu-id="c56cf-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="c56cf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c56cf-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="c56cf-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="c56cf-121">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="c56cf-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c56cf-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c56cf-122">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>  
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>  
 [<span data-ttu-id="c56cf-123">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="c56cf-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
