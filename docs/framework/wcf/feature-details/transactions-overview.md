---
title: Visão geral de transações do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 63f3826215f24a4bab6d84709c2f9da6a9c8f4f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="windows-communication-foundation-transactions-overview"></a>Visão geral de transações do Windows Communication Foundation
As transações fornecem uma maneira de agrupar um conjunto de ações ou operações em uma única unidade indivisível de execução. Uma transação é uma coleção de operações com as seguintes propriedades:  
  
-   Atomicidade. Isso garante que todas as atualizações concluídas em uma transação específica são confirmadas e duráveis ou são todas anuladas e revertidas ao estado anterior.  
  
-   Consistência. Isso garante que as alterações feitas em uma transação representam uma transformação de um estado consistente para outro. Por exemplo, uma transação que transfere dinheiro de uma conta bancária para uma conta de economias não altera a quantidade de dinheiro na conta bancária geral.  
  
-   Isolamento. Isso impede que uma transação observar as alterações não confirmadas que pertencem a outras transações simultâneas. O isolamento fornece uma abstração de simultaneidade, garantindo uma transação não pode ter um impacto inesperado da execução de outra transação.  
  
-   Durabilidade. Isso significa que, depois de confirmada, as atualizações para recursos gerenciados (como um registro de banco de dados) será persistentes diante de falhas.  
  
 Windows Communication Foundation (WCF) fornece um conjunto avançado de recursos que permitem a criação de transações distribuídas em seu aplicativo de serviço Web.  
  
 O WCF implementa o suporte ao protocolo WS-AtomicTransaction (WS-AT) que permite que os aplicativos do WCF para transações de fluxo para aplicativos interoperáveis, como serviços da Web interoperáveis construídos usando a tecnologia de terceiros. WCF também implementa o suporte para o protocolo de transações OLE, que pode ser usado em cenários em que você não precisa interoperabilidade funcionalidade para habilitar o fluxo de transações.  
  
 Você pode usar um arquivo de configuração de aplicativo para configurar as ligações para habilitar ou desabilitar o fluxo de transações, bem como definir o protocolo de transação desejadas em uma associação. Além disso, você pode definir tempos limite de transação no nível de serviço usando o arquivo de configuração. Para obter mais informações, consulte [ativando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atributos de transação no <xref:System.ServiceModel> namespace permitem que você faça o seguinte:  
  
-   Configurar o tempo limite de transação e de filtragem no nível de isolamento usando o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo.  
  
-   Habilitar a funcionalidade de transações e configurar o comportamento de conclusão de transações usando o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.  
  
-   Use o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos em um método de contrato para exigir, permitir ou negar o fluxo de transações.  
  
 Para obter mais informações, consulte [atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Consulte também  
 [Atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)  
 [Habilitando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
