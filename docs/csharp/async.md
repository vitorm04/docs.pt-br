---
title: Programação assíncrona – C#
description: Saiba mais sobre o modelo de programação assíncrona em nível linguagem do C# fornecido pelo .NET Core.
author: cartermp
ms.date: 05/20/2020
ms.technology: csharp-async
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.openlocfilehash: bcea584ded6985a0ef166ab8e24672a19e27b0a3
ms.sourcegitcommit: 3492dafceb5d4183b6b0d2f3bdf4a1abc4d5ed8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/16/2020
ms.locfileid: "86415978"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="1ea67-103">Programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="1ea67-103">Asynchronous programming</span></span>

<span data-ttu-id="1ea67-104">Se você tiver alguma necessidade de ligação de e/s (como solicitar dados de uma rede, acessar um banco de dado ou ler e gravar em um sistema de arquivos), você desejará utilizar a programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="1ea67-104">If you have any I/O-bound needs (such as requesting data from a network, accessing a database, or reading and writing to a file system), you'll want to utilize asynchronous programming.</span></span> <span data-ttu-id="1ea67-105">Você também pode ter código vinculado à CPU, como a execução de um cálculo dispendioso, que também é um bom cenário para escrever código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="1ea67-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="1ea67-106">O C# tem um modelo de programação assíncrona de nível de linguagem, que permite escrever código assíncrono facilmente, sem precisar fazer malabarismos com retornos de chamada ou estar em conformidade com uma biblioteca com suporte para assincronia.</span><span class="sxs-lookup"><span data-stu-id="1ea67-106">C# has a language-level asynchronous programming model, which allows for easily writing asynchronous code, without having to juggle callbacks or conform to a library that supports asynchrony.</span></span> <span data-ttu-id="1ea67-107">Ele segue o que é conhecido como [TAP (Padrão assíncrono baseado em tarefa)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="1ea67-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="overview-of-the-asynchronous-model"></a><span data-ttu-id="1ea67-108">Visão geral do modelo assíncrono</span><span class="sxs-lookup"><span data-stu-id="1ea67-108">Overview of the asynchronous model</span></span>

<span data-ttu-id="1ea67-109">O núcleo da programação assíncrona são os objetos `Task` e `Task<T>`, que modelam as operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="1ea67-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span> <span data-ttu-id="1ea67-110">Eles têm suporte das palavras-chave `async` e `await`.</span><span class="sxs-lookup"><span data-stu-id="1ea67-110">They are supported by the `async` and `await` keywords.</span></span> <span data-ttu-id="1ea67-111">O modelo é bastante simples na maioria dos casos:</span><span class="sxs-lookup"><span data-stu-id="1ea67-111">The model is fairly simple in most cases:</span></span>

- <span data-ttu-id="1ea67-112">Para O código ligado à e/s, você aguarda uma operação que retorna um `Task` ou `Task<T>` dentro de um `async` método.</span><span class="sxs-lookup"><span data-stu-id="1ea67-112">For I/O-bound code, you await an operation that returns a `Task` or `Task<T>` inside of an `async` method.</span></span>
- <span data-ttu-id="1ea67-113">Para código vinculado à CPU, você aguarda uma operação iniciada em um thread em segundo plano com o <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> método.</span><span class="sxs-lookup"><span data-stu-id="1ea67-113">For CPU-bound code, you await an operation that is started on a background thread with the <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="1ea67-114">É na palavra-chave `await` que a mágica acontece.</span><span class="sxs-lookup"><span data-stu-id="1ea67-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="1ea67-115">Ela cede o controle para o chamador do método que executou `await` e, em última instância, permite que uma interface do usuário tenha capacidade de resposta ou que um serviço seja elástico.</span><span class="sxs-lookup"><span data-stu-id="1ea67-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span> <span data-ttu-id="1ea67-116">Embora [haja maneiras](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) de abordar um código assíncrono diferente de `async` e `await` , este artigo se concentra nas construções de nível de linguagem.</span><span class="sxs-lookup"><span data-stu-id="1ea67-116">While [there are ways](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) to approach async code other than `async` and `await`, this article focuses on the language-level constructs.</span></span>

