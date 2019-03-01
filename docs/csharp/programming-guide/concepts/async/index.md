---
title: 'Programação assíncrona com async e await (C#)'
ms.date: 05/22/2017
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
---
# <a name="asynchronous-programming-with-async-and-await-c"></a>Programação assíncrona com async e await (C#)
É possível evitar gargalos de desempenho e aprimorar a resposta geral do seu aplicativo usando a programação assíncrona. No entanto, as técnicas tradicionais para escrever aplicativos assíncronos podem ser complicadas, dificultando sua escrita, depuração e manutenção.  
  
O [C# 5](../../../whats-new/csharp-version-history.md#c-version-50) apresentou uma programação assíncrona de abordagem simplificada que aproveita o suporte assíncrono no .NET Framework 4.5 e superior, no .NET Core e no Windows Runtime. O compilador faz o trabalho difícil que o desenvolvedor costumava fazer, e seu aplicativo mantém a estrutura lógica que se assemelha ao código síncrono. Como resultado, você obtém todas as vantagens da programação assíncrona com uma fração do esforço.  
  
Este tópico oferece uma visão geral de quando e como usar a programação assíncrona e inclui links para tópicos de suporte que contêm detalhes e exemplos.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> A assincronia melhora a capacidade de resposta  
 A assincronia é essencial para atividades que são potencialmente de bloqueio, como o acesso via Web. O acesso a um recurso da Web às vezes é lento ou atrasado. Se tal atividade for bloqueada em um processo síncrono, todo o aplicativo deverá esperar. Em um processo assíncrono, o aplicativo poderá prosseguir com outro trabalho que não dependa do recurso da Web até a tarefa potencialmente causadora do bloqueio terminar.  
  
 A tabela a seguir mostra a áreas típicas onde a programação assíncrona melhora a resposta. As APIs listadas do .NET e do Windows Runtime contêm métodos que dão suporte à programação assíncrona.  
  
| Área do aplicativo    | Tipos .NET com métodos assíncronos     | Tipos Windows Runtime com métodos assíncronos  |
|---------------------|-----------------------------------|-------------------------------------------|
|Acesso à Web|<xref:System.Net.Http.HttpClient>|<xref:Windows.Web.Syndication.SyndicationClient>|
|Trabalhando com arquivos|<xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|<xref:Windows.Storage.StorageFile>|  
|Trabalhando com imagens||<xref:Windows.Media.Capture.MediaCapture>, <xref:Windows.Graphics.Imaging.BitmapEncoder>, <xref:Windows.Graphics.Imaging.BitmapDecoder>|  
|Programação WCF|[Operações síncronas e assíncronas](../../../../framework/wcf/synchronous-and-asynchronous-operations.md)||  
  
A assincronia é especialmente importante para aplicativos que acessam o thread de interface de usuário porque todas as atividades relacionadas à interface do usuário normalmente compartilham um único thread. Se um processo for bloqueado em um aplicativo síncrono, todos serão bloqueados. Seu aplicativo para de responder, o que poderia levar você a concluir que ele falhou quando, na verdade, está apenas aguardando.  
  
 Quando você usa métodos assíncronos, o aplicativo continua a responder à interface do usuário. Você poderá redimensionar ou minimizar uma janela, por exemplo, ou fechar o aplicativo se você não desejar aguardar sua conclusão.  
  
 A abordagem baseada em assincronia adiciona o equivalente de uma transmissão automática à lista de opções disponíveis para escolha ao criar operações assíncronas. Ou seja, você obtém todos os benefícios da programação assíncrona tradicional, mas com muito menos esforço do desenvolvedor.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Os métodos assíncronos são mais fáceis de escrever  
 As palavras-chave [async](../../../../csharp/language-reference/keywords/async.md) e [await](../../../../csharp/language-reference/keywords/await.md) em C# são a parte central da programação assíncrona. Ao usar essas duas palavras-chave, você poderá usar recursos do .NET Framework, do .NET Core ou do Windows Runtime para criar um método assíncrono quase que tão facilmente quanto criar um método síncrono. Os métodos assíncronos que você define usando a palavra-chave `async` são chamados de *métodos assíncronos*.  
  
 O exemplo a seguir mostra um método assíncrono. Quase tudo no código deve ser completamente familiar para você. Os comentários chamam os recursos que você deve adicionar para criar a assincronia.  
  
 O arquivo de exemplo completo do WPF (Windows Presentation Foundation) pode ser encontrado no final deste tópico. Você também pode baixar o exemplo de [Exemplo de assincronia: exemplo de “Programação assíncrona com Async e Await”](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    using (HttpClient client = new HttpClient())  
    {  
        // GetStringAsync returns a Task<string>. That means that when you await the  
        // task you'll get a string (urlContents).  
        Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");  
  
        // You can do work here that doesn't rely on the string from GetStringAsync.  
        DoIndependentWork();  
  
        // The await operator suspends AccessTheWebAsync.  
        //  - AccessTheWebAsync can't continue until getStringTask is complete.  
        //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
        //  - Control resumes here when getStringTask is complete.   
        //  - The await operator then retrieves the string result from getStringTask.  
        string urlContents = await getStringTask;  
  
        // The return statement specifies an integer result.  
        // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
        return urlContents.Length;  
    }  
}  
```  
  
 Se `AccessTheWebAsync` não tiver nenhum trabalho que possa fazer entre chamar `GetStringAsync` e aguardar a conclusão, você poderá simplificar o código ao chamar e esperar na instrução única a seguir.  
  
```csharp  
string urlContents = await client.GetStringAsync("https://docs.microsoft.com");  
```  
 
As características a seguir resumem o que transforma o exemplo anterior em um método assíncrono.  
  
-   A assinatura do método inclui um modificador `async`.  
  
-   O nome de um método assíncrono, por convenção, termina com um sufixo "Async".  
  
-   O tipo de retorno é um dos seguintes tipos:  
  
    -   <xref:System.Threading.Tasks.Task%601> se o método possui uma instrução de retorno em que o operando tem o tipo `TResult`.  
  
    -   <xref:System.Threading.Tasks.Task> se o método não possui instrução de retorno alguma ou se ele possui uma instrução de retorno sem operando.  
  
    -   `void` se você estiver escrevendo um manipulador de eventos assíncronos.  

    -   Qualquer outro tipo que tenha um método `GetAwaiter` (começando com o C# 7.0).
  
     Confira mais informações na seção [Tipos e parâmetros de retorno](#BKMK_ReturnTypesandParameters).  
  
-   O método geralmente inclui pelo menos uma expressão await, a qual marca um ponto onde o método não pode continuar até que a operação assíncrona aguardada seja concluída. Enquanto isso, o método é suspenso e o controle retorna para o chamador do método. A próxima seção deste tópico ilustra o que acontece no ponto de suspensão.  
  
 Em métodos assíncronos, você usa as palavras-chave e os tipos fornecidos para indicar o que deseja fazer, e o compilador faz o resto, inclusive acompanhar o que deve acontecer quando o controle retorna a um ponto de espera em um método suspenso. Alguns processos de rotina, como loops e a manipulação de exceções, podem ser difíceis de manipular em um código assíncrono tradicional. Em um método assíncrono, você escreve esses elementos da mesma forma que faria em uma solução síncrona, e o problema é resolvido.  
  
 Para obter mais informações sobre assincronia nas versões anteriores do .NET Framework, consulte [Programação assíncrona do .NET Framework tradicional e TPL](../../../../standard/parallel-programming/tpl-and-traditional-async-programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> O que acontece em um método assíncrono  
 O mais importante que você deve compreender na programação assíncrona é a forma como o fluxo de controle avança de um método para outro. O diagrama a seguir pode ser usado para conduzi-lo pelo processo.  
  
 ![Rastreie um programa assíncrono](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Os números no diagrama correspondem às etapas a seguir.  
  
1.  Um manipulador de eventos chama e aguarda o método assíncrono `AccessTheWebAsync`.  
  
2.  `AccessTheWebAsync` cria uma instância de <xref:System.Net.Http.HttpClient> e chama o método assíncrono <xref:System.Net.Http.HttpClient.GetStringAsync%2A> para baixar o conteúdo de um site como uma cadeia de caracteres.  
  
3.  Algo acontece em `GetStringAsync` que suspende o andamento. Talvez ele deva aguardar o download de um site ou alguma outra atividade causadora de bloqueio. Para evitar o bloqueio de recursos, `GetStringAsync` transfere o controle para seu chamador, `AccessTheWebAsync`.  
  
     `GetStringAsync` retorna <xref:System.Threading.Tasks.Task%601>, em que `TResult` é uma cadeia de caracteres e `AccessTheWebAsync` atribui a tarefa à variável `getStringTask`. A tarefa representa o processo contínuo para a chamada a `GetStringAsync`, com um compromisso de produzir um valor de cadeia de caracteres real quando o trabalho estiver concluído.  
  
4.  Como o `getStringTask` ainda não foi esperado, `AccessTheWebAsync` pode continuar com outro trabalho que não depende do resultado final de `GetStringAsync`. O trabalho é representado por uma chamada ao método síncrono `DoIndependentWork`.  
  
5.  `DoIndependentWork` é um método síncrono que faz seu trabalho e retorna ao seu chamador.  
  
6.  `AccessTheWebAsync` está sem trabalho que ele possa executar sem um resultado de `getStringTask`. Em seguida, `AccessTheWebAsync` deseja calcular e retornar o comprimento da cadeia de caracteres baixada, mas o método não poderá calcular o valor enquanto o método tiver a cadeia de caracteres.  
  
     Portanto, `AccessTheWebAsync` usa um operador await para suspender seu andamento e para transferir o controle para o método que chamou `AccessTheWebAsync`. `AccessTheWebAsync` retorna um `Task<int>` ao chamador. A tarefa representa uma promessa de produzir um resultado inteiro que é o comprimento da cadeia de caracteres baixada.  
  
    > [!NOTE]
    >  Se `GetStringAsync` (e portanto `getStringTask`) for concluído antes que `AccessTheWebAsync` o espere, o controle permanecerá em `AccessTheWebAsync`. A despesa de suspender e depois retornar para `AccessTheWebAsync` seria desperdiçada caso o processo assíncrono chamado (`getStringTask`) já tivesse sido concluído e `AccessTheWebSync` não tivesse que aguardar o resultado final.  
  
     Dentro do chamador (manipulador de eventos neste exemplo), o processamento do padrão continua. O chamador pode fazer outro trabalho que não dependa do resultado de `AccessTheWebAsync` antes de aguardar o resultado, ou o chamador pode aguardar imediatamente.   O manipulador de eventos está aguardando `AccessTheWebAsync` e `AccessTheWebAsync` está aguardando `GetStringAsync`.  
  
7.  `GetStringAsync` completa e produz um resultado de cadeia de caracteres. O resultado da cadeia de caracteres não é retornado pela chamada para `GetStringAsync` da maneira que você poderia esperar. (Lembre-se de que o método já retornou uma tarefa na etapa 3.) Em vez disso, o resultado da cadeia de caracteres é armazenado na tarefa que representa a conclusão do método, `getStringTask`. O operador await recupera o resultado de `getStringTask`. A instrução de atribuição atribui o resultado retornado a `urlContents`.  
  
8.  Quando `AccessTheWebAsync` tem o resultado da cadeia de caracteres, o método pode calcular o comprimento da cadeia de caracteres. Em seguida, o trabalho de `AccessTheWebAsync` também é concluído e o manipulador de eventos de espera poderá retomar. No exemplo completo no final do tópico, é possível confirmar que o manipulador de eventos recuperou e imprimiu o valor do comprimento do resultado.    
Se você não tiver experiência em programação assíncrona, considere por um minuto a diferença entre o comportamento síncrono e o assíncrono. Um método síncrono retorna quando seu trabalho é concluído (etapa 5), mas um método assíncrono retorna um valor de tarefa quando seu trabalho está suspenso (etapas 3 e 6). Quando o método assíncrono eventualmente concluir seu trabalho, a tarefa será marcada como concluída e o resultado, se houver, será armazenado na tarefa.  
  
Para obter mais informações sobre o fluxo de controle, consulte [Fluxo de controle em programas assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Métodos de assíncronos da API  
 Você pode estar curioso para saber onde encontrar métodos como `GetStringAsync` que oferecem suporte à programação assíncrona. O .NET Framework 4.5 ou superior e o .NET Core contêm muitos membros que funcionam com `async` e com `await`. É possível reconhecê-los pelo sufixo “Async” que é acrescentado ao nome do membro e pelo tipo de retorno de <xref:System.Threading.Tasks.Task> ou de <xref:System.Threading.Tasks.Task%601>. Por exemplo, a classe `System.IO.Stream` contém métodos como <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A> e <xref:System.IO.Stream.WriteAsync%2A>, juntamente com os métodos síncronos <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A> e <xref:System.IO.Stream.Write%2A>.  
  
 O Windows Runtime também contém vários métodos que você pode usar com `async` e `await` em aplicativos do Windows. Confira mais informações em [Programação assíncrona e thread](/windows/uwp/threading-async/) para o desenvolvimento de UWP e em [Programação assíncrona (aplicativos da Windows Store)](https://docs.microsoft.com/previous-versions/windows/apps/hh464924(v=win.10)) além do [Início Rápido: chamada de APIs assíncronas em C# ou Visual Basic](https://docs.microsoft.com/previous-versions/windows/apps/hh452713(v=win.10)) se você usar versões anteriores do Windows Runtime.  
  
##  <a name="BKMK_Threads"></a> Threads  
Os métodos assíncronos destinam-se a ser operações não causadoras de bloqueios. Uma expressão `await` em um método assíncrono não bloqueia o thread atual enquanto a tarefa aguardada está em execução. Em vez disso, a expressão anterior assina o restante do método como uma continuação e retorna o controle para o chamador do método assíncrono.  
  
As palavras-chave `async` e `await` não fazem com que threads adicionais sejam criados. Os métodos assíncronos não exigem multithreading, pois um método assíncrono não executa em seu próprio thread. O método é executado no contexto de sincronização atual e usa tempo no thread somente quando o método está ativo. É possível usar <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType> para mover o trabalho de CPU associado a um thread em segundo plano, mas um thread em segundo plano não ajuda com um processo que está apenas aguardando que os resultados tornem-se disponíveis.  
  
A abordagem baseada em async para a programação assíncrona é preferível às abordagens existentes em quase todos os casos. Essa abordagem é especialmente mais eficiente do que a classe <xref:System.ComponentModel.BackgroundWorker> para operações de entrada e saída, porque o código é mais simples e você não precisa se proteger contra condições de corrida. Em combinação com o método <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=nameWithType>, a programação assíncrona é melhor que <xref:System.ComponentModel.BackgroundWorker> para operações associadas à CPU, porque a programação assíncrona separa os detalhes de coordenação da execução do código do trabalho que `Task.Run` transfere ao pool de threads.  
  
##  <a name="BKMK_AsyncandAwait"></a> async e await  
 Se você especificar que um método é assíncrono usando um modificador [async](../../../../csharp/language-reference/keywords/async.md), você habilitará os dois recursos a seguir.  
  
-   O método assíncrono marcado pode usar [await](../../../../csharp/language-reference/keywords/await.md) para designar pontos de suspensão. O operador `await` informa ao compilador que o método assíncrono não poderá continuar além daquele ponto até que o processo assíncrono aguardado seja concluído. Enquanto isso, o controle retorna para o chamador do método assíncrono.  
  
     A suspensão de um método assíncrono em uma expressão `await` não constitui uma saída de método e os blocos de `finally` não são executados.  
  
-   O método assíncrono marcado pode ele próprio ser aguardado por métodos que o chamam.  
  
Um método assíncrono normalmente contém uma ou mais ocorrências de um operador `await`, mas a ausência de expressões `await` não causa um erro do compilador. Se um método assíncrono não usa um operador `await` para marcar um ponto de suspensão, o método é executado da mesma forma que o método síncrono, independentemente do modificador `async`. O compilador emite um aviso para esses métodos.  
  
 `async` e `await` são palavras-chave contextuais. Para obter mais informações e exemplos, consulte os seguintes tópicos:  
  
-   [async](../../../../csharp/language-reference/keywords/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Tipos e parâmetros de retorno  
Um método assíncrono normalmente retorna <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Dentro de um método assíncrono, um operador `await` é aplicado a uma tarefa que é retornada de uma chamada para outro método assíncrono.  
  
Você especificará <xref:System.Threading.Tasks.Task%601> como o tipo de retorno se o método contiver uma instrução [return](../../../../csharp/language-reference/keywords/return.md) que especifica um operando do tipo `TResult`. 
  
Você usará <xref:System.Threading.Tasks.Task> como o tipo de retorno se o método não tiver nenhuma instrução return ou se tiver uma instrução return que não retorna um operando.  

Começando com C# 7.0, também será possível especificar qualquer outro tipo de retorno, desde que o tipo inclua um método `GetAwaiter`. <xref:System.Threading.Tasks.ValueTask%601> é um exemplo de tal tipo. Ele está disponível no pacote NuGet [System.Threading.Tasks.Extension](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/).
  
 O exemplo a seguir mostra como você declara e chama um método que retorna um <xref:System.Threading.Tasks.Task%601> ou <xref:System.Threading.Tasks.Task>.  
  
```csharp  
// Signature specifies Task<TResult>  
async Task<int> GetTaskOfTResultAsync()  
{  
    int hours = 0;  
    await Task.Delay(0);  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to GetTaskOfTResultAsync  
Task<int> returnedTaskTResult = GetTaskOfTResultAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await GetTaskOfTResultAsync();  
  
// Signature specifies Task  
async Task GetTaskAsync()  
{  
    await Task.Delay(0);  
    // The method has no return statement.    
}  
  
// Calls to GetTaskAsync  
Task returnedTask = GetTaskAsync();  
await returnedTask;  
// or, in a single statement  
await GetTaskAsync();  
```  
  
Cada tarefa retornada representa um trabalho em andamento. Uma tarefa encapsula informações sobre o estado do processo assíncrono e, consequentemente, o resultado final do processo ou a exceção que o processo apresenta quando não é bem-sucedido.  
  
Um método assíncrono também pode ter um tipo de retorno `void`. Esse tipo de retorno é usado principalmente para definir manipuladores de eventos, onde o tipo de retorno `void` é necessário. Os manipuladores de eventos assíncronos geralmente servem como o ponto de partida para programas assíncronos.  
  
Um método assíncrono que tem um tipo de retorno `void` não pode ser esperado, e o chamador de um método que retorna nulo não pode capturar nenhuma exceção acionada pelo método.  
  
O método não pode declarar nenhum parâmetro [in](../../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../../csharp/language-reference/keywords/ref.md) ou [out](../../../../csharp/language-reference/keywords/out-parameter-modifier.md), mas pode chamar métodos com tais parâmetros. Da mesma forma, um método assíncrono não pode retornar um valor por referência, embora possa chamar métodos com valores retornados ref. 
  
Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Para obter mais informações sobre como capturar exceções nos métodos assíncronos, consulte [try-catch](../../../../csharp/language-reference/keywords/try-catch.md). 
  
As APIs assíncronas na programação do Windows Runtime têm um dos seguintes tipos de retorno, que são semelhantes às tarefas:  
  
-   <xref:Windows.Foundation.IAsyncOperation%601>, que corresponde a <xref:System.Threading.Tasks.Task%601>  
  
-   <xref:Windows.Foundation.IAsyncAction>, que corresponde a <xref:System.Threading.Tasks.Task>  
  
-   <xref:Windows.Foundation.IAsyncActionWithProgress%601>  
  
-   <xref:Windows.Foundation.IAsyncOperationWithProgress%602>  
   
  
##  <a name="BKMK_NamingConvention"></a> Convenção de nomenclatura  
Por convenção, os métodos que geralmente retornam tipos awaitable (por exemplo, `Task`, `Task<T>`, `ValueTask` e `ValueTask<T>`) devem ter nomes que terminam com "Async". Os métodos que iniciam uma operação assíncrona, mas não retornam um tipo awaitable não devem ter nomes que terminam com "Async", mas podem começar com "Begin", "Start" ou algum outro verbo que indique que esse método não retorna nem gera o resultado da operação.
  
 É possível ignorar a convenção quando um evento, uma classe base ou um contrato de interface sugere um nome diferente. Por exemplo, você não deve renomear manipuladores de eventos comuns, como `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Tópicos relacionados e exemplos (Visual Studio)  
  
|Título|Descrição|Amostra|  
|-----------|-----------------|------------|  
|[Passo a passo: acesso à Web com o uso de Async e Await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Mostra como converter uma solução síncrona do WPF em uma solução assíncrona do WPF. O aplicativo baixa uma série de sites.|[Exemplo de Async: acesso do passo a passo da Web](https://code.msdn.microsoft.com/Async-Sample-Accessing-the-9c10497f)|  
|[Como: estender o passo a passo Async usando Task.WhenAll (C#)](../../../../csharp/programming-guide/concepts/async/how-to-extend-the-async-walkthrough-by-using-task-whenall.md)|Adiciona <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> à explicação passo a passo anterior. O uso de `WhenAll` inicia todos os downloads ao mesmo tempo.||  
|[Como: fazer várias solicitações da Web em paralelo, usando Async e Await (C#)](../../../../csharp/programming-guide/concepts/async/how-to-make-multiple-web-requests-in-parallel-by-using-async-and-await.md)|Demonstra como iniciar várias tarefas ao mesmo tempo.|[Exemplo de Async: fazer várias solicitações da Web em paralelo](https://code.msdn.microsoft.com/Async-Make-Multiple-Web-49adb82e)|  
|[Tipos de retorno assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Ilustra os tipos que os métodos assíncronos podem retornar e explica quando cada tipo é apropriado.||  
|[Fluxo de controle em programas assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)|Rastreia em detalhes o fluxo de controle por meio de uma sucessão de expressões de espera em um programa assíncrono.|[Exemplo de Async: fluxo de controle em programas assíncronos](https://code.msdn.microsoft.com/Async-Sample-Control-Flow-5c804fc0)|  
|[Ajuste fino de seu aplicativo assíncrono (C#)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Mostra como adicionar a seguinte funcionalidade à sua solução assíncrona:<br /><br /> -   [Cancelar uma tarefa assíncrona ou uma lista de tarefas (C#)](../../../../csharp/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Cancelar tarefas assíncronas após um Período (C#)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Cancelar as demais tarefas assíncronas depois que uma delas estiver concluída (C#)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Iniciar várias tarefas assíncronas e processá-las na conclusão (C#)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Exemplo de Async: ajuste do seu aplicativo](https://code.msdn.microsoft.com/Async-Fine-Tuning-Your-a676abea)|  
|[Tratando a reentrada em aplicativos assíncronos (C#)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Mostra como manipular casos em que uma operação assíncrona ativa é reiniciada enquanto está em execução.||  
|[WhenAny: ponte entre o .NET Framework e o Windows Runtime](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2013/jj635140(v=vs.120))|Mostra como criar uma ponte entre tipos Task no .NET Framework e IAsyncOperations no [!INCLUDE[wrt](~/includes/wrt-md.md)], para que você possa usar o <xref:System.Threading.Tasks.Task.WhenAny%2A> com um método [!INCLUDE[wrt](~/includes/wrt-md.md)].|[Exemplo de Async: ponte entre o .NET e o Windows Runtime (AsTask e WhenAny)](https://code.msdn.microsoft.com/Async-Sample-Bridging-d6a2f739)|  
|Cancelamento de Async: ponte entre o .NET Framework e o Windows Runtime|Mostra como criar uma ponte entre tipos Task no .NET Framework e IAsyncOperations no [!INCLUDE[wrt](~/includes/wrt-md.md)], para que você possa usar o <xref:System.Threading.CancellationTokenSource> com um método [!INCLUDE[wrt](~/includes/wrt-md.md)].|[Exemplo de Async: ponte entre o .NET e o Windows Runtime (AsTask e Cancellation)](https://code.msdn.microsoft.com/Async-Sample-Bridging-9479eca3)|  
|[Usando o Async para acessar arquivos (C#)](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Lista e demonstra as vantagens de usar async e await para acessar arquivos.||  
|[TAP (Padrão Assíncrono Baseado em Tarefa)](../../../../standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)|Descreve um novo padrão de assincronia no .NET Framework. O padrão baseia-se nos tipos <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601>.||  
|[Vídeos sobre assincronia no Channel 9](https://channel9.msdn.com/search?term=async%20&type=All#pubDate=year&ch9Search&lang-en=en)|Fornece links para uma variedade de vídeos sobre programação assíncrona.||  
  
##  <a name="BKMK_CompleteExample"></a> Exemplo completo  
 O código a seguir é o arquivo MainWindow.xaml.cs do aplicativo WPF (Windows Presentation Foundation) discutido neste tópico. Baixe o exemplo de [Exemplo de Async: exemplo de “Programação assíncrona com Async e Await”](https://code.msdn.microsoft.com/Async-Sample-Example-from-9b9f505c).  
  
```csharp  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Text;  
using System.Threading.Tasks;  
using System.Windows;  
using System.Windows.Controls;  
using System.Windows.Data;  
using System.Windows.Documents;  
using System.Windows.Input;  
using System.Windows.Media;  
using System.Windows.Media.Imaging;  
using System.Windows.Navigation;  
using System.Windows.Shapes;  
  
// Add a using directive and a reference for System.Net.Http;  
using System.Net.Http;  
  
namespace AsyncFirstExample  
{  
    public partial class MainWindow : Window  
    {  
        // Mark the event handler with async so you can use await in it.  
        private async void StartButton_Click(object sender, RoutedEventArgs e)  
        {  
            // Call and await separately.  
            //Task<int> getLengthTask = AccessTheWebAsync();  
            //// You can do independent work here.  
            //int contentLength = await getLengthTask;  
  
            int contentLength = await AccessTheWebAsync();  
  
            resultsTextBox.Text +=
                $"\r\nLength of the downloaded string: {contentLength}.\r\n";
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            using (HttpClient client = new HttpClient())  
            {  
                    // GetStringAsync returns a Task<string>. That means that when you await the  
                    // task you'll get a string (urlContents).  
                    Task<string> getStringTask = client.GetStringAsync("https://docs.microsoft.com");  
  
                    // You can do work here that doesn't rely on the string from GetStringAsync.  
                    DoIndependentWork();  
  
                    // The await operator suspends AccessTheWebAsync.  
                    //  - AccessTheWebAsync can't continue until getStringTask is complete.  
                    //  - Meanwhile, control returns to the caller of AccessTheWebAsync.  
                    //  - Control resumes here when getStringTask is complete.   
                    //  - The await operator then retrieves the string result from getStringTask.  
                    string urlContents = await getStringTask;  
  
                    // The return statement specifies an integer result.  
                    // Any methods that are awaiting AccessTheWebAsync retrieve the length value.  
                    return urlContents.Length;  
            }  
        }  
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 25035.  
```  
  
## <a name="see-also"></a>Consulte também

- [async](../../../../csharp/language-reference/keywords/async.md)
- [await](../../../../csharp/language-reference/keywords/await.md)
- [Programação assíncrona](../../../../csharp/async.md)
- [Visão geral da assincronia](../../../../standard/async.md)
