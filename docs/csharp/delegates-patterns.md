---
title: "Padrões Comuns para Delegados"
description: "Saiba mais sobre os padrões comuns para usar delegados em seu código para evitar acoplamento forte entre os componentes."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 83214800fb997e9274cacfd1bae85ab07c4515a2
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="common-patterns-for-delegates"></a><span data-ttu-id="22282-104">Padrões Comuns para Delegados</span><span class="sxs-lookup"><span data-stu-id="22282-104">Common Patterns for Delegates</span></span>

[<span data-ttu-id="22282-105">Anterior</span><span class="sxs-lookup"><span data-stu-id="22282-105">Previous</span></span>](delegates-strongly-typed.md)

<span data-ttu-id="22282-106">Os delegados fornecem um mecanismo que permite designs de software que envolvem acoplamento mínimo entre os componentes.</span><span class="sxs-lookup"><span data-stu-id="22282-106">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="22282-107">Um exemplo excelente desse tipo de design é o LINQ.</span><span class="sxs-lookup"><span data-stu-id="22282-107">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="22282-108">O padrão de expressão de consulta LINQ se baseia em delegados para todos os seus recursos.</span><span class="sxs-lookup"><span data-stu-id="22282-108">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="22282-109">Considere este exemplo simples:</span><span class="sxs-lookup"><span data-stu-id="22282-109">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="22282-110">Isso filtra a sequência de números para somente aqueles com valor menor que 10.</span><span class="sxs-lookup"><span data-stu-id="22282-110">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="22282-111">O método `Where` usa um delegado que determina quais elementos de uma sequência são passados no filtro.</span><span class="sxs-lookup"><span data-stu-id="22282-111">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="22282-112">Quando cria uma consulta LINQ, você fornece a implementação do delegado para essa finalidade específica.</span><span class="sxs-lookup"><span data-stu-id="22282-112">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="22282-113">O protótipo para o método Where é:</span><span class="sxs-lookup"><span data-stu-id="22282-113">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="22282-114">Este exemplo é repetido com todos os métodos que fazem parte do LINQ.</span><span class="sxs-lookup"><span data-stu-id="22282-114">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="22282-115">Todos eles contam com delegados para o código que gerencia a consulta específica.</span><span class="sxs-lookup"><span data-stu-id="22282-115">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="22282-116">Trata-se de um padrão de design de API muito eficiente para se aprender e entender.</span><span class="sxs-lookup"><span data-stu-id="22282-116">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="22282-117">Este exemplo simples ilustra como delegados requerem muito pouco acoplamento entre componentes.</span><span class="sxs-lookup"><span data-stu-id="22282-117">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="22282-118">Você não precisa criar uma classe que deriva de uma classe base específica.</span><span class="sxs-lookup"><span data-stu-id="22282-118">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="22282-119">Você não precisa implementar uma interface específica.</span><span class="sxs-lookup"><span data-stu-id="22282-119">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="22282-120">O único requisito é fornecer a implementação de um método que é fundamental para a tarefa em questão.</span><span class="sxs-lookup"><span data-stu-id="22282-120">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="22282-121">Criando seus próprios componentes com delegados</span><span class="sxs-lookup"><span data-stu-id="22282-121">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="22282-122">Vamos trabalhar naquele exemplo criando um componente usando um design que se baseia em delegados.</span><span class="sxs-lookup"><span data-stu-id="22282-122">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="22282-123">Vamos definir um componente que poderia ser usado para mensagens de log em um sistema grande.</span><span class="sxs-lookup"><span data-stu-id="22282-123">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="22282-124">Os componentes da biblioteca poderiam ser usados em muitos ambientes diferentes, em várias plataformas diferentes.</span><span class="sxs-lookup"><span data-stu-id="22282-124">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="22282-125">Há muitos recursos comuns no componente que gerencia os logs.</span><span class="sxs-lookup"><span data-stu-id="22282-125">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="22282-126">Ele precisará aceitar mensagens de qualquer componente do sistema.</span><span class="sxs-lookup"><span data-stu-id="22282-126">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="22282-127">Essas mensagens terão prioridades diferentes, que o componente de núcleo pode gerenciar.</span><span class="sxs-lookup"><span data-stu-id="22282-127">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="22282-128">As mensagens devem ter carimbos de data/hora em sua forma final arquivada.</span><span class="sxs-lookup"><span data-stu-id="22282-128">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="22282-129">Para cenários mais avançados, é possível filtrar mensagens pelo componente de origem.</span><span class="sxs-lookup"><span data-stu-id="22282-129">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="22282-130">Há um aspecto do recurso que é alterado com frequência: onde as mensagens são gravadas.</span><span class="sxs-lookup"><span data-stu-id="22282-130">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="22282-131">Em alguns ambientes, elas podem ser gravadas no console de erro.</span><span class="sxs-lookup"><span data-stu-id="22282-131">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="22282-132">Em outros, em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="22282-132">In others, a file.</span></span> <span data-ttu-id="22282-133">Outras possibilidades incluem o armazenamento em banco de dados, logs de eventos do sistema operacional ou outro armazenamento de documentos.</span><span class="sxs-lookup"><span data-stu-id="22282-133">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="22282-134">Também há combinações de saídas que podem ser usadas em cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="22282-134">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="22282-135">Talvez você queira gravar mensagens no console e em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="22282-135">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="22282-136">Um design baseado em delegados fornece muita flexibilidade e facilitam o suporte a mecanismos de armazenamento que podem ser adicionados no futuro.</span><span class="sxs-lookup"><span data-stu-id="22282-136">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="22282-137">Nesse design, o componente de log primário pode ser uma classe não virtual, até mesmo lacrada.</span><span class="sxs-lookup"><span data-stu-id="22282-137">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="22282-138">Você pode conectar qualquer conjunto de delegados para gravar as mensagens em diferentes mídias de armazenamento.</span><span class="sxs-lookup"><span data-stu-id="22282-138">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="22282-139">O suporte interno para delegados multicast facilita o suporte a cenários em que as mensagens devem ser gravadas em vários locais (um arquivo e um console).</span><span class="sxs-lookup"><span data-stu-id="22282-139">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="22282-140">Uma primeira implementação</span><span class="sxs-lookup"><span data-stu-id="22282-140">A First Implementation</span></span>

