---
title: <transactionFlow>
ms.date: 03/30/2017
ms.assetid: 8c7b4c5b-ace3-4fe3-89ff-7b13c9aacd13
ms.openlocfilehash: ef3d92e07aaf4d4ba9d90e381017db104f2cc8fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55276985"
---
# <a name="transactionflow"></a>\<transactionFlow>
Especifica o suporte ao fluxo de transação para a associação personalizada.  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<transactionFlow>  
  
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
|[\<binding>](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação de associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento permite que você habilitar ou desabilitar o fluxo de transações de entrada nas configurações de associação de um ponto de extremidade, bem como para especificar o formato de protocolo desejado para transações de entrada. Para obter mais informações sobre como usar este elemento de configuração, consulte [configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md) e [habilitando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
> [!CAUTION]
>  Ao usar o `OleTransactions` do ponto de extremidade ao ponto de extremidade de protocolo para transações de fluxo, o tempo limite da transação pode ser perdido se o ponto de extremidade de destino tenta novamente usando qualquer protocolo diferente de fluxo `OleTransactions`. Isso pode causar uma todos os nós de nível inferior após o salto OleTransactions mais tarde do que o esperado para o tempo limite.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.Configuration.TransactionFlowElement>
- <xref:System.ServiceModel.Channels.TransactionFlowBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Configuração de transação de ServiceModel](../../../../../docs/framework/wcf/feature-details/servicemodel-transaction-configuration.md)
- [Habilitando o fluxo de transação](../../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
