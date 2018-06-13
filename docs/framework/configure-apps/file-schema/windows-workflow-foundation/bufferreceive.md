---
title: '&lt;bufferReceive&gt;'
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: b23c3a54-10d4-4f13-ab6d-98b26b76f22a
ms.openlocfilehash: 07d5b66b14d9495808f972734cdce4476efaefde
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32766830"
---
# <a name="ltbufferreceivegt"></a><span data-ttu-id="39e81-102">&lt;bufferReceive&gt;</span><span class="sxs-lookup"><span data-stu-id="39e81-102">&lt;bufferReceive&gt;</span></span>
<span data-ttu-id="39e81-103">Um comportamento de serviço que permite que um serviço a ser usado em buffer recebe o processamento, que permite que um serviço de fluxo de trabalho processar mensagens de fora de ordem.</span><span class="sxs-lookup"><span data-stu-id="39e81-103">A service behavior that enables a service to use buffered receive processing, which enables a workflow service to process out-of-order messages.</span></span>  
  
<span data-ttu-id="39e81-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="39e81-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="39e81-105">\<comportamentos ></span><span class="sxs-lookup"><span data-stu-id="39e81-105">\<behaviors></span></span>  
<span data-ttu-id="39e81-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="39e81-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="39e81-107">\<comportamento ></span><span class="sxs-lookup"><span data-stu-id="39e81-107">\<behavior></span></span>  
<span data-ttu-id="39e81-108">\<bufferReceive ></span><span class="sxs-lookup"><span data-stu-id="39e81-108">\<bufferReceive></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="39e81-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="39e81-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <bufferReceive maxPendingMessagesPerChannel="Integer" />
    </behavior>
  </serviceBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="39e81-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="39e81-110">Attributes and Elements</span></span>  
 <span data-ttu-id="39e81-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="39e81-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="39e81-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="39e81-112">Attributes</span></span>  
  
|<span data-ttu-id="39e81-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="39e81-113">Attribute</span></span>|<span data-ttu-id="39e81-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="39e81-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="39e81-115">maxPendingMessagesPerChannel</span><span class="sxs-lookup"><span data-stu-id="39e81-115">maxPendingMessagesPerChannel</span></span>|<span data-ttu-id="39e81-116">Um inteiro que especifica o número máximo de mensagens permitido para cada canal pendentes.</span><span class="sxs-lookup"><span data-stu-id="39e81-116">An integer that specifies the maximum number of pending messages allowed for each channel.</span></span> <span data-ttu-id="39e81-117">O valor padrão é 512.</span><span class="sxs-lookup"><span data-stu-id="39e81-117">The default value is 512.</span></span> <span data-ttu-id="39e81-118">Essa propriedade limita o número de mensagens de fora de ordem que pode ser recebido por um serviço de fluxo de trabalho.</span><span class="sxs-lookup"><span data-stu-id="39e81-118">This property limits the number of out-of-order messages that can be received by a workflow service.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="39e81-119">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="39e81-119">Child Elements</span></span>  
 <span data-ttu-id="39e81-120">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="39e81-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="39e81-121">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="39e81-121">Parent Elements</span></span>  
  
|<span data-ttu-id="39e81-122">Elemento</span><span class="sxs-lookup"><span data-stu-id="39e81-122">Element</span></span>|<span data-ttu-id="39e81-123">Descrição</span><span class="sxs-lookup"><span data-stu-id="39e81-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="39e81-124">\<comportamento > de \<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="39e81-124">\<behavior> of \<serviceBehaviors></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/behavior-of-servicebehaviors-of-workflow.md)|<span data-ttu-id="39e81-125">Especifica um elemento de comportamento.</span><span class="sxs-lookup"><span data-stu-id="39e81-125">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="39e81-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="39e81-126">See Also</span></span>  
<!-- <xref:System.ServiceModel.Activities.Description.BufferReceiveServiceBehavior>  -->
 <xref:System.ServiceModel.Activities.Configuration.BufferedReceiveElement>
