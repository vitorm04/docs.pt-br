---
title: "&lt;associação&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 874a3766a64a9abb7c35efd5ac0a0f698707281e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltbindinggt"></a><span data-ttu-id="c1df7-102">&lt;associação&gt;</span><span class="sxs-lookup"><span data-stu-id="c1df7-102">&lt;binding&gt;</span></span>
<span data-ttu-id="c1df7-103">Você pode usar o `binding` predefinidos de elemento para configurar diferentes tipos de associações fornecidas pelo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="c1df7-103">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="c1df7-104">Associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="c1df7-104">System-Provided Binding</span></span>  
 <span data-ttu-id="c1df7-105">Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="c1df7-105">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="c1df7-106">Aplicativos usando associações fornecidas pelo sistema não necessitam de controle total sobre a pilha.</span><span class="sxs-lookup"><span data-stu-id="c1df7-106">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="c1df7-107">Os atributos expostos em cada associação fornecida pelo sistema são as mais apropriada para o cenário de uso, os endereços de associação.</span><span class="sxs-lookup"><span data-stu-id="c1df7-107">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="c1df7-108">A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação.</span><span class="sxs-lookup"><span data-stu-id="c1df7-108">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="c1df7-109">Cada configuração é identificada por um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="c1df7-109">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="c1df7-110">Não é possível adicionar elementos ou atributos em uma associação fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="c1df7-110">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="c1df7-111">Para fazer isso, você deve implementar uma associação personalizada, conforme descrito na seção "Associação personalizada" deste tópico.</span><span class="sxs-lookup"><span data-stu-id="c1df7-111">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="c1df7-112">É possível definir uma associação personalizada que simule um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações de que aplicativo do usuário deseja ter controle sobre.</span><span class="sxs-lookup"><span data-stu-id="c1df7-112">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="c1df7-113">Associação personalizado</span><span class="sxs-lookup"><span data-stu-id="c1df7-113">Custom Binding</span></span>  
 <span data-ttu-id="c1df7-114">Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="c1df7-114">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="c1df7-115">Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="c1df7-115">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="c1df7-116">Cada elemento define e configura um elemento da pilha.</span><span class="sxs-lookup"><span data-stu-id="c1df7-116">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="c1df7-117">Deve haver apenas um `transport` elemento em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c1df7-117">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="c1df7-118">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="c1df7-118">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="c1df7-119">A ordem na qual os elementos aparecem na pilha é importante, porque é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="c1df7-119">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="c1df7-120">A ordem recomendada de elementos da pilha é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c1df7-120">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="c1df7-121">Transações (opcionais)</span><span class="sxs-lookup"><span data-stu-id="c1df7-121">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="c1df7-122">Confiável de mensagens (opcional)</span><span class="sxs-lookup"><span data-stu-id="c1df7-122">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="c1df7-123">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="c1df7-123">Security (optional)</span></span>  
  
4.  <span data-ttu-id="c1df7-124">Codificador</span><span class="sxs-lookup"><span data-stu-id="c1df7-124">Encoder</span></span>  
  
5.  <span data-ttu-id="c1df7-125">Transporte</span><span class="sxs-lookup"><span data-stu-id="c1df7-125">Transport</span></span>  
  
 <span data-ttu-id="c1df7-126">Associações personalizadas são identificadas por seus `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="c1df7-126">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1df7-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c1df7-127">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.BindingsSection>  
 <xref:System.ServiceModel.Channels.Binding>  
 <xref:System.ServiceModel.Channels.BindingElement>  
 <span data-ttu-id="c1df7-128">[Bindings](../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="c1df7-128">[Bindings](../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="c1df7-129">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c1df7-129">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c1df7-130">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c1df7-130">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
