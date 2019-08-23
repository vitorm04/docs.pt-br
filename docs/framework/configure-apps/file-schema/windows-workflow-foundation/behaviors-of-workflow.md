---
title: <behaviors>do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 7dd3b0b20c9d7accd80a85b3693e67ffc9b729e5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946003"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="96cf6-102">\<comportamentos > do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="96cf6-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="96cf6-103">Esse elemento contém a coleção de imcomportamentos.</span><span class="sxs-lookup"><span data-stu-id="96cf6-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="96cf6-104">Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="96cf6-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="96cf6-105">Cada elemento de comportamento é identificado por seu atributo de **nome** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="96cf6-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
 <span data-ttu-id="96cf6-106">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="96cf6-106">\<system.ServiceModel></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96cf6-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96cf6-107">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="96cf6-108">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="96cf6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="96cf6-109">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="96cf6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="96cf6-110">Atributos</span><span class="sxs-lookup"><span data-stu-id="96cf6-110">Attributes</span></span>  
 <span data-ttu-id="96cf6-111">Nenhum</span><span class="sxs-lookup"><span data-stu-id="96cf6-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="96cf6-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="96cf6-112">Child Elements</span></span>  
  
|<span data-ttu-id="96cf6-113">Elemento</span><span class="sxs-lookup"><span data-stu-id="96cf6-113">Element</span></span>|<span data-ttu-id="96cf6-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="96cf6-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96cf6-115">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="96cf6-115">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="96cf6-116">Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="96cf6-116">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="96cf6-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="96cf6-117">Parent Elements</span></span>  
  
|<span data-ttu-id="96cf6-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="96cf6-118">Element</span></span>|<span data-ttu-id="96cf6-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="96cf6-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="96cf6-120">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="96cf6-120">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="96cf6-121">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="96cf6-121">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="96cf6-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96cf6-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="96cf6-123">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="96cf6-123">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
