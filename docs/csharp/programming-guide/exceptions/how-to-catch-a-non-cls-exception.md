---
title: Como capturar uma exceção não compatível com CLS
description: Saiba como capturar uma exceção não-CLS. Consulte um exemplo de código e exiba recursos adicionais disponíveis.
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: db723cb1e29181e9462c5b423c66cdf8de659259
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178665"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="5f8a7-104">Como capturar uma exceção não compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="5f8a7-104">How to catch a non-CLS exception</span></span>

<span data-ttu-id="5f8a7-105">Algumas linguagens .NET, incluindo o C++/CLI, permite que os objetos lancem exceções que não derivam de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-105">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="5f8a7-106">Essas exceções são chamadas de *exceções não CLS* ou *não exceções*.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-106">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="5f8a7-107">Em C#, não é possível gerar exceções que não sejam do CLS, mas você pode capturá-las de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="5f8a7-107">In C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
- <span data-ttu-id="5f8a7-108">Em um bloco `catch (RuntimeWrappedException e)`.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-108">Within a `catch (RuntimeWrappedException e)` block.</span></span>
  
     <span data-ttu-id="5f8a7-109">Por padrão, um assembly do Visual C# captura exceções não CLS como exceções encapsuladas.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-109">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="5f8a7-110">Use este método se você precisar de acesso à exceção original, que pode ser acessada por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-110">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5f8a7-111">O procedimento, mais adiante neste tópico, explica como capturar exceções dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-111">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
- <span data-ttu-id="5f8a7-112">Em um bloco de captura geral (um bloco de captura sem um tipo de exceção especificado), que é colocado após todos os outros blocos `catch`.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-112">Within a general catch block (a catch block without an exception type specified) that is put after all other `catch` blocks.</span></span>
  
     <span data-ttu-id="5f8a7-113">Use esse método quando desejar realizar alguma ação (como gravar em um arquivo de log) em resposta a exceções não CLS e você não precisa de acesso às informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-113">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="5f8a7-114">Por padrão, o Common Language Runtime encapsula todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-114">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="5f8a7-115">Para desabilitar esse comportamento, adicione esse atributo de nível de assembly em seu código, geralmente no arquivo AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-115">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="5f8a7-116">Para capturar uma exceção não CLS</span><span class="sxs-lookup"><span data-stu-id="5f8a7-116">To catch a non-CLS exception</span></span>  
  
<span data-ttu-id="5f8a7-117">Em um bloco `catch(RuntimeWrappedException e)`, acesse a exceção original por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-117">Within a `catch(RuntimeWrappedException e)` block, access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f8a7-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5f8a7-118">Example</span></span>  

 <span data-ttu-id="5f8a7-119">O exemplo a seguir mostra como capturar uma exceção que não é do CLS, que foi gerada por uma biblioteca de classes escrita em C++/CLI.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-119">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLI.</span></span> <span data-ttu-id="5f8a7-120">Observe que, neste exemplo, o código cliente C# sabe com antecedência que o tipo da exceção que está sendo gerada é um <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-120">Note that in this example, the C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5f8a7-121">Você pode converter a propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> de volta a seu tipo original, desde que o tipo seja acessível por meio do código.</span><span class="sxs-lookup"><span data-stu-id="5f8a7-121">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A?displayProperty=nameWithType> property back its original type as long as that type is accessible from your code.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5f8a7-122">Veja também</span><span class="sxs-lookup"><span data-stu-id="5f8a7-122">See also</span></span>

- <xref:System.Runtime.CompilerServices.RuntimeWrappedException>
- [<span data-ttu-id="5f8a7-123">Exceções e manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="5f8a7-123">Exceptions and Exception Handling</span></span>](./index.md)