### <a name="io-bound-example-download-data-from-a-web-service"></a><span data-ttu-id="1ea67-117">Exemplo associado de e/s: baixar dados de um serviço Web</span><span class="sxs-lookup"><span data-stu-id="1ea67-117">I/O-bound example: Download data from a web service</span></span>

<span data-ttu-id="1ea67-118">Talvez seja necessário baixar alguns dados de um serviço Web quando um botão for pressionado, mas não quiser bloquear o thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="1ea67-118">You may need to download some data from a web service when a button is pressed, but don't want to block the UI thread.</span></span> <span data-ttu-id="1ea67-119">Isso pode ser feito da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="1ea67-119">It can be accomplished like this:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

downloadButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI as the request
    // from the web service is happening.
    //
    // The UI thread is now free to perform other work.
    var stringData = await _httpClient.GetStringAsync(URL);
    DoSomethingWithData(stringData);
};
```

<span data-ttu-id="1ea67-120">O código expressa a intenção (Baixando dados de forma assíncrona) sem sobrecarga-lo na interação com `Task` objetos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-120">The code expresses the intent (downloading data asynchronously) without getting bogged down in interacting with `Task` objects.</span></span>

### <a name="cpu-bound-example-perform-a-calculation-for-a-game"></a><span data-ttu-id="1ea67-121">Exemplo associado à CPU: executar um cálculo para um jogo</span><span class="sxs-lookup"><span data-stu-id="1ea67-121">CPU-bound example: Perform a calculation for a game</span></span>

<span data-ttu-id="1ea67-122">Digamos que você está escrevendo um jogo para dispositivo móvel em que, ao pressionar um botão, poderá causar danos a muitos inimigos na tela.</span><span class="sxs-lookup"><span data-stu-id="1ea67-122">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span> <span data-ttu-id="1ea67-123">A realização do cálculo de dano pode ser dispendiosa e fazê-lo no thread da interface do usuário faria com que o jogo parecesse pausar durante a realização do cálculo!</span><span class="sxs-lookup"><span data-stu-id="1ea67-123">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="1ea67-124">A melhor maneira de lidar com isso é iniciar um thread em segundo plano, que faz o trabalho usando `Task.Run` e aguardar seu resultado usando `await` .</span><span class="sxs-lookup"><span data-stu-id="1ea67-124">The best way to handle this is to start a background thread, which does the work using `Task.Run`, and await its result using `await`.</span></span> <span data-ttu-id="1ea67-125">Isso permite que a interface do usuário fique tranqüila, pois o trabalho está sendo feito.</span><span class="sxs-lookup"><span data-stu-id="1ea67-125">This allows the UI to feel smooth as the work is being done.</span></span>

```csharp
private DamageResult CalculateDamageDone()
{
    // Code omitted:
    //
    // Does an expensive calculation and returns
    // the result of that calculation.
}

