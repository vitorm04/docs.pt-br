---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2019
ms.locfileid: "73736308"
---
# <a name="transactionflow"></a><span data-ttu-id="32c78-101">\<transactionFlow ></span><span class="sxs-lookup"><span data-stu-id="32c78-101">\<transactionFlow></span></span>
<span data-ttu-id="32c78-102">Especifica o suporte do fluxo de transações para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="32c78-102">Specifies transaction flow support for the custom binding.</span></span>  
  
<span data-ttu-id="32c78-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="32c78-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="32c78-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="32c78-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="32c78-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações**](bindings.md) ></span><span class="sxs-lookup"><span data-stu-id="32c78-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="32c78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**CustomBinding**](custombinding.md) ></span><span class="sxs-lookup"><span data-stu-id="32c78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="32c78-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Binding** ></span><span class="sxs-lookup"><span data-stu-id="32c78-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="32c78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<transactionFlow >**</span><span class="sxs-lookup"><span data-stu-id="32c78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32c78-109">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32c78-109">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="32c78-110">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="32c78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="32c78-111">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="32c78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="32c78-112">Atributos</span><span class="sxs-lookup"><span data-stu-id="32c78-112">Attributes</span></span>  
  
|<span data-ttu-id="32c78-113">Atributo</span><span class="sxs-lookup"><span data-stu-id="32c78-113">Attribute</span></span>|<span data-ttu-id="32c78-114">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c78-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="32c78-115">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="32c78-115">transactionProtocol</span></span>|<span data-ttu-id="32c78-116">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="32c78-116">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="32c78-117">Os valores válidos incluem o seguinte:</span><span class="sxs-lookup"><span data-stu-id="32c78-117">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="32c78-118">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="32c78-118">-   OleTransactions</span></span><br /><span data-ttu-id="32c78-119">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="32c78-119">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="32c78-120">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="32c78-120">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="32c78-121">Este atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="32c78-121">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="32c78-122">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="32c78-122">Child Elements</span></span>  
 <span data-ttu-id="32c78-123">nenhuma.</span><span class="sxs-lookup"><span data-stu-id="32c78-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="32c78-124">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="32c78-124">Parent Elements</span></span>  
  
|<span data-ttu-id="32c78-125">Elemento</span><span class="sxs-lookup"><span data-stu-id="32c78-125">Element</span></span>|<span data-ttu-id="32c78-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="32c78-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="32c78-127">\<binding ></span><span class="sxs-lookup"><span data-stu-id="32c78-127">\<binding></span></span>](bindings.md)|<span data-ttu-id="32c78-128">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="32c78-128">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32c78-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="32c78-129">Remarks</span></span>  
 <span data-ttu-id="32c78-130">Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como especificar o formato de protocolo desejado para as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="32c78-130">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="32c78-131">Para obter mais informações sobre como usar esse elemento de configuração, consulte [configuração de transação ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) e [habilitação do fluxo de transações](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="32c78-131">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="32c78-132">Ao usar o protocolo de `OleTransactions` para transmitir transações do ponto de extremidade para o ponto de extremidade, o tempo limite da transação poderá ser perdido se o ponto de extremidade de destino tentar fluir novamente usando qualquer protocolo diferente de `OleTransactions`.</span><span class="sxs-lookup"><span data-stu-id="32c78-132">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="32c78-133">Isso pode causar todos os nós de nível inferior após o salto de OleTransactions para o tempo limite mais tarde do esperado.</span><span class="sxs-lookup"><span data-stu-id="32c78-133">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c78-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32c78-134">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="32c78-135">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="32c78-135">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="32c78-136">Habilitando o fluxo de transação</span><span class="sxs-lookup"><span data-stu-id="32c78-136">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="32c78-137">Associações</span><span class="sxs-lookup"><span data-stu-id="32c78-137">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="32c78-138">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="32c78-138">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="32c78-139">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="32c78-139">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="32c78-140">\<CustomBinding</span><span class="sxs-lookup"><span data-stu-id="32c78-140">\<customBinding></span></span>](custombinding.md)
