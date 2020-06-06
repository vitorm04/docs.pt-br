---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: f5bcd142fb2b032ea179bcbba68fee53b98d2d77
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/06/2020
ms.locfileid: "73736308"
---
# \<transactionFlow>
<span data-ttu-id="df212-101">Especifica o suporte do fluxo de transações para a associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="df212-101">Specifies transaction flow support for the custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<transactionFlow>**  
  
## <a name="syntax"></a><span data-ttu-id="df212-102">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="df212-102">Syntax</span></span>  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="df212-103">Atributos e elementos</span><span class="sxs-lookup"><span data-stu-id="df212-103">Attributes and Elements</span></span>  
 <span data-ttu-id="df212-104">As seções a seguir descrevem atributos, elementos filho e elementos pai.</span><span class="sxs-lookup"><span data-stu-id="df212-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="df212-105">Atributos</span><span class="sxs-lookup"><span data-stu-id="df212-105">Attributes</span></span>  
  
|<span data-ttu-id="df212-106">Atributo</span><span class="sxs-lookup"><span data-stu-id="df212-106">Attribute</span></span>|<span data-ttu-id="df212-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="df212-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="df212-108">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="df212-108">transactionProtocol</span></span>|<span data-ttu-id="df212-109">Especifica o protocolo de transação a ser usado.</span><span class="sxs-lookup"><span data-stu-id="df212-109">Specifies the transaction protocol to be used.</span></span> <span data-ttu-id="df212-110">Os valores válidos incluem os seguintes:</span><span class="sxs-lookup"><span data-stu-id="df212-110">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="df212-111">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="df212-111">-   OleTransactions</span></span><br /><span data-ttu-id="df212-112">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="df212-112">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="df212-113">O padrão é OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="df212-113">The default is OleTransactions.</span></span><br /><br /> <span data-ttu-id="df212-114">Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="df212-114">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="df212-115">Elementos filho</span><span class="sxs-lookup"><span data-stu-id="df212-115">Child Elements</span></span>  
 <span data-ttu-id="df212-116">Nenhum.</span><span class="sxs-lookup"><span data-stu-id="df212-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="df212-117">Elementos pai</span><span class="sxs-lookup"><span data-stu-id="df212-117">Parent Elements</span></span>  
  
|<span data-ttu-id="df212-118">Elemento</span><span class="sxs-lookup"><span data-stu-id="df212-118">Element</span></span>|<span data-ttu-id="df212-119">Descrição</span><span class="sxs-lookup"><span data-stu-id="df212-119">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="df212-120">Define todos os recursos de associação da associação personalizada.</span><span class="sxs-lookup"><span data-stu-id="df212-120">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="df212-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="df212-121">Remarks</span></span>  
 <span data-ttu-id="df212-122">Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como especificar o formato de protocolo desejado para as transações de entrada.</span><span class="sxs-lookup"><span data-stu-id="df212-122">This element allows you to enable or disable incoming transaction flow in an endpoint’s binding settings, as well as to specify the desired protocol format for incoming transactions.</span></span> <span data-ttu-id="df212-123">Para obter mais informações sobre como usar esse elemento de configuração, consulte [configuração de transação ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) e [habilitação do fluxo de transações](../../../wcf/feature-details/enabling-transaction-flow.md).</span><span class="sxs-lookup"><span data-stu-id="df212-123">For more information on using this configuration element, see [ServiceModel Transaction Configuration](../../../wcf/feature-details/servicemodel-transaction-configuration.md) and [Enabling Transaction Flow](../../../wcf/feature-details/enabling-transaction-flow.md).</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="df212-124">Ao usar o `OleTransactions` protocolo para transmitir transações do ponto de extremidade para o ponto de extremidade, o tempo limite da transação poderá ser perdido se o ponto de extremidade de destino tentar fluir novamente usando qualquer protocolo diferente de `OleTransactions` .</span><span class="sxs-lookup"><span data-stu-id="df212-124">When using the `OleTransactions` protocol to flow transactions from endpoint to endpoint, the transaction timeout can be lost if the destination endpoint attempts to flow again using any protocol other than `OleTransactions`.</span></span> <span data-ttu-id="df212-125">Isso pode causar todos os nós de nível inferior após o salto de OleTransactions para o tempo limite mais tarde do esperado.</span><span class="sxs-lookup"><span data-stu-id="df212-125">This can cause all down-level nodes after the OleTransactions hop to timeout later than expected.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df212-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="df212-126">See also</span></span>

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="df212-127">Configuração de transação de ServiceModel</span><span class="sxs-lookup"><span data-stu-id="df212-127">ServiceModel Transaction Configuration</span></span>](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [<span data-ttu-id="df212-128">Ativando o fluxo de transações</span><span class="sxs-lookup"><span data-stu-id="df212-128">Enabling Transaction Flow</span></span>](../../../wcf/feature-details/enabling-transaction-flow.md)
- [<span data-ttu-id="df212-129">Associações</span><span class="sxs-lookup"><span data-stu-id="df212-129">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="df212-130">Estendendo associações</span><span class="sxs-lookup"><span data-stu-id="df212-130">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="df212-131">Associações personalizadas</span><span class="sxs-lookup"><span data-stu-id="df212-131">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