<span data-ttu-id="22282-141">Vamos começar pequeno: a implementação inicial aceitará novas mensagens e as gravará usando qualquer delegado anexo.</span><span class="sxs-lookup"><span data-stu-id="22282-141">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="22282-142">Você pode começar com um delegado que grava mensagens no console.</span><span class="sxs-lookup"><span data-stu-id="22282-142">You can start with one delegate that writes messages to the console.</span></span>

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

<span data-ttu-id="22282-143">A classe estática acima é a coisa mais simples que pode funcionar.</span><span class="sxs-lookup"><span data-stu-id="22282-143">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="22282-144">Precisamos escrever a única implementação do método que grava mensagens no console:</span><span class="sxs-lookup"><span data-stu-id="22282-144">We need to write the single implementation for the method that writes messages to the console:</span></span> 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

<span data-ttu-id="22282-145">Por fim, você precisa conectar o delegado anexando-o ao delegado WriteMessage declarado no agente:</span><span class="sxs-lookup"><span data-stu-id="22282-145">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="22282-146">Práticas</span><span class="sxs-lookup"><span data-stu-id="22282-146">Practices</span></span>

<span data-ttu-id="22282-147">Até agora, nossa amostra é bastante simples, mas ainda demonstra algumas das diretrizes importantes para designs que envolvem delegados.</span><span class="sxs-lookup"><span data-stu-id="22282-147">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="22282-148">Usar os tipos de delegados definidos no Core Framework torna mais fácil para os usuários trabalhem com os delegados.</span><span class="sxs-lookup"><span data-stu-id="22282-148">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="22282-149">Você não precisa definir novos tipos e os desenvolvedores que usam sua biblioteca não precisam aprender novos tipos de delegados especializadas.</span><span class="sxs-lookup"><span data-stu-id="22282-149">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="22282-150">As interfaces usadas são tão mínimas e flexíveis quanto possível: para criar um novo agente de saída, você precisa criar um método.</span><span class="sxs-lookup"><span data-stu-id="22282-150">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="22282-151">O método pode ser um método estático ou um método de instância.</span><span class="sxs-lookup"><span data-stu-id="22282-151">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="22282-152">Ele pode ter qualquer acesso.</span><span class="sxs-lookup"><span data-stu-id="22282-152">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="22282-153">Saída de formatação</span><span class="sxs-lookup"><span data-stu-id="22282-153">Formatting Output</span></span>

