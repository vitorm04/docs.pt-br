---
title: <behaviors> fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: b7c5cf93a82ac88c25f9c478ad52cf41eb6f6d65
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790293"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="2749a-102">\<comportamentos > de fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="2749a-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="2749a-103">Esse elemento contém o **serviceBehaviors** coleção.</span><span class="sxs-lookup"><span data-stu-id="2749a-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="2749a-104">Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2749a-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="2749a-105">Cada elemento de comportamento é identificado por seu exclusivo **nome** atributo.</span><span class="sxs-lookup"><span data-stu-id="2749a-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="2749a-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2749a-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2749a-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2749a-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2749a-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2749a-108">Attributes and Elements</span></span>  
 <span data-ttu-id="2749a-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2749a-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2749a-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="2749a-110">Attributes</span></span>  
 <span data-ttu-id="2749a-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="2749a-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2749a-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2749a-112">Child Elements</span></span>  
  
|<span data-ttu-id="2749a-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="2749a-113">Element</span></span>|<span data-ttu-id="2749a-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2749a-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2749a-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="2749a-115">\<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/servicebehaviors-of-workflow.md)|<span data-ttu-id="2749a-116">Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="2749a-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2749a-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2749a-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2749a-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="2749a-118">Element</span></span>|<span data-ttu-id="2749a-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="2749a-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2749a-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="2749a-120">\<system.serviceModel></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|<span data-ttu-id="2749a-121">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="2749a-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2749a-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2749a-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="2749a-123">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="2749a-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
