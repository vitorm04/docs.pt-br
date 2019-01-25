---
title: '&lt;transactionFlow&gt;'
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: d8597a71a9b7afadba7565290085f491052e04d6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622111"
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="0103d-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="0103d-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="0103d-103">Especifica o suporte ao fluxo de transação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0103d-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="0103d-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0103d-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0103d-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0103d-105">\<bindings></span></span>  
<span data-ttu-id="0103d-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0103d-106">\<customBinding></span></span>  
<span data-ttu-id="0103d-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="0103d-107">\<binding></span></span>  
<span data-ttu-id="0103d-108">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="0103d-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0103d-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0103d-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0103d-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0103d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0103d-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0103d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0103d-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="0103d-112">Attributes</span></span>  
  
|<span data-ttu-id="0103d-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="0103d-113">Attribute</span></span>|<span data-ttu-id="0103d-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="0103d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0103d-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="0103d-115">transactionProtocol</span></span>|<span data-ttu-id="0103d-116">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0103d-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="0103d-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0103d-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0103d-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="0103d-118">-   OleTransactions</span></span><br /><span data-ttu-id="0103d-119">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="0103d-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="0103d-120">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="0103d-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="0103d-121">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="0103d-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0103d-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0103d-122">Child Elements</span></span>  
 <span data-ttu-id="0103d-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0103d-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0103d-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0103d-124">Parent Elements</span></span>  
  
|<span data-ttu-id="0103d-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="0103d-125">Element</span></span>|<span data-ttu-id="0103d-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="0103d-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0103d-127">\<binding></span><span class="sxs-lookup"><span data-stu-id="0103d-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0103d-128">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0103d-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0103d-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="0103d-129">Remarks</span></span>  
 <span data-ttu-id="0103d-130">Esse elemento permite que você habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como para especificar o formato de protocolo desejado para transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="0103d-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="0103d-131">Para obter mais informações sobre como usar este elemento de configuração, consulte [configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) e [habilitando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="0103d-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0103d-132">Ao usar o `OleTransactions` do ponto de extremidade ao ponto de extremidade de protocolo para transações de fluxo, o tempo limite da transação pode ser perdido se o ponto de extremidade de destino tenta novamente usando qualquer protocolo diferente de fluxo `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="0103d-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="0103d-133">Isso pode causar uma todos os nós de nível inferior após o salto OleTransactions mais tarde do que o esperado para o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="0103d-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0103d-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0103d-134">See also</span></span>
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0103d-135">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0103d-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="0103d-136">Habilitando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="0103d-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="0103d-137">Associações</span><span class="sxs-lookup"><span data-stu-id="0103d-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="0103d-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="0103d-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0103d-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="0103d-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0103d-140">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0103d-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
