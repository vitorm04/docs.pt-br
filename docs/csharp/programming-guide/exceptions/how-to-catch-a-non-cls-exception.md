---
title: Como capturar uma exceção não compatível com CLS
ms.date: 07/20/2015
helpviewer_keywords:
- exceptions [C#], non-CLS
ms.assetid: db4630b3-5240-471a-b3a7-c7ff6ab31e8d
ms.openlocfilehash: 6169f4b6de2efdfed0dbf43272d708c47b46dbca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33340015"
---
# <a name="how-to-catch-a-non-cls-exception"></a><span data-ttu-id="58d2a-102">Como capturar uma exceção não compatível com CLS</span><span class="sxs-lookup"><span data-stu-id="58d2a-102">How to: Catch a non-CLS Exception</span></span>
<span data-ttu-id="58d2a-103">Algumas linguagens .NET, incluindo o C++/CLI, permite que os objetos lancem exceções que não derivam de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="58d2a-103">Some .NET languages, including C++/CLI, allow objects to throw exceptions that do not derive from <xref:System.Exception>.</span></span> <span data-ttu-id="58d2a-104">Essas exceções são chamadas de *exceções não CLS* ou *não exceções*.</span><span class="sxs-lookup"><span data-stu-id="58d2a-104">Such exceptions are called *non-CLS exceptions* or *non-Exceptions*.</span></span> <span data-ttu-id="58d2a-105">No Visual C# não é possível gerar exceções não CLS, mas você pode capturá-las de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="58d2a-105">In Visual C# you cannot throw non-CLS exceptions, but you can catch them in two ways:</span></span>  
  
-   <span data-ttu-id="58d2a-106">Dentro de um bloco `catch (Exception e)` como uma <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="58d2a-106">Within a `catch (Exception e)` block as a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
     <span data-ttu-id="58d2a-107">Por padrão, um assembly do Visual C# captura exceções não CLS como exceções encapsuladas.</span><span class="sxs-lookup"><span data-stu-id="58d2a-107">By default, a Visual C# assembly catches non-CLS exceptions as wrapped exceptions.</span></span> <span data-ttu-id="58d2a-108">Use este método se você precisar de acesso à exceção original, que pode ser acessada por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.</span><span class="sxs-lookup"><span data-stu-id="58d2a-108">Use this method if you need access to the original exception, which can be accessed through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span> <span data-ttu-id="58d2a-109">O procedimento, mais adiante neste tópico, explica como capturar exceções dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="58d2a-109">The procedure later in this topic explains how to catch exceptions in this manner.</span></span>  
  
-   <span data-ttu-id="58d2a-110">Dentro de um bloco catch geral (um bloco catch sem um tipo de exceção especificado), que é colocado após um bloco `catch (Exception)` ou `catch (Exception e)`.</span><span class="sxs-lookup"><span data-stu-id="58d2a-110">Within a general catch block (a catch block without an exception type specified) that is put after a `catch (Exception)` or `catch (Exception e)` block.</span></span>  
  
     <span data-ttu-id="58d2a-111">Use esse método quando desejar realizar alguma ação (como gravar em um arquivo de log) em resposta a exceções não CLS e você não precisa de acesso às informações de exceção.</span><span class="sxs-lookup"><span data-stu-id="58d2a-111">Use this method when you want to perform some action (such as writing to a log file) in response to non-CLS exceptions, and you do not need access to the exception information.</span></span> <span data-ttu-id="58d2a-112">Por padrão, o Common Language Runtime encapsula todas as exceções.</span><span class="sxs-lookup"><span data-stu-id="58d2a-112">By default the common language runtime wraps all exceptions.</span></span> <span data-ttu-id="58d2a-113">Para desabilitar esse comportamento, adicione esse atributo de nível de assembly em seu código, geralmente no arquivo AssemblyInfo.cs: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span><span class="sxs-lookup"><span data-stu-id="58d2a-113">To disable this behavior, add this assembly-level attribute to your code, typically in the AssemblyInfo.cs file: `[assembly: RuntimeCompatibilityAttribute(WrapNonExceptionThrows = false)]`.</span></span>  
  
### <a name="to-catch-a-non-cls-exception"></a><span data-ttu-id="58d2a-114">Para capturar uma exceção não CLS</span><span class="sxs-lookup"><span data-stu-id="58d2a-114">To catch a non-CLS exception</span></span>  
  
1.  <span data-ttu-id="58d2a-115">Dentro de um `catch(Exception e) block`, use a palavra-chave `as` para testar se `e` pode ser convertido em um <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span><span class="sxs-lookup"><span data-stu-id="58d2a-115">Within a `catch(Exception e) block`, use the `as` keyword to test whether `e` can be cast to a <xref:System.Runtime.CompilerServices.RuntimeWrappedException>.</span></span>  
  
2.  <span data-ttu-id="58d2a-116">Acesse exceção original por meio da propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A>.</span><span class="sxs-lookup"><span data-stu-id="58d2a-116">Access the original exception through the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58d2a-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="58d2a-117">Example</span></span>  
 <span data-ttu-id="58d2a-118">O exemplo a seguir mostra como capturar uma exceção não CLS que foi lançada de uma biblioteca de classes escrita no C++ /CLR.</span><span class="sxs-lookup"><span data-stu-id="58d2a-118">The following example shows how to catch a non-CLS exception that was thrown from a class library written in C++/CLR.</span></span> <span data-ttu-id="58d2a-119">Observe que, neste exemplo, o código do cliente do Visual C# sabe com antecedência que o tipo de exceção que está sendo gerado é um <xref:System.String?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="58d2a-119">Note that in this example, the Visual C# client code knows in advance that the exception type being thrown is a <xref:System.String?displayProperty=nameWithType>.</span></span> <span data-ttu-id="58d2a-120">Você pode converter a propriedade <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> de volta a seu tipo original, desde que o tipo seja acessível por meio do código.</span><span class="sxs-lookup"><span data-stu-id="58d2a-120">You can cast the <xref:System.Runtime.CompilerServices.RuntimeWrappedException.WrappedException%2A> property back its original type as long as that type is accessible from your code.</span></span>  
  
```  
// Class library written in C++/CLR.  
   ThrowNonCLS.Class1 myClass = new ThrowNonCLS.Class1();  
  
   try  
   {  
    // throws gcnew System::String(  
    // "I do not derive from System.Exception!");  
    myClass.TestThrow();   
   }  
  
   catch (Exception e)  
   {  
    RuntimeWrappedException rwe = e as RuntimeWrappedException;  
    if (rwe != null)      
    {  
      String s = rwe.WrappedException as String;  
      if (s != null)  
      {  
        Console.WriteLine(s);  
      }  
    }  
    else  
    {  
       // Handle other System.Exception types.  
    }  
   }             
```  
  
## <a name="see-also"></a><span data-ttu-id="58d2a-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="58d2a-121">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.RuntimeWrappedException>  
 [<span data-ttu-id="58d2a-122">Exceções e manipulação de exceções</span><span class="sxs-lookup"><span data-stu-id="58d2a-122">Exceptions and Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/index.md)
