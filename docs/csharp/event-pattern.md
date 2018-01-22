---
title: "Padrões de evento .NET padrão"
description: "Saiba mais sobre como criar padrões de evento .NET e como criar origens de evento padrão, bem como assinar e processar os eventos padrão em seu código."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 8a3133d6-4ef2-46f9-9c8d-a8ea8898e4c9
ms.openlocfilehash: ff36438ab02ae6822d7df8425a615aef2ddbf2f2
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="standard-net-event-patterns"></a><span data-ttu-id="524a7-104">Padrões de evento .NET padrão</span><span class="sxs-lookup"><span data-stu-id="524a7-104">Standard .NET event patterns</span></span>

[<span data-ttu-id="524a7-105">Anterior</span><span class="sxs-lookup"><span data-stu-id="524a7-105">Previous</span></span>](events-overview.md)

<span data-ttu-id="524a7-106">Os eventos do .NET geralmente seguem alguns padrões conhecidos.</span><span class="sxs-lookup"><span data-stu-id="524a7-106">.NET events generally follow a few known patterns.</span></span> <span data-ttu-id="524a7-107">Adotar esses padrões significa que os desenvolvedores podem aproveitar o conhecimento desses padrões, que podem ser aplicados a qualquer programa de evento do .NET.</span><span class="sxs-lookup"><span data-stu-id="524a7-107">Standardizing on these patterns means that developers can leverage knowledge of those standard patterns, which can be applied to any .NET event program.</span></span>

<span data-ttu-id="524a7-108">Vamos analisar esses padrões para que você obtenha todo o conhecimento que precisa a fim de criar origens do evento padrão e também assinar e processar eventos padrão em seu código.</span><span class="sxs-lookup"><span data-stu-id="524a7-108">Let's go through these standard patterns so you will have all the knowledge you need to create standard event sources, and subscribe and process standard events in your code.</span></span>

## <a name="event-delegate-signatures"></a><span data-ttu-id="524a7-109">Assinaturas de delegado de evento</span><span class="sxs-lookup"><span data-stu-id="524a7-109">Event Delegate Signatures</span></span>

<span data-ttu-id="524a7-110">A assinatura padrão de um delegado de evento do .NET é:</span><span class="sxs-lookup"><span data-stu-id="524a7-110">The standard signature for a .NET event delegate is:</span></span>

```csharp
void OnEventRaised(object sender, EventArgs args);
```

<span data-ttu-id="524a7-111">O tipo de retorno é nulo.</span><span class="sxs-lookup"><span data-stu-id="524a7-111">The return type is void.</span></span> <span data-ttu-id="524a7-112">Os eventos são baseados em delegados e são delegados multicast.</span><span class="sxs-lookup"><span data-stu-id="524a7-112">Events are based on delegates and are multicast delegates.</span></span> <span data-ttu-id="524a7-113">Isso dá suporte a vários assinantes de qualquer origem do evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-113">That supports multiple subscribers for any event source.</span></span> <span data-ttu-id="524a7-114">O único valor retornado de um método não ajusta a escala para vários assinantes do evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-114">The single return value from a method doesn't scale to multiple event subscribers.</span></span> <span data-ttu-id="524a7-115">Qual valor retornado a origem do evento vê depois de gerar um evento?</span><span class="sxs-lookup"><span data-stu-id="524a7-115">Which return value does the event source see after raising an event?</span></span> <span data-ttu-id="524a7-116">Neste artigo, você verá como criar protocolos de evento que oferecem suporte a assinantes de evento que relatam informações para a origem do evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-116">Later in this article you'll see how to create event protocols that support event subscribers that report information to the event source.</span></span>

