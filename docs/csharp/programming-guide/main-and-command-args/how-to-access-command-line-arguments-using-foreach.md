---
title: "Como acessar argumentos de linha de comando usando foreach (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="d26a6-102">Como acessar argumentos de linha de comando usando foreach (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d26a6-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="d26a6-103">Outra abordagem para iterar na matriz é usar a instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md), conforme mostrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="d26a6-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="d26a6-104">A instrução `foreach` pode ser usada para iterar em uma matriz, em uma classe de coleção do .NET Framework ou em qualquer classe ou struct que implementa a interface <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="d26a6-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d26a6-105">Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="d26a6-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d26a6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d26a6-106">Example</span></span>  
 <span data-ttu-id="d26a6-107">Este exemplo demonstra como imprimir os argumentos de linha de comando usando `foreach`.</span><span class="sxs-lookup"><span data-stu-id="d26a6-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d26a6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d26a6-108">See Also</span></span>  
 <xref:System.Array>  
 <xref:System.Collections>  
 [<span data-ttu-id="d26a6-109">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="d26a6-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [<span data-ttu-id="d26a6-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d26a6-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d26a6-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="d26a6-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="d26a6-112">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="d26a6-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [<span data-ttu-id="d26a6-113">Como exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="d26a6-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [<span data-ttu-id="d26a6-114">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="d26a6-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
