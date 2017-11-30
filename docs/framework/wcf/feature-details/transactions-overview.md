---
title: "Visão geral de transações do Windows Communication Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2be5e7622c51da37c0f39c12258f50b74483fa53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-transactions-overview"></a>Visão geral de transações do Windows Communication Foundation
As transações fornecem uma maneira de agrupar um conjunto de ações ou operações em uma única unidade indivisível de execução. Uma transação é uma coleção de operações com as seguintes propriedades:  
  
-   Atomicidade. Isso garante que todas as atualizações concluídas em uma transação específica são confirmadas e duráveis ou são todas anuladas e revertidas ao estado anterior.  
  
-   Consistência. Isso garante que as alterações feitas em uma transação representam uma transformação de um estado consistente para outro. Por exemplo, uma transação que transfere dinheiro de uma conta bancária para uma conta de economias não altera a quantidade de dinheiro na conta bancária geral.  
  
-   Isolamento. Isso impede que uma transação observar as alterações não confirmadas que pertencem a outras transações simultâneas. O isolamento fornece uma abstração de simultaneidade, garantindo uma transação não pode ter um impacto inesperado da execução de outra transação.  
  
-   Durabilidade. Isso significa que, depois de confirmada, as atualizações para recursos gerenciados (como um registro de banco de dados) será persistentes diante de falhas.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Fornece um conjunto avançado de recursos que permitem a criação de transações distribuídas em seu aplicativo de serviço Web.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementa o suporte ao protocolo WS-AtomicTransaction (WS-AT) que permite que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos transações de fluxo para aplicativos interoperáveis, como serviços da Web interoperáveis construídos usando a tecnologia de terceiros. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]também implementa o suporte para o protocolo de transações OLE, que pode ser usado em cenários em que você não precisa interoperabilidade funcionalidade para habilitar o fluxo de transações.  
  
 Você pode usar um arquivo de configuração de aplicativo para configurar as ligações para habilitar ou desabilitar o fluxo de transações, bem como definir o protocolo de transação desejadas em uma associação. Além disso, você pode definir tempos limite de transação no nível de serviço usando o arquivo de configuração. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Ativando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atributos de transação no <xref:System.ServiceModel> namespace permitem que você faça o seguinte:  
  
-   Configurar o tempo limite de transação e de filtragem no nível de isolamento usando o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo.  
  
-   Habilitar a funcionalidade de transações e configurar o comportamento de conclusão de transações usando o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.  
  
-   Use o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos em um método de contrato para exigir, permitir ou negar o fluxo de transações.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [Ativando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
