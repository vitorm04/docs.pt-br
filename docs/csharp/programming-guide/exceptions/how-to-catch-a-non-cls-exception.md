---
title: 'Como: Capturar uma exceção não CLS'
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 27b36d85b2ece957c8ef3fce70a6fd794bb3d4e2
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595663"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="35d9a-102">Como: Capturar uma exceção não CLS</span><span class="sxs-lookup"><span data-stu-id="35d9a-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="35d9a-103">Algumas linguagens .NET, incluindo o C++/CLI, permite que os objetos lancem exceções que não derivam de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="35d9a-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="35d9a-104">Essas exceções são chamadas de *exceções não CLS* ou *não exceções*.</span><span class="sxs-lookup"><span data-stu-id="35d9a-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="35d9a-105">Em C#, não é possível gerar exceções que não sejam do CLS, mas você pode capturá-las de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="35d9a-105">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="35d9a-106">Em um bloco `catch (RuntimeWrappedException e)`.</span><span class="sxs-lookup"><span data-stu-id="35d9a-106">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="35d9a-107">Por padrão, um assembly do Visual C# captura exceções não CLS como exceções encapsuladas.</span><span class="sxs-lookup"><span data-stu-id="35d9a-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="35d9a-108">Use este método se você precisar de acesso à exceção original, que pode ser acessada por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35d9a-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="35d9a-109">O procedimento, mais adiante neste tópico, explica como capturar exceções dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="35d9a-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="35d9a-110">Em um bloco de captura geral (um bloco de captura sem um tipo de exceção especificado), que é colocado após todos os outros blocos `catch`.</span><span class="sxs-lookup"><span data-stu-id="35d9a-110">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="35d9a-111">Use esse método quando desejar realizar alguma ação (como gravar em um arquivo de log) em resposta a exceções não CLS e você não precisa de acesso às informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="35d9a-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="35d9a-112">Por padrão, o Common Language Runtime encapsula todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="35d9a-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="35d9a-113">Para desabilitar esse comportamento, adicione esse atributo de nível de assembly em seu código, geralmente no arquivo AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="35d9a-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="35d9a-114">Para capturar uma exceção não CLS</span><span class="sxs-lookup"><span data-stu-id="35d9a-114">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="35d9a-115">Em um bloco `catch(RuntimeWrappedException e)`, acesse a exceção original por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35d9a-115">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35d9a-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="35d9a-116">Example</span></span>  
 <span data-ttu-id="35d9a-117">O exemplo a seguir mostra como capturar uma exceção que não é do CLS, que foi gerada por uma biblioteca de classes escrita em C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="35d9a-117">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="35d9a-118">Observe que, neste exemplo, o código cliente C# sabe com antecedência que o tipo da exceção que está sendo gerada é um <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35d9a-118">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35d9a-119">Você pode converter a propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> de volta a seu tipo original, desde que o tipo seja acessível por meio do código.</span><span class="sxs-lookup"><span data-stu-id="35d9a-119">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
```csharp
// Class library written in C++/CLI.
var myClass = new ThrowNonCLS.Class1();

try
{
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();
}
catch (RuntimeWrappedException e)
{
    String s = e.WrappedException as String;
    if (s != null)
    {
        Console.WriteLine(s);
    }
}
```  
  
## <a name="see-also"></a><span data-ttu-id="35d9a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="35d9a-120">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="35d9a-121">Exceções e manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="35d9a-121">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
