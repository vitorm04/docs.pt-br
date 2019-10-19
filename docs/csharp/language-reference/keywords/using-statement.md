---
title: Instrução using – Referência de C#
ms.custom: seodec18
ms.date: 10/15/2019
helpviewer_keywords:
- using statement [C#]
ms.assetid: afc355e6-f0b9-4240-94dd-0d93f17d9fc3
ms.openlocfilehash: 7e6d1b663007d430f71f81923f343f1c43f5dd2d
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72579175"
---
# <a name="using-statement-c-reference"></a><span data-ttu-id="532f2-102">Instrução using (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="532f2-102">using statement (C# Reference)</span></span>

<span data-ttu-id="532f2-103">Fornece uma sintaxe conveniente que garante o uso correto de objetos <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="532f2-103">Provides a convenient syntax that ensures the correct use of <xref:System.IDisposable> objects.</span></span>

## <a name="example"></a><span data-ttu-id="532f2-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="532f2-104">Example</span></span>

<span data-ttu-id="532f2-105">O exemplo a seguir mostra como usar a instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="532f2-105">The following example shows how to use the `using` statement.</span></span>

[!code-csharp[csrefKeywordsNamespace#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#4)]

<span data-ttu-id="532f2-106">A partir C# do 8,0, você pode usar a seguinte sintaxe alternativa para a instrução de `using` que não exige chaves:</span><span class="sxs-lookup"><span data-stu-id="532f2-106">Beginning with C# 8.0, you can use the following alternative syntax for the `using` statement that doesn't require braces:</span></span>

[!code-csharp[csrefKeywordsNamespace#New](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#ModernUsing)]

## <a name="remarks"></a><span data-ttu-id="532f2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="532f2-107">Remarks</span></span>

<span data-ttu-id="532f2-108"><xref:System.IO.File> e <xref:System.Drawing.Font> são exemplos de tipos gerenciados que acessam recursos não gerenciados (nesse caso, identificadores de arquivo de caso e contextos de dispositivo).</span><span class="sxs-lookup"><span data-stu-id="532f2-108"><xref:System.IO.File> and <xref:System.Drawing.Font> are examples of managed types that access unmanaged resources (in this case file handles and device contexts).</span></span> <span data-ttu-id="532f2-109">Há muitos outros tipos de recursos não gerenciados e tipos de biblioteca de classes que os encapsula.</span><span class="sxs-lookup"><span data-stu-id="532f2-109">There are many other kinds of unmanaged resources and class library types that encapsulate them.</span></span> <span data-ttu-id="532f2-110">Todos esses tipos devem implementar a interface <xref:System.IDisposable>.</span><span class="sxs-lookup"><span data-stu-id="532f2-110">All such types must implement the <xref:System.IDisposable> interface.</span></span>

<span data-ttu-id="532f2-111">Quando o tempo de vida de um objeto `IDisposable` é limitado a um único método, você deve declará-lo e instanciá-lo na instrução `using`.</span><span class="sxs-lookup"><span data-stu-id="532f2-111">When the lifetime of an `IDisposable` object is limited to a single method, you should declare and instantiate it in the `using` statement.</span></span> <span data-ttu-id="532f2-112">A instrução `using` chama o método <xref:System.IDisposable.Dispose%2A> no objeto da forma correta e (quando você o usa como mostrado anteriormente) ele também faz com que o objeto em si saia do escopo assim que <xref:System.IDisposable.Dispose%2A> é chamado.</span><span class="sxs-lookup"><span data-stu-id="532f2-112">The `using` statement calls the <xref:System.IDisposable.Dispose%2A> method on the object in the correct way, and (when you use it as shown earlier) it also causes the object itself to go out of scope as soon as <xref:System.IDisposable.Dispose%2A> is called.</span></span> <span data-ttu-id="532f2-113">Dentro do bloco `using`, o objeto é somente leitura e não pode ser modificado ou reatribuído.</span><span class="sxs-lookup"><span data-stu-id="532f2-113">Within the `using` block, the object is read-only and cannot be modified or reassigned.</span></span>

<span data-ttu-id="532f2-114">A instrução `using` garante que <xref:System.IDisposable.Dispose%2A> seja chamado, mesmo que ocorra uma exceção dentro do bloco `using`.</span><span class="sxs-lookup"><span data-stu-id="532f2-114">The `using` statement ensures that <xref:System.IDisposable.Dispose%2A> is called even if an exception occurs within the `using` block.</span></span> <span data-ttu-id="532f2-115">Você pode obter o mesmo resultado colocando o objeto dentro de um bloco `try` e então chamando <xref:System.IDisposable.Dispose%2A> em um bloco `finally`. Na verdade, é dessa forma que a instrução `using` é convertida pelo compilador.</span><span class="sxs-lookup"><span data-stu-id="532f2-115">You can achieve the same result by putting the object inside a `try` block and then calling <xref:System.IDisposable.Dispose%2A> in a `finally` block; in fact, this is how the `using` statement is translated by the compiler.</span></span> <span data-ttu-id="532f2-116">O exemplo de código anterior se expande para o seguinte código em tempo de compilação (observe as chaves extras para criar o escopo limitado para o objeto):</span><span class="sxs-lookup"><span data-stu-id="532f2-116">The code example earlier expands to the following code at compile time (note the extra curly braces to create the limited scope for the object):</span></span>

[!code-csharp[csrefKeywordsNamespace#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#5)]

<span data-ttu-id="532f2-117">A sintaxe de instrução `using` mais recente se traduz em um código muito semelhante.</span><span class="sxs-lookup"><span data-stu-id="532f2-117">The newer `using` statement syntax translates to very similar code.</span></span> <span data-ttu-id="532f2-118">O bloco de `try` é aberto onde a variável é declarada.</span><span class="sxs-lookup"><span data-stu-id="532f2-118">The `try` block opens where the variable is declared.</span></span> <span data-ttu-id="532f2-119">O bloco de `finally` é adicionado ao fechamento do bloco delimitador, normalmente no final de um método.</span><span class="sxs-lookup"><span data-stu-id="532f2-119">The `finally` block is added at the close of the enclosing block, typically at the end of a method.</span></span>

<span data-ttu-id="532f2-120">Para obter mais informações sobre a instrução `try`-`finally`, veja o tópico [try-finally](try-finally.md).</span><span class="sxs-lookup"><span data-stu-id="532f2-120">For more information about the `try`-`finally` statement, see the [try-finally](try-finally.md) topic.</span></span>

<span data-ttu-id="532f2-121">Várias instâncias de um tipo podem ser declaradas na instrução `using`, conforme mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="532f2-121">Multiple instances of a type can be declared in the `using` statement, as shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#6)]

<span data-ttu-id="532f2-122">Você pode combinar várias declarações do mesmo tipo usando a nova sintaxe introduzida com C# 8 também.</span><span class="sxs-lookup"><span data-stu-id="532f2-122">You can combine multiple declarations of the same type using the new syntax introduced with C# 8 as well.</span></span> <span data-ttu-id="532f2-123">Isso é mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="532f2-123">This is shown in the following example:</span></span>

[!code-csharp[csrefKeywordsNamespace#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#MultipleUsing)]

<span data-ttu-id="532f2-124">Você pode criar uma instância do objeto de recurso e, em seguida, passar a variável para a instrução `using`, mas isso não é uma prática recomendada.</span><span class="sxs-lookup"><span data-stu-id="532f2-124">You can instantiate the resource object and then pass the variable to the `using` statement, but this is not a best practice.</span></span> <span data-ttu-id="532f2-125">Nesse caso, após o controle sair do bloco `using`, o objeto permanecerá no escopo, mas provavelmente não terá acesso a seus recursos não gerenciados.</span><span class="sxs-lookup"><span data-stu-id="532f2-125">In this case, after control leaves the `using` block, the object remains in scope but probably has no access to its unmanaged resources.</span></span> <span data-ttu-id="532f2-126">Em outras palavras, ele não é mais totalmente inicializado.</span><span class="sxs-lookup"><span data-stu-id="532f2-126">In other words, it's not fully initialized anymore.</span></span> <span data-ttu-id="532f2-127">Se você tentar usar o objeto fora do bloco `using`, corre o risco de causar o lançamento de uma exceção.</span><span class="sxs-lookup"><span data-stu-id="532f2-127">If you try to use the object outside the `using` block, you risk causing an exception to be thrown.</span></span> <span data-ttu-id="532f2-128">Por esse motivo, geralmente é melhor instanciar o objeto na instrução `using` e limitar seu escopo ao bloco `using`.</span><span class="sxs-lookup"><span data-stu-id="532f2-128">For this reason, it's generally better to instantiate the object in the `using` statement and limit its scope to the `using` block.</span></span>

[!code-csharp[csrefKeywordsNamespace#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace.cs#7)]

<span data-ttu-id="532f2-129">Para obter mais informações sobre como descartar objetos `IDisposable`, veja [Usando objetos que implementam IDisposable](../../../standard/garbage-collection/using-objects.md).</span><span class="sxs-lookup"><span data-stu-id="532f2-129">For more information about disposing of `IDisposable` objects, see [Using objects that implement IDisposable](../../../standard/garbage-collection/using-objects.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="532f2-130">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="532f2-130">C# language specification</span></span>

<span data-ttu-id="532f2-131">Para obter mais informações, consulte [A instrução using](~/_csharplang/spec/statements.md#the-using-statement) na [Especificação da linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="532f2-131">For more information, see [The using statement](~/_csharplang/spec/statements.md#the-using-statement) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="532f2-132">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="532f2-132">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="532f2-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="532f2-133">See also</span></span>

- [<span data-ttu-id="532f2-134">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="532f2-134">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="532f2-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="532f2-135">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="532f2-136">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="532f2-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="532f2-137">Diretiva using</span><span class="sxs-lookup"><span data-stu-id="532f2-137">using Directive</span></span>](using-directive.md)
- [<span data-ttu-id="532f2-138">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="532f2-138">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="532f2-139">Usando objetos que implementam IDisposable</span><span class="sxs-lookup"><span data-stu-id="532f2-139">Using objects that implement IDisposable</span></span>](../../../standard/garbage-collection/using-objects.md)
- [<span data-ttu-id="532f2-140">Interface IDisposable</span><span class="sxs-lookup"><span data-stu-id="532f2-140">IDisposable interface</span></span>](xref:System.IDisposable)
- [<span data-ttu-id="532f2-141">usando a instrução C# em 8,0</span><span class="sxs-lookup"><span data-stu-id="532f2-141">using statement in C# 8.0</span></span>](~/_csharplang/proposals/csharp-8.0/using.md)
