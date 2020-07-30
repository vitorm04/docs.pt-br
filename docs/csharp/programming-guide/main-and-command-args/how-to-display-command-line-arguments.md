---
title: Como exibir argumentos de linha de comando – guia de programação C#
description: Saiba como exibir argumentos de linha de comando. Consulte um exemplo de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 1ac5dc5a5f4e974c9202d2ce23f61071494e1977
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381808"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="8edd1-104">Como exibir argumentos de linha de comando (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="8edd1-104">How to display command-line arguments (C# Programming Guide)</span></span>
<span data-ttu-id="8edd1-105">Os argumentos fornecidos a um executável na linha de comando podem ser acessados por meio de um parâmetro opcional para `Main` .</span><span class="sxs-lookup"><span data-stu-id="8edd1-105">Arguments provided to an executable on the command line are accessible through an optional parameter to `Main`.</span></span> <span data-ttu-id="8edd1-106">Os argumentos são fornecidos na forma de uma matriz de cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="8edd1-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="8edd1-107">Cada elemento da matriz contém um argumento.</span><span class="sxs-lookup"><span data-stu-id="8edd1-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="8edd1-108">O espaço em branco entre os argumentos é removido.</span><span class="sxs-lookup"><span data-stu-id="8edd1-108">White-space between arguments is removed.</span></span> <span data-ttu-id="8edd1-109">Por exemplo, considere essas invocações de linha de comando de um executável fictício:</span><span class="sxs-lookup"><span data-stu-id="8edd1-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="8edd1-110">Entrada na linha de comando</span><span class="sxs-lookup"><span data-stu-id="8edd1-110">Input on command line</span></span>|<span data-ttu-id="8edd1-111">Matriz de cadeias de caracteres passada a Main</span><span class="sxs-lookup"><span data-stu-id="8edd1-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="8edd1-112">**executável.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="8edd1-112">**executable.exe a b c**</span></span>|<span data-ttu-id="8edd1-113">"a"</span><span class="sxs-lookup"><span data-stu-id="8edd1-113">"a"</span></span><br /><br /> <span data-ttu-id="8edd1-114">"b"</span><span class="sxs-lookup"><span data-stu-id="8edd1-114">"b"</span></span><br /><br /> <span data-ttu-id="8edd1-115">"c"</span><span class="sxs-lookup"><span data-stu-id="8edd1-115">"c"</span></span>|  
|<span data-ttu-id="8edd1-116">**executável.exe um dois**</span><span class="sxs-lookup"><span data-stu-id="8edd1-116">**executable.exe one two**</span></span>|<span data-ttu-id="8edd1-117">"um"</span><span class="sxs-lookup"><span data-stu-id="8edd1-117">"one"</span></span><br /><br /> <span data-ttu-id="8edd1-118">"dois"</span><span class="sxs-lookup"><span data-stu-id="8edd1-118">"two"</span></span>|  
|<span data-ttu-id="8edd1-119">**executável.exe "um dois" três**</span><span class="sxs-lookup"><span data-stu-id="8edd1-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="8edd1-120">"one two"</span><span class="sxs-lookup"><span data-stu-id="8edd1-120">"one two"</span></span><br /><br /> <span data-ttu-id="8edd1-121">"three"</span><span class="sxs-lookup"><span data-stu-id="8edd1-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="8edd1-122">Quando estiver executando um aplicativo no Visual Studio, você pode especificar argumentos de linha de comando na [Página de depuração, Designer de Projeto](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="8edd1-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8edd1-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8edd1-123">Example</span></span>  
 <span data-ttu-id="8edd1-124">Este exemplo exibe os argumentos de linha de comando passados para um aplicativo de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="8edd1-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="8edd1-125">A saída mostrada é para a primeira entrada da tabela acima.</span><span class="sxs-lookup"><span data-stu-id="8edd1-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="8edd1-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="8edd1-126">See also</span></span>

- [<span data-ttu-id="8edd1-127">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="8edd1-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="8edd1-128">Compilando pela linha de comando com csc.exe</span><span class="sxs-lookup"><span data-stu-id="8edd1-128">Command-line Building With csc.exe</span></span>](../../language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [<span data-ttu-id="8edd1-129">Argumentos Main () e de linha de comando</span><span class="sxs-lookup"><span data-stu-id="8edd1-129">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="8edd1-130">Valores de retorno de Main()</span><span class="sxs-lookup"><span data-stu-id="8edd1-130">Main() Return Values</span></span>](./main-return-values.md)