<span data-ttu-id="22282-154">Vamos fazer esta primeira versão um pouco mais robusta e, então, começar a criar outros mecanismos de registro em log.</span><span class="sxs-lookup"><span data-stu-id="22282-154">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="22282-155">Em seguida, vamos adicionar alguns argumentos para o método `LogMessage()` para que sua classe de log crie mensagens mais estruturadas:</span><span class="sxs-lookup"><span data-stu-id="22282-155">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

<span data-ttu-id="22282-156">Em seguida, vamos usar aquele argumento `Severity` para filtrar as mensagens que são enviadas para o log de saída.</span><span class="sxs-lookup"><span data-stu-id="22282-156">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span> 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a><span data-ttu-id="22282-157">Práticas</span><span class="sxs-lookup"><span data-stu-id="22282-157">Practices</span></span>

<span data-ttu-id="22282-158">Você adicionou novos recursos à infraestrutura de registro em log.</span><span class="sxs-lookup"><span data-stu-id="22282-158">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="22282-159">Como somente o componente do agente está acoplado de forma muito flexível a qualquer mecanismo de saída, esses novos recursos podem ser adicionados sem afetar o código que implementa o delegado do agente.</span><span class="sxs-lookup"><span data-stu-id="22282-159">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="22282-160">Conforme prosseguir com sua criação, você verá mais exemplos de como esse acoplamento flexível permite maior versatilidade para atualizar partes do site sem alterar outros locais.</span><span class="sxs-lookup"><span data-stu-id="22282-160">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="22282-161">De fato, em um aplicativo maior, as classes de saída do agente podem estar em um assembly diferente e nem mesmo precisar ser recriadas.</span><span class="sxs-lookup"><span data-stu-id="22282-161">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="22282-162">Criando um segundo mecanismo de saída</span><span class="sxs-lookup"><span data-stu-id="22282-162">Building a Second Output Engine</span></span>

<span data-ttu-id="22282-163">O componente de Log estará indo bem.</span><span class="sxs-lookup"><span data-stu-id="22282-163">The Log component is coming along well.</span></span> <span data-ttu-id="22282-164">Vamos adicionar mais um mecanismo de saída que registra as mensagens em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="22282-164">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="22282-165">Esse será um mecanismo de saída de um pouco mais envolvido.</span><span class="sxs-lookup"><span data-stu-id="22282-165">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="22282-166">Ele será uma classe que encapsula as operações de arquivo e garante que o arquivo sempre seja fechado após cada gravação.</span><span class="sxs-lookup"><span data-stu-id="22282-166">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="22282-167">Isso garante que todos os dados sejam liberados no disco após cada mensagem ser gerada.</span><span class="sxs-lookup"><span data-stu-id="22282-167">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="22282-168">Este é um agente baseado em arquivo:</span><span class="sxs-lookup"><span data-stu-id="22282-168">Here is that file based logger:</span></span>

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

<span data-ttu-id="22282-169">Após ter criado essa classe, você pode instanciá-la e ela anexa o método LogMessage ao componente do agente:</span><span class="sxs-lookup"><span data-stu-id="22282-169">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

```csharp
var file = new FileLogger("log.txt");
```

