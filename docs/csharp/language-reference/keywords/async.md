---
description: async – Referência de C#
title: async – Referência de C#
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 78079d9940ea5363215411acea6b9ca269ff3ae1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160535"
---
# <a name="async-c-reference"></a><span data-ttu-id="46841-103">async (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="46841-103">async (C# Reference)</span></span>

<span data-ttu-id="46841-104">Use o modificador `async` para especificar que um método, uma [expressão lambda](../operators/lambda-expressions.md) ou um [método anônimo](../operators/delegate-operator.md) é assíncrono.</span><span class="sxs-lookup"><span data-stu-id="46841-104">Use the `async` modifier to specify that a method, [lambda expression](../operators/lambda-expressions.md), or [anonymous method](../operators/delegate-operator.md) is asynchronous.</span></span> <span data-ttu-id="46841-105">Se você usar esse modificador em um método ou expressão, ele será referido como um *método assíncrono*.</span><span class="sxs-lookup"><span data-stu-id="46841-105">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="46841-106">O exemplo a seguir define um método assíncrono chamado `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="46841-106">The following example defines an async method named `ExampleMethodAsync`:</span></span>

```csharp
public async Task<int> ExampleMethodAsync()
{
    //...
}
```

<span data-ttu-id="46841-107">Se você for novo na programação assíncrona ou não entender como um método assíncrono usa o [ `await` operador](../operators/await.md) para executar trabalhos potencialmente de longa duração sem bloquear o thread do chamador, leia a introdução em [programação assíncrona com Async e Await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="46841-107">If you're new to asynchronous programming or do not understand how an async method uses the [`await` operator](../operators/await.md) to do potentially long-running work without blocking the caller's thread, read the introduction in [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="46841-108">O código a seguir é encontrado dentro de um método assíncrono e chama o método <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="46841-108">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span>

```csharp
string contents = await httpClient.GetStringAsync(requestUrl);
```

<span data-ttu-id="46841-109">Um método assíncrono será executado de forma síncrona até atingir sua primeira expressão `await` e, nesse ponto, ele será suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="46841-109">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="46841-110">Enquanto isso, o controle será retornado ao chamador do método, como exibido no exemplo da próxima seção.</span><span class="sxs-lookup"><span data-stu-id="46841-110">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>

<span data-ttu-id="46841-111">Se o método que a palavra-chave `async` modifica não contiver uma expressão ou instrução `await`, ele será executado de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="46841-111">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="46841-112">Um aviso do compilador o alertará sobre quaisquer métodos assíncronos que não contenham instruções `await`, pois essa situação poderá indicar um erro.</span><span class="sxs-lookup"><span data-stu-id="46841-112">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="46841-113">Consulte [Aviso do compilador (nível 1) CS4014](../compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="46841-113">See [Compiler Warning (level 1) CS4014](../compiler-messages/cs4014.md).</span></span>

 <span data-ttu-id="46841-114">A palavra-chave `async` é contextual, pois ela será uma palavra-chave somente quando modificar um método, uma expressão lambda ou um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="46841-114">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="46841-115">Em todos os outros contextos, ela será interpretada como um identificador.</span><span class="sxs-lookup"><span data-stu-id="46841-115">In all other contexts, it's interpreted as an identifier.</span></span>

## <a name="example"></a><span data-ttu-id="46841-116">Exemplo</span><span class="sxs-lookup"><span data-stu-id="46841-116">Example</span></span>

<span data-ttu-id="46841-117">O exemplo a seguir mostra a estrutura e o fluxo de controle entre um manipulador de eventos assíncronos, `StartButton_Click` e um método assíncrono, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="46841-117">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="46841-118">O resultado do método assíncrono é o número de caracteres de uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="46841-118">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="46841-119">O código será adequado para um aplicativo do WPF (Windows Presentation Foundation) ou da Windows Store que você criar no Visual Studio, consulte os comentários do código para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="46841-119">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>

<span data-ttu-id="46841-120">Você pode executar esse código no Visual Studio como um aplicativo do WPF (Windows Presentation Foundation) ou um aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="46841-120">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="46841-121">Você precisa de um controle de botão chamado `StartButton` e de um controle de caixa de texto chamado `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="46841-121">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="46841-122">Lembre-se de definir os nomes e o manipulador para que você tenha algo assim:</span><span class="sxs-lookup"><span data-stu-id="46841-122">Remember to set the names and handler so that you have something like this:</span></span>

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"
        Click="StartButton_Click" Name="StartButton"/>
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>
```

<span data-ttu-id="46841-123">Para executar o código como um aplicativo WPF:</span><span class="sxs-lookup"><span data-stu-id="46841-123">To run the code as a WPF app:</span></span>

- <span data-ttu-id="46841-124">Cole este código na classe `MainWindow` em MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="46841-124">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>
- <span data-ttu-id="46841-125">Adicione uma referência a System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="46841-125">Add a reference to System.Net.Http.</span></span>
- <span data-ttu-id="46841-126">Adicione uma diretiva `using` a System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="46841-126">Add a `using` directive for System.Net.Http.</span></span>

<span data-ttu-id="46841-127">Para executar o código como um aplicativo da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="46841-127">To run the code as a Windows Store app:</span></span>

- <span data-ttu-id="46841-128">Cole este código na classe `MainPage` em MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="46841-128">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>
- <span data-ttu-id="46841-129">Adicione usando diretivas para System.Net.Http e System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="46841-129">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>

[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]

> [!IMPORTANT]
> <span data-ttu-id="46841-130">Para obter mais informações sobre tarefas e o código que é executado enquanto aguarda uma tarefa, consulte [programação assíncrona com Async e Await](../../programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="46841-130">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous programming with async and await](../../programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="46841-131">Para obter um exemplo de console completo que usa elementos semelhantes, consulte [processar tarefas assíncronas conforme elas são concluídas (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span><span class="sxs-lookup"><span data-stu-id="46841-131">For a full console example that uses similar elements, see [Process asynchronous tasks as they complete (C#)](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md).</span></span>

## <a name="return-types"></a><span data-ttu-id="46841-132">Tipos de retorno</span><span class="sxs-lookup"><span data-stu-id="46841-132">Return Types</span></span>

<span data-ttu-id="46841-133">Um método assíncrono pode conter os seguintes tipos de retorno:</span><span class="sxs-lookup"><span data-stu-id="46841-133">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="46841-134">[void](../builtin-types/void.md).</span><span class="sxs-lookup"><span data-stu-id="46841-134">[void](../builtin-types/void.md).</span></span> <span data-ttu-id="46841-135">Os métodos `async void` geralmente são desencorajados para código que não são manipuladores de eventos, porque os chamadores não podem `await` esses métodos e devem implementar um mecanismo diferente para relatar a conclusão bem-sucedida ou condições de erro.</span><span class="sxs-lookup"><span data-stu-id="46841-135">`async void` methods are generally discouraged for code other than event handlers because callers cannot `await` those methods and must implement a different mechanism to report successful completion or error conditions.</span></span>
- <span data-ttu-id="46841-136">Começando com o C# 7.0, qualquer tipo que tenha um método acessível `GetAwaiter`.</span><span class="sxs-lookup"><span data-stu-id="46841-136">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="46841-137">O tipo `System.Threading.Tasks.ValueTask<TResult>` é um exemplo de uma implementação assim.</span><span class="sxs-lookup"><span data-stu-id="46841-137">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="46841-138">Ele está disponível ao adicionar o pacote NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="46841-138">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span>

<span data-ttu-id="46841-139">O método assíncrono não pode declarar os parâmetros [in](./in-parameter-modifier.md), [ref](./ref.md) nem [out](./out-parameter-modifier.md) e também não pode ter um [valor retornado por referência](../../programming-guide/classes-and-structs/ref-returns.md), mas pode chamar métodos que tenham esses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="46841-139">The async method can't declare any [in](./in-parameter-modifier.md), [ref](./ref.md) or [out](./out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>

<span data-ttu-id="46841-140">Você especificará `Task<TResult>` como o tipo de retorno de um método assíncrono se a instrução [return](./return.md) do método especificar um operando do tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="46841-140">You specify `Task<TResult>` as the return type of an async method if the [return](./return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="46841-141">Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído.</span><span class="sxs-lookup"><span data-stu-id="46841-141">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="46841-142">Isto é, uma chamada ao método retorna uma `Task`, mas quando a `Task` for concluída, qualquer expressão `await` que esteja aguardando a `Task` será avaliada como `void`.</span><span class="sxs-lookup"><span data-stu-id="46841-142">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>

<span data-ttu-id="46841-143">O tipo de retorno `void` é usado principalmente para definir manipuladores de eventos que exigem esse tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="46841-143">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="46841-144">O chamador de um método assíncrono de retorno `void` não pode aguardá-lo e capturar exceções acionadas pelo método.</span><span class="sxs-lookup"><span data-stu-id="46841-144">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>

<span data-ttu-id="46841-145">A partir do C# 7.0, você retorna outro tipo, geralmente um tipo de valor, que tenha um método `GetAwaiter` para minimizar as alocações de memória nas seções do código críticas ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="46841-145">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to minimize memory allocations in performance-critical sections of code.</span></span>

<span data-ttu-id="46841-146">Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="46841-146">For more information and examples, see [Async Return Types](../../programming-guide/concepts/async/async-return-types.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="46841-147">Confira também</span><span class="sxs-lookup"><span data-stu-id="46841-147">See also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>
- [<span data-ttu-id="46841-148">await</span><span class="sxs-lookup"><span data-stu-id="46841-148">await</span></span>](../operators/await.md)
- [<span data-ttu-id="46841-149">Programação assíncrona com Async e Await</span><span class="sxs-lookup"><span data-stu-id="46841-149">Asynchronous programming with async and await</span></span>](../../programming-guide/concepts/async/index.md)
- [<span data-ttu-id="46841-150">Processar tarefas assíncronas conforme elas são concluídas</span><span class="sxs-lookup"><span data-stu-id="46841-150">Process asynchronous tasks as they complete</span></span>](../../programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)
