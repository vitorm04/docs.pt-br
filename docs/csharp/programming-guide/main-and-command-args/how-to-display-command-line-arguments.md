---
title: Como exibir argumentos de linha de comando C# – guia de programação
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 3ae2f65696c6661ab4f732b604267116996162b2
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635165"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="de1f9-102">Como exibir argumentos de linha de comandoC# (guia de programação)</span><span class="sxs-lookup"><span data-stu-id="de1f9-102">How to display command line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="de1f9-103">Os argumentos fornecidos a um executável na linha de comando são acessíveis por meio de um parâmetro opcional para `Main`.</span><span class="sxs-lookup"><span data-stu-id="de1f9-103">Arguments provided to an executable on the command-line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="de1f9-104">Os argumentos são fornecidos na forma de uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="de1f9-104">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="de1f9-105">Cada elemento da matriz contém um argumento.</span><span class="sxs-lookup"><span data-stu-id="de1f9-105">Each element of the array contains one argument.</span></span> <span data-ttu-id="de1f9-106">O espaço em branco entre os argumentos é removido.</span><span class="sxs-lookup"><span data-stu-id="de1f9-106">White-space between arguments is removed.</span></span> <span data-ttu-id="de1f9-107">Por exemplo, considere essas invocações de linha de comando de um executável fictício:</span><span class="sxs-lookup"><span data-stu-id="de1f9-107">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="de1f9-108">Entrada na linha de comando</span><span class="sxs-lookup"><span data-stu-id="de1f9-108">Input on Command-line</span></span>|<span data-ttu-id="de1f9-109">Matriz de cadeias de caracteres passada a Main</span><span class="sxs-lookup"><span data-stu-id="de1f9-109">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="de1f9-110">**executável.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="de1f9-110">**executable.exe a b c**</span></span>|<span data-ttu-id="de1f9-111">"a"</span><span class="sxs-lookup"><span data-stu-id="de1f9-111">"a"</span></span><br /><br /> <span data-ttu-id="de1f9-112">"b"</span><span class="sxs-lookup"><span data-stu-id="de1f9-112">"b"</span></span><br /><br /> <span data-ttu-id="de1f9-113">"c"</span><span class="sxs-lookup"><span data-stu-id="de1f9-113">"c"</span></span>|  
|<span data-ttu-id="de1f9-114">**executável.exe um dois**</span><span class="sxs-lookup"><span data-stu-id="de1f9-114">**executable.exe one two**</span></span>|<span data-ttu-id="de1f9-115">"um"</span><span class="sxs-lookup"><span data-stu-id="de1f9-115">"one"</span></span><br /><br /> <span data-ttu-id="de1f9-116">"dois"</span><span class="sxs-lookup"><span data-stu-id="de1f9-116">"two"</span></span>|  
|<span data-ttu-id="de1f9-117">**executável.exe "um dois" três**</span><span class="sxs-lookup"><span data-stu-id="de1f9-117">**executable.exe "one two" three**</span></span>|<span data-ttu-id="de1f9-118">"one two"</span><span class="sxs-lookup"><span data-stu-id="de1f9-118">"one two"</span></span><br /><br /> <span data-ttu-id="de1f9-119">"three"</span><span class="sxs-lookup"><span data-stu-id="de1f9-119">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="de1f9-120">Quando estiver executando um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="de1f9-120">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="de1f9-121">Exemplo</span><span class="sxs-lookup"><span data-stu-id="de1f9-121">Example</span></span>  
 <span data-ttu-id="de1f9-122">Este exemplo exibe os argumentos de linha de comando passados a um aplicativo de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="de1f9-122">This example displays the command line arguments passed to a command-line application.</span></span> <span data-ttu-id="de1f9-123">A saída mostrada é para a primeira entrada da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="de1f9-123">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="de1f9-124">Veja também</span><span class="sxs-lookup"><span data-stu-id="de1f9-124">See also</span></span>

- [<span data-ttu-id="de1f9-125">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="de1f9-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="de1f9-126">Build pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="de1f9-126">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="de1f9-127">Main() e argumentos de linha de comando</span><span class="sxs-lookup"><span data-stu-id="de1f9-127">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="de1f9-128">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="de1f9-128">Main() Return Values</span></span>](./main-return-values.md)
