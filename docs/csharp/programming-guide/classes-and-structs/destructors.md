---
title: "Finalizadores (Guia de Programação em C#)"
ms.date: 2017-05-10
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
caps.latest.revision: 24
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
ms.openlocfilehash: 43bb7e6488da5eda863e7ad70b25c9bf55bebb52
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="ebc3f-102">Finalizadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="ebc3f-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="ebc3f-103">Finalizadores são usados para destruir instâncias de classes.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-103">Finalizers are used to destruct instances of classes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ebc3f-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="ebc3f-104">Remarks</span></span>  
  
-   <span data-ttu-id="ebc3f-105">Os finalizadores não podem ser definidos em structs.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="ebc3f-106">Eles são usados somente com classes.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-106">They are only used with classes.</span></span>  
  
-   <span data-ttu-id="ebc3f-107">Uma classe pode ter somente um finalizador.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-107">A class can only have one finalizer.</span></span>  
  
-   <span data-ttu-id="ebc3f-108">Os finalizadores não podem ser herdados ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
-   <span data-ttu-id="ebc3f-109">Os finalizadores não podem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-109">Finalizers cannot be called.</span></span> <span data-ttu-id="ebc3f-110">Eles são invocados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-110">They are invoked automatically.</span></span>  
  
-   <span data-ttu-id="ebc3f-111">Um finalizador não usa modificadores ou não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="ebc3f-112">Por exemplo, o seguinte é uma declaração de um finalizador para a classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 <span data-ttu-id="ebc3f-113">[!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc3f-113">[!code-cs[csProgGuideObjects#86](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_1.cs)]</span></span>  

<span data-ttu-id="ebc3f-114">Um finalizador também pode ser implementado como uma definição do corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

<span data-ttu-id="ebc3f-115">[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]</span><span class="sxs-lookup"><span data-stu-id="ebc3f-115">[!code-cs[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]</span></span>  
  
 <span data-ttu-id="ebc3f-116">O finalizador chama implicitamente <xref:System.Object.Finalize%2A> na classe base do objeto.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-116">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="ebc3f-117">Portanto, uma chamada para um finalizador é convertida implicitamente para o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="ebc3f-117">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
```csharp  
protected override void Finalize()  
{  
    try  
    {  
        // Cleanup statements...  
    }  
    finally  
    {  
        base.Finalize();  
    }  
}  
```  
  
 <span data-ttu-id="ebc3f-118">Isso significa que o método `Finalize` é chamado de forma recursiva para todas as instâncias da cadeia de herança, da mais derivada à menos derivada.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-118">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ebc3f-119">Finalizadores vazios não devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-119">Empty finalizers should not be used.</span></span> <span data-ttu-id="ebc3f-120">Quando uma classe contém um finalizador, uma entrada é criada na fila `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-120">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="ebc3f-121">Quando o finalizador é chamado, o coletor de lixo é invocado para processar a fila.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-121">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="ebc3f-122">Um finalizador vazio apenas resulta na perda de desempenho desnecessária.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-122">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="ebc3f-123">O programador não tem controle sobre quando o finalizador é chamado porque isso é determinado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-123">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="ebc3f-124">O coletor de lixo procura objetos que não estão mais sendo usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-124">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="ebc3f-125">Se considerar um objeto qualificado para finalização, ele chamará o finalizador (se houver) e recuperará a memória usada para armazenar o objeto.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-125">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> <span data-ttu-id="ebc3f-126">Os finalizadores também são chamados quando o programa é encerrado.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-126">Finalizers are also called when the program exits.</span></span>  
  
 <span data-ttu-id="ebc3f-127">É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A>, mas na maioria das vezes, isso deve ser evitado porque pode criar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-127">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="ebc3f-128">Usando finalizadores para liberar recursos</span><span class="sxs-lookup"><span data-stu-id="ebc3f-128">Using Finalizers to Release Resources</span></span>  
 <span data-ttu-id="ebc3f-129">Em geral, o C# não demanda tanto gerenciamento de memória quanto é necessário quando você desenvolve usando uma linguagem que não tem como destino um tempo de execução com coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-129">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="ebc3f-130">Isso ocorre porque o coletor de lixo do .NET Framework gerencia implicitamente a alocação e a liberação de memória para seus objetos.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-130">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="ebc3f-131">No entanto, quando seu aplicativo encapsula recursos não gerenciados, como janelas, arquivos e conexões de rede, você deve usar finalizadores para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-131">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="ebc3f-132">Quando o objeto está qualificado para finalização, o coletor de lixo executa o método `Finalize` do objeto.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-132">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="ebc3f-133">Liberação explícita de recursos</span><span class="sxs-lookup"><span data-stu-id="ebc3f-133">Explicit Release of Resources</span></span>  
 <span data-ttu-id="ebc3f-134">Se seu aplicativo estiver usando um recurso externo caro, também será recomendável fornecer uma maneira de liberar explicitamente o recurso antes que o coletor de lixo libere o objeto.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-134">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="ebc3f-135">Você faz isso implementando um método `Dispose` da interface <xref:System.IDisposable> que executa a limpeza necessária para o objeto.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-135">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="ebc3f-136">Isso pode melhorar consideravelmente o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-136">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="ebc3f-137">Mesmo com esse controle explícito sobre os recursos, o finalizador se tornará uma proteção usada para limpar os recursos se a chamada para o método `Dispose` falhar.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-137">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="ebc3f-138">Para obter mais detalhes sobre limpeza de recursos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="ebc3f-138">For more details about cleaning up resources, see the following topics:</span></span>  
  
-   [<span data-ttu-id="ebc3f-139">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="ebc3f-139">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
-   [<span data-ttu-id="ebc3f-140">Implementando um método dispose</span><span class="sxs-lookup"><span data-stu-id="ebc3f-140">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
-   [<span data-ttu-id="ebc3f-141">Instrução using</span><span class="sxs-lookup"><span data-stu-id="ebc3f-141">using Statement</span></span>](../../../csharp/language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="ebc3f-142">Exemplo</span><span class="sxs-lookup"><span data-stu-id="ebc3f-142">Example</span></span>  
 <span data-ttu-id="ebc3f-143">O exemplo a seguir cria três classes que compõem uma cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-143">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="ebc3f-144">A classe `First` é a classe base, `Second` é derivado de `First` e `Third` é derivado de `Second`.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-144">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="ebc3f-145">Todas as três têm finalizadores.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-145">All three have finalizers.</span></span> <span data-ttu-id="ebc3f-146">Em `Main`, uma instância da classe mais derivada é criada.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-146">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="ebc3f-147">Quando o programa for executado, observe que os finalizadores das três classes são chamados automaticamente e em ordem, do mais derivado para o menos derivado.</span><span class="sxs-lookup"><span data-stu-id="ebc3f-147">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 <span data-ttu-id="ebc3f-148">[!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="ebc3f-148">[!code-cs[csProgGuideObjects#85](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/destructors_2.cs)]</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ebc3f-149">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="ebc3f-149">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ebc3f-150">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebc3f-150">See Also</span></span>  
 <span data-ttu-id="ebc3f-151"><xref:System.IDisposable></span><span class="sxs-lookup"><span data-stu-id="ebc3f-151"><xref:System.IDisposable></span></span>   
 <span data-ttu-id="ebc3f-152">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="ebc3f-152">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="ebc3f-153">[Construtores](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span><span class="sxs-lookup"><span data-stu-id="ebc3f-153">[Constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md) </span></span>  
 [<span data-ttu-id="ebc3f-154">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="ebc3f-154">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)

