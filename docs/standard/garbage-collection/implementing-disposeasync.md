---
title: Implementar um método DisposeAsync
description: Saiba como implementar os métodos DisposeAsync e DisposeAsyncCore para executar a limpeza assíncrona de recursos.
author: IEvangelist
ms.author: dapine
ms.date: 08/25/2020
ms.technology: dotnet-standard
dev_langs:
- csharp
helpviewer_keywords:
- DisposeAsync method
- garbage collection, DisposeAsync method
ms.openlocfilehash: 268cea7584040ad92e2da75e5e03112480cda93c
ms.sourcegitcommit: 2560a355c76b0a04cba0d34da870df9ad94ceca3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/28/2020
ms.locfileid: "89053172"
---
# <a name="implement-a-disposeasync-method"></a><span data-ttu-id="34ebc-103">Implementar um método DisposeAsync</span><span class="sxs-lookup"><span data-stu-id="34ebc-103">Implement a DisposeAsync method</span></span>

<span data-ttu-id="34ebc-104">A <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface foi introduzida como parte do C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="34ebc-104">The <xref:System.IAsyncDisposable?displayProperty=nameWithType> interface was introduced as part of C# 8.0.</span></span> <span data-ttu-id="34ebc-105">Você implementa o <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> método quando precisa executar a limpeza de recursos, assim como faria ao [implementar um método Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="34ebc-105">You implement the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method when you need to perform resource cleanup, just as you would when [implementing a Dispose method](implementing-dispose.md).</span></span> <span data-ttu-id="34ebc-106">No entanto, uma das principais diferenças é que essa implementação permite operações de limpeza assíncronas.</span><span class="sxs-lookup"><span data-stu-id="34ebc-106">One of the key differences however, is that this implementation allows for asynchronous cleanup operations.</span></span> <span data-ttu-id="34ebc-107">O <xref:System.IAsyncDisposable.DisposeAsync> retorna um <xref:System.Threading.Tasks.ValueTask> que representa a operação de descarte assíncrona.</span><span class="sxs-lookup"><span data-stu-id="34ebc-107">The <xref:System.IAsyncDisposable.DisposeAsync> returns a <xref:System.Threading.Tasks.ValueTask> that represents the asynchronous dispose operation.</span></span>

<span data-ttu-id="34ebc-108">É comum ao implementar a <xref:System.IAsyncDisposable> interface que as classes também implementarão a <xref:System.IDisposable> interface.</span><span class="sxs-lookup"><span data-stu-id="34ebc-108">It is typical when implementing the <xref:System.IAsyncDisposable> interface that classes will also implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="34ebc-109">Um bom padrão de implementação da <xref:System.IAsyncDisposable> interface é estar preparado para o descarte síncrono ou assíncrono.</span><span class="sxs-lookup"><span data-stu-id="34ebc-109">A good implementation pattern of the <xref:System.IAsyncDisposable> interface is to be prepared for either synchronous, or asynchronous dispose.</span></span> <span data-ttu-id="34ebc-110">Todas as diretrizes para implementar o padrão Dispose também se aplicam à implementação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="34ebc-110">All of the guidance for implementing the dispose pattern also applies to the asynchronous implementation.</span></span> <span data-ttu-id="34ebc-111">Este artigo pressupõe que você já esteja familiarizado com a forma de [implementar um método Dispose](implementing-dispose.md).</span><span class="sxs-lookup"><span data-stu-id="34ebc-111">This article assumes that you're already familiar with how to [implement a Dispose method](implementing-dispose.md).</span></span>

## <a name="disposeasync-and-disposeasynccore"></a><span data-ttu-id="34ebc-112">DisposeAsync () e DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="34ebc-112">DisposeAsync() and DisposeAsyncCore()</span></span>

<span data-ttu-id="34ebc-113">A <xref:System.IAsyncDisposable> interface declara um único método sem parâmetros, <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="34ebc-113">The <xref:System.IAsyncDisposable> interface declares a single parameterless method, <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="34ebc-114">Qualquer classe não selada deve ter um `DisposeAsyncCore()` método adicional que também retorna um <xref:System.Threading.Tasks.ValueTask> .</span><span class="sxs-lookup"><span data-stu-id="34ebc-114">Any non-sealed class should have an additional `DisposeAsyncCore()` method that also returns a <xref:System.Threading.Tasks.ValueTask>.</span></span>

