---
title: async (Referência de C#)
ms.date: 05/22/2017
f1_keywords:
- async_CSharpKeyword
helpviewer_keywords:
- async keyword [C#]
- async method [C#]
- async [C#]
ms.assetid: 16f14f09-b2ce-42c7-a875-e4eca5d50674
ms.openlocfilehash: 10f1d62c5aa29f2074106ab102775b9a0283d646
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43510956"
---
# <a name="async-c-reference"></a><span data-ttu-id="4ff60-102">async (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4ff60-102">async (C# Reference)</span></span>
<span data-ttu-id="4ff60-103">Use o modificador `async` para especificar que um método, uma [expressão lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) ou um [método anônimo](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) é assíncrono.</span><span class="sxs-lookup"><span data-stu-id="4ff60-103">Use the `async` modifier to specify that a method, [lambda expression](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md), or [anonymous method](../../../csharp/programming-guide/statements-expressions-operators/anonymous-methods.md) is asynchronous.</span></span> <span data-ttu-id="4ff60-104">Se você usar esse modificador em um método ou expressão, ele será referido como um *método assíncrono*.</span><span class="sxs-lookup"><span data-stu-id="4ff60-104">If you use this modifier on a method or expression, it's referred to as an *async method*.</span></span> <span data-ttu-id="4ff60-105">O exemplo a seguir define um método assíncrono chamado `ExampleMethodAsync`:</span><span class="sxs-lookup"><span data-stu-id="4ff60-105">The following example defines an async method named `ExampleMethodAsync`:</span></span> 
  
```csharp  
public async Task<int> ExampleMethodAsync()  
{  
    // . . . .  
}  
```  
 
<span data-ttu-id="4ff60-106">Se você for iniciante em programação assíncrona ou não compreender como um método assíncrono usa a palavra-chave `await` para fazer trabalhos potencialmente longos sem bloquear o thread do chamador, leia a introdução em [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ff60-106">If you're new to asynchronous programming or do not understand how an async method uses the `await` keyword to do potentially long-running work without blocking the caller’s thread, read the introduction in [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="4ff60-107">O código a seguir é encontrado dentro de um método assíncrono e chama o método <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="4ff60-107">The following code is found inside an async method and calls the <xref:System.Net.Http.HttpClient.GetStringAsync%2a?displayProperty=nameWithType> method:</span></span> 
  
```csharp  
string contents = await httpClient.GetStringAsync(requestUrl);  
```  
  
<span data-ttu-id="4ff60-108">Um método assíncrono será executado de forma síncrona até atingir sua primeira expressão `await` e, nesse ponto, ele será suspenso até que a tarefa aguardada seja concluída.</span><span class="sxs-lookup"><span data-stu-id="4ff60-108">An async method runs synchronously until it reaches its first `await` expression, at which point the method is suspended until the awaited task is complete.</span></span> <span data-ttu-id="4ff60-109">Enquanto isso, o controle será retornado ao chamador do método, como exibido no exemplo da próxima seção.</span><span class="sxs-lookup"><span data-stu-id="4ff60-109">In the meantime, control returns to the caller of the method, as the example in the next section shows.</span></span>  
  
<span data-ttu-id="4ff60-110">Se o método que a palavra-chave `async` modifica não contiver uma expressão ou instrução `await`, ele será executado de forma síncrona.</span><span class="sxs-lookup"><span data-stu-id="4ff60-110">If the method that the `async` keyword modifies doesn't contain an `await` expression or statement, the method executes synchronously.</span></span> <span data-ttu-id="4ff60-111">Um aviso do compilador o alertará sobre quaisquer métodos assíncronos que não contenham instruções `await`, pois essa situação poderá indicar um erro.</span><span class="sxs-lookup"><span data-stu-id="4ff60-111">A compiler warning alerts you to any async methods that don't contain `await` statements, because that situation might indicate an error.</span></span> <span data-ttu-id="4ff60-112">Consulte [Aviso do compilador (nível 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span><span class="sxs-lookup"><span data-stu-id="4ff60-112">See [Compiler Warning (level 1) CS4014](../../../csharp/language-reference/compiler-messages/cs4014.md).</span></span>  
  
 <span data-ttu-id="4ff60-113">A palavra-chave `async` é contextual, pois ela será uma palavra-chave somente quando modificar um método, uma expressão lambda ou um método anônimo.</span><span class="sxs-lookup"><span data-stu-id="4ff60-113">The `async` keyword is contextual in that it's a keyword only when it modifies a method, a lambda expression, or an anonymous method.</span></span> <span data-ttu-id="4ff60-114">Em todos os outros contextos, ela será interpretada como um identificador.</span><span class="sxs-lookup"><span data-stu-id="4ff60-114">In all other contexts, it's interpreted as an identifier.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4ff60-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4ff60-115">Example</span></span>  
<span data-ttu-id="4ff60-116">O exemplo a seguir mostra a estrutura e o fluxo de controle entre um manipulador de eventos assíncronos, `StartButton_Click` e um método assíncrono, `ExampleMethodAsync`.</span><span class="sxs-lookup"><span data-stu-id="4ff60-116">The following example shows the structure and flow of control between an async event handler, `StartButton_Click`, and an async method, `ExampleMethodAsync`.</span></span> <span data-ttu-id="4ff60-117">O resultado do método assíncrono é o número de caracteres de uma página da Web.</span><span class="sxs-lookup"><span data-stu-id="4ff60-117">The result from the async method is the number of characters of a web page.</span></span> <span data-ttu-id="4ff60-118">O código será adequado para um aplicativo do WPF (Windows Presentation Foundation) ou da Windows Store que você criar no Visual Studio, consulte os comentários do código para configurar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4ff60-118">The code is suitable for a Windows Presentation Foundation (WPF) app or Windows Store app that you create in Visual Studio; see the code comments for setting up the app.</span></span>  

<span data-ttu-id="4ff60-119">Você pode executar esse código no Visual Studio como um aplicativo do WPF (Windows Presentation Foundation) ou um aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="4ff60-119">You can run this code in Visual Studio as a Windows Presentation Foundation (WPF) app or a Windows Store app.</span></span> <span data-ttu-id="4ff60-120">Você precisa de um controle de botão chamado `StartButton` e de um controle de caixa de texto chamado `ResultsTextBox`.</span><span class="sxs-lookup"><span data-stu-id="4ff60-120">You need a Button control named `StartButton` and a Textbox control named `ResultsTextBox`.</span></span> <span data-ttu-id="4ff60-121">Lembre-se de definir os nomes e o manipulador para que você tenha algo assim:</span><span class="sxs-lookup"><span data-stu-id="4ff60-121">Remember to set the names and handler so that you have something like this:</span></span>  

```xaml
<Button Content="Button" HorizontalAlignment="Left" Margin="88,77,0,0" VerticalAlignment="Top" Width="75"  
        Click="StartButton_Click" Name="StartButton"/>  
<TextBox HorizontalAlignment="Left" Height="137" Margin="88,140,0,0" TextWrapping="Wrap"   
         Text="&lt;Enter a URL&gt;" VerticalAlignment="Top" Width="310" Name="ResultsTextBox"/>  
```
  
<span data-ttu-id="4ff60-122">Para executar o código como um aplicativo WPF:</span><span class="sxs-lookup"><span data-stu-id="4ff60-122">To run the code as a WPF app:</span></span>  

- <span data-ttu-id="4ff60-123">Cole este código na classe `MainWindow` em MainWindow.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4ff60-123">Paste this code into the `MainWindow` class in MainWindow.xaml.cs.</span></span>  
- <span data-ttu-id="4ff60-124">Adicione uma referência a System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="4ff60-124">Add a reference to System.Net.Http.</span></span>  
- <span data-ttu-id="4ff60-125">Adicione uma diretiva `using` a System.Net.Http.</span><span class="sxs-lookup"><span data-stu-id="4ff60-125">Add a `using` directive for System.Net.Http.</span></span>  
  
<span data-ttu-id="4ff60-126">Para executar o código como um aplicativo da Windows Store:</span><span class="sxs-lookup"><span data-stu-id="4ff60-126">To run the code as a Windows Store app:</span></span>  
- <span data-ttu-id="4ff60-127">Cole este código na classe `MainPage` em MainPage.xaml.cs.</span><span class="sxs-lookup"><span data-stu-id="4ff60-127">Paste this code into the `MainPage` class in MainPage.xaml.cs.</span></span>  
- <span data-ttu-id="4ff60-128">Adicione usando diretivas para System.Net.Http e System.Threading.Tasks.</span><span class="sxs-lookup"><span data-stu-id="4ff60-128">Add using directives for System.Net.Http and System.Threading.Tasks.</span></span>  
  
[!code-csharp[wpf-async](../../../../samples/snippets/csharp/language-reference/keywords/async/wpf/mainwindow.xaml.cs#1)]
  
> [!IMPORTANT]
>  <span data-ttu-id="4ff60-129">Para obter mais informações sobre tarefas e o código que é executado enquanto aguarda uma tarefa, consulte [Programação assíncrona com async e await](../../../csharp/programming-guide/concepts/async/index.md).</span><span class="sxs-lookup"><span data-stu-id="4ff60-129">For more information about tasks and the code that executes while waiting for a task, see [Asynchronous Programming with async and await](../../../csharp/programming-guide/concepts/async/index.md).</span></span> <span data-ttu-id="4ff60-130">Para obter um exemplo WPF completo que usa elementos semelhantes, consulte o [Passo a passo: acessando a Web usando async e await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span><span class="sxs-lookup"><span data-stu-id="4ff60-130">For a full WPF example that uses similar elements, see [Walkthrough: Accessing the Web by Using Async and Await](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md).</span></span>  
  
## <a name="return-types"></a><span data-ttu-id="4ff60-131">Tipos de Retorno</span><span class="sxs-lookup"><span data-stu-id="4ff60-131">Return Types</span></span>  
<span data-ttu-id="4ff60-132">Um método assíncrono pode conter os seguintes tipos de retorno:</span><span class="sxs-lookup"><span data-stu-id="4ff60-132">An async method can have the following return types:</span></span>

- <xref:System.Threading.Tasks.Task>
- <xref:System.Threading.Tasks.Task%601>
- <span data-ttu-id="4ff60-133">[void](../../../csharp/language-reference/keywords/void.md), que só deve ser usado para manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="4ff60-133">[void](../../../csharp/language-reference/keywords/void.md), which should only be used for event handlers.</span></span>
- <span data-ttu-id="4ff60-134">Começando com o C# 7.0, qualquer tipo que tenha um método acessível `GetAwaiter`.</span><span class="sxs-lookup"><span data-stu-id="4ff60-134">Starting with C# 7.0, any type that has an accessible `GetAwaiter` method.</span></span> <span data-ttu-id="4ff60-135">O tipo `System.Threading.Tasks.ValueTask<TResult>` é um exemplo de uma implementação assim.</span><span class="sxs-lookup"><span data-stu-id="4ff60-135">The `System.Threading.Tasks.ValueTask<TResult>` type is one such implementation.</span></span> <span data-ttu-id="4ff60-136">Ele está disponível ao adicionar o pacote NuGet `System.Threading.Tasks.Extensions`.</span><span class="sxs-lookup"><span data-stu-id="4ff60-136">It is available by adding the NuGet package `System.Threading.Tasks.Extensions`.</span></span> 

<span data-ttu-id="4ff60-137">O método assíncrono não pode declarar os parâmetros [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) nem [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) e também não pode ter um [valor retornado por referência](../../programming-guide/classes-and-structs/ref-returns.md), mas pode chamar métodos que tenham esses parâmetros.</span><span class="sxs-lookup"><span data-stu-id="4ff60-137">The async method can't declare any [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters, nor can it have a [reference return value](../../programming-guide/classes-and-structs/ref-returns.md), but it can call methods that have such parameters.</span></span>  
  
<span data-ttu-id="4ff60-138">Você especificará `Task<TResult>` como o tipo de retorno de um método assíncrono se a instrução [return](../../../csharp/language-reference/keywords/return.md) do método especificar um operando do tipo `TResult`.</span><span class="sxs-lookup"><span data-stu-id="4ff60-138">You specify `Task<TResult>` as the return type of an async method if the [return](../../../csharp/language-reference/keywords/return.md) statement of the method specifies an operand of type `TResult`.</span></span> <span data-ttu-id="4ff60-139">Você usará `Task` se nenhum valor significativo for retornado quando o método for concluído.</span><span class="sxs-lookup"><span data-stu-id="4ff60-139">You use `Task` if no meaningful value is returned when the method is completed.</span></span> <span data-ttu-id="4ff60-140">Isto é, uma chamada ao método retorna uma `Task`, mas quando a `Task` for concluída, qualquer expressão `await` que esteja aguardando a `Task` será avaliada como `void`.</span><span class="sxs-lookup"><span data-stu-id="4ff60-140">That is, a call to the method returns a `Task`, but when the `Task` is completed, any `await` expression that's awaiting the `Task` evaluates to `void`.</span></span>  
  
<span data-ttu-id="4ff60-141">O tipo de retorno `void` é usado principalmente para definir manipuladores de eventos que exigem esse tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="4ff60-141">You use the `void` return type primarily to define event handlers, which require that return type.</span></span> <span data-ttu-id="4ff60-142">O chamador de um método assíncrono de retorno `void` não pode aguardá-lo e capturar exceções acionadas pelo método.</span><span class="sxs-lookup"><span data-stu-id="4ff60-142">The caller of a `void`-returning async method can't await it and can't catch exceptions that the method throws.</span></span>  

<span data-ttu-id="4ff60-143">Começando com o C# 7.0, você retorna outro tipo, geralmente um tipo de valor, que tenha um método `GetAwaiter` para minimizar as alocações de memória nas seções do código críticas quanto ao desempenho.</span><span class="sxs-lookup"><span data-stu-id="4ff60-143">Starting with C# 7.0, you return another type, typically a value type, that has a `GetAwaiter` method to miminize memory allocations in performance-critical sections of code.</span></span> 

<span data-ttu-id="4ff60-144">Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span><span class="sxs-lookup"><span data-stu-id="4ff60-144">For more information and examples, see [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff60-145">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ff60-145">See Also</span></span>

- <xref:System.Runtime.CompilerServices.AsyncStateMachineAttribute>  
- [<span data-ttu-id="4ff60-146">await</span><span class="sxs-lookup"><span data-stu-id="4ff60-146">await</span></span>](../../../csharp/language-reference/keywords/await.md)  
- [<span data-ttu-id="4ff60-147">Instruções passo a passo: acessando a Web e usando Async e Await</span><span class="sxs-lookup"><span data-stu-id="4ff60-147">Walkthrough: Accessing the Web by Using Async and Await</span></span>](../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)  
- [<span data-ttu-id="4ff60-148">Programação assíncrona com async e await</span><span class="sxs-lookup"><span data-stu-id="4ff60-148">Asynchronous Programming with async and await</span></span>](../../../csharp/programming-guide/concepts/async/index.md)
