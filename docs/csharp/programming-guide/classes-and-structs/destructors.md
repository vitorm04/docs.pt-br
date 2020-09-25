---
title: Finalizadores – Guia de Programação em C#
description: Os finalizadores em C#, que também são chamados de destruidores, executam qualquer limpeza final necessária quando uma instância de classe está sendo coletada pelo coletor de lixo.
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 61a00e766b0f975691b9f2a7c7561bb4f1d33c02
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174297"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="c44e5-103">Finalizadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="c44e5-103">Finalizers (C# Programming Guide)</span></span>

<span data-ttu-id="c44e5-104">Os finalizadores (que também são chamados de **destruidores**) são usados para executar qualquer limpeza final necessária, quando uma instância da classe está sendo coletada pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="c44e5-104">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c44e5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="c44e5-105">Remarks</span></span>  
  
- <span data-ttu-id="c44e5-106">Os finalizadores não podem ser definidos em structs.</span><span class="sxs-lookup"><span data-stu-id="c44e5-106">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="c44e5-107">Eles são usados somente com classes.</span><span class="sxs-lookup"><span data-stu-id="c44e5-107">They are only used with classes.</span></span>  
  
- <span data-ttu-id="c44e5-108">Uma classe pode ter somente um finalizador.</span><span class="sxs-lookup"><span data-stu-id="c44e5-108">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="c44e5-109">Os finalizadores não podem ser herdados ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="c44e5-109">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="c44e5-110">Os finalizadores não podem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="c44e5-110">Finalizers cannot be called.</span></span> <span data-ttu-id="c44e5-111">Eles são invocados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="c44e5-111">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="c44e5-112">Um finalizador não usa modificadores ou não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="c44e5-112">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="c44e5-113">Por exemplo, o seguinte é uma declaração de um finalizador para a classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="c44e5-113">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="c44e5-114">Um finalizador também pode ser implementado como uma definição do corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c44e5-114">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="c44e5-115">O finalizador chama implicitamente <xref:System.Object.Finalize%2A> na classe base do objeto.</span><span class="sxs-lookup"><span data-stu-id="c44e5-115">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="c44e5-116">Portanto, uma chamada para um finalizador é convertida implicitamente para o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="c44e5-116">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="c44e5-117">Esse design significa que o `Finalize` método é chamado recursivamente para todas as instâncias na cadeia de herança, do mais derivado para o menos derivado.</span><span class="sxs-lookup"><span data-stu-id="c44e5-117">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c44e5-118">Finalizadores vazios não devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="c44e5-118">Empty finalizers should not be used.</span></span> <span data-ttu-id="c44e5-119">Quando uma classe contém um finalizador, uma entrada é criada na fila `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="c44e5-119">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="c44e5-120">Quando o finalizador é chamado, o coletor de lixo é invocado para processar a fila.</span><span class="sxs-lookup"><span data-stu-id="c44e5-120">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="c44e5-121">Um finalizador vazio apenas resulta na perda de desempenho desnecessária.</span><span class="sxs-lookup"><span data-stu-id="c44e5-121">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="c44e5-122">O programador não tem controle sobre quando o finalizador é chamado; o coletor de lixo decide quando chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="c44e5-122">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="c44e5-123">O coletor de lixo procura objetos que não estão mais sendo usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c44e5-123">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="c44e5-124">Se considerar um objeto qualificado para finalização, ele chamará o finalizador (se houver) e recuperará a memória usada para armazenar o objeto.</span><span class="sxs-lookup"><span data-stu-id="c44e5-124">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="c44e5-125">Em aplicativos .NET Framework (mas não em aplicativos .NET Core), os finalizadores também são chamados quando o programa é encerrado.</span><span class="sxs-lookup"><span data-stu-id="c44e5-125">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="c44e5-126">É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A> , mas, na maioria das vezes, essa chamada deve ser evitada, pois ela pode criar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="c44e5-126">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="c44e5-127">Usar finalizadores para liberar recursos</span><span class="sxs-lookup"><span data-stu-id="c44e5-127">Using finalizers to release resources</span></span>  

 <span data-ttu-id="c44e5-128">Em geral, o C# não exige tanto gerenciamento de memória por parte do desenvolvedor como linguagens que não têm como alvo um tempo de execução com coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="c44e5-128">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="c44e5-129">Isso ocorre porque o coletor de lixo do .NET gerencia implicitamente a alocação e a liberação da memória para seus objetos.</span><span class="sxs-lookup"><span data-stu-id="c44e5-129">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="c44e5-130">No entanto, quando o aplicativo encapsula recursos não gerenciados, como Windows, arquivos e conexões de rede, você deve usar os finalizadores para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="c44e5-130">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="c44e5-131">Quando o objeto está qualificado para finalização, o coletor de lixo executa o método `Finalize` do objeto.</span><span class="sxs-lookup"><span data-stu-id="c44e5-131">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="c44e5-132">Liberação explícita de recursos</span><span class="sxs-lookup"><span data-stu-id="c44e5-132">Explicit release of resources</span></span>  

 <span data-ttu-id="c44e5-133">Se seu aplicativo estiver usando um recurso externo caro, também será recomendável fornecer uma maneira de liberar explicitamente o recurso antes que o coletor de lixo libere o objeto.</span><span class="sxs-lookup"><span data-stu-id="c44e5-133">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="c44e5-134">Para liberar o recurso, implemente um `Dispose` método da <xref:System.IDisposable> interface que executa a limpeza necessária para o objeto.</span><span class="sxs-lookup"><span data-stu-id="c44e5-134">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="c44e5-135">Isso pode melhorar consideravelmente o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="c44e5-135">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="c44e5-136">Mesmo com esse controle explícito sobre os recursos, o finalizador torna-se uma proteção para limpar os recursos se a chamada para o `Dispose` método falhar.</span><span class="sxs-lookup"><span data-stu-id="c44e5-136">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="c44e5-137">Para obter mais informações sobre como limpar recursos, consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="c44e5-137">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="c44e5-138">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="c44e5-138">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="c44e5-139">Implementando um método Dispose</span><span class="sxs-lookup"><span data-stu-id="c44e5-139">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="c44e5-140">Instrução using</span><span class="sxs-lookup"><span data-stu-id="c44e5-140">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="c44e5-141">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c44e5-141">Example</span></span>  

 <span data-ttu-id="c44e5-142">O exemplo a seguir cria três classes que compõem uma cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="c44e5-142">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="c44e5-143">A classe `First` é a classe base, `Second` é derivado de `First` e `Third` é derivado de `Second`.</span><span class="sxs-lookup"><span data-stu-id="c44e5-143">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="c44e5-144">Todas as três têm finalizadores.</span><span class="sxs-lookup"><span data-stu-id="c44e5-144">All three have finalizers.</span></span> <span data-ttu-id="c44e5-145">Em `Main`, uma instância da classe mais derivada é criada.</span><span class="sxs-lookup"><span data-stu-id="c44e5-145">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="c44e5-146">Quando o programa for executado, observe que os finalizadores das três classes são chamados automaticamente e em ordem, do mais derivado para o menos derivado.</span><span class="sxs-lookup"><span data-stu-id="c44e5-146">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c44e5-147">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="c44e5-147">C# language specification</span></span>  

<span data-ttu-id="c44e5-148">Para obter mais informações, confira a seção [Destruidores](~/_csharplang/spec/classes.md#destructors) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="c44e5-148">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="c44e5-149">Confira também</span><span class="sxs-lookup"><span data-stu-id="c44e5-149">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="c44e5-150">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="c44e5-150">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c44e5-151">Construtores</span><span class="sxs-lookup"><span data-stu-id="c44e5-151">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="c44e5-152">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="c44e5-152">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
