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
ms.openlocfilehash: faf992aa50f8d705caa5f502f61a0fd18cb7ab05
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="lttransactionflowgt"></a><span data-ttu-id="c09b8-102">&lt;transactionFlow&gt;</span><span class="sxs-lookup"><span data-stu-id="c09b8-102">&lt;transactionFlow&gt;</span></span>
<span data-ttu-id="c09b8-103">Especifica o suporte de fluxo de transação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c09b8-103">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="c09b8-104">\<System. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="c09b8-104">\<system.serviceModel></span></span>  
<span data-ttu-id="c09b8-105">\<associações ></span><span class="sxs-lookup"><span data-stu-id="c09b8-105">\<bindings></span></span>  
<span data-ttu-id="c09b8-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c09b8-106">\<customBinding></span></span>  
<span data-ttu-id="c09b8-107">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c09b8-107">\<binding></span></span>  
<span data-ttu-id="c09b8-108">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="c09b8-108">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c09b8-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c09b8-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c09b8-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="c09b8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c09b8-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="c09b8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c09b8-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="c09b8-112">Attributes</span></span>  
  
|<span data-ttu-id="c09b8-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="c09b8-113">Attribute</span></span>|<span data-ttu-id="c09b8-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="c09b8-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c09b8-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="c09b8-115">transactionProtocol</span></span>|<span data-ttu-id="c09b8-116">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="c09b8-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="c09b8-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="c09b8-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="c09b8-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="c09b8-118">-   OleTransactions</span></span><br /><span data-ttu-id="c09b8-119">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="c09b8-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="c09b8-120">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="c09b8-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="c09b8-121">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="c09b8-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c09b8-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="c09b8-122">Child Elements</span></span>  
 <span data-ttu-id="c09b8-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="c09b8-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c09b8-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="c09b8-124">Parent Elements</span></span>  
  
|<span data-ttu-id="c09b8-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="c09b8-125">Element</span></span>|<span data-ttu-id="c09b8-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="c09b8-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c09b8-127">\<associação ></span><span class="sxs-lookup"><span data-stu-id="c09b8-127">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="c09b8-128">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c09b8-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c09b8-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="c09b8-129">Remarks</span></span>  
 <span data-ttu-id="c09b8-130">Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como para especificar o formato do protocolo desejado para as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="c09b8-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="c09b8-131">Para obter mais informações sobre como usar este elemento de configuração, consulte [configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) e [ativando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="c09b8-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="c09b8-132">Ao usar o `OleTransactions` de ponto de extremidade ao ponto de extremidade de protocolo para transações de fluxo, o tempo limite da transação pode ser perdido se o ponto de extremidade de destino tenta novamente usando qualquer protocolo diferente de fluxo `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="c09b8-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="c09b8-133">Isso pode causar a todos os nós de nível inferior após o salto OleTransactions para o tempo limite mais tarde do que o esperado.</span><span class="sxs-lookup"><span data-stu-id="c09b8-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c09b8-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c09b8-134">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.TransactionFlowElement>  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="c09b8-135">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c09b8-135">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)  
 [<span data-ttu-id="c09b8-136">Ativando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="c09b8-136">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)  
 <span data-ttu-id="c09b8-137">[Bindings](../../../../../docs/framework/wcf/bindings.md) (Associações)</span><span class="sxs-lookup"><span data-stu-id="c09b8-137">[Bindings](../../../../../docs/framework/wcf/bindings.md)</span></span>  
 [<span data-ttu-id="c09b8-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="c09b8-138">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="c09b8-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="c09b8-139">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="c09b8-140">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="c09b8-140">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
