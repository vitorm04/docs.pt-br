---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 626ae03d622221ab3e956bd03898b6cc30482c98
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59179147"
---
# <a name="transactionflow"></a><span data-ttu-id="15f77-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="15f77-101">\<transactionFlow></span></span>
<span data-ttu-id="15f77-102">Especifica o suporte ao fluxo de transação para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="15f77-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="15f77-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="15f77-103">\<system.serviceModel></span></span>  
<span data-ttu-id="15f77-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="15f77-104">\<bindings></span></span>  
<span data-ttu-id="15f77-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="15f77-105">\<customBinding></span></span>  
<span data-ttu-id="15f77-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="15f77-106">\<binding></span></span>  
<span data-ttu-id="15f77-107">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="15f77-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15f77-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="15f77-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15f77-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="15f77-109">Attributes and Elements</span></span>  
 <span data-ttu-id="15f77-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="15f77-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15f77-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="15f77-111">Attributes</span></span>  
  
|<span data-ttu-id="15f77-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="15f77-112">Attribute</span></span>|<span data-ttu-id="15f77-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="15f77-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15f77-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="15f77-114">transactionProtocol</span></span>|<span data-ttu-id="15f77-115">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="15f77-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="15f77-116">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="15f77-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="15f77-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="15f77-117">-   OleTransactions</span></span><br /><span data-ttu-id="15f77-118">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="15f77-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="15f77-119">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="15f77-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="15f77-120">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="15f77-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15f77-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="15f77-121">Child Elements</span></span>  
 <span data-ttu-id="15f77-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="15f77-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="15f77-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="15f77-123">Parent Elements</span></span>  
  
|<span data-ttu-id="15f77-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="15f77-124">Element</span></span>|<span data-ttu-id="15f77-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="15f77-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15f77-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="15f77-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="15f77-127">Define todos os recursos de associação de associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="15f77-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="15f77-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="15f77-128">Remarks</span></span>  
 <span data-ttu-id="15f77-129">Esse elemento permite que você habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como para especificar o formato de protocolo desejado para transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="15f77-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="15f77-130">Para obter mais informações sobre como usar este elemento de configuração, consulte [configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) e [habilitando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="15f77-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="15f77-131">Ao usar o `OleTransactions` do ponto de extremidade ao ponto de extremidade de protocolo para transações de fluxo, o tempo limite da transação pode ser perdido se o ponto de extremidade de destino tenta novamente usando qualquer protocolo diferente de fluxo `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="15f77-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="15f77-132">Isso pode causar uma todos os nós de nível inferior após o salto OleTransactions mais tarde do que o esperado para o tempo limite.</span><span class="sxs-lookup"><span data-stu-id="15f77-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15f77-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="15f77-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="15f77-134">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="15f77-134">ServiceModel Transaction Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="15f77-135">Habilitando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="15f77-135">Enabling Transaction Flow</span></span>](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="15f77-136">Associações</span><span class="sxs-lookup"><span data-stu-id="15f77-136">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="15f77-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="15f77-137">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="15f77-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="15f77-138">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="15f77-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="15f77-139">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
