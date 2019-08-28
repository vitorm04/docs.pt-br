---
title: 'Como: Implementar um formulário que usa uma operação em segundo plano'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- components [Windows Forms], asynchronous
- forms [Windows Forms], background operations
- background threads
- threading [Windows Forms], background operations
- background operations
ms.assetid: 9f483f93-1613-4be1-a021-b4934e9c78f3
ms.openlocfilehash: e06b18558f6b3fa3cef47613bbaef16fb7c740f0
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2019
ms.locfileid: "70046198"
---
# <a name="how-to-implement-a-form-that-uses-a-background-operation"></a><span data-ttu-id="162bf-102">Como: Implementar um formulário que usa uma operação em segundo plano</span><span class="sxs-lookup"><span data-stu-id="162bf-102">How to: Implement a Form That Uses a Background Operation</span></span>
<span data-ttu-id="162bf-103">O programa de exemplo a seguir cria um formulário que calcula os números de Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="162bf-103">The following example program creates a form that calculates Fibonacci numbers.</span></span> <span data-ttu-id="162bf-104">O cálculo é executado em um thread separado do thread da interface do usuário, portanto, a interface do usuário continua a ser executada sem atrasos conforme o cálculo continua.</span><span class="sxs-lookup"><span data-stu-id="162bf-104">The calculation runs on a thread that is separate from the user interface thread, so the user interface continues to run without delays as the calculation proceeds.</span></span>  
  
 <span data-ttu-id="162bf-105">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="162bf-105">There is extensive support for this task in Visual Studio.</span></span>  
  
 <span data-ttu-id="162bf-106">Consulte [também o passo a passos: Implementação de um formulário que usa uma operação](walkthrough-implementing-a-form-that-uses-a-background-operation.md)em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="162bf-106">Also see [Walkthrough: Implementing a Form That Uses a Background Operation](walkthrough-implementing-a-form-that-uses-a-background-operation.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="162bf-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="162bf-107">Example</span></span>  
 [!code-cpp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#1)]
 [!code-csharp[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#1)]
 [!code-vb[System.ComponentModel.BackgroundWorker#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="162bf-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="162bf-108">Compiling the Code</span></span>  
 <span data-ttu-id="162bf-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="162bf-109">This example requires:</span></span>  
  
- <span data-ttu-id="162bf-110">Referências aos assemblies System, System.Drawing e System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="162bf-110">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="162bf-111">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="162bf-111">Robust Programming</span></span>  
  
> [!CAUTION]
> <span data-ttu-id="162bf-112">O uso de multithreading de qualquer tipo pode expor o computador a bugs muito sérios e complexos.</span><span class="sxs-lookup"><span data-stu-id="162bf-112">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="162bf-113">Consulte as [Melhores práticas de threading gerenciado](../../../standard/threading/managed-threading-best-practices.md) antes de implementar qualquer solução que use multithreading.</span><span class="sxs-lookup"><span data-stu-id="162bf-113">Consult the [Managed Threading Best Practices](../../../standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="162bf-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="162bf-114">See also</span></span>

- <xref:System.ComponentModel.BackgroundWorker>
- <xref:System.ComponentModel.DoWorkEventArgs>
- [<span data-ttu-id="162bf-115">Visão Geral do Padrão Assíncrono Baseado em Evento</span><span class="sxs-lookup"><span data-stu-id="162bf-115">Event-based Asynchronous Pattern Overview</span></span>](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)
- [<span data-ttu-id="162bf-116">Práticas recomendadas de threading gerenciado</span><span class="sxs-lookup"><span data-stu-id="162bf-116">Managed Threading Best Practices</span></span>](../../../standard/threading/managed-threading-best-practices.md)
