---
title: Usando objetos que implementam IDisposable
ms.date: 05/13/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Dispose method
- try/finally block
- garbage collection, encapsulating resources
ms.assetid: 81b2cdb5-c91a-4a31-9c83-eadc52da5cf0
ms.openlocfilehash: 87eefe2bd347ba1564b2f06d49bbee3b85efdb97
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287591"
---
# <a name="using-objects-that-implement-idisposable"></a><span data-ttu-id="b5542-102">Usando objetos que implementam IDisposable</span><span class="sxs-lookup"><span data-stu-id="b5542-102">Using objects that implement IDisposable</span></span>

<span data-ttu-id="b5542-103">O coletor de lixo do Common Language Runtime recupera a memória usada por objetos gerenciados, mas os tipos que usam recursos não gerenciados implementam a <xref:System.IDisposable> interface para permitir que os recursos necessários a esses recursos não gerenciados sejam recuperados.</span><span class="sxs-lookup"><span data-stu-id="b5542-103">The common language runtime's garbage collector reclaims the memory used by managed objects, but types that use unmanaged resources implement the <xref:System.IDisposable> interface to allow the resources needed by these unmanaged resources to be reclaimed.</span></span> <span data-ttu-id="b5542-104">Após terminar de usar um objeto que implementa <xref:System.IDisposable>, você deverá chamar a implementação de <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do objeto.</span><span class="sxs-lookup"><span data-stu-id="b5542-104">When you finish using an object that implements <xref:System.IDisposable>, you should call the object's <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="b5542-105">É possível fazer isso de duas formas:</span><span class="sxs-lookup"><span data-stu-id="b5542-105">You can do this in one of two ways:</span></span>

- <span data-ttu-id="b5542-106">Com a `using` instrução C# ( `Using` em Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="b5542-106">With the C# `using` statement (`Using` in Visual Basic).</span></span>
- <span data-ttu-id="b5542-107">Implementando um `try/finally` bloco e chamando o <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> no `finally` .</span><span class="sxs-lookup"><span data-stu-id="b5542-107">By implementing a `try/finally` block, and calling the <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> in the `finally`.</span></span>

## <a name="the-using-statement"></a><span data-ttu-id="b5542-108">A instrução using</span><span class="sxs-lookup"><span data-stu-id="b5542-108">The using statement</span></span>

<span data-ttu-id="b5542-109">A [ `using` instrução](../../csharp/language-reference/keywords/using-statement.md) em C# e a [ `Using` instrução](../../visual-basic/language-reference/statements/using-statement.md) em Visual Basic simplificam o código que você deve escrever para limpar um objeto.</span><span class="sxs-lookup"><span data-stu-id="b5542-109">The [`using` statement](../../csharp/language-reference/keywords/using-statement.md) in C# and the [`Using` statement](../../visual-basic/language-reference/statements/using-statement.md) in Visual Basic simplify the code that you must write to cleanup an object.</span></span> <span data-ttu-id="b5542-110">A instrução `using` obtém um ou mais recursos, executa as instruções que você especifica e descarta o objeto automaticamente.</span><span class="sxs-lookup"><span data-stu-id="b5542-110">The `using` statement obtains one or more resources, executes the statements that you specify, and automatically disposes of the object.</span></span> <span data-ttu-id="b5542-111">Entretanto, a instrução `using` é útil apenas para os objetos que são usados no escopo do método no qual eles são criados.</span><span class="sxs-lookup"><span data-stu-id="b5542-111">However, the `using` statement is useful only for objects that are used within the scope of the method in which they are constructed.</span></span>

<span data-ttu-id="b5542-112">O exemplo a seguir usa a instrução `using` para criar e liberar um objeto <xref:System.IO.StreamReader?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b5542-112">The following example uses the `using` statement to create and release a <xref:System.IO.StreamReader?displayProperty=nameWithType> object.</span></span>

