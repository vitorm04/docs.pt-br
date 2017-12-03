---
title: "Comparando transações em COM+ e ServiceModel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e493bcdd-b91a-4486-853f-83dbcd1931b7
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5229c872c4843df916cf538b7f2e88e451dc6b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="comparing-transactions-in-com-and-servicemodel"></a>Comparando transações em COM+ e ServiceModel
Este tópico discute como simular o comportamento de uma transação COM+ serviço usando o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] atributos o <xref:System.ServiceModel> namespace fornece.  
  
## <a name="emulating-com-using-servicemodel-attributes"></a>Emulando COM+ usando atributos de ServiceModel  
 A tabela a seguir compara o <xref:System.EnterpriseServices.TransactionOption> enumeração usada para criar um `EnterpriseServices` transações e como eles se correlacionam a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] atributos o <xref:System.ServiceModel> namespace fornece.  
  
|Atributo de COM+|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]atributos|  
|---------------------|------------------------------------------------------------------------|  
|RequiresNew|<xref:System.ServiceModel.TransactionFlowAttribute> é definido como <xref:System.ServiceModel.TransactionFlowOption.NotAllowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`.<br /><br /> O `TransactionFlow` atributo no elemento de associação é `false`.|  
|Necessária|<xref:System.ServiceModel.TransactionFlowAttribute> é definido como <xref:System.ServiceModel.TransactionFlowOption.Allowed>.<br /><br /> <xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `true`.<br /><br /> O `TransactionFlow` atributo no elemento de associação é `true`.|  
|Com suporte|Não há nenhum equivalente direto. Em geral, você deve adotar o comportamento especificado para `Required` em vez disso.|  
|Não suportado|<xref:System.ServiceModel.OperationBehaviorAttribute.TransactionScopeRequired%2A> é `false`.<br /><br /> O `TransactionFlow` atributo no elemento de associação é `false`.|  
|Disabled|Não há nenhum equivalente direto. Em geral, você deve adotar o comportamento especificado para `NotSupported` em vez disso.|
