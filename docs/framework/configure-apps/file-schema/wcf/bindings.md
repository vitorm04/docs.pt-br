---
title: "&lt;associações&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ed672ee918ad969feb8be6d20c9206e6b5d12278
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindingsgt"></a><span data-ttu-id="c2d89-102">&lt;associações&gt;</span><span class="sxs-lookup"><span data-stu-id="c2d89-102">&lt;bindings&gt;</span></span>
<span data-ttu-id="c2d89-103">Esta seção contém uma coleção de associações padrão e personalizadas.</span><span class="sxs-lookup"><span data-stu-id="c2d89-103">This section holds a collection of standard and custom bindings.</span></span> <span data-ttu-id="c2d89-104">Cada entrada é um `binding` elemento que pode ser identificado pelo seu exclusivo `name`.</span><span class="sxs-lookup"><span data-stu-id="c2d89-104">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="c2d89-105">Serviços usar associações vinculando-as usando o `name`.</span><span class="sxs-lookup"><span data-stu-id="c2d89-105">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="c2d89-106">Começando com [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="c2d89-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="c2d89-107">Para obter mais informações sobre a configuração padrão e associações de nomes e comportamentos, consulte [configuração simplificada](../../../../../docs/framework/wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="c2d89-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="c2d89-108">Associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c2d89-108">System-Provided Binding</span></span>  
 <span data-ttu-id="c2d89-109">Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="c2d89-109">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="c2d89-110">Aplicativos usando associações fornecidas pelo sistema não necessitam de controle total sobre a pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d89-110">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="c2d89-111">Os atributos expostos em cada associação fornecida pelo sistema são as mais apropriada para o cenário de uso, os endereços de associação.</span><span class="sxs-lookup"><span data-stu-id="c2d89-111">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="c2d89-112">A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação.</span><span class="sxs-lookup"><span data-stu-id="c2d89-112">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="c2d89-113">Cada configuração é identificada por um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="c2d89-113">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="c2d89-114">Não é possível adicionar elementos ou atributos em uma associação fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="c2d89-114">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="c2d89-115">Para fazer isso, você deve implementar uma associação personalizada, conforme descrito na seção "Associação personalizada" deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c2d89-115">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="c2d89-116">É possível definir uma associação personalizada que simule um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações de que aplicativo do usuário deseja ter controle sobre.</span><span class="sxs-lookup"><span data-stu-id="c2d89-116">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
 <span data-ttu-id="c2d89-117">Para obter uma lista de associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../../docs/framework/wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c2d89-117">For a list of system-provided bindings, see [System-Provided Bindings](../../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="c2d89-118">Associação personalizado</span><span class="sxs-lookup"><span data-stu-id="c2d89-118">Custom Binding</span></span>  
 <span data-ttu-id="c2d89-119">Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="c2d89-119">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="c2d89-120">Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d89-120">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="c2d89-121">Cada elemento define e configura um elemento da pilha.</span><span class="sxs-lookup"><span data-stu-id="c2d89-121">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="c2d89-122">Deve haver apenas um `transport` elemento em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c2d89-122">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="c2d89-123">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="c2d89-123">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="c2d89-124">A ordem na qual os elementos aparecem na pilha é importante, porque é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="c2d89-124">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="c2d89-125">A ordem exigida de elementos da pilha é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c2d89-125">The required order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="c2d89-126">Transações (opcionais)</span><span class="sxs-lookup"><span data-stu-id="c2d89-126">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="c2d89-127">Confiável de mensagens (opcional)</span><span class="sxs-lookup"><span data-stu-id="c2d89-127">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="c2d89-128">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="c2d89-128">Security (optional)</span></span>  
  
4.  <span data-ttu-id="c2d89-129">Codificador</span><span class="sxs-lookup"><span data-stu-id="c2d89-129">Encoder</span></span>  
  
5.  <span data-ttu-id="c2d89-130">Transporte</span><span class="sxs-lookup"><span data-stu-id="c2d89-130">Transport</span></span>  
  
 <span data-ttu-id="c2d89-131">Associações personalizadas são identificadas por seus `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="c2d89-131">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="c2d89-132">Para obter mais informações sobre associações personalizadas, consulte [associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="c2d89-132">For more information on custom bindings, see [Custom Bindings](../../../../../docs/framework/wcf/extending/custom-bindings.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2d89-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c2d89-133">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <span data-ttu-id="c2d89-134">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="c2d89-134">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="c2d89-135">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c2d89-135">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c2d89-136">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c2d89-136">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [<span data-ttu-id="c2d89-137">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c2d89-137">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
