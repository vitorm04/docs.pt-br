---
title: Programação assíncrona – C#
description: Saiba mais sobre o modelo de programação assíncrona em nível linguagem do C# fornecido pelo .NET Core.
author: cartermp
ms.date: 06/20/2016
ms.assetid: b878c34c-a78f-419e-a594-a2b44fa521a4
ms.custom: seodec18
ms.openlocfilehash: 8570692c02855cda7a1990f10ef97590449baccd
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59184659"
---
# <a name="asynchronous-programming"></a><span data-ttu-id="cc765-103">Programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="cc765-103">Asynchronous programming</span></span>

<span data-ttu-id="cc765-104">Se você tiver qualquer necessidade vinculada à E/S (como a solicitação de dados de uma rede ou o acesso a um banco de dados), você desejará usar a programação assíncrona.</span><span class="sxs-lookup"><span data-stu-id="cc765-104">If you have any I/O-bound needs (such as requesting data from a network or accessing a database), you'll want to utilize asynchronous programming.</span></span>  <span data-ttu-id="cc765-105">Você também pode ter código vinculado à CPU, como a execução de um cálculo dispendioso, que também é um bom cenário para escrever código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="cc765-105">You could also have CPU-bound code, such as performing an expensive calculation, which is also a good scenario for writing async code.</span></span>

<span data-ttu-id="cc765-106">O C# tem um modelo de programação assíncrono em nível de linguagem que permite escrever facilmente o código assíncrono sem precisar manipular retornos de chamada ou estar em conformidade com uma biblioteca que dá suporte à assincronia.</span><span class="sxs-lookup"><span data-stu-id="cc765-106">C# has a language-level asynchronous programming model which allows for easily writing asynchronous code without having to juggle callbacks or conform to a library which supports asynchrony.</span></span> <span data-ttu-id="cc765-107">Ele segue o que é conhecido como [TAP (Padrão assíncrono baseado em tarefa)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="cc765-107">It follows what is known as the [Task-based Asynchronous Pattern (TAP)](../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>

## <a name="basic-overview-of-the-asynchronous-model"></a><span data-ttu-id="cc765-108">Visão geral básica do modelo assíncrono</span><span class="sxs-lookup"><span data-stu-id="cc765-108">Basic Overview of the Asynchronous Model</span></span>

<span data-ttu-id="cc765-109">O núcleo da programação assíncrona são os objetos `Task` e `Task<T>`, que modelam as operações assíncronas.</span><span class="sxs-lookup"><span data-stu-id="cc765-109">The core of async programming is the `Task` and `Task<T>` objects, which model asynchronous operations.</span></span>  <span data-ttu-id="cc765-110">Eles têm suporte das palavras-chave `async` e `await`.</span><span class="sxs-lookup"><span data-stu-id="cc765-110">They are supported by the `async` and `await` keywords.</span></span>  <span data-ttu-id="cc765-111">O modelo é bastante simples na maioria dos casos:</span><span class="sxs-lookup"><span data-stu-id="cc765-111">The model is fairly simple in most cases:</span></span>

<span data-ttu-id="cc765-112">Para o código vinculado à E/S, você `await` uma operação que retorna um `Task` ou `Task<T>` dentro de um método `async`.</span><span class="sxs-lookup"><span data-stu-id="cc765-112">For I/O-bound code, you `await` an operation which returns a `Task` or `Task<T>` inside of an `async` method.</span></span>

