---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 16d4546bce461b55695e0deed093396ce1c2b0b6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189559"
---
# \<bufferReceive>

<span data-ttu-id="effd2-101">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="effd2-101">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.ServiceModel>**](system-servicemodel-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors-of-workflow.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<bufferReceive>**  
  
## <a name="syntax"></a><span data-ttu-id="effd2-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="effd2-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="effd2-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="effd2-103">Attributes and Elements</span></span>  

 <span data-ttu-id="effd2-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="effd2-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="effd2-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="effd2-105">Attributes</span></span>  
  
|<span data-ttu-id="effd2-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="effd2-106">Attribute</span></span>|<span data-ttu-id="effd2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="effd2-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="effd2-108">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="effd2-108">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="effd2-109">Um inteiro que especifica o número máximo de mensagens permitido para cada canal pendentes.</span><span class="sxs-lookup"><span data-stu-id="effd2-109">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="effd2-110">O valor padrão é 512.</span><span class="sxs-lookup"><span data-stu-id="effd2-110">The default value is 512.</span></span> <span data-ttu-id="effd2-111">Essa propriedade limita o número de mensagens de fora de ordem que pode ser recebido por um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="effd2-111">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="effd2-112">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="effd2-112">Child Elements</span></span>  

 <span data-ttu-id="effd2-113">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="effd2-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="effd2-114">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="effd2-114">Parent Elements</span></span>  
  
|<span data-ttu-id="effd2-115">Elemento</span><span class="sxs-lookup"><span data-stu-id="effd2-115">Element</span></span>|<span data-ttu-id="effd2-116">Descrição</span><span class="sxs-lookup"><span data-stu-id="effd2-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="effd2-117">\<behavior> desse \<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="effd2-117">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="effd2-118">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="effd2-118">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="effd2-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="effd2-119">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
