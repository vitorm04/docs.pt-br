---
title: Como acessar argumentos de linha de comando usando foreach (Guia de Programação em C#)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 811ee09aec7afac70f3f2c2fe5fb002232935028
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43511330"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a><span data-ttu-id="4c9d6-102">Como acessar argumentos de linha de comando usando foreach (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="4c9d6-102">How to: Access Command-Line Arguments Using foreach (C# Programming Guide)</span></span>
<span data-ttu-id="4c9d6-103">Outra abordagem para iterar na matriz é usar a instrução [foreach](../../../csharp/language-reference/keywords/foreach-in.md), conforme mostrado neste exemplo.</span><span class="sxs-lookup"><span data-stu-id="4c9d6-103">Another approach to iterating over the array is to use the [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement as shown in this example.</span></span> <span data-ttu-id="4c9d6-104">A instrução `foreach` pode ser usada para iterar em uma matriz, em uma classe de coleção do .NET Framework ou em qualquer classe ou struct que implementa a interface <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="4c9d6-104">The `foreach` statement can be used to iterate over an array, a .NET Framework collection class, or any class or struct that implements the <xref:System.Collections.IEnumerable> interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4c9d6-105">Ao executar um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="4c9d6-105">When running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c9d6-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4c9d6-106">Example</span></span>  
 <span data-ttu-id="4c9d6-107">Este exemplo demonstra como imprimir os argumentos de linha de comando usando `foreach`.</span><span class="sxs-lookup"><span data-stu-id="4c9d6-107">This example demonstrates how to print out the command line arguments using `foreach`.</span></span>  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4c9d6-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c9d6-108">See Also</span></span>

- <xref:System.Array>  
- <xref:System.Collections>  
- [<span data-ttu-id="4c9d6-109">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="4c9d6-109">Command-line Building With csc.exe</span></span>](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
- [<span data-ttu-id="4c9d6-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4c9d6-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4c9d6-111">foreach, in</span><span class="sxs-lookup"><span data-stu-id="4c9d6-111">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
- [<span data-ttu-id="4c9d6-112">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="4c9d6-112">Main() and Command-Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/index.md)  
- [<span data-ttu-id="4c9d6-113">Como exibir argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="4c9d6-113">How to: Display Command Line Arguments</span></span>](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
- [<span data-ttu-id="4c9d6-114">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="4c9d6-114">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
