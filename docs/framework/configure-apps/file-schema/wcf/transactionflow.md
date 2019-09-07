---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: 8247dd62f4dda853487fe52f00f8f548b627c075
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399390"
---
# <a name="transactionflow"></a>\<transactionFlow>
Especifica o suporte do fluxo de transações para a associação personalizada.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<associações >** ](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de CustomBinding**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de associação**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> transactionFlow**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<transactionFlow transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004" />
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|transactionProtocol|Especifica o protocolo de transação a ser usado. Os valores válidos incluem o seguinte:<br /><br /> -OleTransactions<br />-   WSAtomicTransactionOctober2004<br /><br /> O padrão é OleTransactions.<br /><br /> Esse atributo é do tipo <xref:System.ServiceModel.TransactionProtocol>.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<binding>](../../../misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento permite habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como especificar o formato de protocolo desejado para as transações de entrada. Para obter mais informações sobre como usar esse elemento de configuração, consulte [configuração de transação ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md) e [habilitação do fluxo de transações](../../../wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
> Ao usar o `OleTransactions` protocolo para transmitir transações do ponto de extremidade para o ponto de extremidade, o tempo limite da transação poderá ser perdido se o ponto de extremidade de `OleTransactions`destino tentar fluir novamente usando qualquer protocolo diferente de. Isso pode causar todos os nós de nível inferior após o salto de OleTransactions para o tempo limite mais tarde do esperado.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Configuração de transação de ServiceModel](../../../wcf/feature-details/servicemodel-transaction-configuration.md)
- [Habilitando o fluxo de transação](../../../wcf/feature-details/enabling-transaction-flow.md)
- [Associações](../../../wcf/bindings.md)
- [Estendendo associações](../../../wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
