---
title: Como implementar um cliente do padrão assíncrono baseado em evento
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
ms.openlocfilehash: 4176d1a4cec91c5740b03c10d1a6d2cc263dba28
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44266303"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a>Como implementar um cliente do padrão assíncrono baseado em evento
O código a seguir descreve como usar um componente que respeita a [Visão geral do Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md). O formulário desse exemplo usa o componente `PrimeNumberCalculator` descrito em [Como: implementar um componente compatível com o Padrão assíncrono baseado em evento](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Quando você executa um projeto que usa este exemplo, você verá um formulário de "Calculadora de números primos" com uma grade e dois botões: **Iniciar Nova Tarefa** e **Cancelar**. Você pode clicar no botão **Iniciar Nova Tarefa** várias vezes consecutivas e, para cada clique, uma operação assíncrona iniciará uma computação para determinar se um número gerado aleatoriamente é primo. O formulário exibirá periodicamente o progresso e os resultados incrementais. Cada operação recebe uma ID de tarefa exclusiva. O resultado da computação é exibido na coluna **Resultado**. Se o número do teste não for primo, ele será rotulado como **Composto** e seu primeiro divisor será exibido.  
  
 Todas as operações pendentes podem ser canceladas com o botão **Cancelar**. Várias seleções podem ser feitas.  
  
> [!NOTE]
>  A maioria dos números não será primo. Se não tiver encontrado um número primo após várias operações concluídas, inicie mais tarefas e, eventualmente, você encontrará alguns números primos.  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/CS/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.AsyncOperationManager/VB/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ComponentModel.AsyncOperation>  
- <xref:System.ComponentModel.AsyncOperationManager>  
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
