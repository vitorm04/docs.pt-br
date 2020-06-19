---
title: Finalizadores – Guia de Programação em C#
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 62fc531a8064a8a5cb144a89aa9975b3199db976
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/18/2020
ms.locfileid: "84990109"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="7b7dc-102">Finalizadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="7b7dc-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="7b7dc-103">Os finalizadores (que também são chamados de **destruidores**) são usados para executar qualquer limpeza final necessária, quando uma instância da classe está sendo coletada pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b7dc-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b7dc-104">Remarks</span></span>  
  
- <span data-ttu-id="7b7dc-105">Os finalizadores não podem ser definidos em structs.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="7b7dc-106">Eles são usados somente com classes.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="7b7dc-107">Uma classe pode ter somente um finalizador.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="7b7dc-108">Os finalizadores não podem ser herdados ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="7b7dc-109">Os finalizadores não podem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-109">Finalizers cannot be called.</span></span> <span data-ttu-id="7b7dc-110">Eles são invocados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="7b7dc-111">Um finalizador não usa modificadores ou não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="7b7dc-112">Por exemplo, o seguinte é uma declaração de um finalizador para a classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="7b7dc-113">Um finalizador também pode ser implementado como uma definição do corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="7b7dc-114">O finalizador chama implicitamente <xref:System.Object.Finalize%2A> na classe base do objeto.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="7b7dc-115">Portanto, uma chamada para um finalizador é convertida implicitamente para o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7b7dc-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="7b7dc-116">Esse design significa que o `Finalize` método é chamado recursivamente para todas as instâncias na cadeia de herança, do mais derivado para o menos derivado.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-116">This design means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b7dc-117">Finalizadores vazios não devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="7b7dc-118">Quando uma classe contém um finalizador, uma entrada é criada na fila `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="7b7dc-119">Quando o finalizador é chamado, o coletor de lixo é invocado para processar a fila.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="7b7dc-120">Um finalizador vazio apenas resulta na perda de desempenho desnecessária.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="7b7dc-121">O programador não tem controle sobre quando o finalizador é chamado; o coletor de lixo decide quando chamá-lo.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-121">The programmer has no control over when the finalizer is called; the garbage collector decides when to call it.</span></span> <span data-ttu-id="7b7dc-122">O coletor de lixo procura objetos que não estão mais sendo usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="7b7dc-123">Se considerar um objeto qualificado para finalização, ele chamará o finalizador (se houver) e recuperará a memória usada para armazenar o objeto.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span>

 <span data-ttu-id="7b7dc-124">Em aplicativos .NET Framework (mas não em aplicativos .NET Core), os finalizadores também são chamados quando o programa é encerrado.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span>
  
 <span data-ttu-id="7b7dc-125">É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A> , mas, na maioria das vezes, essa chamada deve ser evitada, pois ela pode criar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-125">It's possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this call should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="7b7dc-126">Usar finalizadores para liberar recursos</span><span class="sxs-lookup"><span data-stu-id="7b7dc-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="7b7dc-127">Em geral, o C# não exige tanto gerenciamento de memória por parte do desenvolvedor como linguagens que não têm como alvo um tempo de execução com coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-127">In general, C# does not require as much memory management on the part of the developer as languages that don't target a runtime with garbage collection.</span></span> <span data-ttu-id="7b7dc-128">Isso ocorre porque o coletor de lixo do .NET gerencia implicitamente a alocação e a liberação da memória para seus objetos.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-128">This is because the .NET garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="7b7dc-129">No entanto, quando o aplicativo encapsula recursos não gerenciados, como Windows, arquivos e conexões de rede, você deve usar os finalizadores para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-129">However, when your application encapsulates unmanaged resources, such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="7b7dc-130">Quando o objeto está qualificado para finalização, o coletor de lixo executa o método `Finalize` do objeto.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="7b7dc-131">Liberação explícita de recursos</span><span class="sxs-lookup"><span data-stu-id="7b7dc-131">Explicit release of resources</span></span>  
 <span data-ttu-id="7b7dc-132">Se seu aplicativo estiver usando um recurso externo caro, também será recomendável fornecer uma maneira de liberar explicitamente o recurso antes que o coletor de lixo libere o objeto.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="7b7dc-133">Para liberar o recurso, implemente um `Dispose` método da <xref:System.IDisposable> interface que executa a limpeza necessária para o objeto.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-133">To release the resource, implement a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="7b7dc-134">Isso pode melhorar consideravelmente o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="7b7dc-135">Mesmo com esse controle explícito sobre os recursos, o finalizador torna-se uma proteção para limpar os recursos se a chamada para o `Dispose` método falhar.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method fails.</span></span>  
  
 <span data-ttu-id="7b7dc-136">Para obter mais informações sobre como limpar recursos, consulte os seguintes artigos:</span><span class="sxs-lookup"><span data-stu-id="7b7dc-136">For more information about cleaning up resources, see the following articles:</span></span>  
  
- [<span data-ttu-id="7b7dc-137">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="7b7dc-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="7b7dc-138">Implementando um método Dispose</span><span class="sxs-lookup"><span data-stu-id="7b7dc-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="7b7dc-139">Instrução using</span><span class="sxs-lookup"><span data-stu-id="7b7dc-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="7b7dc-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7b7dc-140">Example</span></span>  
 <span data-ttu-id="7b7dc-141">O exemplo a seguir cria três classes que compõem uma cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="7b7dc-142">A classe `First` é a classe base, `Second` é derivado de `First` e `Third` é derivado de `Second`.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="7b7dc-143">Todas as três têm finalizadores.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-143">All three have finalizers.</span></span> <span data-ttu-id="7b7dc-144">Em `Main`, uma instância da classe mais derivada é criada.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="7b7dc-145">Quando o programa for executado, observe que os finalizadores das três classes são chamados automaticamente e em ordem, do mais derivado para o menos derivado.</span><span class="sxs-lookup"><span data-stu-id="7b7dc-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="7b7dc-146">especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="7b7dc-146">C# language specification</span></span>  

<span data-ttu-id="7b7dc-147">Para obter mais informações, confira a seção [Destruidores](~/_csharplang/spec/classes.md#destructors) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="7b7dc-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="7b7dc-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="7b7dc-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="7b7dc-149">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="7b7dc-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="7b7dc-150">Construtores</span><span class="sxs-lookup"><span data-stu-id="7b7dc-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="7b7dc-151">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="7b7dc-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
