---
title: "Como implementar um cliente do padrão assíncrono baseado em evento"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b70d4ba205d39ad8fcbc7c7f6fa1f5b34a36c98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Como implementar um cliente do padrão assíncrono baseado em evento
O exemplo de código a seguir demonstra como usar um componente que cumpre o [baseado em evento visão geral do padrão assíncrono](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). O formulário para este exemplo usa o `PrimeNumberCalculator` componente descrito em [como: implementar um componente compatível com o padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Quando você executa um projeto que usa este exemplo, você verá um formulário de "Número primo Calculadora" com uma grade e dois botões: **iniciar nova tarefa** e **Cancelar**. Você pode clicar no **iniciar nova tarefa** botão várias vezes consecutivas, e cada clique, uma operação assíncrona será iniciado um cálculo para determinar se um número gerado aleatoriamente é primo. O formulário periodicamente exibirá o progresso e os resultados incrementais. Cada operação recebe uma ID exclusiva da tarefa O resultado da computação é exibido no **resultados** coluna; se o número de teste não é ideal, ele é rotulado como **composto,** e sua primeira divisor é exibida.  
  
 Todas as operações pendentes podem ser canceladas com o **Cancelar** botão. Várias seleções podem ser feitas.  
  
> [!NOTE]
>  A maioria dos números não será primos. Se você não encontrou um número primo após várias operações concluídas, simplesmente inicie mais tarefas e, eventualmente, você encontrará alguns números primos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ComponentModel.AsyncOperation>  
 <xref:System.ComponentModel.AsyncOperationManager>  
 <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
