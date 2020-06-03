---
title: Implementar um método DisposeAsync
description: ''
ms.date: 06/02/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: c4f541d5a4f5b5fd31b344a299789d86cd78424c
ms.sourcegitcommit: 5280b2aef60a1ed99002dba44e4b9e7f6c830604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/03/2020
ms.locfileid: "84311010"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="fe671-102">Implementar um método DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="fe671-102">Implement a DisposeAsync method</span></span>

<span data-ttu-id="fe671-103">A <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface foi introduzida como parte do C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="fe671-103">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="fe671-104">Você implementa o <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> método quando precisa executar a limpeza de recursos, assim como faria ao [implementar um método Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="fe671-104">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="fe671-105">No entanto, uma das principais diferenças é que essa implementação permite operações de limpeza assíncronas.</span><span class="sxs-lookup"><span data-stu-id="fe671-105">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="fe671-106">O <xref:System.IAsyncDisposable.DisposeAsync> retorna um <xref:System.Threading.Tasks.ValueTask> que representa a operação de descarte assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fe671-106">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="fe671-107">É comum que, ao implementar a <xref:System.IAsyncDisposable> interface, as classes também implementem a <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="fe671-107">It is typical that when implementing the <xref:System.IAsyncDisposable> interface, classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="fe671-108">Um bom padrão de implementação da <xref:System.IAsyncDisposable> interface é estar preparado para o descarte síncrono ou assíncrono.</span><span class="sxs-lookup"><span data-stu-id="fe671-108">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="fe671-109">Todas as diretrizes para implementar o padrão Dispose se aplicam à implementação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="fe671-109">All of the guidance for implementing the dispose pattern applies to the asynchronous implementation.</span></span> <span data-ttu-id="fe671-110">Este artigo pressupõe que você já esteja familiarizado com a forma de [implementar um método Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="fe671-110">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="fe671-111">DisposeAsync () e DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="fe671-111">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="fe671-112">A <xref:System.IAsyncDisposable> interface declara um único método sem parâmetros, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="fe671-112">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="fe671-113">Qualquer classe não selada deve ter um `DisposeAsyncCore()` método adicional que também retorna um <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="fe671-113">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="fe671-114">Uma `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementação que não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="fe671-114">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="fe671-115">Um `protected virtual ValueTask DisposeAsyncCore()` método cuja assinatura é:</span><span class="sxs-lookup"><span data-stu-id="fe671-115">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

```csharp
protected virtual ValueTask DisposeAsyncCore()
{
}
```

<span data-ttu-id="fe671-116">O `DisposeAsyncCore()` método é `virtual` para que as classes derivadas possam definir limpeza adicional em suas substituições.</span><span class="sxs-lookup"><span data-stu-id="fe671-116">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

### <a name="the-disposeasync-method"></a><span data-ttu-id="fe671-117">O método DisposeAsync ()</span><span class="sxs-lookup"><span data-stu-id="fe671-117">The DisposeAsync() method</span></span>

<span data-ttu-id="fe671-118">O `public` método sem parâmetros `DisposeAsync()` é chamado implicitamente em uma `await using` instrução, e sua finalidade é liberar recursos não gerenciados, executar a limpeza geral e indicar que o finalizador, se houver, não precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="fe671-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, needn't run.</span></span> <span data-ttu-id="fe671-119">Liberar a memória associada a um objeto gerenciado é sempre o domínio do coletor de [lixo](index.md).</span><span class="sxs-lookup"><span data-stu-id="fe671-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="fe671-120">Por isso, ele tem uma implementação padrão:</span><span class="sxs-lookup"><span data-stu-id="fe671-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of managed resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="fe671-121">Uma diferença principal no padrão de descarte assíncrono comparado ao padrão Dispose é que a chamada de <xref:System.IAsyncDisposable.DisposeAsync> para o `Dispose(bool)` método Overload é fornecida `false` como um argumento.</span><span class="sxs-lookup"><span data-stu-id="fe671-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="fe671-122"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>No entanto, ao implementar o método, `true` será passado.</span><span class="sxs-lookup"><span data-stu-id="fe671-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="fe671-123">Isso ajuda a garantir a equivalência funcional com o padrão de descarte síncrono e garante ainda mais que os caminhos de código do finalizador ainda sejam invocados.</span><span class="sxs-lookup"><span data-stu-id="fe671-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="fe671-124">Em outras palavras, o `DisposeAsyncCore()` método descartará os recursos gerenciados de forma assíncrona, de modo que você não deseje descartar também de maneira síncrona.</span><span class="sxs-lookup"><span data-stu-id="fe671-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="fe671-125">Portanto, chame `Dispose(false)` em vez de `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="fe671-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="fe671-126">Implementar o padrão de descarte assíncrono</span><span class="sxs-lookup"><span data-stu-id="fe671-126">Implement the async dispose pattern</span></span>

<span data-ttu-id="fe671-127">Todas as classes não seladas devem ser consideradas uma classe base em potencial, pois elas podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="fe671-127">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="fe671-128">Se você implementar o padrão de descarte assíncrono para qualquer classe base em potencial, você deve fornecer o `protected virtual ValueTask DisposeAsyncCore()` método.</span><span class="sxs-lookup"><span data-stu-id="fe671-128">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="fe671-129">Aqui está um exemplo de implementação do padrão de descarte assíncrono que usa um <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="fe671-129">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="fe671-130">O exemplo anterior usou o <xref:System.Text.Json.Utf8JsonWriter> , para obter mais informações sobre `System.Text.Json` , consulte [migrar de Newtonsoft. JSON para System. Text. JSON](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="fe671-130">The previous example used the <xref:System.Text.Json.Utf8JsonWriter>, for more information on `System.Text.Json`, see, [migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="fe671-131">Usando o descartável assíncrono</span><span class="sxs-lookup"><span data-stu-id="fe671-131">Using async disposable</span></span>

<span data-ttu-id="fe671-132">Para consumir corretamente um objeto que implementa a <xref:System.IAsyncDisposable> interface, use o [Await](../../csharp/language-reference/operators/await.md)e o [uso](../../csharp/language-reference/keywords/using.md) de palavras-chave juntas.</span><span class="sxs-lookup"><span data-stu-id="fe671-132">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using.md) keywords together.</span></span> <span data-ttu-id="fe671-133">Considere o exemplo a seguir, em que a `ExampleAsyncDisposable` classe é instanciada e, em seguida, encapsulada em uma `await using` instrução.</span><span class="sxs-lookup"><span data-stu-id="fe671-133">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated, then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="fe671-134">Use o <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> método de extensão da <xref:System.IAsyncDisposable> interface para configurar como a continuação da tarefa é marshalled em seu contexto ou Agendador original.</span><span class="sxs-lookup"><span data-stu-id="fe671-134">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="fe671-135">Para obter mais informações sobre o `ConfigureAwait` , consulte [perguntas frequentes](https://devblogs.microsoft.com/dotnet/configureawait-faq/)sobre o ConfigureAwait.</span><span class="sxs-lookup"><span data-stu-id="fe671-135">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="fe671-136">Para situações em que o uso de `ConfigureAwait` não é necessário, a `await using` instrução poderia ser simplificada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="fe671-136">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="fe671-137">Além disso, ele poderia ser escrito para usar o escopo implícito de uma [declaração using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="fe671-137">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="fe671-138">Uso empilhado</span><span class="sxs-lookup"><span data-stu-id="fe671-138">Stacked usings</span></span>

<span data-ttu-id="fe671-139">Em situações em que você cria e usa vários objetos que implementam <xref:System.IAsyncDisposable> , é possível que as `using` instruções de empilhamento em condições errônea pudessem impedir chamadas para <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="fe671-139">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="fe671-140">Para ajudar a evitar possíveis preocupações, você deve evitar o empilhamento e, em vez disso, seguir este padrão de exemplo:</span><span class="sxs-lookup"><span data-stu-id="fe671-140">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="fe671-141">Confira também</span><span class="sxs-lookup"><span data-stu-id="fe671-141">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
