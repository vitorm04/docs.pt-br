---
title: Instrução using (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fdf37e1bfc57bf850b332f167e57d3e05d23e78
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="1d73e-102">Instrução using (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1d73e-102">using Statement (C# Reference)</span></span>
<span data-ttu-id="1d73e-103">Fornece uma sintaxe conveniente que garante o uso correto de objetos <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="1d73e-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d73e-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d73e-104">Example</span></span>  
 <span data-ttu-id="1d73e-105">O exemplo a seguir mostra como usar a instrução using.</span><span class="sxs-lookup"><span data-stu-id="1d73e-105">The following example shows how to use the using statement.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_1.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="1d73e-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d73e-106">Remarks</span></span>  
 <span data-ttu-id="1d73e-107"><xref:System.IO.File> e <xref:System.Drawing.Font> são exemplos de tipos gerenciados que acessam recursos não gerenciados (nesse caso, identificadores de arquivo de caso e contextos de dispositivo).</span><span class="sxs-lookup"><span data-stu-id="1d73e-107"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="1d73e-108">Há muitos outros tipos de recursos não gerenciados e tipos de biblioteca de classes que os encapsula.</span><span class="sxs-lookup"><span data-stu-id="1d73e-108">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="1d73e-109">Todos esses tipos devem implementar a interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="1d73e-109">All such types must implement the <xref:System.IDisposable> interface.</span></span>  
  
<span data-ttu-id="1d73e-110">Quando o tempo de vida de um `IDisposable` objeto está limitado a um único método, você deve declarar e instanciá-la em um `using` instrução.</span><span class="sxs-lookup"><span data-stu-id="1d73e-110">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in a `using` statement.</span></span> <span data-ttu-id="1d73e-111">A instrução `using` chama o método <xref:System.IDisposable.Dispose%2A> no objeto da forma correta e (quando você o usa como mostrado anteriormente) ele também faz com que o objeto em si saia do escopo assim que <xref:System.IDisposable.Dispose%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="1d73e-111">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="1d73e-112">Dentro do bloco `using`, o objeto é somente leitura e não pode ser modificado ou reatribuído.</span><span class="sxs-lookup"><span data-stu-id="1d73e-112">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>  
  
 <span data-ttu-id="1d73e-113">A instrução `using` garante que <xref:System.IDisposable.Dispose%2A> seja chamado mesmo se ocorrer uma exceção enquanto você estiver chamando métodos no objeto.</span><span class="sxs-lookup"><span data-stu-id="1d73e-113">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs while you are calling methods on the object.</span></span> <span data-ttu-id="1d73e-114">Você pode obter o mesmo resultado colocando o objeto dentro de um bloco try e, em seguida, chamando <xref:System.IDisposable.Dispose%2A> em um bloco finally. Na verdade, é dessa forma que a instrução `using` é convertida pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="1d73e-114">You can achieve the same result by putting the object inside a try block and then calling <xref:System.IDisposable.Dispose%2A> in a finally block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="1d73e-115">O exemplo de código anterior se expande para o seguinte código em tempo de compilação (observe as chaves extras para criar o escopo limitado para o objeto):</span><span class="sxs-lookup"><span data-stu-id="1d73e-115">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_2.cs)]  
  
 <span data-ttu-id="1d73e-116">Várias instâncias de um tipo podem ser declaradas em uma instrução `using`, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="1d73e-116">Multiple instances of a type can be declared in a `using` statement, as shown in the following example.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_3.cs)]  
  
 <span data-ttu-id="1d73e-117">Você pode criar uma instância do objeto de recurso e, em seguida, passar a variável para a instrução `using`, mas isso não é uma prática recomendada.</span><span class="sxs-lookup"><span data-stu-id="1d73e-117">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="1d73e-118">Nesse caso, o objeto permanece no escopo depois que o controle sai do bloco `using` mesmo que provavelmente ele não tenha mais acesso aos seus recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="1d73e-118">In this case, the object remains in scope after control leaves the `using` block even though it will probably no longer have access to its unmanaged resources.</span></span> <span data-ttu-id="1d73e-119">Em outras palavras, ele será não será mais totalmente inicializado.</span><span class="sxs-lookup"><span data-stu-id="1d73e-119">In other words, it will no longer be fully initialized.</span></span> <span data-ttu-id="1d73e-120">Se você tentar usar o objeto fora do bloco `using`, corre o risco de causar o lançamento de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="1d73e-120">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="1d73e-121">Por esse motivo, geralmente é melhor instanciar o objeto na instrução `using` e limitar seu escopo ao bloco `using`.</span><span class="sxs-lookup"><span data-stu-id="1d73e-121">For this reason, it is generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>  
  
 [!code-csharp[csrefKeywordsNamespace#7](../../../csharp/language-reference/keywords/codesnippet/CSharp/using-statement_4.cs)]  
  
<span data-ttu-id="1d73e-122">Para obter mais informações sobre como descartar `IDisposable` objetos, consulte [usando objetos que implementam IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="1d73e-122">For more information on disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d73e-123">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="1d73e-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1d73e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d73e-124">See Also</span></span>  
 [<span data-ttu-id="1d73e-125">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="1d73e-125">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="1d73e-126">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="1d73e-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="1d73e-127">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="1d73e-127">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="1d73e-128">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="1d73e-128">using Directive</span></span>](../../../csharp/language-reference/keywords/using-directive.md)  
 [<span data-ttu-id="1d73e-129">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="1d73e-129">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
 [<span data-ttu-id="1d73e-130">Usando objetos que implementam IDisposable</span><span class="sxs-lookup"><span data-stu-id="1d73e-130">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)  
 [<span data-ttu-id="1d73e-131">Interface IDisposable</span><span class="sxs-lookup"><span data-stu-id="1d73e-131">IDisposable interface</span></span>](xref:System.IDisposable)