calculateButton.Clicked += async (o, e) =>
{
    // This line will yield control to the UI while CalculateDamageDone()
    // performs its work. The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="1ea67-126">Esse código expressa claramente a intenção do evento de clique do botão. Ele não requer o gerenciamento manual de um thread em segundo plano e ele faz isso sem bloqueios.</span><span class="sxs-lookup"><span data-stu-id="1ea67-126">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="1ea67-127">O que acontece nos bastidores</span><span class="sxs-lookup"><span data-stu-id="1ea67-127">What happens under the covers</span></span>

<span data-ttu-id="1ea67-128">Há muitas partes móveis nas quais as operações assíncronas se preocupam.</span><span class="sxs-lookup"><span data-stu-id="1ea67-128">There are many moving pieces where asynchronous operations are concerned.</span></span> <span data-ttu-id="1ea67-129">Se você estiver curioso sobre o que está acontecendo nos bastidores do `Task` e do `Task<T>` , consulte o artigo sobre o [Async em profundidade](../standard/async-in-depth.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="1ea67-129">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, see the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="1ea67-130">No lado do C# das coisas, o compilador transforma seu código em um computador de estado que controla coisas como produzir a execução quando um `await` é atingido e retomar a execução quando um trabalho em segundo plano é concluído.</span><span class="sxs-lookup"><span data-stu-id="1ea67-130">On the C# side of things, the compiler transforms your code into a state machine that keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="1ea67-131">Para os que gostam da teoria, essa é uma implementação do [Modelo Promise de assincronia](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="1ea67-131">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="1ea67-132">Principais partes a serem compreendidas</span><span class="sxs-lookup"><span data-stu-id="1ea67-132">Key pieces to understand</span></span>

* <span data-ttu-id="1ea67-133">O código assíncrono pode ser usado tanto para o código vinculado à E/S quanto vinculado à CPU, mas de maneira diferente para cada cenário.</span><span class="sxs-lookup"><span data-stu-id="1ea67-133">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="1ea67-134">O código assíncrono usa `Task<T>` e `Task`, que são constructos usados para modelar o trabalho que está sendo feito em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="1ea67-134">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="1ea67-135">A palavra-chave `async` transforma um método em um método assíncrono, o que permite que você use a palavra-chave `await` em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="1ea67-135">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="1ea67-136">Quando a palavra-chave `await` é aplicada, ela suspende o método de chamada e transfere o controle de volta ao seu chamador até que a tarefa em espera seja concluída.</span><span class="sxs-lookup"><span data-stu-id="1ea67-136">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* <span data-ttu-id="1ea67-137">A `await` só pode ser usada dentro de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="1ea67-137">`await` can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="1ea67-138">Reconhecer O trabalho associado à CPU e à e/s</span><span class="sxs-lookup"><span data-stu-id="1ea67-138">Recognize CPU-bound and I/O-bound work</span></span>

<span data-ttu-id="1ea67-139">Os primeiros dois exemplos deste guia mostraram como você pode usar `async` e `await` para trabalho vinculado à E/S e vinculado à CPU.</span><span class="sxs-lookup"><span data-stu-id="1ea67-139">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span> <span data-ttu-id="1ea67-140">É fundamental que você saiba identificar quando um trabalho que você precisa fazer é vinculado à E/S ou vinculado à CPU, porque isso pode afetar significativamente o desempenho do seu código e poderia potencialmente levar ao uso indevido de determinados constructos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-140">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="1ea67-141">Aqui estão duas perguntas que devem ser feitas antes de escrever qualquer código:</span><span class="sxs-lookup"><span data-stu-id="1ea67-141">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="1ea67-142">Seu código ficará em "espera" por alguma coisa, como dados de um banco de dados?</span><span class="sxs-lookup"><span data-stu-id="1ea67-142">Will your code be "waiting" for something, such as data from a database?</span></span>

   <span data-ttu-id="1ea67-143">Se a resposta é "sim", seu trabalho é **vinculado à E/S**.</span><span class="sxs-lookup"><span data-stu-id="1ea67-143">If your answer is "yes", then your work is **I/O-bound**.</span></span>

1. <span data-ttu-id="1ea67-144">Seu código estará executando uma computação cara?</span><span class="sxs-lookup"><span data-stu-id="1ea67-144">Will your code be performing an expensive computation?</span></span>

   <span data-ttu-id="1ea67-145">Se você respondeu "sim", seu trabalho é **vinculado à CPU**.</span><span class="sxs-lookup"><span data-stu-id="1ea67-145">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="1ea67-146">Se o seu trabalho for **vinculado à E/S**, use `async` e `await` *sem* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="1ea67-146">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span> <span data-ttu-id="1ea67-147">Você *não deve* usar a biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="1ea67-147">You *should not* use the Task Parallel Library.</span></span> <span data-ttu-id="1ea67-148">O motivo disso é descrito em [Async em profundidade](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="1ea67-148">The reason for this is outlined in [Async in Depth](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="1ea67-149">Se o trabalho que você tem está **vinculado à CPU** e você se preocupa com a capacidade de resposta, use `async` and `await` , mas gera o trabalho em outro thread *com* `Task.Run` .</span><span class="sxs-lookup"><span data-stu-id="1ea67-149">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await`, but spawn off the work on another thread *with* `Task.Run`.</span></span> <span data-ttu-id="1ea67-150">Se o trabalho for apropriado para simultaneidade e paralelismo, considere também usar a [biblioteca de tarefas paralelas](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="1ea67-150">If the work is appropriate for concurrency and parallelism, also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="1ea67-151">Além disso, você sempre deve medir a execução do seu código.</span><span class="sxs-lookup"><span data-stu-id="1ea67-151">Additionally, you should always measure the execution of your code.</span></span> <span data-ttu-id="1ea67-152">Por exemplo, talvez você tenha uma situação em que seu trabalho vinculado à CPU não é caro o suficiente em comparação com os custos gerais das trocas de contexto ao realizar o multithreading.</span><span class="sxs-lookup"><span data-stu-id="1ea67-152">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span> <span data-ttu-id="1ea67-153">Cada opção tem vantagens e desvantagens e você deve escolher o que é correto para a sua situação.</span><span class="sxs-lookup"><span data-stu-id="1ea67-153">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="1ea67-154">Mais exemplos</span><span class="sxs-lookup"><span data-stu-id="1ea67-154">More examples</span></span>

<span data-ttu-id="1ea67-155">Os exemplos a seguir demonstram várias maneiras para escrever código assíncrono no C#.</span><span class="sxs-lookup"><span data-stu-id="1ea67-155">The following examples demonstrate various ways you can write async code in C#.</span></span> <span data-ttu-id="1ea67-156">Elas abordam alguns cenários diferentes que você pode encontrar.</span><span class="sxs-lookup"><span data-stu-id="1ea67-156">They cover a few different scenarios you may come across.</span></span>

### <a name="extract-data-from-a-network"></a><span data-ttu-id="1ea67-157">Extrair dados de uma rede</span><span class="sxs-lookup"><span data-stu-id="1ea67-157">Extract data from a network</span></span>

<span data-ttu-id="1ea67-158">Esse trecho de código baixa o HTML da Home Page em <https://dotnetfoundation.org> e conta o número de vezes que a cadeia de caracteres ".net" ocorre no HTML.</span><span class="sxs-lookup"><span data-stu-id="1ea67-158">This snippet downloads the HTML from the homepage at <https://dotnetfoundation.org> and counts the number of times the string ".NET" occurs in the HTML.</span></span> <span data-ttu-id="1ea67-159">Ele usa ASP.NET para definir um método de controlador da API Web, que executa essa tarefa e retorna o número.</span><span class="sxs-lookup"><span data-stu-id="1ea67-159">It uses ASP.NET to define a Web API controller method, which performs this task and returns the number.</span></span>

> [!NOTE]
> <span data-ttu-id="1ea67-160">Se você pretende fazer análise de HTML no código de produção, não use expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="1ea67-160">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="1ea67-161">Use uma biblioteca de análise.</span><span class="sxs-lookup"><span data-stu-id="1ea67-161">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet, Route("DotNetCount")]
public async Task<int> GetDotNetCount()
{
    // Suspends GetDotNetCount() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="1ea67-162">Aqui está o mesmo cenário escrito para um aplicativo universal do Windows, que executa a mesma tarefa quando um botão for pressionado:</span><span class="sxs-lookup"><span data-stu-id="1ea67-162">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void OnSeeTheDotNetsButtonClick(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends OnSeeTheDotNetsButtonClick(), returning control to its caller.
    // This is what allows the app to be responsive and not block the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="wait-for-multiple-tasks-to-complete"></a><span data-ttu-id="1ea67-163">Aguardar a conclusão de várias tarefas</span><span class="sxs-lookup"><span data-stu-id="1ea67-163">Wait for multiple tasks to complete</span></span>

<span data-ttu-id="1ea67-164">Você pode encontrar em uma situação em que precisa recuperar várias partes de dados simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="1ea67-164">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span> <span data-ttu-id="1ea67-165">A `Task` API contém dois métodos <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> , que permitem que você escreva um código assíncrono que executa uma espera sem bloqueio em vários trabalhos em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="1ea67-165">The `Task` API contains two methods, <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> and <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>, that allow you to write asynchronous code that performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="1ea67-166">Este exemplo mostra como você pode obter os dados `User` para um conjunto de `userId`s.</span><span class="sxs-lookup"><span data-stu-id="1ea67-166">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<IEnumerable<User>> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = new List<Task<User>>();
    foreach (int userId in userIds)
    {
        getUserTasks.Add(GetUserAsync(userId));
    }

    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="1ea67-167">Esta é outra maneira de escrever isso de forma mais sucinta, usando LINQ:</span><span class="sxs-lookup"><span data-stu-id="1ea67-167">Here's another way to write this more succinctly, using LINQ:</span></span>

```csharp
public async Task<User> GetUserAsync(int userId)
{
    // Code omitted:
    //
    // Given a user Id {userId}, retrieves a User object corresponding
    // to the entry in the database with {userId} as its Id.
}

public static async Task<User[]> GetUsersAsync(IEnumerable<int> userIds)
{
    var getUserTasks = userIds.Select(id => GetUserAsync(id));
    return await Task.WhenAll(getUserTasks);
}
```

<span data-ttu-id="1ea67-168">Embora seja menos código, tome cuidado ao misturar LINQ com código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="1ea67-168">Although it's less code, use caution when mixing LINQ with asynchronous code.</span></span> <span data-ttu-id="1ea67-169">Como o LINQ utiliza a execução adiada (lenta), as chamadas assíncronas não acontecerão imediatamente como em um loop `foreach`, a menos que você force a sequência gerada a iterar com uma chamada a `.ToList()` ou `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="1ea67-169">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="1ea67-170">Informações importantes e conselhos</span><span class="sxs-lookup"><span data-stu-id="1ea67-170">Important info and advice</span></span>

<span data-ttu-id="1ea67-171">Com a programação assíncrona, há alguns detalhes a serem considerados, o que pode impedir um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="1ea67-171">With async programming there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* <span data-ttu-id="1ea67-172">Os métodos `async` \*\* precisam ter uma palavra-chave\*\* `await` \*\* no corpo ou eles nunca transferirão!\*\*</span><span class="sxs-lookup"><span data-stu-id="1ea67-172">`async` **methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

  <span data-ttu-id="1ea67-173">É importante ter isso em mente.</span><span class="sxs-lookup"><span data-stu-id="1ea67-173">This is important to keep in mind.</span></span> <span data-ttu-id="1ea67-174">Se `await` não for usado no corpo de um `async` método, o compilador C# gerará um aviso, mas o código será compilado e executado como se fosse um método normal.</span><span class="sxs-lookup"><span data-stu-id="1ea67-174">If `await` is not used in the body of an `async` method, the C# compiler generates a warning, but the code compiles and runs as if it were a normal method.</span></span> <span data-ttu-id="1ea67-175">Isso é incrivelmente ineficiente, pois a máquina de estado gerada pelo compilador C# para o método assíncrono não está realizando nada.</span><span class="sxs-lookup"><span data-stu-id="1ea67-175">This is incredibly inefficient, as the state machine generated by the C# compiler for the async method is not accomplishing anything.</span></span>

* <span data-ttu-id="1ea67-176">**Você deve adicionar "Async" como o sufixo de cada nome de método assíncrono que escrever.**</span><span class="sxs-lookup"><span data-stu-id="1ea67-176">**You should add "Async" as the suffix of every async method name you write.**</span></span>

<span data-ttu-id="1ea67-177">Essa é a convenção usada no .NET para diferenciar mais facilmente os métodos síncronos e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-177">This is the convention used in .NET to more easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="1ea67-178">Determinados métodos que não são chamados explicitamente pelo seu código (como manipuladores de eventos ou métodos de controlador da Web) não necessariamente se aplicam.</span><span class="sxs-lookup"><span data-stu-id="1ea67-178">Certain methods that aren't explicitly called by your code (such as event handlers or web controller methods) don't necessarily apply.</span></span> <span data-ttu-id="1ea67-179">Como eles não são chamados explicitamente pelo seu código, ser explícito sobre a nomenclatura não é tão importante.</span><span class="sxs-lookup"><span data-stu-id="1ea67-179">Because they are not explicitly called by your code, being explicit about their naming isn't as important.</span></span>

* <span data-ttu-id="1ea67-180">`async void`**deve ser usado somente para manipuladores de eventos.**</span><span class="sxs-lookup"><span data-stu-id="1ea67-180">`async void` **should only to be used for event handlers.**</span></span>

<span data-ttu-id="1ea67-181">O `async void` é a única maneira de permitir que os manipuladores de eventos assíncronos trabalhem, pois os eventos não têm tipos de retorno (portanto, não podem fazer uso de `Task` e `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="1ea67-181">`async void` is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="1ea67-182">Qualquer outro uso de `async void` não segue o modelo TAP e pode ser um desafio utilizá-lo, como:</span><span class="sxs-lookup"><span data-stu-id="1ea67-182">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="1ea67-183">Exceções geradas em um `async void` método não podem ser detectadas fora desse método.</span><span class="sxs-lookup"><span data-stu-id="1ea67-183">Exceptions thrown in an `async void` method can't be caught outside of that method.</span></span>
* <span data-ttu-id="1ea67-184">`async void`os métodos são difíceis de testar.</span><span class="sxs-lookup"><span data-stu-id="1ea67-184">`async void` methods are difficult to test.</span></span>
* <span data-ttu-id="1ea67-185">`async void`os métodos podem causar efeitos colaterais ruins se o chamador não estiver esperando que eles sejam assíncronos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-185">`async void` methods can cause bad side effects if the caller isn't expecting them to be async.</span></span>

* <span data-ttu-id="1ea67-186">**Vá com cuidado ao usar lambdas assíncronas em expressões LINQ**</span><span class="sxs-lookup"><span data-stu-id="1ea67-186">**Tread carefully when using async lambdas in LINQ expressions**</span></span>

<span data-ttu-id="1ea67-187">As expressões lambda no LINQ usam a execução adiada, o que significa que o código pode acabar sendo executado por vez, quando você não está esperando.</span><span class="sxs-lookup"><span data-stu-id="1ea67-187">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you're not expecting it to.</span></span> <span data-ttu-id="1ea67-188">A introdução de tarefas de bloqueio no meio disso poderia facilmente resultar em um deadlock, se não estivessem escritas corretamente.</span><span class="sxs-lookup"><span data-stu-id="1ea67-188">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="1ea67-189">Além disso, o aninhamento de código assíncrono dessa maneira também pode dificultar a ponderação a respeito da execução do código.</span><span class="sxs-lookup"><span data-stu-id="1ea67-189">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="1ea67-190">A assíncrona e a LINQ são poderosas, mas devem ser usadas de uma maneira mais cuidadosa e clara possível.</span><span class="sxs-lookup"><span data-stu-id="1ea67-190">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* <span data-ttu-id="1ea67-191">**Escrever código que aguarda tarefas de uma maneira sem bloqueio**</span><span class="sxs-lookup"><span data-stu-id="1ea67-191">**Write code that awaits Tasks in a non-blocking manner**</span></span>

<span data-ttu-id="1ea67-192">O bloqueio do thread atual como um meio de esperar por um `Task` para concluir pode resultar em deadlocks e threads de contexto bloqueados e pode exigir tratamento de erros mais complexo.</span><span class="sxs-lookup"><span data-stu-id="1ea67-192">Blocking the current thread as a means to wait for a `Task` to complete can result in deadlocks and blocked context threads, and can require more complex error-handling.</span></span> <span data-ttu-id="1ea67-193">A tabela a seguir fornece orientação sobre como lidar com a espera de tarefas de uma maneira sem bloqueio:</span><span class="sxs-lookup"><span data-stu-id="1ea67-193">The following table provides guidance on how to deal with waiting for tasks in a non-blocking way:</span></span>

| <span data-ttu-id="1ea67-194">Use isto...</span><span class="sxs-lookup"><span data-stu-id="1ea67-194">Use this...</span></span>          | <span data-ttu-id="1ea67-195">Em vez disto...</span><span class="sxs-lookup"><span data-stu-id="1ea67-195">Instead of this...</span></span>           | <span data-ttu-id="1ea67-196">Quando desejar fazer isso...</span><span class="sxs-lookup"><span data-stu-id="1ea67-196">When wishing to do this...</span></span>                 |
|----------------------|------------------------------|--------------------------------------------|
| `await`              | <span data-ttu-id="1ea67-197">`Task.Wait` ou `Task.Result`</span><span class="sxs-lookup"><span data-stu-id="1ea67-197">`Task.Wait` or `Task.Result`</span></span> | <span data-ttu-id="1ea67-198">Recuperação do resultado de uma tarefa em segundo plano</span><span class="sxs-lookup"><span data-stu-id="1ea67-198">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny`               | <span data-ttu-id="1ea67-199">Aguardar a conclusão de qualquer tarefa</span><span class="sxs-lookup"><span data-stu-id="1ea67-199">Waiting for any task to complete</span></span>           |
| `await Task.WhenAll` | `Task.WaitAll`               | <span data-ttu-id="1ea67-200">Aguardar a conclusão de todas as tarefas</span><span class="sxs-lookup"><span data-stu-id="1ea67-200">Waiting for all tasks to complete</span></span>          |
| `await Task.Delay`   | `Thread.Sleep`               | <span data-ttu-id="1ea67-201">Aguardar por um período de tempo</span><span class="sxs-lookup"><span data-stu-id="1ea67-201">Waiting for a period of time</span></span>               |

* <span data-ttu-id="1ea67-202">**Considere usar** `ValueTask` **sempre que possível**</span><span class="sxs-lookup"><span data-stu-id="1ea67-202">**Consider using** `ValueTask` **where possible**</span></span>

<span data-ttu-id="1ea67-203">Retornar um objeto `Task` de métodos assíncronos pode introduzir gargalos de desempenho em determinados caminhos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-203">Returning a `Task` object from async methods can introduce performance bottlenecks in certain paths.</span></span> <span data-ttu-id="1ea67-204">`Task` é um tipo de referência, portanto, usá-lo significa alocar um objeto.</span><span class="sxs-lookup"><span data-stu-id="1ea67-204">`Task` is a reference type, so using it means allocating an object.</span></span> <span data-ttu-id="1ea67-205">Nos casos em que um método declarado com o `async` modificador retorna um resultado em cache ou é concluído de forma síncrona, as alocações extras podem se tornar um custo de tempo significativo nas seções críticas de desempenho do código.</span><span class="sxs-lookup"><span data-stu-id="1ea67-205">In cases where a method declared with the `async` modifier returns a cached result or completes synchronously, the extra allocations can become a significant time cost in performance critical sections of code.</span></span> <span data-ttu-id="1ea67-206">Isso pode se tornar caro se essas alocações ocorrem em loops rígidos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-206">It can become costly if those allocations occur in tight loops.</span></span> <span data-ttu-id="1ea67-207">Para obter mais informações, consulte [tipos de retorno assíncrono generalizados](whats-new/csharp-7.md#generalized-async-return-types).</span><span class="sxs-lookup"><span data-stu-id="1ea67-207">For more information, see [generalized async return types](whats-new/csharp-7.md#generalized-async-return-types).</span></span>

* <span data-ttu-id="1ea67-208">**Considere usar** `ConfigureAwait(false)`</span><span class="sxs-lookup"><span data-stu-id="1ea67-208">**Consider using** `ConfigureAwait(false)`</span></span>

<span data-ttu-id="1ea67-209">Uma pergunta comum é "quando devo usar o <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> método?".</span><span class="sxs-lookup"><span data-stu-id="1ea67-209">A common question is, "when should I use the <xref:System.Threading.Tasks.Task.ConfigureAwait(System.Boolean)?displayProperty=nameWithType> method?".</span></span> <span data-ttu-id="1ea67-210">O método permite que uma `Task` instância configure seu aguardador.</span><span class="sxs-lookup"><span data-stu-id="1ea67-210">The method allows for a `Task` instance to configure its awaiter.</span></span> <span data-ttu-id="1ea67-211">Essa é uma consideração importante e a configuração incorreta pode potencialmente ter implicações de desempenho e até mesmo deadlocks.</span><span class="sxs-lookup"><span data-stu-id="1ea67-211">This is an important consideration and setting it incorrectly could potentially have performance implications and even deadlocks.</span></span> <span data-ttu-id="1ea67-212">Para obter mais informações sobre `ConfigureAwait` o, consulte as [perguntas frequentes do ConfigureAwait](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span><span class="sxs-lookup"><span data-stu-id="1ea67-212">For more information on `ConfigureAwait`, see the [ConfigureAwait FAQ](https://devblogs.microsoft.com/dotnet/configureawait-faq).</span></span>

* <span data-ttu-id="1ea67-213">**Escrever código com menos monitoração de estado**</span><span class="sxs-lookup"><span data-stu-id="1ea67-213">**Write less stateful code**</span></span>

<span data-ttu-id="1ea67-214">Não dependa do estado de objetos globais ou da execução de determinados métodos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-214">Don't depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="1ea67-215">Em vez disso, depender apenas dos valores retornados dos métodos.</span><span class="sxs-lookup"><span data-stu-id="1ea67-215">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="1ea67-216">Por quê?</span><span class="sxs-lookup"><span data-stu-id="1ea67-216">Why?</span></span>

* <span data-ttu-id="1ea67-217">Será mais fácil raciocinar sobre o código.</span><span class="sxs-lookup"><span data-stu-id="1ea67-217">Code will be easier to reason about.</span></span>
* <span data-ttu-id="1ea67-218">O código será mais fácil de testar.</span><span class="sxs-lookup"><span data-stu-id="1ea67-218">Code will be easier to test.</span></span>
* <span data-ttu-id="1ea67-219">Misturar código assíncrono e síncrono será muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="1ea67-219">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="1ea67-220">As condições de corrida poderão, normalmente, ser completamente evitadas.</span><span class="sxs-lookup"><span data-stu-id="1ea67-220">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="1ea67-221">Dependendo dos valores retornados, a coordenação de código assíncrono se tornará simples.</span><span class="sxs-lookup"><span data-stu-id="1ea67-221">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="1ea67-222">(Bônus) funciona muito bem com a injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="1ea67-222">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="1ea67-223">Uma meta recomendada é alcançar a [Transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) completa ou quase completa em seu código.</span><span class="sxs-lookup"><span data-stu-id="1ea67-223">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="1ea67-224">Isso resultará em uma base de código extremamente previsível, testável e de fácil manutenção.</span><span class="sxs-lookup"><span data-stu-id="1ea67-224">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="1ea67-225">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="1ea67-225">Other resources</span></span>

* <span data-ttu-id="1ea67-226">A [Programação assíncrona em detalhes](../standard/async-in-depth.md) fornece mais informações sobre o funcionamento de Tarefas.</span><span class="sxs-lookup"><span data-stu-id="1ea67-226">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="1ea67-227">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="1ea67-227">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="1ea67-228">[Seis dicas essenciais para a programação assíncrona](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) de Lucian Wischik é um ótimo recurso para a programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="1ea67-228">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>
