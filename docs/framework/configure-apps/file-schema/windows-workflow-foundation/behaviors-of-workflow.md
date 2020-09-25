---
title: <behaviors> do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 21974f77526f55a47c014a285efd3bbac6fc1f7b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189598"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="41e04-102">\<behaviors> do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="41e04-102">\<behaviors> of workflow</span></span>

<span data-ttu-id="41e04-103">Esse elemento contém a coleção de **Imcomportamentos** .</span><span class="sxs-lookup"><span data-stu-id="41e04-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="41e04-104">Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="41e04-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="41e04-105">Cada elemento de comportamento é identificado por seu atributo de **nome** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="41e04-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="41e04-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="41e04-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41e04-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="41e04-107">Attributes and Elements</span></span>  

 <span data-ttu-id="41e04-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="41e04-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41e04-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="41e04-109">Attributes</span></span>  

 <span data-ttu-id="41e04-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="41e04-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41e04-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="41e04-111">Child Elements</span></span>  
  
|<span data-ttu-id="41e04-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="41e04-112">Element</span></span>|<span data-ttu-id="41e04-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="41e04-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="41e04-114">Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="41e04-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="41e04-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="41e04-115">Parent Elements</span></span>  
  
|<span data-ttu-id="41e04-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="41e04-116">Element</span></span>|<span data-ttu-id="41e04-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="41e04-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="41e04-118">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="41e04-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="41e04-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="41e04-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="41e04-120">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="41e04-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
