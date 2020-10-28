---
title: 'Como: Implementar um cliente do padrão assíncrono baseado em evento'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET], asynchronous features
- components [.NET], asynchronous
- AsyncOperation class
- threading [Windows Forms], asynchronous features
- AsyncCompletedEventArgs class
ms.assetid: 21a858c1-3c99-4904-86ee-0d17b49804fa
ms.openlocfilehash: 95997f219a08c131905cfc86b78e94c36f3ec851
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888809"
---
# <a name="how-to-implement-a-client-of-the-event-based-asynchronous-pattern"></a><span data-ttu-id="88c2c-102">Como: Implementar um cliente do padrão assíncrono baseado em evento</span><span class="sxs-lookup"><span data-stu-id="88c2c-102">How to: Implement a Client of the Event-based Asynchronous Pattern</span></span>
<span data-ttu-id="88c2c-103">O código a seguir descreve como usar um componente que respeita a [Visão geral do Padrão assíncrono baseado em evento](event-based-asynchronous-pattern-overview.md).</span><span class="sxs-lookup"><span data-stu-id="88c2c-103">The following code example demonstrates how to use a component that adheres to the [Event-based Asynchronous Pattern Overview](event-based-asynchronous-pattern-overview.md).</span></span> <span data-ttu-id="88c2c-104">O formulário desse exemplo usa o componente `PrimeNumberCalculator` descrito em [Como: implementar um componente compatível com o Padrão assíncrono baseado em evento](component-that-supports-the-event-based-asynchronous-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="88c2c-104">The form for this example uses the `PrimeNumberCalculator` component described in [How to: Implement a Component That Supports the Event-based Asynchronous Pattern](component-that-supports-the-event-based-asynchronous-pattern.md).</span></span>  
  
 <span data-ttu-id="88c2c-105">Quando você executa um projeto que usa este exemplo, você verá um formulário de "Calculadora de números primos" com uma grade e dois botões: **Iniciar Nova Tarefa** e **Cancelar** .</span><span class="sxs-lookup"><span data-stu-id="88c2c-105">When you run a project that uses this example, you will see a "Prime Number Calculator" form with a grid and two buttons: **Start New Task** and **Cancel** .</span></span> <span data-ttu-id="88c2c-106">Você pode clicar no botão **Iniciar Nova Tarefa** várias vezes consecutivas e, para cada clique, uma operação assíncrona iniciará uma computação para determinar se um número gerado aleatoriamente é primo.</span><span class="sxs-lookup"><span data-stu-id="88c2c-106">You can click the **Start New Task** button several times in succession, and for each click, an asynchronous operation will begin a computation to determine if a randomly generated test number is prime.</span></span> <span data-ttu-id="88c2c-107">O formulário exibirá periodicamente o progresso e os resultados incrementais.</span><span class="sxs-lookup"><span data-stu-id="88c2c-107">The form will periodically display progress and incremental results.</span></span> <span data-ttu-id="88c2c-108">Cada operação recebe uma ID de tarefa exclusiva.</span><span class="sxs-lookup"><span data-stu-id="88c2c-108">Each operation is assigned a unique task ID.</span></span> <span data-ttu-id="88c2c-109">O resultado da computação é exibido na coluna **Resultado** . Se o número do teste não for primo, ele será rotulado como **Composto** e seu primeiro divisor será exibido.</span><span class="sxs-lookup"><span data-stu-id="88c2c-109">The result of the computation is displayed in the **Result** column; if the test number is not prime, it is labeled as **Composite,** and its first divisor is displayed.</span></span>  
  
 <span data-ttu-id="88c2c-110">Todas as operações pendentes podem ser canceladas com o botão **Cancelar** .</span><span class="sxs-lookup"><span data-stu-id="88c2c-110">Any pending operation can be canceled with the **Cancel** button.</span></span> <span data-ttu-id="88c2c-111">Várias seleções podem ser feitas.</span><span class="sxs-lookup"><span data-stu-id="88c2c-111">Multiple selections can be made.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="88c2c-112">A maioria dos números não será primo.</span><span class="sxs-lookup"><span data-stu-id="88c2c-112">Most numbers will not be prime.</span></span> <span data-ttu-id="88c2c-113">Se não tiver encontrado um número primo após várias operações concluídas, inicie mais tarefas e, eventualmente, você encontrará alguns números primos.</span><span class="sxs-lookup"><span data-stu-id="88c2c-113">If you have not found a prime number after several completed operations, simply start more tasks, and eventually you will find some prime numbers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88c2c-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88c2c-114">Example</span></span>  
 [!code-csharp[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/csharp/primenumbercalculatormain.cs#10)]
 [!code-vb[System.ComponentModel.AsyncOperationManager#10](snippets/component-that-supports-the-event-based-asynchronous-pattern/vb/primenumbercalculatormain.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="88c2c-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="88c2c-115">See also</span></span>

- <xref:System.ComponentModel.AsyncOperation>
- <xref:System.ComponentModel.AsyncOperationManager>
- <xref:System.Windows.Forms.WindowsFormsSynchronizationContext>
