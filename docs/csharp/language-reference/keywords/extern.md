---
title: Modificador extern – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 5f4a4b143578603a3285b1a3bc0b1efa11840e77
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422819"
---
# <a name="extern-c-reference"></a><span data-ttu-id="40ce2-102">extern (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="40ce2-102">extern (C# Reference)</span></span>

<span data-ttu-id="40ce2-103">O modificador `extern` é usado para declarar um método implementado externamente.</span><span class="sxs-lookup"><span data-stu-id="40ce2-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="40ce2-104">Um uso comum do modificador `extern` é com o atributo `DllImport` quando você está usando serviços Interop para chamar código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="40ce2-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="40ce2-105">Nesse caso, o método também deve ser declarado como `static` conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="40ce2-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="40ce2-106">A palavra-chave `extern` também pode definir um alias de assembly externo que possibilita referenciar diferentes versões do mesmo componente de dentro de um único assembly.</span><span class="sxs-lookup"><span data-stu-id="40ce2-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="40ce2-107">Para obter mais informações, consulte [alias externo](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="40ce2-107">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="40ce2-108">É um erro usar os modificadores [abstract](abstract.md) e `extern` juntos para modificar o mesmo membro.</span><span class="sxs-lookup"><span data-stu-id="40ce2-108">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="40ce2-109">Usar o modificador `extern` significa que esse método é implementado fora do código C#, enquanto que usar o modificador `abstract` significa que a implementação do método não é fornecida na classe.</span><span class="sxs-lookup"><span data-stu-id="40ce2-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="40ce2-110">A palavra-chave extern possui utilizações mais limitadas em C# do que em C++.</span><span class="sxs-lookup"><span data-stu-id="40ce2-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="40ce2-111">Para comparar a palavra-chave de C# com a palavra-chave de C++, consulte Usando extern para especificar vínculos na referência da linguagem C++.</span><span class="sxs-lookup"><span data-stu-id="40ce2-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="40ce2-112">Exemplo 1</span><span class="sxs-lookup"><span data-stu-id="40ce2-112">Example 1</span></span>

<span data-ttu-id="40ce2-113">Neste exemplo, o programa recebe uma cadeia de caracteres do usuário e a exibe dentro de uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="40ce2-113">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="40ce2-114">O programa usa o método `MessageBox` importado da biblioteca User32.dll.</span><span class="sxs-lookup"><span data-stu-id="40ce2-114">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="40ce2-115">Exemplo 2</span><span class="sxs-lookup"><span data-stu-id="40ce2-115">Example 2</span></span>

<span data-ttu-id="40ce2-116">Este exemplo ilustra um programa C# que chama uma biblioteca em C (uma DLL nativa).</span><span class="sxs-lookup"><span data-stu-id="40ce2-116">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="40ce2-117">Crie o seguinte arquivo em C e atribua o nome `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="40ce2-117">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="40ce2-118">Abra uma janela do Prompt de Comando de Ferramentas Nativas do Visual Studio x64 (ou x32) do diretório de instalação do Visual Studio e compile o arquivo `cmdll.c` digitando **cl -LD cmdll.c** no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="40ce2-118">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="40ce2-119">No mesmo diretório, crie o seguinte arquivo em C# e atribua o nome `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="40ce2-119">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="40ce2-120">Abra uma janela do Prompt de Comando de Ferramentas Nativas do Visual Studio x64 (ou x32) do diretório de instalação do Visual Studio e compile o arquivo `cm.cs` ao digitar:</span><span class="sxs-lookup"><span data-stu-id="40ce2-120">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="40ce2-121">**csc cm.cs** (para o prompt de comando do x64) – ou – **csc -platform:x86 cm.cs** (para o prompt de comando do x32)</span><span class="sxs-lookup"><span data-stu-id="40ce2-121">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="40ce2-122">Isso criará o arquivo executável `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="40ce2-122">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="40ce2-123">Execute `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="40ce2-123">Run `cm.exe`.</span></span> <span data-ttu-id="40ce2-124">O método `SampleMethod` passa o valor 5 ao arquivo de DLL que retorna o valor multiplicado por 10.</span><span class="sxs-lookup"><span data-stu-id="40ce2-124">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="40ce2-125">O programa produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="40ce2-125">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="40ce2-126">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="40ce2-126">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="40ce2-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="40ce2-127">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="40ce2-128">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="40ce2-128">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="40ce2-129">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="40ce2-129">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="40ce2-130">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="40ce2-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="40ce2-131">Modificadores</span><span class="sxs-lookup"><span data-stu-id="40ce2-131">Modifiers</span></span>](index.md)
