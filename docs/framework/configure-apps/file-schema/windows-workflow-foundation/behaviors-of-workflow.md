---
title: <behaviors>do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398873"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="7d7f9-102">\<comportamentos > do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="7d7f9-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="7d7f9-103">Esse elemento contém a coleção de **Imcomportamentos** .</span><span class="sxs-lookup"><span data-stu-id="7d7f9-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="7d7f9-104">Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7d7f9-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="7d7f9-105">Cada elemento de comportamento é identificado por seu atributo de **nome** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="7d7f9-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
<span data-ttu-id="7d7f9-106">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="7d7f9-106">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="7d7f9-107">&nbsp;&nbsp;[ **\<sistema. > ServiceModel**](system-servicemodel-of-workflow.md)</span><span class="sxs-lookup"><span data-stu-id="7d7f9-107">&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)</span></span>\
<span data-ttu-id="7d7f9-108">&nbsp;&nbsp;&nbsp;&nbsp; **\<comportamentos >**</span><span class="sxs-lookup"><span data-stu-id="7d7f9-108">&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7f9-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d7f9-109">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d7f9-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="7d7f9-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7d7f9-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="7d7f9-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d7f9-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="7d7f9-112">Attributes</span></span>  
 <span data-ttu-id="7d7f9-113">Nenhum</span><span class="sxs-lookup"><span data-stu-id="7d7f9-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7d7f9-114">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="7d7f9-114">Child Elements</span></span>  
  
|<span data-ttu-id="7d7f9-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="7d7f9-115">Element</span></span>|<span data-ttu-id="7d7f9-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d7f9-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d7f9-117">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="7d7f9-117">\<serviceBehaviors></span></span>](servicebehaviors-of-workflow.md)|<span data-ttu-id="7d7f9-118">Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="7d7f9-118">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d7f9-119">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="7d7f9-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7d7f9-120">Elemento</span><span class="sxs-lookup"><span data-stu-id="7d7f9-120">Element</span></span>|<span data-ttu-id="7d7f9-121">Descrição</span><span class="sxs-lookup"><span data-stu-id="7d7f9-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7d7f9-122">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="7d7f9-122">\<system.serviceModel></span></span>](../wcf/system-servicemodel.md)|<span data-ttu-id="7d7f9-123">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="7d7f9-123">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7d7f9-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d7f9-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="7d7f9-125">Configurando e estendendo o tempo de execução com comportamentos</span><span class="sxs-lookup"><span data-stu-id="7d7f9-125">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
