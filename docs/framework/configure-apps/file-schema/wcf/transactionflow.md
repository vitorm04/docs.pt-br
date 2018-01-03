---
title: '&lt;transactionFlow&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3720294ac937c6aa7ce99ab687efa76b2e860abb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="1875f-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="1875f-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="1875f-103">Especifica o suporte de fluxo de transação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1875f-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="1875f-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="1875f-104">\<system.serviceModel></span></span>  
<span data-ttu-id="1875f-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="1875f-105">\<bindings></span></span>  
<span data-ttu-id="1875f-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1875f-106">\<customBinding></span></span>  
<span data-ttu-id="1875f-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1875f-107">\<binding></span></span>  
<span data-ttu-id="1875f-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="1875f-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1875f-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1875f-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1875f-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="1875f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1875f-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="1875f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1875f-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="1875f-112">Attributes</span></span>  
  
|<span data-ttu-id="1875f-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="1875f-113">Attribute</span></span>|<span data-ttu-id="1875f-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="1875f-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1875f-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="1875f-115">transactionProtocol</span></span>|<span data-ttu-id="1875f-116">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="1875f-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="1875f-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="1875f-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="1875f-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="1875f-118">-   OleTransactions</span></span><br /><span data-ttu-id="1875f-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="1875f-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="1875f-120">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="1875f-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="1875f-121">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="1875f-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1875f-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="1875f-122">Child Elements</span></span>  
 <span data-ttu-id="1875f-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="1875f-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1875f-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="1875f-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1875f-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="1875f-125">Element</span></span>|<span data-ttu-id="1875f-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="1875f-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1875f-127">\<associação ></span><span class="sxs-lookup"><span data-stu-id="1875f-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="1875f-128">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="1875f-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1875f-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="1875f-129">Remarks</span></span>  
 <span data-ttu-id="1875f-130">Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como para especificar o formato do protocolo desejado para as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="1875f-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="1875f-131">Para obter mais informações sobre como usar este elemento de configuração, consulte [configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) e [ativando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="1875f-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="1875f-132">Ao usar o `OleTransactions` de ponto de extremidade ao ponto de extremidade de protocolo para transações de fluxo, o tempo limite da transação pode ser perdido se o ponto de extremidade de destino tenta novamente usando qualquer protocolo diferente de fluxo `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="1875f-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="1875f-133">Isso pode causar a todos os nós de nível inferior após o salto OleTransactions para o tempo limite mais tarde do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="1875f-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1875f-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1875f-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="1875f-135">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1875f-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="1875f-136">Habilitando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="1875f-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 [<span data-ttu-id="1875f-137">Associações</span><span class="sxs-lookup"><span data-stu-id="1875f-137">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="1875f-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="1875f-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="1875f-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="1875f-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="1875f-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="1875f-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
