---
description: '##line – Referência de C#'
title: '##line – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#line'
helpviewer_keywords:
- '#line directive [C#]'
ms.assetid: 6439e525-5dd5-4acb-b8ea-efabb32ff95b
ms.openlocfilehash: e2a5ecb6c29184123b8a88ae1b12caf24ec7296a
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89137988"
---
# <a name="line-c-reference"></a><span data-ttu-id="6bf23-103">#line (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6bf23-103">#line (C# Reference)</span></span>

<span data-ttu-id="6bf23-104">O `#line` permite modificar o número de linha do compilador e (opcionalmente) a saída do nome de arquivo para erros e avisos.</span><span class="sxs-lookup"><span data-stu-id="6bf23-104">`#line` lets you modify the compiler's line numbering and (optionally) the file name output for errors and warnings.</span></span>

<span data-ttu-id="6bf23-105">O exemplo a seguir mostra como relatar dois avisos associados aos números de linha.</span><span class="sxs-lookup"><span data-stu-id="6bf23-105">The following example shows how to report two warnings associated with line numbers.</span></span> <span data-ttu-id="6bf23-106">A diretiva `#line 200` força o próximo número de linha a ser 200 (embora o padrão seja #6) e, até a próxima diretiva `#line`, o nome de arquivo será relatado como "Special".</span><span class="sxs-lookup"><span data-stu-id="6bf23-106">The `#line 200` directive forces the next line's number to be 200 (although the default is #6), and until the next `#line` directive, the filename will be reported as "Special".</span></span> <span data-ttu-id="6bf23-107">A diretiva `#line default` retorna a numeração de linhas à sua numeração padrão, que conta as linhas que foram renumeradas pela diretiva anterior.</span><span class="sxs-lookup"><span data-stu-id="6bf23-107">The `#line default` directive returns the line numbering to its default numbering, which counts the lines that were renumbered by the previous directive.</span></span>

```csharp
class MainClass
{
    static void Main()
    {
#line 200 "Special"
        int i;
        int j;
#line default
        char c;
        float f;
#line hidden // numbering not affected
        string s;
        double d;
    }
}
```

<span data-ttu-id="6bf23-108">A compilação produz a saída a seguir:</span><span class="sxs-lookup"><span data-stu-id="6bf23-108">Compilation produces the following output:</span></span>

```console
Special(200,13): warning CS0168: The variable 'i' is declared but never used
Special(201,13): warning CS0168: The variable 'j' is declared but never used
MainClass.cs(9,14): warning CS0168: The variable 'c' is declared but never used
MainClass.cs(10,15): warning CS0168: The variable 'f' is declared but never used
MainClass.cs(12,16): warning CS0168: The variable 's' is declared but never used
MainClass.cs(13,16): warning CS0168: The variable 'd' is declared but never used
```

## <a name="remarks"></a><span data-ttu-id="6bf23-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6bf23-109">Remarks</span></span>

<span data-ttu-id="6bf23-110">A diretiva `#line` pode ser usada em uma etapa intermediária e automatizada no processo de build.</span><span class="sxs-lookup"><span data-stu-id="6bf23-110">The `#line` directive might be used in an automated, intermediate step in the build process.</span></span> <span data-ttu-id="6bf23-111">Por exemplo, se linhas fossem removidas do arquivo de código-fonte original, mas você ainda deseja que o compilador gere a saída com base na numeração de linha original no arquivo, seria possível remover as linhas e, em seguida, simular a numeração de linha original com `#line`.</span><span class="sxs-lookup"><span data-stu-id="6bf23-111">For example, if lines were removed from the original source code file, but you still wanted the compiler to generate output based on the original line numbering in the file, you could remove lines and then simulate the original line numbering with `#line`.</span></span>

<span data-ttu-id="6bf23-112">A diretiva `#line hidden` oculta as linhas sucessivas do depurador, de modo que, quando o desenvolvedor percorrer o código, quaisquer linhas entre um `#line hidden` e a próxima diretiva `#line` (supondo que não seja outra diretiva `#line hidden`) serão puladas.</span><span class="sxs-lookup"><span data-stu-id="6bf23-112">The `#line hidden` directive hides the successive lines from the debugger, such that when the developer steps through the code, any lines between a `#line hidden` and the next `#line` directive (assuming that it is not another `#line hidden` directive) will be stepped over.</span></span> <span data-ttu-id="6bf23-113">Essa opção também pode ser usada para permitir que o ASP.NET diferencie entre o código gerado pelo computador e definido pelo usuário.</span><span class="sxs-lookup"><span data-stu-id="6bf23-113">This option can also be used to allow ASP.NET to differentiate between user-defined and machine-generated code.</span></span> <span data-ttu-id="6bf23-114">Embora o ASP.NET seja o principal consumidor desse recurso, é provável que mais geradores de origem façam uso dele.</span><span class="sxs-lookup"><span data-stu-id="6bf23-114">Although ASP.NET is the primary consumer of this feature, it is likely that more source generators will make use of it.</span></span>

<span data-ttu-id="6bf23-115">A diretiva `#line hidden` não afeta os nomes de arquivo ou números de linha nos relatórios de erro.</span><span class="sxs-lookup"><span data-stu-id="6bf23-115">A `#line hidden` directive does not affect file names or line numbers in error reporting.</span></span> <span data-ttu-id="6bf23-116">Ou seja, se um erro for encontrado em um bloco oculto, o compilador reportará o nome do arquivo atual e o número de linha do erro.</span><span class="sxs-lookup"><span data-stu-id="6bf23-116">That is, if an error is encountered in a hidden block, the compiler will report the current file name and line number of the error.</span></span>

<span data-ttu-id="6bf23-117">A diretiva `#line filename` especifica o nome de arquivo que você deseja que seja exibido na saída do compilador.</span><span class="sxs-lookup"><span data-stu-id="6bf23-117">The `#line filename` directive specifies the file name you want to appear in the compiler output.</span></span> <span data-ttu-id="6bf23-118">Por padrão, é usado o nome real do arquivo de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="6bf23-118">By default, the actual name of the source code file is used.</span></span> <span data-ttu-id="6bf23-119">O nome de arquivo deve estar entre aspas duplas ("") e deve ser precedido por um número de linha.</span><span class="sxs-lookup"><span data-stu-id="6bf23-119">The file name must be in double quotation marks ("") and must be preceded by a line number.</span></span>

<span data-ttu-id="6bf23-120">Um arquivo de código-fonte pode ter qualquer número de diretivas `#line`.</span><span class="sxs-lookup"><span data-stu-id="6bf23-120">A source code file can have any number of `#line` directives.</span></span>

## <a name="example-1"></a><span data-ttu-id="6bf23-121">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="6bf23-121">Example 1</span></span>

<span data-ttu-id="6bf23-122">O exemplo a seguir mostra como o depurador ignora as linhas ocultas no código.</span><span class="sxs-lookup"><span data-stu-id="6bf23-122">The following example shows how the debugger ignores the hidden lines in the code.</span></span> <span data-ttu-id="6bf23-123">Quando você executar o exemplo, ele exibirá três linhas de texto.</span><span class="sxs-lookup"><span data-stu-id="6bf23-123">When you run the example, it will display three lines of text.</span></span> <span data-ttu-id="6bf23-124">No entanto, quando você definir um ponto de interrupção, conforme mostrado no exemplo e apertar F10 para percorrer o código, você observará que o depurador ignorará a linha oculta.</span><span class="sxs-lookup"><span data-stu-id="6bf23-124">However, when you set a break point, as shown in the example, and hit F10 to step through the code, you will notice that the debugger ignores the hidden line.</span></span> <span data-ttu-id="6bf23-125">Observe também que, mesmo que você defina um ponto de interrupção na linha oculta, o depurador ainda a ignorará.</span><span class="sxs-lookup"><span data-stu-id="6bf23-125">Notice also that even if you set a break point at the hidden line, the debugger will still ignore it.</span></span>

```csharp
// preprocessor_linehidden.cs
using System;
class MainClass
{
    static void Main()
    {
        Console.WriteLine("Normal line #1."); // Set break point here.
#line hidden
        Console.WriteLine("Hidden line.");
#line default
        Console.WriteLine("Normal line #2.");
    }
}
```

## <a name="see-also"></a><span data-ttu-id="6bf23-126">Confira também</span><span class="sxs-lookup"><span data-stu-id="6bf23-126">See also</span></span>

- [<span data-ttu-id="6bf23-127">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="6bf23-127">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6bf23-128">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="6bf23-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6bf23-129">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="6bf23-129">C# Preprocessor Directives</span></span>](./index.md)