<span data-ttu-id="22282-170">Os dois não são mutuamente exclusivos.</span><span class="sxs-lookup"><span data-stu-id="22282-170">These two are not mutually exclusive.</span></span> <span data-ttu-id="22282-171">Você pode anexar os dois métodos de log e gerar mensagens para o console e um arquivo:</span><span class="sxs-lookup"><span data-stu-id="22282-171">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

<span data-ttu-id="22282-172">Posteriormente, mesmo no mesmo aplicativo, você pode remover um dos delegados sem problemas para o sistema:</span><span class="sxs-lookup"><span data-stu-id="22282-172">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="22282-173">Práticas</span><span class="sxs-lookup"><span data-stu-id="22282-173">Practices</span></span>

<span data-ttu-id="22282-174">Agora, você adicionou um segundo manipulador de saída para o subsistema de registro em log.</span><span class="sxs-lookup"><span data-stu-id="22282-174">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="22282-175">Este precisa de um pouco mais infraestrutura para dar suporte ao sistema de arquivos corretamente.</span><span class="sxs-lookup"><span data-stu-id="22282-175">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="22282-176">O delegado um método de instância.</span><span class="sxs-lookup"><span data-stu-id="22282-176">The delegate is an instance method.</span></span> <span data-ttu-id="22282-177">Ele também é um método particular.</span><span class="sxs-lookup"><span data-stu-id="22282-177">It's also a private method.</span></span>
<span data-ttu-id="22282-178">Não é necessário ter mais acessibilidade porque a infraestrutura de delegados pode conectar os delegados.</span><span class="sxs-lookup"><span data-stu-id="22282-178">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="22282-179">Em segundo lugar, o design baseado em delegados permite vários métodos de saída sem nenhum código extra.</span><span class="sxs-lookup"><span data-stu-id="22282-179">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="22282-180">Não é necessário criar nenhuma infraestrutura adicional para dar suporte a vários métodos de saída.</span><span class="sxs-lookup"><span data-stu-id="22282-180">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="22282-181">Eles simplesmente se tornam outro método na lista de invocação.</span><span class="sxs-lookup"><span data-stu-id="22282-181">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="22282-182">Dedique atenção especial ao código no método de saída do registro em log de arquivos.</span><span class="sxs-lookup"><span data-stu-id="22282-182">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="22282-183">Ele é codificado para garantir que não gere nenhuma exceção.</span><span class="sxs-lookup"><span data-stu-id="22282-183">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="22282-184">Embora isso nem sempre seja estritamente necessário, geralmente é uma boa prática.</span><span class="sxs-lookup"><span data-stu-id="22282-184">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="22282-185">Se um dos métodos de delegado gerar uma exceção, os delegados restantes que fazem parte da invocação não serão invocados.</span><span class="sxs-lookup"><span data-stu-id="22282-185">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="22282-186">Como uma última observação, o agente de arquivos deve gerenciar seus recursos abrindo e fechando o arquivo em cada mensagem de log.</span><span class="sxs-lookup"><span data-stu-id="22282-186">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="22282-187">Você pode optar por manter o arquivo aberto e implementar IDisposable para fechar o arquivo quando terminar.</span><span class="sxs-lookup"><span data-stu-id="22282-187">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="22282-188">Cada método tem suas vantagens e desvantagens.</span><span class="sxs-lookup"><span data-stu-id="22282-188">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="22282-189">Ambos criam um pouco mais de acoplamento entre as classes.</span><span class="sxs-lookup"><span data-stu-id="22282-189">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="22282-190">Nenhum código na classe de agente precisaria ser atualizado para dar suporte a um dos cenários.</span><span class="sxs-lookup"><span data-stu-id="22282-190">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="22282-191">Tratando delegados nulos</span><span class="sxs-lookup"><span data-stu-id="22282-191">Handling Null Delegates</span></span>

