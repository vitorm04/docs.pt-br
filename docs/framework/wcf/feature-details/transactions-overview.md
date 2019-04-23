---
title: Visão geral de transações do Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- transactions [WCF]
- WCF, transactions
- Windows Communication Foundation, transactions
ms.assetid: c7757854-1207-4019-8b31-552578b7d570
ms.openlocfilehash: 42276a9b450b6f0664901747239195ab13f7c44d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223102"
---
# <a name="windows-communication-foundation-transactions-overview"></a>Visão geral de transações do Windows Communication Foundation
As transações fornecem uma maneira de agrupar um conjunto de ações ou operações em uma única unidade indivisível de execução. Uma transação é uma coleção de operações com as seguintes propriedades:  
  
-   Atomicidade. Isso garante que todas as atualizações concluídas em uma transação específica são confirmadas e tornam-se duráveis ou eles são todos anulados e revertidos ao estado anterior.  
  
-   Consistência. Isso garante que as alterações feitas em uma transação representam uma transformação de um estado consistente para outro. Por exemplo, uma transação que transfere dinheiro de uma conta bancária para uma conta de economias não altera a quantidade de dinheiro na conta bancária geral.  
  
-   Isolamento. Isso impede que uma transação de observar as alterações não confirmadas que pertencem a outras transações simultâneas. O isolamento fornece uma abstração de simultaneidade, garantindo uma transação não pode ter um impacto inesperado na execução de outra transação.  
  
-   Durabilidade. Isso significa que, depois de confirmado, atualizações para recursos gerenciados (como um registro de banco de dados) será persistentes no caso de falhas.  
  
 Windows Communication Foundation (WCF) oferece um conjunto avançado de recursos que permitem a criação de transações distribuídas em seu aplicativo de serviço Web.  
  
 O WCF implementa o suporte ao protocolo WS-AtomicTransaction (WS-AT) que permite que os aplicativos do WCF para transações de fluxo para aplicativos interoperáveis, como serviços da Web interoperáveis construídos usando a tecnologia de produtos de terceiros. O WCF também implementa o suporte para o protocolo de transações OLE, que pode ser usado em cenários em que você não precisa interoperabilidade funcionalidade para habilitar o fluxo de transações.  
  
 Você pode usar um arquivo de configuração de aplicativo para configurar associações para habilitar ou desabilitar o fluxo de transações, bem como definir o protocolo de transação desejadas em uma associação. Além disso, você pode definir tempos limite de transação no nível de serviço usando o arquivo de configuração. Para obter mais informações, consulte [habilitando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md).  
  
 Atributos de transação no <xref:System.ServiceModel> namespace permitem que você faça o seguinte:  
  
-   Configurar tempos limite de transação e a filtragem no nível de isolamento usando o <xref:System.ServiceModel.ServiceBehaviorAttribute> atributo.  
  
-   Habilitar a funcionalidade de transações e configurar o comportamento de conclusão de transações usando o <xref:System.ServiceModel.OperationBehaviorAttribute> atributo.  
  
-   Use o <xref:System.ServiceModel.ServiceContractAttribute> e <xref:System.ServiceModel.OperationContractAttribute> atributos em um método de contrato para exigir, permitir ou negar o fluxo de transações.  
  
 Para obter mais informações, consulte [atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md).  
  
## <a name="see-also"></a>Consulte também

- [Atributos de transação de ServiceModel](../../../../docs/framework/wcf/feature-details/servicemodel-transaction-attributes.md)
- [Habilitando o fluxo de transação](../../../../docs/framework/wcf/feature-details/enabling-transaction-flow.md)
