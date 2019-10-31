---
title: Finalizadores – Guia de Programação em C#
ms.custom: seodec18
ms.date: 10/08/2018
helpviewer_keywords:
- ~ [C#], in finalizers
- C# language, finalizers
- finalizers [C#]
ms.assetid: 1ae6e46d-a4b1-4a49-abe5-b97f53d9e049
ms.openlocfilehash: 9936d56582afd160bf3464d18efd3acf47c7af60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924493"
---
# <a name="finalizers-c-programming-guide"></a><span data-ttu-id="9bd25-102">Finalizadores (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="9bd25-102">Finalizers (C# Programming Guide)</span></span>
<span data-ttu-id="9bd25-103">Os finalizadores (que também são chamados de **destruidores**) são usados para executar qualquer limpeza final necessária, quando uma instância da classe está sendo coletada pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="9bd25-103">Finalizers (which are also called **destructors**) are used to perform any necessary final clean-up when a class instance is being collected by the garbage collector.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9bd25-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="9bd25-104">Remarks</span></span>  
  
- <span data-ttu-id="9bd25-105">Os finalizadores não podem ser definidos em structs.</span><span class="sxs-lookup"><span data-stu-id="9bd25-105">Finalizers cannot be defined in structs.</span></span> <span data-ttu-id="9bd25-106">Eles são usados somente com classes.</span><span class="sxs-lookup"><span data-stu-id="9bd25-106">They are only used with classes.</span></span>  
  
- <span data-ttu-id="9bd25-107">Uma classe pode ter somente um finalizador.</span><span class="sxs-lookup"><span data-stu-id="9bd25-107">A class can only have one finalizer.</span></span>  
  
- <span data-ttu-id="9bd25-108">Os finalizadores não podem ser herdados ou sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="9bd25-108">Finalizers cannot be inherited or overloaded.</span></span>  
  
- <span data-ttu-id="9bd25-109">Os finalizadores não podem ser chamados.</span><span class="sxs-lookup"><span data-stu-id="9bd25-109">Finalizers cannot be called.</span></span> <span data-ttu-id="9bd25-110">Eles são invocados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="9bd25-110">They are invoked automatically.</span></span>  
  
- <span data-ttu-id="9bd25-111">Um finalizador não usa modificadores ou não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="9bd25-111">A finalizer does not take modifiers or have parameters.</span></span>  
  
 <span data-ttu-id="9bd25-112">Por exemplo, o seguinte é uma declaração de um finalizador para a classe `Car`.</span><span class="sxs-lookup"><span data-stu-id="9bd25-112">For example, the following is a declaration of a finalizer for the `Car` class.</span></span>
  
 [!code-csharp[csProgGuideObjects#86](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#86)]  

<span data-ttu-id="9bd25-113">Um finalizador também pode ser implementado como uma definição do corpo da expressão, como mostra o exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="9bd25-113">A finalizer can also be implemented as an expression body definition, as the following example shows.</span></span>

[!code-csharp[expression-bodied-finalizer](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/expr-bodied-destructor.cs#1)]  
  
 <span data-ttu-id="9bd25-114">O finalizador chama implicitamente <xref:System.Object.Finalize%2A> na classe base do objeto.</span><span class="sxs-lookup"><span data-stu-id="9bd25-114">The finalizer implicitly calls <xref:System.Object.Finalize%2A> on the base class of the object.</span></span> <span data-ttu-id="9bd25-115">Portanto, uma chamada para um finalizador é convertida implicitamente para o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="9bd25-115">Therefore, a call to a finalizer is implicitly translated to the following code:</span></span>  
  
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
  
 <span data-ttu-id="9bd25-116">Isso significa que o método `Finalize` é chamado de forma recursiva para todas as instâncias da cadeia de herança, da mais derivada à menos derivada.</span><span class="sxs-lookup"><span data-stu-id="9bd25-116">This means that the `Finalize` method is called recursively for all instances in the inheritance chain, from the most-derived to the least-derived.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bd25-117">Finalizadores vazios não devem ser usados.</span><span class="sxs-lookup"><span data-stu-id="9bd25-117">Empty finalizers should not be used.</span></span> <span data-ttu-id="9bd25-118">Quando uma classe contém um finalizador, uma entrada é criada na fila `Finalize`.</span><span class="sxs-lookup"><span data-stu-id="9bd25-118">When a class contains a finalizer, an entry is created in the `Finalize` queue.</span></span> <span data-ttu-id="9bd25-119">Quando o finalizador é chamado, o coletor de lixo é invocado para processar a fila.</span><span class="sxs-lookup"><span data-stu-id="9bd25-119">When the finalizer is called, the garbage collector is invoked to process the queue.</span></span> <span data-ttu-id="9bd25-120">Um finalizador vazio apenas resulta na perda de desempenho desnecessária.</span><span class="sxs-lookup"><span data-stu-id="9bd25-120">An empty finalizer just causes a needless loss of performance.</span></span>  
  
 <span data-ttu-id="9bd25-121">O programador não tem controle sobre quando o finalizador é chamado porque isso é determinado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="9bd25-121">The programmer has no control over when the finalizer is called because this is determined by the garbage collector.</span></span> <span data-ttu-id="9bd25-122">O coletor de lixo procura objetos que não estão mais sendo usados pelo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bd25-122">The garbage collector checks for objects that are no longer being used by the application.</span></span> <span data-ttu-id="9bd25-123">Se considerar um objeto qualificado para finalização, ele chamará o finalizador (se houver) e recuperará a memória usada para armazenar o objeto.</span><span class="sxs-lookup"><span data-stu-id="9bd25-123">If it considers an object eligible for finalization, it calls the finalizer (if any) and reclaims the memory used to store the object.</span></span> 
 
 <span data-ttu-id="9bd25-124">Em aplicativos .NET Framework (mas não em aplicativos .NET Core), os finalizadores também são chamados quando o programa é encerrado.</span><span class="sxs-lookup"><span data-stu-id="9bd25-124">In .NET Framework applications (but not in .NET Core applications), finalizers are also called when the program exits.</span></span> 
  
 <span data-ttu-id="9bd25-125">É possível forçar a coleta de lixo chamando <xref:System.GC.Collect%2A>, mas na maioria das vezes, isso deve ser evitado porque pode criar problemas de desempenho.</span><span class="sxs-lookup"><span data-stu-id="9bd25-125">It is possible to force garbage collection by calling <xref:System.GC.Collect%2A>, but most of the time, this should be avoided because it may create performance issues.</span></span>  
  
## <a name="using-finalizers-to-release-resources"></a><span data-ttu-id="9bd25-126">Usar finalizadores para liberar recursos</span><span class="sxs-lookup"><span data-stu-id="9bd25-126">Using finalizers to release resources</span></span>  
 <span data-ttu-id="9bd25-127">Em geral, o C# não demanda tanto gerenciamento de memória quanto é necessário quando você desenvolve usando uma linguagem que não tem como destino um tempo de execução com coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="9bd25-127">In general, C# does not require as much memory management as is needed when you develop with a language that does not target a runtime with garbage collection.</span></span> <span data-ttu-id="9bd25-128">Isso ocorre porque o coletor de lixo do .NET Framework gerencia implicitamente a alocação e a liberação de memória para seus objetos.</span><span class="sxs-lookup"><span data-stu-id="9bd25-128">This is because the .NET Framework garbage collector implicitly manages the allocation and release of memory for your objects.</span></span> <span data-ttu-id="9bd25-129">No entanto, quando seu aplicativo encapsula recursos não gerenciados, como janelas, arquivos e conexões de rede, você deve usar finalizadores para liberar esses recursos.</span><span class="sxs-lookup"><span data-stu-id="9bd25-129">However, when your application encapsulates unmanaged resources such as windows, files, and network connections, you should use finalizers to free those resources.</span></span> <span data-ttu-id="9bd25-130">Quando o objeto está qualificado para finalização, o coletor de lixo executa o método `Finalize` do objeto.</span><span class="sxs-lookup"><span data-stu-id="9bd25-130">When the object is eligible for finalization, the garbage collector runs the `Finalize` method of the object.</span></span>  
  
## <a name="explicit-release-of-resources"></a><span data-ttu-id="9bd25-131">Liberação explícita de recursos</span><span class="sxs-lookup"><span data-stu-id="9bd25-131">Explicit release of resources</span></span>  
 <span data-ttu-id="9bd25-132">Se seu aplicativo estiver usando um recurso externo caro, também será recomendável fornecer uma maneira de liberar explicitamente o recurso antes que o coletor de lixo libere o objeto.</span><span class="sxs-lookup"><span data-stu-id="9bd25-132">If your application is using an expensive external resource, we also recommend that you provide a way to explicitly release the resource before the garbage collector frees the object.</span></span> <span data-ttu-id="9bd25-133">Você faz isso implementando um método `Dispose` da interface <xref:System.IDisposable> que executa a limpeza necessária para o objeto.</span><span class="sxs-lookup"><span data-stu-id="9bd25-133">You do this by implementing a `Dispose` method from the <xref:System.IDisposable> interface that performs the necessary cleanup for the object.</span></span> <span data-ttu-id="9bd25-134">Isso pode melhorar consideravelmente o desempenho do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="9bd25-134">This can considerably improve the performance of the application.</span></span> <span data-ttu-id="9bd25-135">Mesmo com esse controle explícito sobre os recursos, o finalizador se tornará uma proteção usada para limpar os recursos se a chamada para o método `Dispose` falhar.</span><span class="sxs-lookup"><span data-stu-id="9bd25-135">Even with this explicit control over resources, the finalizer becomes a safeguard to clean up resources if the call to the `Dispose` method failed.</span></span>  
  
 <span data-ttu-id="9bd25-136">Para obter mais detalhes sobre limpeza de recursos, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="9bd25-136">For more details about cleaning up resources, see the following topics:</span></span>  
  
- [<span data-ttu-id="9bd25-137">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="9bd25-137">Cleaning Up Unmanaged Resources</span></span>](../../../standard/garbage-collection/unmanaged.md)  
  
- [<span data-ttu-id="9bd25-138">Implementando um método dispose</span><span class="sxs-lookup"><span data-stu-id="9bd25-138">Implementing a Dispose Method</span></span>](../../../standard/garbage-collection/implementing-dispose.md)  
  
- [<span data-ttu-id="9bd25-139">Instrução using</span><span class="sxs-lookup"><span data-stu-id="9bd25-139">using Statement</span></span>](../../language-reference/keywords/using-statement.md)  
  
## <a name="example"></a><span data-ttu-id="9bd25-140">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9bd25-140">Example</span></span>  
 <span data-ttu-id="9bd25-141">O exemplo a seguir cria três classes que compõem uma cadeia de herança.</span><span class="sxs-lookup"><span data-stu-id="9bd25-141">The following example creates three classes that make a chain of inheritance.</span></span> <span data-ttu-id="9bd25-142">A classe `First` é a classe base, `Second` é derivado de `First` e `Third` é derivado de `Second`.</span><span class="sxs-lookup"><span data-stu-id="9bd25-142">The class `First` is the base class, `Second` is derived from `First`, and `Third` is derived from `Second`.</span></span> <span data-ttu-id="9bd25-143">Todas as três têm finalizadores.</span><span class="sxs-lookup"><span data-stu-id="9bd25-143">All three have finalizers.</span></span> <span data-ttu-id="9bd25-144">Em `Main`, uma instância da classe mais derivada é criada.</span><span class="sxs-lookup"><span data-stu-id="9bd25-144">In `Main`, an instance of the most-derived class is created.</span></span> <span data-ttu-id="9bd25-145">Quando o programa for executado, observe que os finalizadores das três classes são chamados automaticamente e em ordem, do mais derivado para o menos derivado.</span><span class="sxs-lookup"><span data-stu-id="9bd25-145">When the program runs, notice that the finalizers for the three classes are called automatically, and in order, from the most-derived to the least-derived.</span></span>  
  
 [!code-csharp[csProgGuideObjects#85](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#85)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="9bd25-146">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="9bd25-146">C# language specification</span></span>  

<span data-ttu-id="9bd25-147">Para obter mais informações, confira a seção [Destruidores](~/_csharplang/spec/classes.md#destructors) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="9bd25-147">For more information, see the [Destructors](~/_csharplang/spec/classes.md#destructors) section of the [C# language specification](../../language-reference/language-specification/index.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="9bd25-148">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9bd25-148">See also</span></span>

- <xref:System.IDisposable>
- [<span data-ttu-id="9bd25-149">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9bd25-149">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="9bd25-150">Construtores</span><span class="sxs-lookup"><span data-stu-id="9bd25-150">Constructors</span></span>](./constructors.md)
- [<span data-ttu-id="9bd25-151">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="9bd25-151">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
