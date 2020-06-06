---
title: <behaviors>do fluxo de trabalho
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 3c6017b6-0c4f-4192-bd67-9515f5d1ec82
ms.openlocfilehash: 05a15cdf5c043eb5d94b36028324310d2b7a8413
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398873"
---
# <a name="behaviors-of-workflow"></a><span data-ttu-id="697d2-102">\<behaviors>do fluxo de trabalho</span><span class="sxs-lookup"><span data-stu-id="697d2-102">\<behaviors> of workflow</span></span>
<span data-ttu-id="697d2-103">Esse elemento contém a coleção de **Imcomportamentos** .</span><span class="sxs-lookup"><span data-stu-id="697d2-103">This element contains the **serviceBehaviors** collection.</span></span>  <span data-ttu-id="697d2-104">Cada elemento na coleção define elementos de comportamento consumidos pelos serviços de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="697d2-104">Each element in the collection defines behavior elements consumed by workflow services.</span></span> <span data-ttu-id="697d2-105">Cada elemento de comportamento é identificado por seu atributo de **nome** exclusivo.</span><span class="sxs-lookup"><span data-stu-id="697d2-105">Each behavior element is identified by its unique **name** attribute.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<behaviors>**  
  
## <a name="syntax"></a><span data-ttu-id="697d2-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="697d2-106">Syntax</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
  </serviceBehaviors>  
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="697d2-107">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="697d2-107">Attributes and Elements</span></span>  
 <span data-ttu-id="697d2-108">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="697d2-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="697d2-109">Atributos</span><span class="sxs-lookup"><span data-stu-id="697d2-109">Attributes</span></span>  
 <span data-ttu-id="697d2-110">Nenhum</span><span class="sxs-lookup"><span data-stu-id="697d2-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="697d2-111">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="697d2-111">Child Elements</span></span>  
  
|<span data-ttu-id="697d2-112">Elemento</span><span class="sxs-lookup"><span data-stu-id="697d2-112">Element</span></span>|<span data-ttu-id="697d2-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="697d2-113">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceBehaviors>](servicebehaviors-of-workflow.md)|<span data-ttu-id="697d2-114">Esta seção de configuração representa todos os comportamentos definidos para um serviço de fluxo de trabalho específico.</span><span class="sxs-lookup"><span data-stu-id="697d2-114">This configuration section represents all the behaviors defined for a specific workflow service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="697d2-115">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="697d2-115">Parent Elements</span></span>  
  
|<span data-ttu-id="697d2-116">Elemento</span><span class="sxs-lookup"><span data-stu-id="697d2-116">Element</span></span>|<span data-ttu-id="697d2-117">Descrição</span><span class="sxs-lookup"><span data-stu-id="697d2-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel>](../wcf/system-servicemodel.md)|<span data-ttu-id="697d2-118">O elemento raiz de todos os elementos de configuração do fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="697d2-118">The root element of all workflow configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="697d2-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="697d2-119">See also</span></span>

- <xref:System.ServiceModel.Configuration.BehaviorsSection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>
- <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>
- [<span data-ttu-id="697d2-120">Configurando e estendendo o runtime com comportamentos</span><span class="sxs-lookup"><span data-stu-id="697d2-120">Configuring and Extending the Runtime with Behaviors</span></span>](../../../wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)
