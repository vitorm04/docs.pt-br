---
title: "Como exibir argumentos de linha de comando (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: cf8a57cce252b3596f0a19c9df643427615467c6
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="99ccb-102">Como exibir argumentos de linha de comando (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="99ccb-102">How to: Display Command Line Arguments (C# Programming Guide)</span></span>
<span data-ttu-id="99ccb-103">Os argumentos fornecidos a um executável na linha de comando são acessíveis por meio de um parâmetro opcional para `Main`.</span><span class="sxs-lookup"><span data-stu-id="99ccb-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="99ccb-104">Os argumentos são fornecidos na forma de uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="99ccb-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="99ccb-105">Cada elemento da matriz contém um argumento.</span><span class="sxs-lookup"><span data-stu-id="99ccb-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="99ccb-106">O espaço em branco entre os argumentos é removido.</span><span class="sxs-lookup"><span data-stu-id="99ccb-106">White-space between arguments is removed.</span></span> <span data-ttu-id="99ccb-107">Por exemplo, considere essas invocações de linha de comando de um executável fictício:</span><span class="sxs-lookup"><span data-stu-id="99ccb-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="99ccb-108">Entrada na linha de comando</span><span class="sxs-lookup"><span data-stu-id="99ccb-108">Input on Command-line</span></span>|<span data-ttu-id="99ccb-109">Matriz de cadeias de caracteres passada a Main</span><span class="sxs-lookup"><span data-stu-id="99ccb-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="99ccb-110">**executável.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="99ccb-110">**executable.exe a b c**</span></span>|<span data-ttu-id="99ccb-111">"a"</span><span class="sxs-lookup"><span data-stu-id="99ccb-111">"a"</span></span><br /><br /> <span data-ttu-id="99ccb-112">"b"</span><span class="sxs-lookup"><span data-stu-id="99ccb-112">"b"</span></span><br /><br /> <span data-ttu-id="99ccb-113">"c"</span><span class="sxs-lookup"><span data-stu-id="99ccb-113">"c"</span></span>|  
|<span data-ttu-id="99ccb-114">**executável.exe um dois**</span><span class="sxs-lookup"><span data-stu-id="99ccb-114">**executable.exe one two**</span></span>|<span data-ttu-id="99ccb-115">"um"</span><span class="sxs-lookup"><span data-stu-id="99ccb-115">"one"</span></span><br /><br /> <span data-ttu-id="99ccb-116">"dois"</span><span class="sxs-lookup"><span data-stu-id="99ccb-116">"two"</span></span>|  
|<span data-ttu-id="99ccb-117">**executável.exe "um dois" três**</span><span class="sxs-lookup"><span data-stu-id="99ccb-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="99ccb-118">“one two”</span><span class="sxs-lookup"><span data-stu-id="99ccb-118">"one two"</span></span><br /><br /> <span data-ttu-id="99ccb-119">"three"</span><span class="sxs-lookup"><span data-stu-id="99ccb-119">"three"</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="99ccb-120">Quando estiver executando um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="99ccb-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99ccb-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="99ccb-121">Example</span></span>  
 <span data-ttu-id="99ccb-122">Este exemplo exibe os argumentos de linha de comando passados a um aplicativo de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="99ccb-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="99ccb-123">A saída mostrada é para a primeira entrada da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="99ccb-123">The output shown is for the first entry in the table above.</span></span>  
  
 <span data-ttu-id="99ccb-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="99ccb-124">[!code-cs[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99ccb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="99ccb-125">See Also</span></span>  
 <span data-ttu-id="99ccb-126">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="99ccb-126">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="99ccb-127">[Compilação de linha de comando com csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span><span class="sxs-lookup"><span data-stu-id="99ccb-127">[Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) </span></span>  
 <span data-ttu-id="99ccb-128">[Main() e argumentos de linha de comando](../../../csharp/programming-guide/main-and-command-args/index.md) </span><span class="sxs-lookup"><span data-stu-id="99ccb-128">[Main() and Command-Line Arguments](../../../csharp/programming-guide/main-and-command-args/index.md) </span></span>  
 <span data-ttu-id="99ccb-129">[Como acessar argumentos de linha de comando usando foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span><span class="sxs-lookup"><span data-stu-id="99ccb-129">[How to: Access Command-Line Arguments Using foreach](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md) </span></span>  
 [<span data-ttu-id="99ccb-130">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="99ccb-130">Main() Return Values</span></span>](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)

