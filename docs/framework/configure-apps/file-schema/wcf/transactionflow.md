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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 8c40b3a79567ccc1ca5a83631253d3ff6ead0f84
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="2b76c-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="2b76c-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="2b76c-103">Especifica o suporte de fluxo de transação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2b76c-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="2b76c-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2b76c-104">\<system.serviceModel></span></span>  
<span data-ttu-id="2b76c-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="2b76c-105">\<bindings></span></span>  
<span data-ttu-id="2b76c-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b76c-106">\<customBinding></span></span>  
<span data-ttu-id="2b76c-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="2b76c-107">\<binding></span></span>  
<span data-ttu-id="2b76c-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="2b76c-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b76c-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b76c-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2b76c-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="2b76c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2b76c-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="2b76c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2b76c-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="2b76c-112">Attributes</span></span>  
  
|<span data-ttu-id="2b76c-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="2b76c-113">Attribute</span></span>|<span data-ttu-id="2b76c-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b76c-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2b76c-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="2b76c-115">transactionProtocol</span></span>|<span data-ttu-id="2b76c-116">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="2b76c-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="2b76c-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="2b76c-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2b76c-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="2b76c-118">-   OleTransactions</span></span><br /><span data-ttu-id="2b76c-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="2b76c-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="2b76c-120">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="2b76c-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="2b76c-121">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="2b76c-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2b76c-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="2b76c-122">Child Elements</span></span>  
 <span data-ttu-id="2b76c-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="2b76c-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2b76c-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="2b76c-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2b76c-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="2b76c-125">Element</span></span>|<span data-ttu-id="2b76c-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b76c-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2b76c-127">\<associação ></span><span class="sxs-lookup"><span data-stu-id="2b76c-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="2b76c-128">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="2b76c-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b76c-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b76c-129">Remarks</span></span>  
 <span data-ttu-id="2b76c-130">Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como para especificar o formato do protocolo desejado para as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="2b76c-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="2b76c-131">Para obter mais informações sobre como usar este elemento de configuração, consulte [configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) e [ativando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="2b76c-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="2b76c-132">Ao usar o `OleTransactions` de ponto de extremidade ao ponto de extremidade de protocolo para transações de fluxo, o tempo limite da transação pode ser perdido se o ponto de extremidade de destino tenta novamente usando qualquer protocolo diferente de fluxo `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="2b76c-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="2b76c-133">Isso pode causar a todos os nós de nível inferior após o salto OleTransactions para o tempo limite mais tarde do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="2b76c-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b76c-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2b76c-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="2b76c-135">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2b76c-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="2b76c-136">Ativando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="2b76c-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 <span data-ttu-id="2b76c-137">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="2b76c-137">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="2b76c-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="2b76c-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="2b76c-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="2b76c-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="2b76c-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="2b76c-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
