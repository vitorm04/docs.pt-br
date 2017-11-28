---
title: "extern (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 106ceb6a4acf57daa01919acb38e4245655fca2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="extern-c-reference"></a><span data-ttu-id="43d64-102">extern (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="43d64-102">extern (C# Reference)</span></span>
<span data-ttu-id="43d64-103">O modificador `extern` é usado para declarar um método implementado externamente.</span><span class="sxs-lookup"><span data-stu-id="43d64-103">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="43d64-104">Um uso comum do modificador `extern` é com o atributo `DllImport` quando você está usando serviços Interop para chamar código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="43d64-104">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="43d64-105">Nesse caso, o método também deve ser declarado como `static` conforme mostrado no seguinte exemplo:</span><span class="sxs-lookup"><span data-stu-id="43d64-105">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>  
  
```  
[DllImport("avifil32.dll")]  
private static extern void AVIFileInit();  
```  
  
 <span data-ttu-id="43d64-106">A palavra-chave `extern` também pode definir um alias de assembly externo que possibilita referenciar diferentes versões do mesmo componente de dentro de um único assembly.</span><span class="sxs-lookup"><span data-stu-id="43d64-106">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="43d64-107">Para obter mais informações, consulte [alias extern](../../../csharp/language-reference/keywords/extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="43d64-107">For more information, see [extern alias](../../../csharp/language-reference/keywords/extern-alias.md).</span></span>  
  
 <span data-ttu-id="43d64-108">É um erro usar os modificadores [abstract](../../../csharp/language-reference/keywords/abstract.md) e `extern` juntos para modificar o mesmo membro.</span><span class="sxs-lookup"><span data-stu-id="43d64-108">It is an error to use the [abstract](../../../csharp/language-reference/keywords/abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="43d64-109">Usar o modificador `extern` significa que esse método é implementado fora do código C#, enquanto que usar o modificador `abstract` significa que a implementação do método não é fornecida na classe.</span><span class="sxs-lookup"><span data-stu-id="43d64-109">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>  
  
 <span data-ttu-id="43d64-110">A palavra-chave extern possui utilizações mais limitadas em C# do que em C++.</span><span class="sxs-lookup"><span data-stu-id="43d64-110">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="43d64-111">Para comparar a palavra-chave de C# com a palavra-chave de C++, consulte Usando extern para especificar vínculos na referência da linguagem C++.</span><span class="sxs-lookup"><span data-stu-id="43d64-111">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>  
  
## <a name="example"></a><span data-ttu-id="43d64-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43d64-112">Example</span></span>  
 <span data-ttu-id="43d64-113">**Exemplo 1.**</span><span class="sxs-lookup"><span data-stu-id="43d64-113">**Example 1.**</span></span> <span data-ttu-id="43d64-114">Neste exemplo, o programa recebe uma cadeia de caracteres do usuário e a exibe dentro de uma caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="43d64-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="43d64-115">O programa usa o método `MessageBox` importado da biblioteca User32.dll.</span><span class="sxs-lookup"><span data-stu-id="43d64-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/extern_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="43d64-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43d64-116">Example</span></span>  
 <span data-ttu-id="43d64-117">**Exemplo 2.**</span><span class="sxs-lookup"><span data-stu-id="43d64-117">**Example 2.**</span></span> <span data-ttu-id="43d64-118">Este exemplo ilustra um programa C# que chama uma biblioteca em C (uma DLL nativa).</span><span class="sxs-lookup"><span data-stu-id="43d64-118">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>  
  
 1. <span data-ttu-id="43d64-119">Crie o seguinte arquivo em C e atribua o nome `cmdll.c`:</span><span class="sxs-lookup"><span data-stu-id="43d64-119">Create the following C file and name it `cmdll.c`:</span></span>  
  
```  
// cmdll.c  
// Compile with: /LD  
int __declspec(dllexport) SampleMethod(int i)  
{  
   return i*10;  
}  
```  
  
## <a name="example"></a><span data-ttu-id="43d64-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43d64-120">Example</span></span>  
 2. <span data-ttu-id="43d64-121">Abra uma janela do Prompt de Comando de Ferramentas Nativas do Visual Studio x64 (ou x32) do diretório de instalação do Visual Studio e compile o arquivo `cmdll.c` digitando **cl /LD cmdll.c** no prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="43d64-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl /LD cmdll.c** at the command prompt.</span></span>  
  
 3. <span data-ttu-id="43d64-122">No mesmo diretório, crie o seguinte arquivo em C# e atribua o nome `cm.cs`:</span><span class="sxs-lookup"><span data-stu-id="43d64-122">In the same directory, create the following C# file and name it `cm.cs`:</span></span>  
  
```  
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
  
## <a name="example"></a><span data-ttu-id="43d64-123">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43d64-123">Example</span></span>  
 3. <span data-ttu-id="43d64-124">Abra uma janela do Prompt de Comando de Ferramentas Nativas do Visual Studio x64 (ou x32) do diretório de instalação do Visual Studio e compile o arquivo `cm.cs` ao digitar:</span><span class="sxs-lookup"><span data-stu-id="43d64-124">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>  
  
> <span data-ttu-id="43d64-125">**csc cm.cs** (para o prompt de comando x64)</span><span class="sxs-lookup"><span data-stu-id="43d64-125">**csc cm.cs** (for the x64 command prompt)</span></span>   
>  <span data-ttu-id="43d64-126">—ou—</span><span class="sxs-lookup"><span data-stu-id="43d64-126">—or—</span></span>  
> <span data-ttu-id="43d64-127">**csc /platform:x86 cm.cs** (para o prompt de comando x32)</span><span class="sxs-lookup"><span data-stu-id="43d64-127">**csc /platform:x86 cm.cs** (for the x32 command prompt)</span></span>  
  
 <span data-ttu-id="43d64-128">Isso criará o arquivo executável `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="43d64-128">This will create the executable file `cm.exe`.</span></span>  
  
 4. <span data-ttu-id="43d64-129">Execute `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="43d64-129">Run `cm.exe`.</span></span> <span data-ttu-id="43d64-130">O método `SampleMethod` passa o valor 5 ao arquivo de DLL que retorna o valor multiplicado por 10.</span><span class="sxs-lookup"><span data-stu-id="43d64-130">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="43d64-131">O programa produz a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="43d64-131">The program produces the following output:</span></span>  
  
```  
SampleMethod() returns 50.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="43d64-132">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="43d64-132">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="43d64-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43d64-133">See Also</span></span>  
 <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>  
 [<span data-ttu-id="43d64-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="43d64-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="43d64-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="43d64-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="43d64-136">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="43d64-136">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="43d64-137">Modificadores</span><span class="sxs-lookup"><span data-stu-id="43d64-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)