<span data-ttu-id="cc765-113">Para o código vinculado à CPU, você `await` uma operação que é iniciada em um thread em segundo plano com o método `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="cc765-113">For CPU-bound code, you `await` an operation which is started on a background thread with the `Task.Run` method.</span></span>

<span data-ttu-id="cc765-114">É na palavra-chave `await` que a mágica acontece.</span><span class="sxs-lookup"><span data-stu-id="cc765-114">The `await` keyword is where the magic happens.</span></span> <span data-ttu-id="cc765-115">Ela cede o controle para o chamador do método que executou `await` e, em última instância, permite que uma interface do usuário tenha capacidade de resposta ou que um serviço seja elástico.</span><span class="sxs-lookup"><span data-stu-id="cc765-115">It yields control to the caller of the method that performed `await`, and it ultimately allows a UI to be responsive or a service to be elastic.</span></span>

<span data-ttu-id="cc765-116">Existem outras maneiras de abordar o código assíncrono, diferentes de `async` e `await`, como mencionado no artigo TAP no link acima, mas este documento se concentrará nos constructos de nível de linguagem daqui em diante.</span><span class="sxs-lookup"><span data-stu-id="cc765-116">There are other ways to approach async code than `async` and `await` outlined in the TAP article linked above, but this document will focus on the language-level constructs from this point forward.</span></span>

### <a name="io-bound-example-downloading-data-from-a-web-service"></a><span data-ttu-id="cc765-117">Exemplo vinculado à E/S: Baixando dados de um serviço Web</span><span class="sxs-lookup"><span data-stu-id="cc765-117">I/O-Bound Example: Downloading data from a web service</span></span>

<span data-ttu-id="cc765-118">Talvez você queira baixar alguns dados de um serviço Web quando um botão for pressionado, mas não deseja bloquear o thread da interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="cc765-118">You may need to download some data from a web service when a button is pressed, but don’t want to block the UI thread.</span></span> <span data-ttu-id="cc765-119">Isso pode ser realizado simplesmente assim:</span><span class="sxs-lookup"><span data-stu-id="cc765-119">It can be accomplished simply like this:</span></span>

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

<span data-ttu-id="cc765-120">E pronto!</span><span class="sxs-lookup"><span data-stu-id="cc765-120">And that’s it!</span></span> <span data-ttu-id="cc765-121">O código expressa a intenção (baixar alguns dados de forma assíncrona) sem enroscar na interação com objetos de tarefa.</span><span class="sxs-lookup"><span data-stu-id="cc765-121">The code expresses the intent (downloading some data asynchronously) without getting bogged down in interacting with Task objects.</span></span>

### <a name="cpu-bound-example-performing-a-calculation-for-a-game"></a><span data-ttu-id="cc765-122">Exemplo vinculado à CPU: Executando um cálculo para um jogo</span><span class="sxs-lookup"><span data-stu-id="cc765-122">CPU-bound Example: Performing a Calculation for a Game</span></span>

<span data-ttu-id="cc765-123">Digamos que você está escrevendo um jogo para dispositivo móvel em que, ao pressionar um botão, poderá causar danos a muitos inimigos na tela.</span><span class="sxs-lookup"><span data-stu-id="cc765-123">Say you're writing a mobile game where pressing a button can inflict damage on many enemies on the screen.</span></span>  <span data-ttu-id="cc765-124">A realização do cálculo de dano pode ser dispendiosa e fazê-lo no thread da interface do usuário faria com que o jogo parecesse pausar durante a realização do cálculo!</span><span class="sxs-lookup"><span data-stu-id="cc765-124">Performing the damage calculation can be expensive, and doing it on the UI thread would make the game appear to pause as the calculation is performed!</span></span>

<span data-ttu-id="cc765-125">A melhor maneira de lidar com isso é iniciar um thread em segundo plano que faz o trabalho usando `Task.Run` e `await` seu resultado.</span><span class="sxs-lookup"><span data-stu-id="cc765-125">The best way to handle this is to start a background thread which does the work using `Task.Run`, and `await` its result.</span></span>  <span data-ttu-id="cc765-126">Isso permitirá que a interface do usuário pareça suave enquanto o trabalho está sendo feito.</span><span class="sxs-lookup"><span data-stu-id="cc765-126">This will allow the UI to feel smooth as the work is being done.</span></span>

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
    // performs its work.  The UI thread is free to perform other work.
    var damageResult = await Task.Run(() => CalculateDamageDone());
    DisplayDamage(damageResult);
};
```

<span data-ttu-id="cc765-127">E pronto.</span><span class="sxs-lookup"><span data-stu-id="cc765-127">And that's it!</span></span>  <span data-ttu-id="cc765-128">Esse código expressa claramente a intenção do evento de clique do botão. Ele não requer o gerenciamento manual de um thread em segundo plano e ele faz isso sem bloqueios.</span><span class="sxs-lookup"><span data-stu-id="cc765-128">This code cleanly expresses the intent of the button's click event, it doesn't require managing a background thread manually, and it does so in a non-blocking way.</span></span>

### <a name="what-happens-under-the-covers"></a><span data-ttu-id="cc765-129">O que acontece nos bastidores</span><span class="sxs-lookup"><span data-stu-id="cc765-129">What happens under the covers</span></span>

<span data-ttu-id="cc765-130">Há muitas partes se movendo nos locais em que as operações assíncronas acontecem.</span><span class="sxs-lookup"><span data-stu-id="cc765-130">There's a lot of moving pieces where asynchronous operations are concerned.</span></span>  <span data-ttu-id="cc765-131">Se você estiver curioso sobre o que está acontecendo nos bastidores de `Task` e `Task<T>`, dê uma olhada no artigo [Programação assíncrona em detalhes](../standard/async-in-depth.md) para obter mais informações.</span><span class="sxs-lookup"><span data-stu-id="cc765-131">If you're curious about what's happening underneath the covers of `Task` and `Task<T>`, checkout the [Async in-depth](../standard/async-in-depth.md) article for more information.</span></span>