<span data-ttu-id="22282-192">Por fim, vamos atualizar o método LogMessage para que ele seja robusto para os casos em que nenhum mecanismo de saída está selecionado.</span><span class="sxs-lookup"><span data-stu-id="22282-192">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="22282-193">A implementação atual gerará um `NullReferenceException` quando o delegado `WriteMessage` não tiver uma lista de invocação anexada.</span><span class="sxs-lookup"><span data-stu-id="22282-193">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="22282-194">Talvez você prefira um design que continua silenciosamente quando não nenhum método tiver sido anexado.</span><span class="sxs-lookup"><span data-stu-id="22282-194">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="22282-195">Isso é fácil usando o operador condicional nulo, combinado com o método `Delegate.Invoke()`:</span><span class="sxs-lookup"><span data-stu-id="22282-195">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="22282-196">O operador condicional nulo (`?.`) entra em curto-circuito quando o operando esquerdo (`WriteMessage` nesse caso) for nulo, o que significa que não é feita nenhuma tentativa de registrar uma mensagem.</span><span class="sxs-lookup"><span data-stu-id="22282-196">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="22282-197">Você não encontrará o método `Invoke()` listado na documentação de `System.Delegate` ou `System.MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="22282-197">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="22282-198">O compilador gera um método `Invoke` fortemente tipado para qualquer tipo de delegado declarado.</span><span class="sxs-lookup"><span data-stu-id="22282-198">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="22282-199">Neste exemplo, isso significa que `Invoke` usa um único argumento `string` e tem um tipo de retorno nulo.</span><span class="sxs-lookup"><span data-stu-id="22282-199">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="22282-200">Resumo das práticas</span><span class="sxs-lookup"><span data-stu-id="22282-200">Summary of Practices</span></span>

<span data-ttu-id="22282-201">Você já viu o início de um componente de log que poderia ser expandido com outros gravadores e outros recursos.</span><span class="sxs-lookup"><span data-stu-id="22282-201">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="22282-202">Com o uso de delegados no design, esses diferentes componentes ficam acoplados de forma bastante flexível.</span><span class="sxs-lookup"><span data-stu-id="22282-202">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="22282-203">Isso traz vários benefícios.</span><span class="sxs-lookup"><span data-stu-id="22282-203">This provides several advantages.</span></span> <span data-ttu-id="22282-204">É muito fácil criar novos mecanismos de saída e anexá-los ao sistema.</span><span class="sxs-lookup"><span data-stu-id="22282-204">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="22282-205">Esses outros mecanismos precisam de apenas um método: o método que grava a mensagem de log.</span><span class="sxs-lookup"><span data-stu-id="22282-205">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="22282-206">Trata-se de um design que é muito flexível quando novos recursos são adicionados.</span><span class="sxs-lookup"><span data-stu-id="22282-206">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="22282-207">O contrato necessário para qualquer gravador é implementar um método.</span><span class="sxs-lookup"><span data-stu-id="22282-207">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="22282-208">Esse método pode ser estático ou de instância.</span><span class="sxs-lookup"><span data-stu-id="22282-208">That method could be a static or instance method.</span></span> <span data-ttu-id="22282-209">Ele pode ser ter acesso público, privado ou qualquer outro acesso válido.</span><span class="sxs-lookup"><span data-stu-id="22282-209">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="22282-210">A classe de agente pode fazer vários aprimoramentos ou alterações sem introduzir alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="22282-210">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="22282-211">Assim como qualquer classe, você não pode modificar a API pública sem o risco de fazer alterações significativas.</span><span class="sxs-lookup"><span data-stu-id="22282-211">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="22282-212">Mas, como o acoplamento entre o agente e qualquer mecanismo de saída ocorre somente por meio do delegado, nenhum outro tipo (como interfaces ou classes base) é envolvido.</span><span class="sxs-lookup"><span data-stu-id="22282-212">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="22282-213">O acoplamento é o menor possível.</span><span class="sxs-lookup"><span data-stu-id="22282-213">The coupling is as small as possible.</span></span>

[<span data-ttu-id="22282-214">Avançar</span><span class="sxs-lookup"><span data-stu-id="22282-214">Next</span></span>](events-overview.md)