<span data-ttu-id="524a7-117">A lista de argumentos contém dois argumentos: o remetente e os argumentos do evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-117">The argument list contains two arguments: the sender, and the event arguments.</span></span> <span data-ttu-id="524a7-118">O tipo de tempo de compilação de `sender` é `System.Object`, mas é provável que você conheça um tipo mais derivado que sempre estaria correto.</span><span class="sxs-lookup"><span data-stu-id="524a7-118">The compile time type of `sender` is `System.Object`, even though you likely know a more derived type that would always be correct.</span></span> <span data-ttu-id="524a7-119">Por convenção, use `object`.</span><span class="sxs-lookup"><span data-stu-id="524a7-119">By convention, use `object`.</span></span>

<span data-ttu-id="524a7-120">O segundo argumento normalmente tem sido um tipo derivado de `System.EventArgs`.</span><span class="sxs-lookup"><span data-stu-id="524a7-120">The second argument has typically been a type that is derived from `System.EventArgs`.</span></span> <span data-ttu-id="524a7-121">(Você verá na [próxima seção](modern-events.md) que essa convenção não é mais imposta). Se seu tipo de evento não precisar de nenhum argumento adicional, você ainda fornecerá os dois argumentos.</span><span class="sxs-lookup"><span data-stu-id="524a7-121">(You'll see in the [next section](modern-events.md) that this convention is no longer enforced.) If your event type does not need any additional arguments, you will still provide both arguments.</span></span>
<span data-ttu-id="524a7-122">Há um valor especial, o `EventArgs.Empty`, que você deve usar para indicar que o evento não contém nenhuma informação adicional.</span><span class="sxs-lookup"><span data-stu-id="524a7-122">There is a special value, `EventArgs.Empty` that you should use to denote that your event does not contain any additional information.</span></span>

<span data-ttu-id="524a7-123">Vamos criar uma classe que lista os arquivos em um diretório ou em qualquer um de seus subdiretórios, que seguem um padrão.</span><span class="sxs-lookup"><span data-stu-id="524a7-123">Let's build a class that lists files in a directory, or any of its subdirectories that follow a pattern.</span></span> <span data-ttu-id="524a7-124">Esse componente aciona um evento para cada arquivo encontrado que corresponde ao padrão.</span><span class="sxs-lookup"><span data-stu-id="524a7-124">This component raises an event for each file found that matches the pattern.</span></span>

<span data-ttu-id="524a7-125">O uso de um modelo de evento fornece algumas vantagens de design.</span><span class="sxs-lookup"><span data-stu-id="524a7-125">Using an event model provides some design advantages.</span></span> <span data-ttu-id="524a7-126">Você pode criar vários ouvintes de eventos que realizam ações diferentes quando um arquivo procurado é encontrado.</span><span class="sxs-lookup"><span data-stu-id="524a7-126">You can create multiple event listeners that perform different actions when a sought file is found.</span></span> <span data-ttu-id="524a7-127">A combinação de diferentes ouvintes pode criar algoritmos mais robustos.</span><span class="sxs-lookup"><span data-stu-id="524a7-127">Combining the different listeners can create more robust algorithms.</span></span>

<span data-ttu-id="524a7-128">Aqui está a declaração de argumento de evento inicial para localizar um arquivo pesquisado:</span><span class="sxs-lookup"><span data-stu-id="524a7-128">Here is the initial event argument declaration for finding a sought file:</span></span> 

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

<span data-ttu-id="524a7-129">Embora esse tipo se pareça com um tipo pequeno de somente dados, você deve seguir a convenção e torná-lo um tipo de referência (`class`).</span><span class="sxs-lookup"><span data-stu-id="524a7-129">Even though this type looks like a small, data-only type, you should follow the convention and make it a reference (`class`) type.</span></span> <span data-ttu-id="524a7-130">Isso significa que o objeto de argumento será passado por referência e todas as atualizações nos dados serão visualizadas por todos os assinantes.</span><span class="sxs-lookup"><span data-stu-id="524a7-130">That means the argument object will be passed by reference, and any updates to the data will be viewed by all subscribers.</span></span> <span data-ttu-id="524a7-131">A primeira versão é um objeto imutável.</span><span class="sxs-lookup"><span data-stu-id="524a7-131">The first version is an immutable object.</span></span> <span data-ttu-id="524a7-132">É preferível tornar as propriedades em seu tipo de argumento de evento imutáveis.</span><span class="sxs-lookup"><span data-stu-id="524a7-132">You should prefer to make the properties in your event argument type immutable.</span></span> <span data-ttu-id="524a7-133">Dessa forma, um assinante não poderá alterar os valores antes que outro assinante os veja.</span><span class="sxs-lookup"><span data-stu-id="524a7-133">That way, one subscriber cannot change the values before another subscriber sees them.</span></span> <span data-ttu-id="524a7-134">(Há exceções, como você verá abaixo).</span><span class="sxs-lookup"><span data-stu-id="524a7-134">(There are exceptions to this, as you'll see below.)</span></span>  

<span data-ttu-id="524a7-135">Em seguida, precisamos criar a declaração de evento na classe FileSearcher.</span><span class="sxs-lookup"><span data-stu-id="524a7-135">Next, we need to create the event declaration in the FileSearcher class.</span></span> <span data-ttu-id="524a7-136">O aproveitamento do tipo `EventHandler<T>` significa que não é necessário criar outra definição de tipo.</span><span class="sxs-lookup"><span data-stu-id="524a7-136">Leveraging the `EventHandler<T>` type means that you don't need to create yet another type definition.</span></span> <span data-ttu-id="524a7-137">Você simplesmente usa uma especialização genérica.</span><span class="sxs-lookup"><span data-stu-id="524a7-137">You simply use a generic specialization.</span></span>

<span data-ttu-id="524a7-138">Vamos preencher a classe FileSearcher para pesquisar arquivos que correspondam a um padrão e acionar o evento correto quando uma correspondência for descoberta.</span><span class="sxs-lookup"><span data-stu-id="524a7-138">Let's fill out the FileSearcher class to search for files that match a pattern, and raise the correct event when a match is discovered.</span></span>

```csharp
public class FileSearcher
{
    public event EventHandler<FileFoundArgs> FileFound;

    public void Search(string directory, string searchPattern)
    {
        foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
        {
            FileFound?.Invoke(this, new FileFoundArgs(file));
        }
    }
}
```

## <a name="definining-and-raising-field-like-events"></a><span data-ttu-id="524a7-139">Definindo e acionando eventos semelhantes a campo</span><span class="sxs-lookup"><span data-stu-id="524a7-139">Definining and Raising Field-Like Events</span></span>

<span data-ttu-id="524a7-140">A maneira mais simples de adicionar um evento à sua classe é declarar esse evento como um campo público, como no exemplo acima:</span><span class="sxs-lookup"><span data-stu-id="524a7-140">The simplest way to add an event to your class is to declare that event as a public field, as in the above example:</span></span>

```csharp
public event EventHandler<FileFoundArgs> FileFound;
```

<span data-ttu-id="524a7-141">Isso é semelhante à declaração de um campo público, o que parece ser uma prática ruim orientada a objetos.</span><span class="sxs-lookup"><span data-stu-id="524a7-141">This looks like it's declaring a public field, which would appear to be bad object oriented practice.</span></span> <span data-ttu-id="524a7-142">Você deseja proteger o acesso a dados por meio de propriedades ou métodos.</span><span class="sxs-lookup"><span data-stu-id="524a7-142">You want to protect data access through properties, or methods.</span></span> <span data-ttu-id="524a7-143">Ao mesmo tempo em que isso se parece com uma prática ruim, o código gerado pelo compilador cria wrappers para que os objetos de evento só possam ser acessados de maneiras seguras.</span><span class="sxs-lookup"><span data-stu-id="524a7-143">While this make look like a bad practice, the code generated by the compiler does create wrappers so that the event objects can only be accessed in safe ways.</span></span> <span data-ttu-id="524a7-144">As únicas operações disponíveis em um evento semelhante a campo são adicionar manipulador:</span><span class="sxs-lookup"><span data-stu-id="524a7-144">The only operations available on a field-like event are add handler:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
    Console.WriteLine(eventArgs.FoundFile);
lister.FileFound += onFileFound;
```

<span data-ttu-id="524a7-145">e remover manipulador:</span><span class="sxs-lookup"><span data-stu-id="524a7-145">and remove handler:</span></span>

```csharp
lister.FileFound -= onFileFound;
```

<span data-ttu-id="524a7-146">Observe que há uma variável local para o manipulador.</span><span class="sxs-lookup"><span data-stu-id="524a7-146">Note that there's a local variable for the handler.</span></span> <span data-ttu-id="524a7-147">Se você usou o corpo de lambda, a operação remover não funcionará corretamente.</span><span class="sxs-lookup"><span data-stu-id="524a7-147">If you used the body of the lambda, the remove would not work correctly.</span></span> <span data-ttu-id="524a7-148">Ela seria uma instância diferente do delegado e silenciosamente não faria nada.</span><span class="sxs-lookup"><span data-stu-id="524a7-148">It would be a different instance of the delegate, and silently do nothing.</span></span>

<span data-ttu-id="524a7-149">O código fora da classe não pode acionar o evento nem executar outras operações.</span><span class="sxs-lookup"><span data-stu-id="524a7-149">Code outside the class cannot raise the event, nor can it perform any other operations.</span></span>

## <a name="returning-values-from-event-subscribers"></a><span data-ttu-id="524a7-150">Valor retornados de assinantes de evento</span><span class="sxs-lookup"><span data-stu-id="524a7-150">Returning Values from Event Subscribers</span></span>

<span data-ttu-id="524a7-151">Sua versão simples está funcionando bem.</span><span class="sxs-lookup"><span data-stu-id="524a7-151">Your simple version is working fine.</span></span> <span data-ttu-id="524a7-152">Vamos adicionar outro recurso: cancelamento.</span><span class="sxs-lookup"><span data-stu-id="524a7-152">Let's add another feature: Cancellation.</span></span>

<span data-ttu-id="524a7-153">Quando você acionar o evento encontrado, os ouvintes devem ser capazes de parar o processamento, se esse arquivo for aquele que era procurado.</span><span class="sxs-lookup"><span data-stu-id="524a7-153">When you raise the found event, listeners should be able to stop further processing, if this file is that last one sought.</span></span>

<span data-ttu-id="524a7-154">Os manipuladores de eventos não retornam um valor, por isso você precisa comunicar isso de outra forma.</span><span class="sxs-lookup"><span data-stu-id="524a7-154">The event handlers do not return a value, so you need to communicate that in another way.</span></span> <span data-ttu-id="524a7-155">O padrão de evento usa o objeto EventArgs para incluir campos que os assinantes de evento podem usar para comunicar o cancelamento.</span><span class="sxs-lookup"><span data-stu-id="524a7-155">The standard event pattern uses the EventArgs object to include fields that event subscribers can use to communicate cancel.</span></span>

<span data-ttu-id="524a7-156">Há dois padrões diferentes que podem ser usados, com base na semântica do contrato de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="524a7-156">There are two different patterns that could be used, based on the semantics of the Cancel contract.</span></span> <span data-ttu-id="524a7-157">Em ambos os casos, você adicionará um campo booliano no EventArguments para o evento de arquivo encontrado.</span><span class="sxs-lookup"><span data-stu-id="524a7-157">In both cases, you'll add a boolean field to the EventArguments for the found file event.</span></span> 

<span data-ttu-id="524a7-158">Um padrão permitiria a qualquer assinante cancelar a operação.</span><span class="sxs-lookup"><span data-stu-id="524a7-158">One pattern would allow any one subscriber to cancel the operation.</span></span>
<span data-ttu-id="524a7-159">Para esse padrão, o novo campo é inicializado para `false`.</span><span class="sxs-lookup"><span data-stu-id="524a7-159">For this pattern, the new field is initialized to `false`.</span></span> <span data-ttu-id="524a7-160">Qualquer assinante pode alterá-lo para `true`.</span><span class="sxs-lookup"><span data-stu-id="524a7-160">Any subscriber can change it to `true`.</span></span> <span data-ttu-id="524a7-161">Depois que todos os assinantes viram o evento acionado, o componente FileSearcher examina o valor booliano e toma uma ação.</span><span class="sxs-lookup"><span data-stu-id="524a7-161">After all subscribers have seen the event raised, the FileSearcher component examines the boolean value and takes action.</span></span>

<span data-ttu-id="524a7-162">O segundo padrão só cancelaria a operação se todos os assinantes quisessem que a operação fosse cancelada.</span><span class="sxs-lookup"><span data-stu-id="524a7-162">The second pattern would only cancel the operation if all subscribers wanted the operation cancelled.</span></span> <span data-ttu-id="524a7-163">Nesse padrão, o novo campo é inicializado para indicar que a operação deve ser cancelada e qualquer assinante poderia alterá-lo para indicar que a operação deve continuar.</span><span class="sxs-lookup"><span data-stu-id="524a7-163">In this pattern, the new field is initialized to indicate the operation should cancel, and any subscriber could change it to indicate the operation should continue.</span></span>
<span data-ttu-id="524a7-164">Depois que todos os assinantes viram o evento acionado, o componente FileSearcher examina o booliano e toma uma ação.</span><span class="sxs-lookup"><span data-stu-id="524a7-164">After all subscribers have seen the event raised, the FileSearcher component examines the boolean and takes action.</span></span> <span data-ttu-id="524a7-165">Há uma etapa adicional nesse padrão: o componente precisa saber se algum assinante viu o evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-165">There is one extra step in this pattern: the component needs to know if any subscribers have seen the event.</span></span> <span data-ttu-id="524a7-166">Se não houver nenhum assinante, o campo indicaria incorretamente um cancelamento.</span><span class="sxs-lookup"><span data-stu-id="524a7-166">If there are no subscribers, the field would indicate a cancel incorrectly.</span></span>

<span data-ttu-id="524a7-167">Vamos implementar a primeira versão deste exemplo.</span><span class="sxs-lookup"><span data-stu-id="524a7-167">Let's implement the first version for this sample.</span></span> <span data-ttu-id="524a7-168">Você precisa adicionar um campo booliano ao tipo FileFoundEventArgs:</span><span class="sxs-lookup"><span data-stu-id="524a7-168">You need to add a boolean field to the FileFoundEventArgs type:</span></span>

```csharp
public class FileFoundArgs : EventArgs
{
    public string FoundFile { get; }
    public bool CancelRequested { get; set; }

    public FileFoundArgs(string fileName)
    {
        FoundFile = fileName;
    }
}
```

<span data-ttu-id="524a7-169">Esse novo campo deve ser inicializado como falso, de forma que você não cancele sem motivo.</span><span class="sxs-lookup"><span data-stu-id="524a7-169">This new Field should be initialized to false, so you don't cancel for no reason.</span></span> <span data-ttu-id="524a7-170">Esse é o valor padrão de um campo booliano, portanto isso acontece automaticamente.</span><span class="sxs-lookup"><span data-stu-id="524a7-170">That is the default value for a boolean field, so that happens automatically.</span></span> <span data-ttu-id="524a7-171">A única alteração adicional no componente é verificar o sinalizador depois de acionar o evento, para ver se qualquer um dos assinantes solicitou um cancelamento:</span><span class="sxs-lookup"><span data-stu-id="524a7-171">The only other change to the component is to check the flag after raising the event to see if any of the subscribers have requested a cancellation:</span></span>

```csharp
public void List(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="524a7-172">Uma vantagem desse padrão é que ele não é uma alteração significativa.</span><span class="sxs-lookup"><span data-stu-id="524a7-172">One advantage of this pattern is that it isn't a breaking change.</span></span>
<span data-ttu-id="524a7-173">Nenhum dos assinantes solicitou um cancelamento antes e ainda não o fizeram.</span><span class="sxs-lookup"><span data-stu-id="524a7-173">None of the subscribers requested a cancel before, and they still are not.</span></span> <span data-ttu-id="524a7-174">Nenhuma parte do código de assinante precisa ser atualizado, a menos que eles queiram dar suporte ao novo protocolo de cancelamento.</span><span class="sxs-lookup"><span data-stu-id="524a7-174">None of the subscriber code needs updating unless they want to support the new cancel protocol.</span></span> <span data-ttu-id="524a7-175">Ele é acoplado de forma bem livre.</span><span class="sxs-lookup"><span data-stu-id="524a7-175">It's very loosely coupled.</span></span>

<span data-ttu-id="524a7-176">Vamos atualizar o assinante para que ele solicite um cancelamento, depois de encontrar o primeiro executável:</span><span class="sxs-lookup"><span data-stu-id="524a7-176">Let's update the subscriber so that it requests a cancellation once it finds the first executable:</span></span>

```csharp
EventHandler<FileFoundArgs> onFileFound = (sender, eventArgs) =>
{
    Console.WriteLine(eventArgs.FoundFile);
    eventArgs.CancelRequested = true;
};
```

## <a name="adding-another-event-declaration"></a><span data-ttu-id="524a7-177">Adicionar outra declaração de evento</span><span class="sxs-lookup"><span data-stu-id="524a7-177">Adding Another Event Declaration</span></span>

<span data-ttu-id="524a7-178">Vamos adicionar mais um recurso e demonstrar outras expressões de linguagem para eventos.</span><span class="sxs-lookup"><span data-stu-id="524a7-178">Let's add one more feature, and demonstrate other language idioms for events.</span></span> <span data-ttu-id="524a7-179">Vamos adicionar uma sobrecarga do método `Search()` que percorre todas os subdiretórios pesquisando arquivos.</span><span class="sxs-lookup"><span data-stu-id="524a7-179">Let's add an overload of the `Search()` method that traverses all subdirectories in search of files.</span></span>

<span data-ttu-id="524a7-180">Isso poderia se tornar uma operação demorada em um diretório com muitos subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="524a7-180">This could get to be a lengthy operation in a directory with many sub-directories.</span></span> <span data-ttu-id="524a7-181">Vamos adicionar um evento que é acionado no início de cada nova pesquisa de diretório.</span><span class="sxs-lookup"><span data-stu-id="524a7-181">Let's add an event that gets raised when each new directory search begins.</span></span> <span data-ttu-id="524a7-182">Isso permite que os assinantes acompanhem o progresso e atualizem o usuário sobre o progresso.</span><span class="sxs-lookup"><span data-stu-id="524a7-182">This enables subscribers to track progress, and update the user as to progress.</span></span> <span data-ttu-id="524a7-183">Todos os exemplos que você criou até agora são públicos.</span><span class="sxs-lookup"><span data-stu-id="524a7-183">All the samples you've created so far are public.</span></span> <span data-ttu-id="524a7-184">Vamos fazer com que esse seja um evento interno.</span><span class="sxs-lookup"><span data-stu-id="524a7-184">Let's make this one an internal event.</span></span> <span data-ttu-id="524a7-185">Isso significa que você também pode fazer com que os tipos usados para os argumentos sejam internos.</span><span class="sxs-lookup"><span data-stu-id="524a7-185">That means you can also make the types used for the arguments internal as well.</span></span>

<span data-ttu-id="524a7-186">Você começará criando a nova classe derivada EventArgs para relatar o novo diretório e o andamento.</span><span class="sxs-lookup"><span data-stu-id="524a7-186">You'll start by creating the new EventArgs derived class for reporting the new directory and progress.</span></span> 

```csharp
internal class SearchDirectoryArgs : EventArgs
{
    internal string CurrentSearchDirectory { get; }
    internal int TotalDirs { get; }
    internal int CompletedDirs { get; }

    internal SearchDirectoryArgs(string dir, int totalDirs, int completedDirs)
    {
        CurrentSearchDirectory = dir;
        TotalDirs = totalDirs;
        CompletedDirs = completedDirs;
    }
}
``` 

<span data-ttu-id="524a7-187">Novamente, você pode seguir as recomendações para criar um tipo de referência imutável para os argumentos do evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-187">Again, you can follow the recommendations to make an immutable reference type for the event arguments.</span></span>

<span data-ttu-id="524a7-188">Em seguida, defina o evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-188">Next, define the event.</span></span> <span data-ttu-id="524a7-189">Desta vez, você usará uma sintaxe diferente.</span><span class="sxs-lookup"><span data-stu-id="524a7-189">This time, you'll use a different syntax.</span></span> <span data-ttu-id="524a7-190">Além de usar a sintaxe de campo, você pode explicitamente criar a propriedade com os manipuladores adicionar e remover.</span><span class="sxs-lookup"><span data-stu-id="524a7-190">In addition to using the field syntax, you can explicitly create the property, with add and remove handlers.</span></span> <span data-ttu-id="524a7-191">Neste projeto de exemplo, você não precisará de código extra nos manipuladores, mas será mostrado como criá-los.</span><span class="sxs-lookup"><span data-stu-id="524a7-191">In this sample, you won't need extra code in those handlers in this project, but this shows how you would create them.</span></span>

```csharp
internal event EventHandler<SearchDirectoryArgs> DirectoryChanged
{
    add { directoryChanged += value; }
    remove { directoryChanged -= value; }
}
private EventHandler<SearchDirectoryArgs> directoryChanged;
```

<span data-ttu-id="524a7-192">O código que você escreverá aqui é bem parecido com o código que o compilador gera para as definições de evento de campo vistas anteriormente.</span><span class="sxs-lookup"><span data-stu-id="524a7-192">In may ways, the code you write here mirrors the code the compiler generates for the field event definitions you've seen earlier.</span></span> <span data-ttu-id="524a7-193">Você cria o evento usando uma sintaxe muito parecida àquela utilizada para [propriedades](properties.md).</span><span class="sxs-lookup"><span data-stu-id="524a7-193">You create the event using syntax very similar to that used for [properties](properties.md).</span></span> <span data-ttu-id="524a7-194">Observe que os manipuladores têm nomes diferentes: `add` e `remove`.</span><span class="sxs-lookup"><span data-stu-id="524a7-194">Notice that the handlers have different names: `add` and `remove`.</span></span> <span data-ttu-id="524a7-195">Eles são chamados para assinar o evento ou cancelar a inscrição do evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-195">These are called to subscribe to the event, or unsubscribe from the event.</span></span> <span data-ttu-id="524a7-196">Observe que você também deve declarar um campo de suporte particular para armazenar a variável de evento.</span><span class="sxs-lookup"><span data-stu-id="524a7-196">Notice that you also must declare a private backing field to store the event variable.</span></span> <span data-ttu-id="524a7-197">Ele é inicializado como null.</span><span class="sxs-lookup"><span data-stu-id="524a7-197">It is initialized to null.</span></span>

<span data-ttu-id="524a7-198">Em seguida, vamos adicionar a sobrecarga do método Search() que percorre os subdiretórios e aciona os dois eventos.</span><span class="sxs-lookup"><span data-stu-id="524a7-198">Next, let's add the overload of the Search() method that traverses subdirectories and raises both events.</span></span> <span data-ttu-id="524a7-199">A maneira mais fácil de fazer isso é usar um argumento padrão para especificar que você deseja pesquisar todas as pastas:</span><span class="sxs-lookup"><span data-stu-id="524a7-199">The easiest way to accomplish this is to use a default argument to specify that you want to search all directories:</span></span>

```csharp
public void Search(string directory, string searchPattern, bool searchSubDirs = false)
{
    if (searchSubDirs)
    {
        var allDirectories = Directory.GetDirectories(directory, "*.*", SearchOption.AllDirectories);
        var completedDirs = 0;
        var totalDirs = allDirectories.Length + 1;
        foreach (var dir in allDirectories)
        {
            directoryChanged?.Invoke(this,
                new SearchDirectoryArgs(dir, totalDirs, completedDirs++));
            // Recursively search this child directory:
            SearchDirectory(dir, searchPattern);
        }
        // Include the Current Directory:
        directoryChanged?.Invoke(this,
            new SearchDirectoryArgs(directory, totalDirs, completedDirs++));
        SearchDirectory(directory, searchPattern);
    }
    else
    {
        SearchDirectory(directory, searchPattern);
    }
}

private void SearchDirectory(string directory, string searchPattern)
{
    foreach (var file in Directory.EnumerateFiles(directory, searchPattern))
    {
        var args = new FileFoundArgs(file);
        FileFound?.Invoke(this, args);
        if (args.CancelRequested)
            break;
    }
}
```

<span data-ttu-id="524a7-200">Neste momento, você pode executar o aplicativo, chamando a sobrecarga para pesquisar todos os subdiretórios.</span><span class="sxs-lookup"><span data-stu-id="524a7-200">At this point, you can run the application calling the overload for searching all sub-directories.</span></span> <span data-ttu-id="524a7-201">Não há nenhum assinante no novo evento `ChangeDirectory`, mas o uso da expressão `?.Invoke()` garante que isso funcione corretamente.</span><span class="sxs-lookup"><span data-stu-id="524a7-201">There are no subscribers on the new `ChangeDirectory` event, but using the `?.Invoke()` idiom ensures that this works correctly.</span></span>

 <span data-ttu-id="524a7-202">Vamos adicionar um manipulador para escrever uma linha que mostra o andamento na janela do console.</span><span class="sxs-lookup"><span data-stu-id="524a7-202">Let's add a handler to write a line that shows the progress in the console window.</span></span> 

```csharp
lister.DirectoryChanged += (sender, eventArgs) =>
{
    Console.Write($"Entering '{eventArgs.CurrentSearchDirectory}'.");
    Console.WriteLine($" {eventArgs.CompletedDirs} of {eventArgs.TotalDirs} completed...");
};
```

<span data-ttu-id="524a7-203">Você viu os padrões que são seguidos em todo o ecossistema do .NET.</span><span class="sxs-lookup"><span data-stu-id="524a7-203">You've seen patterns that are followed throughout the .NET ecosystem.</span></span>
<span data-ttu-id="524a7-204">Ao aprender esses padrões e convenções, você escreverá expressões idiomáticas de C# e .NET rapidamente.</span><span class="sxs-lookup"><span data-stu-id="524a7-204">By learning these patterns and conventions, you'll be writing idiomatic C# and .NET quickly.</span></span>

<span data-ttu-id="524a7-205">Em seguida, você verá algumas alterações nesses padrões na versão mais recente do .NET.</span><span class="sxs-lookup"><span data-stu-id="524a7-205">Next, you'll see some changes in these patterns in the most recent release of .NET.</span></span>

[<span data-ttu-id="524a7-206">Avançar</span><span class="sxs-lookup"><span data-stu-id="524a7-206">Next</span></span>](modern-events.md)
