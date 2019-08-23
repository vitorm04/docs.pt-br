---
title: <bufferReceive>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 1d4611d6fee9dad057985f7d8f5ef961d384efcd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69945969"
---
# <a name="bufferreceive"></a><span data-ttu-id="3df93-101">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="3df93-101">\<bufferReceive></span></span>
<span data-ttu-id="3df93-102">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="3df93-102">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="3df93-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="3df93-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="3df93-104">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="3df93-104">\<behaviors></span></span>  
<span data-ttu-id="3df93-105">\<> de portais</span><span class="sxs-lookup"><span data-stu-id="3df93-105">\<serviceBehaviors></span></span>  
<span data-ttu-id="3df93-106">\<> de comportamento</span><span class="sxs-lookup"><span data-stu-id="3df93-106">\<behavior></span></span>  
<span data-ttu-id="3df93-107">\<bufferReceive></span><span class="sxs-lookup"><span data-stu-id="3df93-107">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3df93-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3df93-108">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3df93-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="3df93-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3df93-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="3df93-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3df93-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="3df93-111">Attributes</span></span>  
  
|<span data-ttu-id="3df93-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="3df93-112">Attribute</span></span>|<span data-ttu-id="3df93-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df93-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3df93-114">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="3df93-114">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="3df93-115">Um inteiro que especifica o número máximo de mensagens permitido para cada canal pendentes.</span><span class="sxs-lookup"><span data-stu-id="3df93-115">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="3df93-116">O valor padrão é 512.</span><span class="sxs-lookup"><span data-stu-id="3df93-116">The default value is 512.</span></span> <span data-ttu-id="3df93-117">Essa propriedade limita o número de mensagens de fora de ordem que pode ser recebido por um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="3df93-117">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3df93-118">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="3df93-118">Child Elements</span></span>  
 <span data-ttu-id="3df93-119">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="3df93-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3df93-120">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="3df93-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3df93-121">Elemento</span><span class="sxs-lookup"><span data-stu-id="3df93-121">Element</span></span>|<span data-ttu-id="3df93-122">Descrição</span><span class="sxs-lookup"><span data-stu-id="3df93-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3df93-123">\<comportamento > de \<percomportamentos ></span><span class="sxs-lookup"><span data-stu-id="3df93-123">\<behavior> of \<serviceBehaviors></span></span>](behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="3df93-124">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="3df93-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3df93-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3df93-125">See also</span></span>

- <xref:System.ServiceModel.Activities.Description.BufferedReceiveServiceBehavior>
- <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
