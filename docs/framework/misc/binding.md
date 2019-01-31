---
title: <binding>
ms.date: 03/30/2017
ms.topic: reference
ms.assetid: 666183d6-4d1f-45c7-ac64-bdf93ee8f36f
ms.openlocfilehash: fb51eb1962603439b89a203eb668dfb543049170
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271467"
---
# <a name="binding"></a><span data-ttu-id="1fca0-101">\<binding></span><span class="sxs-lookup"><span data-stu-id="1fca0-101">\<binding></span></span>
<span data-ttu-id="1fca0-102">Você pode usar o `binding` predefinidos de elemento para configurar diferentes tipos de associações fornecidas pelo Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="1fca0-102">You can use the `binding` element to configure different types of predefined bindings provided by Windows Communication Foundation (WCF).</span></span>  
  
## <a name="system-provided-binding"></a><span data-ttu-id="1fca0-103">Associação fornecida pelo sistema</span><span class="sxs-lookup"><span data-stu-id="1fca0-103">System-Provided Binding</span></span>  
 <span data-ttu-id="1fca0-104">Associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="1fca0-104">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="1fca0-105">Aplicativos que usam associações fornecidas pelo sistema não exigem controle total sobre a pilha.</span><span class="sxs-lookup"><span data-stu-id="1fca0-105">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="1fca0-106">Os atributos expostos em cada associação fornecida pelo sistema são aqueles mais apropriada para o cenário de uso, os endereços de associação.</span><span class="sxs-lookup"><span data-stu-id="1fca0-106">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>  
  
 <span data-ttu-id="1fca0-107">A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação.</span><span class="sxs-lookup"><span data-stu-id="1fca0-107">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="1fca0-108">Cada configuração é identificada por um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="1fca0-108">Each configuration is identified by a unique name.</span></span>  
  
 <span data-ttu-id="1fca0-109">Não é possível adicionar elementos ou atributos para uma associação fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="1fca0-109">It is not possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="1fca0-110">Para fazer isso, você deve implementar uma ligação personalizada, conforme descrito na seção "Associação personalizada" deste tópico.</span><span class="sxs-lookup"><span data-stu-id="1fca0-110">To do so, you should implement a custom binding as described in the "Custom Binding" section of this topic.</span></span> <span data-ttu-id="1fca0-111">É possível definir uma ligação personalizada que imita um fornecido pelo sistema de associação perfeitamente e adiciona algumas configurações que o aplicativo de usuário deseja ter controle sobre.</span><span class="sxs-lookup"><span data-stu-id="1fca0-111">It is possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  
  
## <a name="custom-binding"></a><span data-ttu-id="1fca0-112">Associação personalizado</span><span class="sxs-lookup"><span data-stu-id="1fca0-112">Custom Binding</span></span>  
 <span data-ttu-id="1fca0-113">Associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="1fca0-113">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="1fca0-114">Uma associação individual define a pilha de mensagem, especificando os elementos de configuração para os elementos da pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="1fca0-114">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="1fca0-115">Cada elemento define e configura um elemento da pilha.</span><span class="sxs-lookup"><span data-stu-id="1fca0-115">Each element defines and configures the one element of the stack.</span></span> <span data-ttu-id="1fca0-116">Deve haver apenas um `transport` elemento em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1fca0-116">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="1fca0-117">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="1fca0-117">Without this element, the messaging stack is incomplete.</span></span>  
  
 <span data-ttu-id="1fca0-118">A ordem na qual os elementos aparecem na pilha é importante, porque ele é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="1fca0-118">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="1fca0-119">A ordem recomendada de elementos da pilha é o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1fca0-119">The recommended order of stack elements is the following:</span></span>  
  
1.  <span data-ttu-id="1fca0-120">Transações (opcionais)</span><span class="sxs-lookup"><span data-stu-id="1fca0-120">Transactions (optional)</span></span>  
  
2.  <span data-ttu-id="1fca0-121">(Opcional) de mensagens confiáveis</span><span class="sxs-lookup"><span data-stu-id="1fca0-121">Reliable Messaging (optional)</span></span>  
  
3.  <span data-ttu-id="1fca0-122">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="1fca0-122">Security (optional)</span></span>  
  
4.  <span data-ttu-id="1fca0-123">Codificador</span><span class="sxs-lookup"><span data-stu-id="1fca0-123">Encoder</span></span>  
  
5.  <span data-ttu-id="1fca0-124">Transporte</span><span class="sxs-lookup"><span data-stu-id="1fca0-124">Transport</span></span>  
  
 <span data-ttu-id="1fca0-125">Associações personalizadas são identificadas por seus `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="1fca0-125">Custom bindings are identified by their `name` attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fca0-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1fca0-126">See also</span></span>
- <xref:System.ServiceModel.Configuration.BindingsSection>
- <xref:System.ServiceModel.Channels.Binding>
- <xref:System.ServiceModel.Channels.BindingElement>
- [<span data-ttu-id="1fca0-127">Associações</span><span class="sxs-lookup"><span data-stu-id="1fca0-127">Bindings</span></span>](../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="1fca0-128">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1fca0-128">Custom Bindings</span></span>](../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="1fca0-129">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="1fca0-129">\<customBinding></span></span>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
