---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 206a684e1279871eee4aed95a087921123f8efb9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918654"
---
# <a name="transactionflow"></a><span data-ttu-id="0f167-101">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="0f167-101">\<transactionFlow></span></span>
<span data-ttu-id="0f167-102">Especifica o suporte do fluxo de transações para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0f167-102">Specifies transaction flow support for the custom binding.</span></span>  
  
 <span data-ttu-id="0f167-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="0f167-103">\<system.serviceModel></span></span>  
<span data-ttu-id="0f167-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="0f167-104">\<bindings></span></span>  
<span data-ttu-id="0f167-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0f167-105">\<customBinding></span></span>  
<span data-ttu-id="0f167-106">\<> de associação</span><span class="sxs-lookup"><span data-stu-id="0f167-106">\<binding></span></span>  
<span data-ttu-id="0f167-107">\<transactionFlow></span><span class="sxs-lookup"><span data-stu-id="0f167-107">\<transactionFlow></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f167-108">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f167-108">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0f167-109">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="0f167-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0f167-110">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="0f167-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0f167-111">Atributos</span><span class="sxs-lookup"><span data-stu-id="0f167-111">Attributes</span></span>  
  
|<span data-ttu-id="0f167-112">Atributo</span><span class="sxs-lookup"><span data-stu-id="0f167-112">Attribute</span></span>|<span data-ttu-id="0f167-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f167-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0f167-114">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="0f167-114">transactionProtocol</span></span>|<span data-ttu-id="0f167-115">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="0f167-115">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="0f167-116">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="0f167-116">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="0f167-117">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="0f167-117">-   OleTransactions</span></span><br /><span data-ttu-id="0f167-118">-   WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="0f167-118">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="0f167-119">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="0f167-119">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="0f167-120">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="0f167-120">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0f167-121">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="0f167-121">Child Elements</span></span>  
 <span data-ttu-id="0f167-122">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="0f167-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0f167-123">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="0f167-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0f167-124">Elemento</span><span class="sxs-lookup"><span data-stu-id="0f167-124">Element</span></span>|<span data-ttu-id="0f167-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="0f167-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0f167-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="0f167-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="0f167-127">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="0f167-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0f167-128">Comentários</span><span class="sxs-lookup"><span data-stu-id="0f167-128">Remarks</span></span>  
 <span data-ttu-id="0f167-129">Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como especificar o formato de protocolo desejado para as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="0f167-129">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="0f167-130">Para obter mais informações sobre como usar esse elemento de configuração, consulte [configuração de transação ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) e habilitação do [fluxo de transações](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="0f167-130">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="0f167-131">Ao usar o `OleTransactions` protocolo para transmitir transações do ponto de extremidade para o ponto de extremidade, o tempo limite da transação poderá ser perdido se o ponto de extremidade de `OleTransactions`destino tentar fluir novamente usando qualquer protocolo diferente de.</span><span class="sxs-lookup"><span data-stu-id="0f167-131">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="0f167-132">Isso pode causar todos os nós de nível inferior após o salto de OleTransactions para o tempo limite mais tarde do esperado.</span><span class="sxs-lookup"><span data-stu-id="0f167-132">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f167-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f167-133">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="0f167-134">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="0f167-134">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="0f167-135">Habilitando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="0f167-135">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="0f167-136">Associações</span><span class="sxs-lookup"><span data-stu-id="0f167-136">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="0f167-137">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="0f167-137">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="0f167-138">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="0f167-138">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="0f167-139">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="0f167-139">\<customBinding></span></span>](custombinding.md)