- <span data-ttu-id="34ebc-115">Uma `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementação que não tem parâmetros.</span><span class="sxs-lookup"><span data-stu-id="34ebc-115">A `public` <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> implementation that has no parameters.</span></span>
- <span data-ttu-id="34ebc-116">Um `protected virtual ValueTask DisposeAsyncCore()` método cuja assinatura é:</span><span class="sxs-lookup"><span data-stu-id="34ebc-116">A `protected virtual ValueTask DisposeAsyncCore()` method whose signature is:</span></span>

  ```csharp
  protected virtual ValueTask DisposeAsyncCore()
  {
  }
  ```

### <a name="the-disposeasync-method"></a><span data-ttu-id="34ebc-117">O método DisposeAsync ()</span><span class="sxs-lookup"><span data-stu-id="34ebc-117">The DisposeAsync() method</span></span>

<span data-ttu-id="34ebc-118">O `public` método sem parâmetros `DisposeAsync()` é chamado implicitamente em uma `await using` instrução, e sua finalidade é liberar recursos não gerenciados, executar a limpeza geral e indicar que o finalizador, se houver, não precisa ser executado.</span><span class="sxs-lookup"><span data-stu-id="34ebc-118">The `public` parameterless `DisposeAsync()` method is called implicitly in an `await using` statement, and its purpose is to free unmanaged resources, perform general cleanup, and to indicate that the finalizer, if one is present, need not run.</span></span> <span data-ttu-id="34ebc-119">Liberar a memória associada a um objeto gerenciado é sempre o domínio do coletor de [lixo](index.md).</span><span class="sxs-lookup"><span data-stu-id="34ebc-119">Freeing the memory associated with a managed object is always the domain of the [garbage collector](index.md).</span></span> <span data-ttu-id="34ebc-120">Por isso, ele tem uma implementação padrão:</span><span class="sxs-lookup"><span data-stu-id="34ebc-120">Because of this, it has a standard implementation:</span></span>

```csharp
public async ValueTask DisposeAsync()
{
    // Perform async cleanup.
    await DisposeAsyncCore();

    // Dispose of unmanaged resources.
    Dispose(false);
    // Suppress finalization.
    GC.SuppressFinalize(this);
}
```

> [!NOTE]
> <span data-ttu-id="34ebc-121">Uma diferença principal no padrão de descarte assíncrono comparado ao padrão Dispose é que a chamada de <xref:System.IAsyncDisposable.DisposeAsync> para o `Dispose(bool)` método Overload é fornecida `false` como um argumento.</span><span class="sxs-lookup"><span data-stu-id="34ebc-121">One primary difference in the async dispose pattern compared to the dispose pattern, is that the call from <xref:System.IAsyncDisposable.DisposeAsync> to the `Dispose(bool)` overload method is given `false` as an argument.</span></span> <span data-ttu-id="34ebc-122"><xref:System.IDisposable.Dispose?displayProperty=nameWithType>No entanto, ao implementar o método, `true` será passado.</span><span class="sxs-lookup"><span data-stu-id="34ebc-122">When implementing the <xref:System.IDisposable.Dispose?displayProperty=nameWithType> method, however; `true` is passed instead.</span></span> <span data-ttu-id="34ebc-123">Isso ajuda a garantir a equivalência funcional com o padrão de descarte síncrono e garante ainda mais que os caminhos de código do finalizador ainda sejam invocados.</span><span class="sxs-lookup"><span data-stu-id="34ebc-123">This helps ensure functional equivalence with the synchronous dispose pattern, and further ensures that finalizer code paths still get invoked.</span></span> <span data-ttu-id="34ebc-124">Em outras palavras, o `DisposeAsyncCore()` método descartará os recursos gerenciados de forma assíncrona, de modo que você não deseje descartar também de maneira síncrona.</span><span class="sxs-lookup"><span data-stu-id="34ebc-124">In other words, the `DisposeAsyncCore()` method will dispose of managed resources asynchronously, so you don't want to dispose of them synchronously as well.</span></span> <span data-ttu-id="34ebc-125">Portanto, chame `Dispose(false)` em vez de `Dispose(true)` .</span><span class="sxs-lookup"><span data-stu-id="34ebc-125">Therefore, call `Dispose(false)` instead of `Dispose(true)`.</span></span>

### <a name="the-disposeasynccore-method"></a><span data-ttu-id="34ebc-126">O método DisposeAsyncCore ()</span><span class="sxs-lookup"><span data-stu-id="34ebc-126">The DisposeAsyncCore() method</span></span>

<span data-ttu-id="34ebc-127">O `DisposeAsyncCore()` método destina-se a executar a limpeza assíncrona de recursos gerenciados ou para chamadas em cascata para o `DisposeAsync()` .</span><span class="sxs-lookup"><span data-stu-id="34ebc-127">The `DisposeAsyncCore()` method is intended to perform the asynchronous cleanup of managed resources or for cascading calls to `DisposeAsync()`.</span></span> <span data-ttu-id="34ebc-128">Ele encapsula as operações comuns de limpeza assíncrona quando uma subclasse herda uma classe base que é uma implementação de <xref:System.IAsyncDisposable> .</span><span class="sxs-lookup"><span data-stu-id="34ebc-128">It encapsulates the common asynchronous cleanup operations when a subclass inherits a base class that is an implementation of <xref:System.IAsyncDisposable>.</span></span> <span data-ttu-id="34ebc-129">O `DisposeAsyncCore()` método é `virtual` para que as classes derivadas possam definir limpeza adicional em suas substituições.</span><span class="sxs-lookup"><span data-stu-id="34ebc-129">The `DisposeAsyncCore()` method is `virtual` so that derived classes can define additional cleanup in their overrides.</span></span>

> [!TIP]
> <span data-ttu-id="34ebc-130">Se uma implementação do <xref:System.IAsyncDisposable> for `sealed` , o `DisposeAsyncCore()` método não será necessário e a limpeza assíncrona poderá ser executada diretamente no <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="34ebc-130">If an implementation of <xref:System.IAsyncDisposable> is `sealed`, the `DisposeAsyncCore()` method is not needed, and the asynchronous cleanup can be performed directly in the <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType> method.</span></span>

## <a name="implement-the-async-dispose-pattern"></a><span data-ttu-id="34ebc-131">Implementar o padrão de descarte assíncrono</span><span class="sxs-lookup"><span data-stu-id="34ebc-131">Implement the async dispose pattern</span></span>

<span data-ttu-id="34ebc-132">Todas as classes não seladas devem ser consideradas uma classe base em potencial, pois elas podem ser herdadas.</span><span class="sxs-lookup"><span data-stu-id="34ebc-132">All non-sealed classes should be considered a potential base class, because they could be inherited.</span></span> <span data-ttu-id="34ebc-133">Se você implementar o padrão de descarte assíncrono para qualquer classe base em potencial, você deve fornecer o `protected virtual ValueTask DisposeAsyncCore()` método.</span><span class="sxs-lookup"><span data-stu-id="34ebc-133">If you implement the async dispose pattern for any potential base class, you must provide the `protected virtual ValueTask DisposeAsyncCore()` method.</span></span> <span data-ttu-id="34ebc-134">Aqui está um exemplo de implementação do padrão de descarte assíncrono que usa um <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="34ebc-134">Here is an example implementation of the async dispose pattern that uses a <xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/disposeasync.cs":::

<span data-ttu-id="34ebc-135">O exemplo anterior usa o <xref:System.Text.Json.Utf8JsonWriter> .</span><span class="sxs-lookup"><span data-stu-id="34ebc-135">The preceding example uses the <xref:System.Text.Json.Utf8JsonWriter>.</span></span> <span data-ttu-id="34ebc-136">Para obter mais informações sobre `System.Text.Json` o, consulte [como migrar do Newtonsoft.Jspara o System.Text.Jsno](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="34ebc-136">For more information about `System.Text.Json`, see [How to migrate from Newtonsoft.Json to System.Text.Json](../serialization/system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

## <a name="using-async-disposable"></a><span data-ttu-id="34ebc-137">Usando o descartável assíncrono</span><span class="sxs-lookup"><span data-stu-id="34ebc-137">Using async disposable</span></span>

<span data-ttu-id="34ebc-138">Para consumir corretamente um objeto que implementa a <xref:System.IAsyncDisposable> interface, use o [Await](../../csharp/language-reference/operators/await.md)e o [uso](../../csharp/language-reference/keywords/using-statement.md) de palavras-chave juntas.</span><span class="sxs-lookup"><span data-stu-id="34ebc-138">To properly consume an object that implements the <xref:System.IAsyncDisposable> interface, you use the [await](../../csharp/language-reference/operators/await.md), and [using](../../csharp/language-reference/keywords/using-statement.md) keywords together.</span></span> <span data-ttu-id="34ebc-139">Considere o exemplo a seguir, em que a `ExampleAsyncDisposable` classe é instanciada e, em seguida, encapsulada em uma `await using` instrução.</span><span class="sxs-lookup"><span data-stu-id="34ebc-139">Consider the following example, where the `ExampleAsyncDisposable` class is instantiated and then wrapped in an `await using` statement.</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/proper-await-using.cs":::

> [!IMPORTANT]
> <span data-ttu-id="34ebc-140">Use o <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> método de extensão da <xref:System.IAsyncDisposable> interface para configurar como a continuação da tarefa é marshalled em seu contexto ou Agendador original.</span><span class="sxs-lookup"><span data-stu-id="34ebc-140">Use the <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)> extension method of the <xref:System.IAsyncDisposable> interface to configure how the continuation of the task is marshalled on its original context or scheduler.</span></span> <span data-ttu-id="34ebc-141">Para obter mais informações sobre o `ConfigureAwait` , consulte [perguntas frequentes](https://devblogs.microsoft.com/dotnet/configureawait-faq/)sobre o ConfigureAwait.</span><span class="sxs-lookup"><span data-stu-id="34ebc-141">For more information on `ConfigureAwait`, see [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq/).</span></span>

<span data-ttu-id="34ebc-142">Para situações em que o uso de `ConfigureAwait` não é necessário, a `await using` instrução poderia ser simplificada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="34ebc-142">For situations where the usage of `ConfigureAwait` is not needed, the `await using` statement could be simplified as follows:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-non-configureawait.cs":::

<span data-ttu-id="34ebc-143">Além disso, ele poderia ser escrito para usar o escopo implícito de uma [declaração using](../../csharp/whats-new/csharp-8.md#using-declarations).</span><span class="sxs-lookup"><span data-stu-id="34ebc-143">Furthermore, it could be written to use the implicit scoping of a [using declaration](../../csharp/whats-new/csharp-8.md#using-declarations).</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/await-using-declaration.cs":::

## <a name="stacked-usings"></a><span data-ttu-id="34ebc-144">Uso empilhado</span><span class="sxs-lookup"><span data-stu-id="34ebc-144">Stacked usings</span></span>

<span data-ttu-id="34ebc-145">Em situações em que você cria e usa vários objetos que implementam <xref:System.IAsyncDisposable> , é possível que as `using` instruções de empilhamento em condições errônea pudessem impedir chamadas para <xref:System.IAsyncDisposable.DisposeAsync> .</span><span class="sxs-lookup"><span data-stu-id="34ebc-145">In situations where you create and use multiple objects that implement <xref:System.IAsyncDisposable>, it's possible that stacking `using` statements in errant conditions could prevent calls to <xref:System.IAsyncDisposable.DisposeAsync>.</span></span> <span data-ttu-id="34ebc-146">Para ajudar a evitar possíveis preocupações, você deve evitar o empilhamento e, em vez disso, seguir este padrão de exemplo:</span><span class="sxs-lookup"><span data-stu-id="34ebc-146">In order to help prevent potential concern, you should avoid stacking, and instead follow this example pattern:</span></span>

:::code language="csharp" source="../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.asyncdisposable/stacked-await-usings.cs":::

## <a name="see-also"></a><span data-ttu-id="34ebc-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="34ebc-147">See also</span></span>

- <xref:System.IAsyncDisposable>
- <xref:System.IAsyncDisposable.DisposeAsync?displayProperty=nameWithType>
- <xref:System.Threading.Tasks.TaskAsyncEnumerableExtensions.ConfigureAwait(System.IAsyncDisposable,System.Boolean)>
