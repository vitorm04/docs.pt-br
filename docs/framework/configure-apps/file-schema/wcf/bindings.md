---
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: fe8f620668e35183890b8bba1f254a74c962f8d3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139667"
---
# \<bindings>

<span data-ttu-id="bc45e-101">Você pode usar o `bindings` elemento para configurar uma coleção de associações padrão e personalizadas para Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="bc45e-101">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="bc45e-102">Cada entrada é um `binding` elemento que pode ser identificado por seu exclusivo `name` .</span><span class="sxs-lookup"><span data-stu-id="bc45e-102">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="bc45e-103">Os serviços usam associações vinculando-os usando o `name` .</span><span class="sxs-lookup"><span data-stu-id="bc45e-103">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="bc45e-104">A partir do .NET Framework 4, associações e comportamentos não precisam ter um nome.</span><span class="sxs-lookup"><span data-stu-id="bc45e-104">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="bc45e-105">Para obter mais informações sobre configurações padrão e associações e comportamentos do sem nome, consulte [configuração simplificada](../../../wcf/simplified-configuration.md) e [configuração simplificada para serviços WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="bc45e-105">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="bc45e-106">Associações fornecidas pelo sistema</span><span class="sxs-lookup"><span data-stu-id="bc45e-106">System-provided bindings</span></span>

<span data-ttu-id="bc45e-107">As associações fornecidas pelo sistema ocultam a complexidade da pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="bc45e-107">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="bc45e-108">Os aplicativos que usam associações fornecidas pelo sistema não exigem controle total sobre a pilha.</span><span class="sxs-lookup"><span data-stu-id="bc45e-108">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="bc45e-109">Os atributos expostos em cada associação fornecida pelo sistema são os mais apropriados para o cenário de uso os endereços de associação.</span><span class="sxs-lookup"><span data-stu-id="bc45e-109">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="bc45e-110">A seção de configuração para cada associação fornecida pelo sistema pode definir várias configurações usadas para configurar a associação.</span><span class="sxs-lookup"><span data-stu-id="bc45e-110">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="bc45e-111">Cada configuração é identificada por um nome exclusivo.</span><span class="sxs-lookup"><span data-stu-id="bc45e-111">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="bc45e-112">Não é possível adicionar elementos ou atributos a uma associação fornecida pelo sistema.</span><span class="sxs-lookup"><span data-stu-id="bc45e-112">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="bc45e-113">Para fazer isso, você deve implementar uma associação personalizada, conforme descrito na seção [associações personalizadas](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="bc45e-113">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="bc45e-114">É possível definir uma ligação personalizada que imita perfeitamente uma associação fornecida pelo sistema e adiciona algumas configurações para as quais o aplicativo do usuário deseja ter controle.</span><span class="sxs-lookup"><span data-stu-id="bc45e-114">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="bc45e-115">Para obter uma lista de associações fornecidas pelo sistema, consulte [associações fornecidas pelo sistema](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="bc45e-115">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="bc45e-116">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bc45e-116">Custom bindings</span></span>

<span data-ttu-id="bc45e-117">As associações personalizadas fornecem controle total sobre a pilha de mensagens do WCF.</span><span class="sxs-lookup"><span data-stu-id="bc45e-117">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="bc45e-118">Uma associação individual define a pilha de mensagens especificando os elementos de configuração dos elementos de pilha na ordem em que aparecem na pilha.</span><span class="sxs-lookup"><span data-stu-id="bc45e-118">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="bc45e-119">Cada elemento define e configura um elemento da pilha.</span><span class="sxs-lookup"><span data-stu-id="bc45e-119">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="bc45e-120">Deve haver apenas um `transport` elemento em cada associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="bc45e-120">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="bc45e-121">Sem esse elemento, a pilha de mensagens está incompleta.</span><span class="sxs-lookup"><span data-stu-id="bc45e-121">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="bc45e-122">A ordem na qual os elementos aparecem na pilha é importante, pois é a ordem na qual as operações são aplicadas à mensagem.</span><span class="sxs-lookup"><span data-stu-id="bc45e-122">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="bc45e-123">A ordem necessária dos elementos de pilha é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="bc45e-123">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="bc45e-124">Transações (opcional)</span><span class="sxs-lookup"><span data-stu-id="bc45e-124">Transactions (optional)</span></span>  

2. <span data-ttu-id="bc45e-125">Mensagens confiáveis (opcional)</span><span class="sxs-lookup"><span data-stu-id="bc45e-125">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="bc45e-126">Segurança (opcional)</span><span class="sxs-lookup"><span data-stu-id="bc45e-126">Security (optional)</span></span>  

4. <span data-ttu-id="bc45e-127">Codificador</span><span class="sxs-lookup"><span data-stu-id="bc45e-127">Encoder</span></span>  

5. <span data-ttu-id="bc45e-128">Transport</span><span class="sxs-lookup"><span data-stu-id="bc45e-128">Transport</span></span>  

 <span data-ttu-id="bc45e-129">As associações personalizadas são identificadas por seu `name` atributo.</span><span class="sxs-lookup"><span data-stu-id="bc45e-129">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="bc45e-130">Para obter mais informações sobre associações personalizadas, consulte [associações personalizadas](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="bc45e-130">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bc45e-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="bc45e-131">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="bc45e-132">Associações</span><span class="sxs-lookup"><span data-stu-id="bc45e-132">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="bc45e-133">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="bc45e-133">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