[!code-csharp[Conceptual.Disposable#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using1.cs#1)]
[!code-vb[Conceptual.Disposable#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using1.vb#1)]

<span data-ttu-id="b5542-113">Embora a <xref:System.IO.StreamReader> classe implemente a <xref:System.IDisposable> interface, que indica que ela usa um recurso não gerenciado, o exemplo não chama explicitamente o <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="b5542-113">Although the <xref:System.IO.StreamReader> class implements the <xref:System.IDisposable> interface, which indicates that it uses an unmanaged resource, the example doesn't explicitly call the <xref:System.IO.StreamReader.Dispose%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="b5542-114">Quando o compilador do C# ou do Visual Basic encontra a instrução `using`, ele emite a IL (linguagem intermediária) que equivale ao seguinte código que contém explicitamente um bloco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="b5542-114">When the C# or Visual Basic compiler encounters the `using` statement, it emits intermediate language (IL) that is equivalent to the following code that explicitly contains a `try/finally` block.</span></span>

[!code-csharp[Conceptual.Disposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using3.cs#3)]
[!code-vb[Conceptual.Disposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using3.vb#3)]

<span data-ttu-id="b5542-115">A instrução `using` do C# também permite que você adquira vários recursos em uma única instrução, o que é internamente equivalente a instruções `using` aninhadas.</span><span class="sxs-lookup"><span data-stu-id="b5542-115">The C# `using` statement also allows you to acquire multiple resources in a single statement, which is internally equivalent to nested `using` statements.</span></span> <span data-ttu-id="b5542-116">O exemplo a seguir cria instancia dois objetos <xref:System.IO.StreamReader> para ler o conteúdo de dois arquivos diferentes.</span><span class="sxs-lookup"><span data-stu-id="b5542-116">The following example instantiates two <xref:System.IO.StreamReader> objects to read the contents of two different files.</span></span>

[!code-csharp[Conceptual.Disposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using4.cs#4)]

## <a name="tryfinally-block"></a><span data-ttu-id="b5542-117">Bloco Try/finally</span><span class="sxs-lookup"><span data-stu-id="b5542-117">Try/finally block</span></span>

<span data-ttu-id="b5542-118">Em vez de incluir um bloco `try/finally` em uma instrução `using`, você pode optar por implementar diretamente o bloco `try/finally`.</span><span class="sxs-lookup"><span data-stu-id="b5542-118">Instead of wrapping a `try/finally` block in a `using` statement, you may choose to implement the `try/finally` block directly.</span></span> <span data-ttu-id="b5542-119">Pode ser seu estilo de codificação pessoal ou você pode desejar fazer isso por um dos seguintes motivos:</span><span class="sxs-lookup"><span data-stu-id="b5542-119">It may be your personal coding style, or you might want to do this for one of the following reasons:</span></span>

- <span data-ttu-id="b5542-120">Para incluir um `catch` bloco para tratar as exceções lançadas no `try` bloco.</span><span class="sxs-lookup"><span data-stu-id="b5542-120">To include a `catch` block to handle exceptions thrown in the `try` block.</span></span> <span data-ttu-id="b5542-121">Caso contrário, as exceções geradas na `using` instrução não serão manipuladas.</span><span class="sxs-lookup"><span data-stu-id="b5542-121">Otherwise, any exceptions thrown within the `using` statement are unhandled.</span></span>

- <span data-ttu-id="b5542-122">Para criar uma instância de um objeto que implementa <xref:System.IDisposable> cujo escopo não é local para o bloco dentro do qual é declarado.</span><span class="sxs-lookup"><span data-stu-id="b5542-122">To instantiate an object that implements <xref:System.IDisposable> whose scope is not local to the block within which it is declared.</span></span>

<span data-ttu-id="b5542-123">O exemplo a seguir é semelhante ao exemplo anterior, exceto que ele usa um bloco `try/catch/finally` para criar uma instância, usar e descartar um objeto <xref:System.IO.StreamReader> e também para manipular todas as exceções lançadas pelo construtor <xref:System.IO.StreamReader> e pelo método <xref:System.IO.StreamReader.ReadToEnd%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5542-123">The following example is similar to the previous example, except that it uses a `try/catch/finally` block to instantiate, use, and dispose of a <xref:System.IO.StreamReader> object, and to handle any exceptions thrown by the <xref:System.IO.StreamReader> constructor and its <xref:System.IO.StreamReader.ReadToEnd%2A> method.</span></span> <span data-ttu-id="b5542-124">O código no `finally` bloco verifica se o objeto que implementa <xref:System.IDisposable> não está `null` antes de chamar o <xref:System.IDisposable.Dispose%2A> método.</span><span class="sxs-lookup"><span data-stu-id="b5542-124">The code in the `finally` block checks that the object that implements <xref:System.IDisposable> isn't `null` before it calls the <xref:System.IDisposable.Dispose%2A> method.</span></span> <span data-ttu-id="b5542-125">Não fazer isso poderá levar a uma exceção de <xref:System.NullReferenceException> em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b5542-125">Failure to do this can result in a <xref:System.NullReferenceException> exception at run time.</span></span>

[!code-csharp[Conceptual.Disposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/using5.cs#6)]
[!code-vb[Conceptual.Disposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/using5.vb#6)]

<span data-ttu-id="b5542-126">Você poderá seguir esse padrão básico se optar por implementar ou precisar implementar um bloco `try/finally`, pois a linguagem de programação não oferece suporte a uma instrução `using`, mas permite chamadas diretas para o método <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="b5542-126">You can follow this basic pattern if you choose to implement or must implement a `try/finally` block, because your programming language doesn't support a `using` statement but does allow direct calls to the <xref:System.IDisposable.Dispose%2A> method.</span></span>

## <a name="idisposable-instance-members"></a><span data-ttu-id="b5542-127">Membros da instância IDisposable</span><span class="sxs-lookup"><span data-stu-id="b5542-127">IDisposable instance members</span></span>

<span data-ttu-id="b5542-128">Se uma classe mantém uma <xref:System.IDisposable> implementação como um membro de instância, seja um campo ou uma propriedade, a classe também deve implementar <xref:System.IDisposable> .</span><span class="sxs-lookup"><span data-stu-id="b5542-128">If a class holds an <xref:System.IDisposable> implementation as an instance member, either a field or a property, the class should also implement <xref:System.IDisposable>.</span></span> <span data-ttu-id="b5542-129">Para obter mais informações, consulte [implementar uma disposição em cascata](implementing-dispose.md#cascade-dispose-calls).</span><span class="sxs-lookup"><span data-stu-id="b5542-129">For more information, see [implement a cascade dispose](implementing-dispose.md#cascade-dispose-calls).</span></span>

## <a name="see-also"></a><span data-ttu-id="b5542-130">Veja também</span><span class="sxs-lookup"><span data-stu-id="b5542-130">See also</span></span>

- [<span data-ttu-id="b5542-131">Limpando recursos não gerenciados</span><span class="sxs-lookup"><span data-stu-id="b5542-131">Cleaning up unmanaged resources</span></span>](unmanaged.md)
- [<span data-ttu-id="b5542-132">Instrução using (referência C#)</span><span class="sxs-lookup"><span data-stu-id="b5542-132">using Statement (C# Reference)</span></span>](../../csharp/language-reference/keywords/using-statement.md)
- [<span data-ttu-id="b5542-133">Instrução Using (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b5542-133">Using Statement (Visual Basic)</span></span>](../../visual-basic/language-reference/statements/using-statement.md)
