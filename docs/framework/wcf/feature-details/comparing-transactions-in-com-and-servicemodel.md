---
title: Comparando transações em COM+ e ServiceModel
ms.date: 03/30/2017
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
ms.openlocfilehash: 4a47fe1686dff2e705b06b001d7d5e4ea6e8c5f2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857864"
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Comparando transações em COM+ e ServiceModel
Este tópico discute como simular o comportamento de um COM+ serviço transacional usando os atributos do Windows Communication Foundation (WCF) a <xref:System.ServiceModel> namespace fornece.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulando COM+ usando atributos de ServiceModel  
 A tabela a seguir compara os <xref:System.EnterpriseServices.TransactionOption> enumeração usada para criar um `EnterpriseServices` transação e como eles se correlacionam com os atributos do WCF a <xref:System.ServiceModel> namespace fornece.  
  
|Atributo de COM+|Atributos do WCF|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> é definido como <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`.<br /><br /> O `TransactionFlow` atributo no elemento de associação é `false`.|  
|Necessária|<xref:System.ServiceModel.TransactionFlowAttribute> é definido como <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`.<br /><br /> O `TransactionFlow` atributo no elemento de associação é `true`.|  
|Com suporte|Não há nenhum equivalente direto. Em geral, você deve adotar o comportamento especificado para `Required` em vez disso.|  
|NotSupported|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `false`.<br /><br /> O `TransactionFlow` atributo no elemento de associação é `false`.|  
|Disabled|Não há nenhum equivalente direto. Em geral, você deve adotar o comportamento especificado para `NotSupported` em vez disso.|