<span data-ttu-id="cc765-132">No lado C# das coisas, o compilador transforma seu código em uma máquina de estado que mantém o controle de coisas, como transferir a execução quando uma `await` é alcançada e continuar a execução quando um trabalho em segundo plano for concluído.</span><span class="sxs-lookup"><span data-stu-id="cc765-132">On the C# side of things, the compiler transforms your code into a state machine which keeps track of things like yielding execution when an `await` is reached and resuming execution when a background job has finished.</span></span>

<span data-ttu-id="cc765-133">Para os que gostam da teoria, essa é uma implementação do [Modelo Promise de assincronia](https://en.wikipedia.org/wiki/Futures_and_promises).</span><span class="sxs-lookup"><span data-stu-id="cc765-133">For the theoretically-inclined, this is an implementation of the [Promise Model of asynchrony](https://en.wikipedia.org/wiki/Futures_and_promises).</span></span>

## <a name="key-pieces-to-understand"></a><span data-ttu-id="cc765-134">Informações importantes para entender</span><span class="sxs-lookup"><span data-stu-id="cc765-134">Key Pieces to Understand</span></span>

* <span data-ttu-id="cc765-135">O código assíncrono pode ser usado tanto para o código vinculado à E/S quanto vinculado à CPU, mas de maneira diferente para cada cenário.</span><span class="sxs-lookup"><span data-stu-id="cc765-135">Async code can be used for both I/O-bound and CPU-bound code, but differently for each scenario.</span></span>
* <span data-ttu-id="cc765-136">O código assíncrono usa `Task<T>` e `Task`, que são constructos usados para modelar o trabalho que está sendo feito em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cc765-136">Async code uses `Task<T>` and `Task`, which are constructs used to model work being done in the background.</span></span>
* <span data-ttu-id="cc765-137">A palavra-chave `async` transforma um método em um método assíncrono, o que permite que você use a palavra-chave `await` em seu corpo.</span><span class="sxs-lookup"><span data-stu-id="cc765-137">The `async` keyword turns a method into an async method, which allows you to use the `await` keyword in its body.</span></span>
* <span data-ttu-id="cc765-138">Quando a palavra-chave `await` é aplicada, ela suspende o método de chamada e transfere o controle de volta ao seu chamador até que a tarefa em espera seja concluída.</span><span class="sxs-lookup"><span data-stu-id="cc765-138">When the `await` keyword is applied, it suspends the calling method and yields control back to its caller until the awaited task is complete.</span></span>
* `await` <span data-ttu-id="cc765-139">só pode ser usada dentro de um método assíncrono.</span><span class="sxs-lookup"><span data-stu-id="cc765-139">can only be used inside an async method.</span></span>

## <a name="recognize-cpu-bound-and-io-bound-work"></a><span data-ttu-id="cc765-140">Reconhecer trabalho vinculado à CPU e vinculado à E/S</span><span class="sxs-lookup"><span data-stu-id="cc765-140">Recognize CPU-Bound and I/O-Bound Work</span></span>

<span data-ttu-id="cc765-141">Os primeiros dois exemplos deste guia mostraram como você pode usar `async` e `await` para trabalho vinculado à E/S e vinculado à CPU.</span><span class="sxs-lookup"><span data-stu-id="cc765-141">The first two examples of this guide showed how you can use `async` and `await` for I/O-bound and CPU-bound work.</span></span>  <span data-ttu-id="cc765-142">É fundamental que você saiba identificar quando um trabalho que você precisa fazer é vinculado à E/S ou vinculado à CPU, porque isso pode afetar significativamente o desempenho do seu código e poderia potencialmente levar ao uso indevido de determinados constructos.</span><span class="sxs-lookup"><span data-stu-id="cc765-142">It's key that you can identify when a job you need to do is I/O-bound or CPU-bound, because it can greatly affect the performance of your code and could potentially lead to misusing certain constructs.</span></span>

<span data-ttu-id="cc765-143">Aqui estão duas perguntas que devem ser feitas antes de escrever qualquer código:</span><span class="sxs-lookup"><span data-stu-id="cc765-143">Here are two questions you should ask before you write any code:</span></span>

1. <span data-ttu-id="cc765-144">Seu código ficará em "espera" por alguma coisa, como dados de um banco de dados?</span><span class="sxs-lookup"><span data-stu-id="cc765-144">Will your code be "waiting" for something, such as data from a database?</span></span>

    <span data-ttu-id="cc765-145">Se a resposta é "sim", seu trabalho é **vinculado à E/S**.</span><span class="sxs-lookup"><span data-stu-id="cc765-145">If your answer is "yes", then your work is **I/O-bound**.</span></span>

2. <span data-ttu-id="cc765-146">Seu código executará uma computação muito dispendiosa?</span><span class="sxs-lookup"><span data-stu-id="cc765-146">Will your code be performing a very expensive computation?</span></span>

    <span data-ttu-id="cc765-147">Se você respondeu "sim", seu trabalho é **vinculado à CPU**.</span><span class="sxs-lookup"><span data-stu-id="cc765-147">If you answered "yes", then your work is **CPU-bound**.</span></span>

<span data-ttu-id="cc765-148">Se o seu trabalho for **vinculado à E/S**, use `async` e `await` *sem* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="cc765-148">If the work you have is **I/O-bound**, use `async` and `await` *without* `Task.Run`.</span></span>  <span data-ttu-id="cc765-149">Você *não deve* usar a biblioteca de paralelismo de tarefas.</span><span class="sxs-lookup"><span data-stu-id="cc765-149">You *should not* use the Task Parallel Library.</span></span>  <span data-ttu-id="cc765-150">A razão para isso está descrita no [artigo Programação assíncrona em detalhes](../standard/async-in-depth.md).</span><span class="sxs-lookup"><span data-stu-id="cc765-150">The reason for this is outlined in the [Async in Depth article](../standard/async-in-depth.md).</span></span>

<span data-ttu-id="cc765-151">Se o seu trabalho for **vinculado à CPU** e você se importa com a capacidade de resposta, use `async` e `await`, mas gere o trabalho em outro thread *com* `Task.Run`.</span><span class="sxs-lookup"><span data-stu-id="cc765-151">If the work you have is **CPU-bound** and you care about responsiveness, use `async` and `await` but spawn the work off on another thread *with* `Task.Run`.</span></span>  <span data-ttu-id="cc765-152">Se o trabalho for adequado para a simultaneidade e paralelismo, você também deverá considerar o uso da [Biblioteca de paralelismo de tarefas](../standard/parallel-programming/task-parallel-library-tpl.md).</span><span class="sxs-lookup"><span data-stu-id="cc765-152">If the work is appropriate for concurrency and parallelism, you should also consider using the [Task Parallel Library](../standard/parallel-programming/task-parallel-library-tpl.md).</span></span>

<span data-ttu-id="cc765-153">Além disso, você sempre deve medir a execução do seu código.</span><span class="sxs-lookup"><span data-stu-id="cc765-153">Additionally, you should always measure the execution of your code.</span></span>  <span data-ttu-id="cc765-154">Por exemplo, talvez você tenha uma situação em que seu trabalho vinculado à CPU não é caro o suficiente em comparação com os custos gerais das trocas de contexto ao realizar o multithreading.</span><span class="sxs-lookup"><span data-stu-id="cc765-154">For example, you may find yourself in a situation where your CPU-bound work is not costly enough compared with the overhead of context switches when multithreading.</span></span>  <span data-ttu-id="cc765-155">Cada opção tem vantagens e desvantagens e você deve escolher o que é correto para a sua situação.</span><span class="sxs-lookup"><span data-stu-id="cc765-155">Every choice has its tradeoff, and you should pick the correct tradeoff for your situation.</span></span>

## <a name="more-examples"></a><span data-ttu-id="cc765-156">Mais exemplos</span><span class="sxs-lookup"><span data-stu-id="cc765-156">More Examples</span></span>

<span data-ttu-id="cc765-157">Os exemplos a seguir demonstram várias maneiras para escrever código assíncrono no C#.</span><span class="sxs-lookup"><span data-stu-id="cc765-157">The following examples demonstrate various ways you can write async code in C#.</span></span>  <span data-ttu-id="cc765-158">Elas abordam alguns cenários diferentes que você pode encontrar.</span><span class="sxs-lookup"><span data-stu-id="cc765-158">They cover a few different scenarios you may come across.</span></span>

### <a name="extracting-data-from-a-network"></a><span data-ttu-id="cc765-159">Extrair dados de uma rede</span><span class="sxs-lookup"><span data-stu-id="cc765-159">Extracting Data from a Network</span></span>

<span data-ttu-id="cc765-160">Este snippet de código baixa o HTML da página inicial em [www.dotnetfoundation.org](https://www.dotnetfoundation.org) e conta o número de vezes que a cadeia de caracteres ".NET" ocorre no HTML.</span><span class="sxs-lookup"><span data-stu-id="cc765-160">This snippet downloads the HTML from the homepage at [www.dotnetfoundation.org](https://www.dotnetfoundation.org) and counts the number of times the string ".NET" occurs in the HTML.</span></span>  <span data-ttu-id="cc765-161">Ele usa o ASP.NET MVC para definir um método do controlador da Web que realiza essa tarefa, retornando o número.</span><span class="sxs-lookup"><span data-stu-id="cc765-161">It uses ASP.NET MVC to define a web controller method which performs this task, returning the number.</span></span>

> [!NOTE]
> <span data-ttu-id="cc765-162">Se você pretende fazer análise de HTML no código de produção, não use expressões regulares.</span><span class="sxs-lookup"><span data-stu-id="cc765-162">If you plan on doing HTML parsing in production code, don't use regular expressions.</span></span> <span data-ttu-id="cc765-163">Use uma biblioteca de análise.</span><span class="sxs-lookup"><span data-stu-id="cc765-163">Use a parsing library instead.</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

[HttpGet]
[Route("DotNetCount")]
public async Task<int> GetDotNetCountAsync()
{
    // Suspends GetDotNetCountAsync() to allow the caller (the web server)
    // to accept another request, rather than blocking on this one.
    var html = await _httpClient.GetStringAsync("https://dotnetfoundation.org");

    return Regex.Matches(html, @"\.NET").Count;
}
```

<span data-ttu-id="cc765-164">Aqui está o mesmo cenário escrito para um aplicativo universal do Windows, que executa a mesma tarefa quando um botão for pressionado:</span><span class="sxs-lookup"><span data-stu-id="cc765-164">Here's the same scenario written for a Universal Windows App, which performs the same task when a Button is pressed:</span></span>

```csharp
private readonly HttpClient _httpClient = new HttpClient();

private async void SeeTheDotNets_Click(object sender, RoutedEventArgs e)
{
    // Capture the task handle here so we can await the background task later.
    var getDotNetFoundationHtmlTask = _httpClient.GetStringAsync("https://www.dotnetfoundation.org");

    // Any other work on the UI thread can be done here, such as enabling a Progress Bar.
    // This is important to do here, before the "await" call, so that the user
    // sees the progress bar before execution of this method is yielded.
    NetworkProgressBar.IsEnabled = true;
    NetworkProgressBar.Visibility = Visibility.Visible;

    // The await operator suspends SeeTheDotNets_Click, returning control to its caller.
    // This is what allows the app to be responsive and not hang on the UI thread.
    var html = await getDotNetFoundationHtmlTask;
    int count = Regex.Matches(html, @"\.NET").Count;

    DotNetCountLabel.Text = $"Number of .NETs on dotnetfoundation.org: {count}";

    NetworkProgressBar.IsEnabled = false;
    NetworkProgressBar.Visibility = Visibility.Collapsed;
}
```

### <a name="waiting-for-multiple-tasks-to-complete"></a><span data-ttu-id="cc765-165">Aguardar a conclusão de várias tarefas</span><span class="sxs-lookup"><span data-stu-id="cc765-165">Waiting for Multiple Tasks to Complete</span></span>

<span data-ttu-id="cc765-166">Você pode encontrar em uma situação em que precisa recuperar várias partes de dados simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="cc765-166">You may find yourself in a situation where you need to retrieve multiple pieces of data concurrently.</span></span>  <span data-ttu-id="cc765-167">A API `Task` contém dois métodos, `Task.WhenAll` e `Task.WhenAny`, que permitem escrever um código assíncrono que realiza uma espera sem bloqueio em vários trabalhos em segundo plano.</span><span class="sxs-lookup"><span data-stu-id="cc765-167">The `Task` API contains two methods, `Task.WhenAll` and `Task.WhenAny` which allow you to write asynchronous code which performs a non-blocking wait on multiple background jobs.</span></span>

<span data-ttu-id="cc765-168">Este exemplo mostra como você pode obter os dados `User` para um conjunto de `userId`s.</span><span class="sxs-lookup"><span data-stu-id="cc765-168">This example shows how you might grab `User` data for a set of `userId`s.</span></span>

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

<span data-ttu-id="cc765-169">Aqui está outro jeito de escrever isso, de forma um pouco mais sucinta, usando LINQ:</span><span class="sxs-lookup"><span data-stu-id="cc765-169">Here's another way to write this a bit more succinctly, using LINQ:</span></span>

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

<span data-ttu-id="cc765-170">Embora seja menos código, tome cuidado ao misturar LINQ com código assíncrono.</span><span class="sxs-lookup"><span data-stu-id="cc765-170">Although it's less code, take care when mixing LINQ with asynchronous code.</span></span>  <span data-ttu-id="cc765-171">Como o LINQ utiliza a execução adiada (lenta), as chamadas assíncronas não acontecerão imediatamente como em um loop `foreach()`, a menos que você force a sequência gerada a iterar com uma chamada a `.ToList()` ou `.ToArray()`.</span><span class="sxs-lookup"><span data-stu-id="cc765-171">Because LINQ uses deferred (lazy) execution, async calls won't happen immediately as they do in a `foreach()` loop unless you force the generated sequence to iterate with a call to `.ToList()` or `.ToArray()`.</span></span>

## <a name="important-info-and-advice"></a><span data-ttu-id="cc765-172">Conselhos e informações importantes</span><span class="sxs-lookup"><span data-stu-id="cc765-172">Important Info and Advice</span></span>

<span data-ttu-id="cc765-173">Embora a programação assíncrona seja relativamente simples, há alguns detalhes para ter em mente, que podem evitar um comportamento inesperado.</span><span class="sxs-lookup"><span data-stu-id="cc765-173">Although async programming is relatively straightforward, there are some details to keep in mind which can prevent unexpected behavior.</span></span>

* `async` <span data-ttu-id="cc765-174">Os métodos  **precisam ter uma palavra-chave** `await`  **no corpo ou eles nunca transferirão!**</span><span class="sxs-lookup"><span data-stu-id="cc765-174">**methods need to have an** `await` **keyword in their body or they will never yield!**</span></span>

<span data-ttu-id="cc765-175">É importante ter isso em mente.</span><span class="sxs-lookup"><span data-stu-id="cc765-175">This is important to keep in mind.</span></span>  <span data-ttu-id="cc765-176">Se `await` não for usado no corpo de um método `async`, o compilador do C# gerará um aviso, mas o código será compilado e executado como se fosse um método normal.</span><span class="sxs-lookup"><span data-stu-id="cc765-176">If `await` is not used in the body of an `async` method, the C# compiler will generate a warning, but the code will compile and run as if it were a normal method.</span></span>  <span data-ttu-id="cc765-177">Observe que isso também seria extremamente ineficiente, pois a máquina de estado, gerada pelo compilador do C# para o método assíncrono, não realizaria nada.</span><span class="sxs-lookup"><span data-stu-id="cc765-177">Note that this would also be incredibly inefficient, as the state machine generated by the C# compiler for the async method would not be accomplishing anything.</span></span>

* **<span data-ttu-id="cc765-178">Você deve adicionar "Async" como o sufixo de cada nome de método assíncrono que escrever.</span><span class="sxs-lookup"><span data-stu-id="cc765-178">You should add "Async" as the suffix of every async method name you write.</span></span>**

<span data-ttu-id="cc765-179">Essa é a convenção usada no .NET para diferenciar mais facilmente os métodos síncronos e assíncronos.</span><span class="sxs-lookup"><span data-stu-id="cc765-179">This is the convention used in .NET to more-easily differentiate synchronous and asynchronous methods.</span></span> <span data-ttu-id="cc765-180">Observe que isso não se aplica, necessariamente, a alguns métodos que não são explicitamente chamados pelo seu código (como manipuladores de eventos ou métodos do controlador da Web).</span><span class="sxs-lookup"><span data-stu-id="cc765-180">Note that certain methods which aren’t explicitly called by your code (such as event handlers or web controller methods) don’t necessarily apply.</span></span> <span data-ttu-id="cc765-181">Como eles não são chamados explicitamente pelo seu código, ser explícito em relação à sua nomenclatura não é tão importante.</span><span class="sxs-lookup"><span data-stu-id="cc765-181">Because these are not explicitly called by your code, being explicit about their naming isn’t as important.</span></span>

* `async void` **<span data-ttu-id="cc765-182">só deve ser usado para manipuladores de eventos.</span><span class="sxs-lookup"><span data-stu-id="cc765-182">should only be used for event handlers.</span></span>**

`async void` <span data-ttu-id="cc765-183">é a única maneira de permitir que os manipuladores de eventos assíncronos trabalhem porque os eventos não têm tipos de retorno (portanto, não podem fazer uso de `Task` e `Task<T>`).</span><span class="sxs-lookup"><span data-stu-id="cc765-183">is the only way to allow asynchronous event handlers to work because events do not have return types (thus cannot make use of `Task` and `Task<T>`).</span></span> <span data-ttu-id="cc765-184">Qualquer outro uso de `async void` não segue o modelo TAP e pode ser um desafio utilizá-lo, como:</span><span class="sxs-lookup"><span data-stu-id="cc765-184">Any other use of `async void` does not follow the TAP model and can be challenging to use, such as:</span></span>

* <span data-ttu-id="cc765-185">As exceções lançadas em um método `async void` não podem ser capturadas fora desse método.</span><span class="sxs-lookup"><span data-stu-id="cc765-185">Exceptions thrown in an `async void` method can’t be caught outside of that method.</span></span>
* `async void` <span data-ttu-id="cc765-186">métodos são muito difíceis de testar.</span><span class="sxs-lookup"><span data-stu-id="cc765-186">methods are very difficult to test.</span></span>
* `async void` <span data-ttu-id="cc765-187">métodos poderão causar efeitos colaterais indesejados se o chamador não estiver esperando que eles sejam assíncronos.</span><span class="sxs-lookup"><span data-stu-id="cc765-187">methods can cause bad side effects if the caller isn’t expecting them to be async.</span></span>

* **<span data-ttu-id="cc765-188">Vá com cuidado ao usar lambdas assíncronas em expressões LINQ</span><span class="sxs-lookup"><span data-stu-id="cc765-188">Tread carefully when using async lambdas in LINQ expressions</span></span>**

<span data-ttu-id="cc765-189">As expressões lambda em LINQ usam a execução adiada, o que significa que o código poderia acabar executando em um momento que você não está esperando.</span><span class="sxs-lookup"><span data-stu-id="cc765-189">Lambda expressions in LINQ use deferred execution, meaning code could end up executing at a time when you’re not expecting it to.</span></span> <span data-ttu-id="cc765-190">A introdução de tarefas de bloqueio no meio disso poderia facilmente resultar em um deadlock, se não estivessem escritas corretamente.</span><span class="sxs-lookup"><span data-stu-id="cc765-190">The introduction of blocking tasks into this can easily result in a deadlock if not written correctly.</span></span> <span data-ttu-id="cc765-191">Além disso, o aninhamento de código assíncrono dessa maneira também pode dificultar a ponderação a respeito da execução do código.</span><span class="sxs-lookup"><span data-stu-id="cc765-191">Additionally, the nesting of asynchronous code like this can also make it more difficult to reason about the execution of the code.</span></span> <span data-ttu-id="cc765-192">A assíncrona e a LINQ são poderosas, mas devem ser usadas de uma maneira mais cuidadosa e clara possível.</span><span class="sxs-lookup"><span data-stu-id="cc765-192">Async and LINQ are powerful, but should be used together as carefully and clearly as possible.</span></span>

* **<span data-ttu-id="cc765-193">Escrever código que aguarda tarefas de uma maneira sem bloqueio</span><span class="sxs-lookup"><span data-stu-id="cc765-193">Write code that awaits Tasks in a non-blocking manner</span></span>**

<span data-ttu-id="cc765-194">Bloquear o thread atual como um meio de aguardar a conclusão de uma tarefa pode resultar em deadlocks e threads de contexto bloqueados e pode exigir tratamento de erros significativamente mais complexo.</span><span class="sxs-lookup"><span data-stu-id="cc765-194">Blocking the current thread as a means to wait for a Task to complete can result in deadlocks and blocked context threads, and can require significantly more complex error-handling.</span></span> <span data-ttu-id="cc765-195">A tabela a seguir fornece diretrizes de como lidar com a espera de tarefas de uma forma sem bloqueio:</span><span class="sxs-lookup"><span data-stu-id="cc765-195">The following table provides guidance on how to deal with waiting for Tasks in a non-blocking way:</span></span>

| <span data-ttu-id="cc765-196">Use isto...</span><span class="sxs-lookup"><span data-stu-id="cc765-196">Use this...</span></span> | <span data-ttu-id="cc765-197">Em vez disto...</span><span class="sxs-lookup"><span data-stu-id="cc765-197">Instead of this...</span></span> | <span data-ttu-id="cc765-198">Quando desejar fazer isso</span><span class="sxs-lookup"><span data-stu-id="cc765-198">When wishing to do this</span></span> |
| --- | --- | --- |
| `await` | `Task.Wait` <span data-ttu-id="cc765-199">ou</span><span class="sxs-lookup"><span data-stu-id="cc765-199">or</span></span> `Task.Result` | <span data-ttu-id="cc765-200">Recuperação do resultado de uma tarefa em segundo plano</span><span class="sxs-lookup"><span data-stu-id="cc765-200">Retrieving the result of a background task</span></span> |
| `await Task.WhenAny` | `Task.WaitAny` | <span data-ttu-id="cc765-201">Aguardar a conclusão de qualquer tarefa</span><span class="sxs-lookup"><span data-stu-id="cc765-201">Waiting for any task to complete</span></span> |
| `await Task.WhenAll` | `Task.WaitAll` | <span data-ttu-id="cc765-202">Aguardar a conclusão de todas as tarefas</span><span class="sxs-lookup"><span data-stu-id="cc765-202">Waiting for all tasks to complete</span></span> |
| `await Task.Delay` | `Thread.Sleep` | <span data-ttu-id="cc765-203">Aguardar por um período de tempo</span><span class="sxs-lookup"><span data-stu-id="cc765-203">Waiting for a period of time</span></span> |

* **<span data-ttu-id="cc765-204">Escrever código com menos monitoração de estado</span><span class="sxs-lookup"><span data-stu-id="cc765-204">Write less stateful code</span></span>**

<span data-ttu-id="cc765-205">Não depender do estado de objetos globais ou da execução de determinados métodos.</span><span class="sxs-lookup"><span data-stu-id="cc765-205">Don’t depend on the state of global objects or the execution of certain methods.</span></span> <span data-ttu-id="cc765-206">Em vez disso, depender apenas dos valores retornados dos métodos.</span><span class="sxs-lookup"><span data-stu-id="cc765-206">Instead, depend only on the return values of methods.</span></span> <span data-ttu-id="cc765-207">Por quê?</span><span class="sxs-lookup"><span data-stu-id="cc765-207">Why?</span></span>

* <span data-ttu-id="cc765-208">Será mais fácil raciocinar sobre o código.</span><span class="sxs-lookup"><span data-stu-id="cc765-208">Code will be easier to reason about.</span></span>
* <span data-ttu-id="cc765-209">O código será mais fácil de testar.</span><span class="sxs-lookup"><span data-stu-id="cc765-209">Code will be easier to test.</span></span>
* <span data-ttu-id="cc765-210">Misturar código assíncrono e síncrono será muito mais simples.</span><span class="sxs-lookup"><span data-stu-id="cc765-210">Mixing async and synchronous code is far simpler.</span></span>
* <span data-ttu-id="cc765-211">As condições de corrida poderão, normalmente, ser completamente evitadas.</span><span class="sxs-lookup"><span data-stu-id="cc765-211">Race conditions can typically be avoided altogether.</span></span>
* <span data-ttu-id="cc765-212">Dependendo dos valores retornados, a coordenação de código assíncrono se tornará simples.</span><span class="sxs-lookup"><span data-stu-id="cc765-212">Depending on return values makes coordinating async code simple.</span></span>
* <span data-ttu-id="cc765-213">(Bônus) funciona muito bem com a injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="cc765-213">(Bonus) it works really well with dependency injection.</span></span>

<span data-ttu-id="cc765-214">Uma meta recomendada é alcançar a [Transparência referencial](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) completa ou quase completa em seu código.</span><span class="sxs-lookup"><span data-stu-id="cc765-214">A recommended goal is to achieve complete or near-complete [Referential Transparency](https://en.wikipedia.org/wiki/Referential_transparency_%28computer_science%29) in your code.</span></span> <span data-ttu-id="cc765-215">Isso resultará em uma base de código extremamente previsível, testável e de fácil manutenção.</span><span class="sxs-lookup"><span data-stu-id="cc765-215">Doing so will result in an extremely predictable, testable, and maintainable codebase.</span></span>

## <a name="other-resources"></a><span data-ttu-id="cc765-216">Outros recursos</span><span class="sxs-lookup"><span data-stu-id="cc765-216">Other Resources</span></span>

* <span data-ttu-id="cc765-217">A [Programação assíncrona em detalhes](../standard/async-in-depth.md) fornece mais informações sobre o funcionamento de Tarefas.</span><span class="sxs-lookup"><span data-stu-id="cc765-217">[Async in-depth](../standard/async-in-depth.md) provides more information about how Tasks work.</span></span>
* [<span data-ttu-id="cc765-218">Programação assíncrona com async e await (C#)</span><span class="sxs-lookup"><span data-stu-id="cc765-218">Asynchronous programming with async and await (C#)</span></span>](./programming-guide/concepts/async/index.md)
* <span data-ttu-id="cc765-219">[Seis dicas essenciais para a programação assíncrona](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) de Lucian Wischik é um ótimo recurso para a programação assíncrona</span><span class="sxs-lookup"><span data-stu-id="cc765-219">Lucian Wischik's [Six Essential Tips for Async](https://channel9.msdn.com/Series/Three-Essential-Tips-for-Async) are a wonderful resource for async programming</span></span>