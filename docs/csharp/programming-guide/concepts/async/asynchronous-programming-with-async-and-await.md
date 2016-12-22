---
title: "Programa&#231;&#227;o ass&#237;ncrona com async e await (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: 9bcf896a-5826-4189-8c1a-3e35fa08243a
caps.latest.revision: 5
caps.handback.revision: 4
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Programa&#231;&#227;o ass&#237;ncrona com async e await (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Você pode evitar gargalos de desempenho e melhorar a resposta geral do seu aplicativo usando a programação assíncrona. No entanto, técnicas tradicionais para escrever aplicativos assíncronos podem ser complicados, tornando difícil escrever, depurar e mantêm.  
  
 Visual Studio 2012 introduziu uma abordagem simplificada à programação assíncrona que aproveita o suporte assíncrono no .NET Framework 4.5 e superior, bem como o tempo de execução do Windows. O compilador faz o trabalho difícil que o desenvolvedor costumava fazer, e seu aplicativo mantém uma estrutura lógica que se parece com o código síncrono. Como resultado, você obtém todas as vantagens da programação assíncrona com uma fração do esforço.  
  
 Este tópico fornece uma visão geral de quando e como usar a programação assíncrona e inclui links para tópicos que contêm detalhes e exemplos de suporte.  
  
##  <a name="BKMK_WhentoUseAsynchrony"></a> A assincronia melhora a capacidade de resposta  
 A assincronia é essencial para atividades potencialmente bloqueio, como quando o aplicativo acessa a web. Acesso a um recurso da web às vezes é lento ou atrasado. Se tal atividade for bloqueada dentro de um processo síncrono, todo o aplicativo deve aguardar. Em um processo assíncrono, o aplicativo pode continuar com outro trabalho que não depende do recurso da web até que a tarefa potencialmente bloqueio termina.  
  
 A tabela a seguir mostra as áreas típicas onde a programação assíncrona melhora a capacidade de resposta. As APIs listadas do .NET Framework 4.5 e o tempo de execução do Windows contêm métodos que oferecem suporte a programação assíncrona.  
  
|Área do aplicativo|APIs de suporte que contêm métodos assíncronos|  
|------------------------|----------------------------------------------------|  
|Acesso via Web|<xref:System.Net.Http.HttpClient>, [SyndicationClient](http://go.microsoft.com/fwlink/p/?LinkId=259441)|  
|Trabalhando com arquivos|[StorageFile](http://go.microsoft.com/fwlink/p/?LinkId=248220), <xref:System.IO.StreamWriter>, <xref:System.IO.StreamReader>, <xref:System.Xml.XmlReader>|  
|Trabalhando com imagens|[MediaCapture](http://go.microsoft.com/fwlink/p/?LinkId=261839), [BitmapEncoder](http://go.microsoft.com/fwlink/p/?LinkId=261840), [BitmapDecoder](http://go.microsoft.com/fwlink/p/?LinkId=261841)|  
|Programação do WCF|[Operações síncronas e assíncronas](http://go.microsoft.com/fwlink/p/?LinkID=192382)|  
|||  
  
 A assincronia é especialmente útil para aplicativos que acessam o thread da interface do usuário porque todas as atividades relacionadas à interface do usuário normalmente compartilham um único thread. Se um processo for bloqueado em um aplicativo síncrono, todos serão bloqueados. Seu aplicativo para de responder, e você pode concluir que falhou em vez disso, está apenas aguardando.  
  
 Quando você usa métodos assíncronos, o aplicativo continua a responder à interface do usuário. Você pode redimensionar ou minimizar uma janela, por exemplo, ou você pode fechar o aplicativo se você não desejar aguardar sua conclusão.  
  
 A abordagem baseada em assincronia adiciona o equivalente de uma transmissão automática à lista de opções que você pode escolher ao criar operações assíncronas. Ou seja, você obtém todos os benefícios da programação assíncrona tradicional, mas com muito menos esforço do desenvolvedor.  
  
##  <a name="BKMK_HowtoWriteanAsyncMethod"></a> Os métodos assíncronos são mais fáceis de escrever  
 O [async](../../../../visual-basic/language-reference/modifiers/async.md) e [await](../../../../csharp/language-reference/keywords/await.md) palavras\-chave em c\# são o coração da programação assíncrona. Usando essas duas palavras\-chave, você pode usar os recursos do .NET Framework ou o tempo de execução do Windows para criar um método assíncrono quase tão fácil quanto criar um método síncrono. Métodos assíncronos que você define usando `async` e `await` são chamados de métodos assíncronos.  
  
 O exemplo a seguir mostra um método assíncrono. Quase tudo no código deve ser completamente familiar para você. Os comentários chamam os recursos que você adicionar para criar a assincronia.  
  
 Você pode encontrar um arquivo de exemplo do Windows Presentation Foundation \(WPF\) completo no final deste tópico, e você pode baixar o exemplo de [exemplo de assincronia: exemplo de "Programação assíncrona com Async e Await"](http://go.microsoft.com/fwlink/?LinkID=261549).  
  
```c#  
// Three things to note in the signature:  
//  - The method has an async modifier.   
//  - The return type is Task or Task<T>. (See "Return Types" section.)  
//    Here, it is Task<int> because the return statement returns an integer.  
//  - The method name ends in "Async."  
async Task<int> AccessTheWebAsync()  
{   
    // You need to add a reference to System.Net.Http to declare client.  
    HttpClient client = new HttpClient();  
  
    // GetStringAsync returns a Task<string>. That means that when you await the  
    // task you'll get a string (urlContents).  
    Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
```  
  
 Se `AccessTheWebAsync` não tem qualquer trabalho que ele possa fazer entre chamar `GetStringAsync` e aguardar a conclusão, você pode simplificar o seu código chamando e aguardando a seguinte instrução única.  
  
```c#  
string urlContents = await client.GetStringAsync();  
```  
  
 As características a seguir resumem o que torna o exemplo anterior, um método assíncrono.  
  
-   A assinatura do método inclui um `async` modificador.  
  
-   O nome de um método assíncrono, por convenção, termina com um sufixo "Async".  
  
-   O tipo de retorno é um dos seguintes tipos:  
  
    -   <xref:System.Threading.Tasks.Task%601> Se o método possui uma instrução de retorno que o operando tem o tipo TResult.  
  
    -   <xref:System.Threading.Tasks.Task> Se o método não tiver nenhuma instrução return ou uma instrução de retorno sem operando.  
  
    -   `Void` Se você estiver escrevendo um manipulador de eventos assíncronos.  
  
     Para obter mais informações, consulte "Tipos e parâmetros de retorno" posteriormente neste tópico.  
  
-   O método geralmente inclui pelo menos uma expressão await, que marca o ponto em que o método não pode continuar até que a operação assíncrona aguardada seja concluída. Enquanto isso, o método é suspenso, e o controle retorna para o chamador do método. A próxima seção deste tópico ilustra o que acontece no ponto de suspensão.  
  
 Em métodos assíncronos, use os tipos e palavras\-chave fornecidas para indicar o que você deseja fazer, e o compilador faz o resto, inclusive acompanhar o que deve acontecer quando o controle retorna para um ponto de espera em um método suspenso. Alguns processos de rotina, como loops e manipulação de exceção, podem ser difícil lidar com em código assíncrono tradicional. Um método assíncrono, você escreve esses elementos assim como faria em uma solução síncrona, e o problema é resolvido.  
  
 Para obter mais informações sobre assincronia nas versões anteriores do .NET Framework, consulte [TPL e programação assíncrona do .NET Framework](../Topic/TPL%20and%20Traditional%20.NET%20Framework%20Asynchronous%20Programming.md).  
  
##  <a name="BKMK_WhatHappensUnderstandinganAsyncMethod"></a> O que acontece em um método assíncrono  
 A coisa mais importante para compreender na programação assíncrona é como o fluxo de controle se move para cada método. O diagrama a seguir o orientarão durante o processo.  
  
 ![Rastrear um programa assíncrono](../../../../csharp/programming-guide/concepts/async/media/navigationtrace.png "NavigationTrace")  
  
 Os números no diagrama correspondem às etapas a seguir.  
  
1.  Um manipulador de eventos chama e aguarda o  `AccessTheWebAsync` método assíncrono.  
  
2.  `AccessTheWebAsync` cria um <xref:System.Net.Http.HttpClient> instância e chama o <xref:System.Net.Http.HttpClient.GetStringAsync%2A> método assíncrono para baixar o conteúdo de um site como uma cadeia de caracteres.  
  
3.  Algo acontece em `GetStringAsync` que suspende o andamento. Talvez ele deverá aguardar por um site para download ou alguma outra atividade de bloqueio. Para evitar o bloqueio de recursos, `GetStringAsync` transfere o controle para seu chamador, `AccessTheWebAsync`.  
  
     `GetStringAsync` Retorna um <xref:System.Threading.Tasks.Task%601> onde `TResult` é uma cadeia de caracteres e `AccessTheWebAsync` atribui a tarefa de `getStringTask` variável. A tarefa representa o processo contínuo para a chamada `GetStringAsync`, com um compromisso de produzir um valor de cadeia de caracteres real quando o trabalho for concluído.  
  
4.  Porque `getStringTask` ainda não foi esperado, `AccessTheWebAsync` pode continuar com outro trabalho que não dependa do resultado final de `GetStringAsync`. Trabalho é representado por uma chamada para o método síncrono `DoIndependentWork`.  
  
5.  `DoIndependentWork` é um método síncrono que faz seu trabalho e retorna ao chamador.  
  
6.  `AccessTheWebAsync` ficou sem trabalho que ele pode fazer sem um resultado de `getStringTask`.`AccessTheWebAsync` próxima deseja calcular e retornar o comprimento da cadeia de caracteres baixada, mas o método não pode calcular esse valor até que o método tenha a cadeia de caracteres.  
  
     Portanto, `AccessTheWebAsync` usa um operador await para suspender seu andamento e transferir o controle para o método chamado `AccessTheWebAsync`.`AccessTheWebAsync` Retorna um `Task<int>` ao chamador. A tarefa representa uma promessa de produzir um resultado de inteiro é o comprimento da cadeia de caracteres baixada.  
  
    > [!NOTE]
    >  Se `GetStringAsync` \(e, portanto, `getStringTask`\) é concluída antes de `AccessTheWebAsync` espere, o controle permanecerá em `AccessTheWebAsync`. A despesa de suspender e então retornar para `AccessTheWebAsync` seria desperdiçada caso o processo assíncrono chamado \(`getStringTask`\) já foi concluído e AccessTheWebSync não precisa esperar o resultado final.  
  
     Dentro do chamador \(o manipulador de eventos neste exemplo\), o padrão de processamento continua. O chamador pode fazer outro trabalho que não dependa do resultado de `AccessTheWebAsync` antes de aguardando o resultado, ou o chamador pode aguardar imediatamente.   O manipulador de eventos está aguardando `AccessTheWebAsync`, e `AccessTheWebAsync` está aguardando `GetStringAsync`.  
  
7.  `GetStringAsync` completa e produz um resultado de cadeia de caracteres. O resultado de cadeia de caracteres não é retornado pela chamada para `GetStringAsync` da maneira que você esperava. \(Lembre\-se de que o método já retornou uma tarefa na etapa 3.\) Em vez disso, o resultado de cadeia de caracteres é armazenado na tarefa que representa a conclusão do método, `getStringTask`. O operador await recupera o resultado de `getStringTask`. A instrução de atribuição atribui o resultado retornado para `urlContents`.  
  
8.  Quando `AccessTheWebAsync` tem o resultado da cadeia de caracteres, o método pode calcular o comprimento da cadeia de caracteres. Em seguida, o trabalho de `AccessTheWebAsync` também é concluído, e o manipulador de eventos de espera pode continuar. O exemplo completo no final do tópico, você pode confirmar que o manipulador de eventos recupera e imprime o valor do comprimento do resultado.  
  
 Se você for novo para programação assíncrona, reserve um minuto para considerar a diferença entre o comportamento síncrono e assíncrono. Um método síncrono retorna quando seu trabalho é concluído \(etapa 5\), mas um método assíncrono retorna um valor de tarefa quando seu trabalho está suspenso \(etapas 3 e 6\). Quando o método assíncrono eventualmente concluir seu trabalho, a tarefa é marcada como concluída e o resultado, se houver, é armazenado na tarefa.  
  
 Para obter mais informações sobre o fluxo de controle, consulte [Fluxo de controle em programas assíncronos \(c\#\)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md).  
  
##  <a name="BKMK_APIAsyncMethods"></a> Métodos assíncronos de API  
 Você deve estar se perguntando onde encontrar métodos como `GetStringAsync` que suporte a programação assíncrona. O .NET Framework 4.5 ou superior contém muitos membros que funcionam com `async` e `await`. Você pode reconhecer esses membros pelo sufixo "Async" que é anexado ao nome do membro e um tipo de retorno de <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>. Por exemplo, a `System.IO.Stream` classe contém métodos como <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.ReadAsync%2A>, e <xref:System.IO.Stream.WriteAsync%2A> juntamente com os métodos síncronos <xref:System.IO.Stream.CopyTo%2A>, <xref:System.IO.Stream.Read%2A>, e <xref:System.IO.Stream.Write%2A>.  
  
 O tempo de execução do Windows também contém vários métodos que você pode usar com `async` e `await` em aplicativos do Windows. Para obter mais informações e métodos de exemplo, consulte [início rápido: usando o operador de espera para programação assíncrona](http://go.microsoft.com/fwlink/?LinkId=248545), [\(aplicativos da Windows Store\) de programação assíncrona](http://go.microsoft.com/fwlink/?LinkId=259592), e [WhenAny: Bridging between the .NET Framework and the Windows Runtime \(C\#\)](../Topic/WhenAny:%20Bridging%20between%20the%20.NET%20Framework%20and%20the%20Windows%20Runtime%20\(C%23\).md).  
  
##  <a name="BKMK_Threads"></a> Threads  
 Os métodos assíncronos devem ser desbloqueado operações. Um `await` expressão em um método assíncrono não bloqueie o thread atual enquanto a tarefa aguardada está em execução. Em vez disso, a expressão anterior assina o restante do método como uma continuação e retorna o controle para o chamador do método assíncrono.  
  
 O `async` e `await` palavras\-chave não fazem com que os threads adicionais a serem criados. Métodos assíncronos não exigem multithreading porque um método assíncrono não é executado em seu próprio thread. O método é executado no contexto de sincronização atual e usa tempo no thread somente quando o método está ativo. Você pode usar <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=fullName> para mover trabalho vinculado à CPU um thread em segundo plano, mas um plano de fundo thread não ajuda com um processo que está apenas esperando resultados se torne disponível.  
  
 A abordagem baseada em async para programação assíncrona é preferível às abordagens existentes em quase todos os casos. Em particular, essa abordagem é melhor do que <xref:System.ComponentModel.BackgroundWorker> limite de e\/s operações porque o código é mais simples e você não precisa se proteger contra condições de corrida. Em combinação com <xref:System.Threading.Tasks.Task.Run%2A?displayProperty=fullName>, programação assíncrona é melhor do que <xref:System.ComponentModel.BackgroundWorker> para operações associadas à CPU porque a programação async separa os detalhes de coordenação da execução do código do trabalho `Task.Run` transfere ao threadpool.  
  
##  <a name="BKMK_AsyncandAwait"></a> Async e await  
 Se você especificar que um método é um método assíncrono usando um [async](../../../../visual-basic/language-reference/modifiers/async.md) modificador, habilite os recursos a seguir.  
  
-   O método assíncrono marcado pode usar [await](../../../../csharp/language-reference/keywords/await.md) para designar pontos de suspensão. O operador await informa ao compilador que o método assíncrono não pode continuar além daquele ponto até que o processo assíncrono aguardado seja concluído. Enquanto isso, o controle retorna para o chamador do método assíncrono.  
  
     A suspensão de um método assíncrono em um `await` expressão não constitui uma saída do método, e `finally` blocos não são executados.  
  
-   O método assíncrono marcado pode ele próprio ser aguardado por métodos que chamá\-lo.  
  
 Um método assíncrono normalmente contém uma ou mais ocorrências de um `await` operador, mas a ausência de `await` expressões não causa um erro do compilador. Se um método assíncrono não usa um `await` operador para marcar um ponto de suspensão, o método executa como um método síncrono, apesar do `async` modificador. O compilador emite um aviso para esses métodos.  
  
 `async` e `await` são palavras\-chave contextuais. Para obter mais informações e exemplos, consulte os tópicos a seguir:  
  
-   [async](../../../../visual-basic/language-reference/modifiers/async.md)  
  
-   [await](../../../../csharp/language-reference/keywords/await.md)  
  
##  <a name="BKMK_ReturnTypesandParameters"></a> Tipos de retorno e parâmetros  
 Na programação do .NET Framework, um método assíncrono normalmente retorna um <xref:System.Threading.Tasks.Task> ou um <xref:System.Threading.Tasks.Task%601>. Dentro de um método assíncrono, um `await` operador é aplicado a uma tarefa que é retornada de uma chamada para outro método assíncrono.  
  
 Especificar <xref:System.Threading.Tasks.Task%601> como o tipo de retorno se o método contém um [retornar](../../../../csharp/language-reference/keywords/return.md) instrução que especifica um operando do tipo `TResult`.  
  
 Você usa `Task` como o tipo de retorno se o método possua nenhuma instrução return ou tenha uma instrução return que não retorna um operando.  
  
 O exemplo a seguir mostra como declarar e chamar um método que retorna um <xref:System.Threading.Tasks.Task%601> ou um <xref:System.Threading.Tasks.Task>.  
  
```c#  
// Signature specifies Task<TResult>  
async Task<int> TaskOfTResult_MethodAsync()  
{  
    int hours;  
    // . . .  
    // Return statement specifies an integer result.  
    return hours;  
}  
  
// Calls to TaskOfTResult_MethodAsync  
Task<int> returnedTaskTResult = TaskOfTResult_MethodAsync();  
int intResult = await returnedTaskTResult;  
// or, in a single statement  
int intResult = await TaskOfTResult_MethodAsync();  
  
// Signature specifies Task  
async Task Task_MethodAsync()  
{  
    // . . .  
    // The method has no return statement.    
}  
  
// Calls to Task_MethodAsync  
Task returnedTask = Task_MethodAsync();  
await returnedTask;  
// or, in a single statement  
await Task_MethodAsync();  
  
```  
  
 Cada tarefa retornada representa o trabalho em andamento. Uma tarefa encapsula informações sobre o estado do processo assíncrono e, finalmente, o resultado final do processo ou a exceção de que o processo gera se ele não tiver êxito.  
  
 Um método assíncrono também pode ter um `void` tipo de retorno. Isso retornará o tipo é usado principalmente para definir manipuladores de eventos, onde um `void` tipo de retorno é necessário. Manipuladores de eventos assíncronos geralmente servem como ponto de partida para programas assíncronos.  
  
 Um método assíncrono que tem um `void` retornar o tipo não pode ser esperado, e o chamador de um método de retorno nulo não pode capturar todas as exceções que o método lança.  
  
 Não é possível declarar um método assíncrono [ref](../../../../csharp/language-reference/keywords/ref.md) ou [out](../../../../csharp/language-reference/keywords/out.md) parâmetros, mas o método pode chamar métodos que possuem esses parâmetros.  
  
 Para obter mais informações e exemplos, consulte [Tipos de retorno assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/async-return-types.md). Para obter mais informações sobre como capturar exceções em métodos assíncronos, consulte [try\-catch](../../../../csharp/language-reference/keywords/try-catch.md).  
  
 APIs assíncronas na programação de tempo de execução do Windows tem um dos seguintes tipos de retorno, que são semelhantes às tarefas:  
  
-   [IAsyncOperation](http://go.microsoft.com/fwlink/p/?LinkId=261896), que corresponde ao <xref:System.Threading.Tasks.Task%601>  
  
-   [IAsyncAction](http://go.microsoft.com/fwlink/p/?LinkId=261897), que corresponde ao <xref:System.Threading.Tasks.Task>  
  
-   [IAsyncActionWithProgress](http://go.microsoft.com/fwlink/p/?LinkId=261898)  
  
-   [IAsyncOperationWithProgress](http://go.microsoft.com/fwlink/p/?LinkID=259454)  
  
 Para obter mais informações e um exemplo, consulte [início rápido: usando o operador de espera para programação assíncrona](http://go.microsoft.com/fwlink/p/?LinkId=248545).  
  
##  <a name="BKMK_NamingConvention"></a> Convenção de nomenclatura  
 Por convenção, acrescentar "Async" aos nomes dos métodos que possuem um `async` modificador.  
  
 Você pode ignorar a convenção em que um evento, uma classe base ou um contrato de interface sugere um nome diferente. Por exemplo, você não deve renomear manipuladores de eventos comuns, como `Button1_Click`.  
  
##  <a name="BKMK_RelatedTopics"></a> Tópicos relacionados e exemplos \(Visual Studio\)  
  
|Título|Descrição|Exemplo|  
|------------|---------------|-------------|  
|[Passo a passo: Acessando a Web usando o async e await \(c\#\)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)|Mostra como converter uma solução síncrona do WPF para uma solução assíncrona do WPF. O aplicativo baixa uma série de sites.|[Exemplo de assincronia: Acessando o passo a passo da Web](http://go.microsoft.com/fwlink/p/?LinkID=255191&clcid=0x409)|  
|[Como: estender o async passo a passo pelo usando WhenAll \(c\#\)](../Topic/How%20to:%20Extend%20the%20async%20Walkthrough%20by%20Using%20Task.WhenAll%20\(C%23\).md)|Adiciona <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=fullName> para o passo a passo anterior. O uso de `WhenAll` inicia todos os downloads ao mesmo tempo.||  
|[Como: fazer várias solicitações da Web em paralelo usando async e await \(c\#\)](../Topic/How%20to:%20Make%20Multiple%20Web%20Requests%20in%20Parallel%20by%20Using%20async%20and%20await%20\(C%23\).md)|Demonstra como iniciar várias tarefas ao mesmo tempo.|[Exemplo de assincronia: Fazer várias solicitações da Web em paralelo](http://go.microsoft.com/fwlink/p/?LinkID=254906&clcid=0x409)|  
|[Tipos de retorno assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/async-return-types.md)|Ilustra os tipos de métodos assíncronos podem retornar e explica quando cada tipo é apropriado.||  
|[Fluxo de controle em programas assíncronos \(c\#\)](../../../../visual-basic/programming-guide/concepts/async/control-flow-in-async-programs.md)|Rastreia em detalhes o fluxo de controle por meio de uma sucessão de expressões em um programa assíncrono await.|[Exemplo de assincronia: Fluxo de controle em programas assíncronos](http://go.microsoft.com/fwlink/p/?LinkID=255285&clcid=0x409)|  
|[Ajustando seu aplicativo Async \(c\#\)](../../../../csharp/programming-guide/concepts/async/fine-tuning-your-async-application.md)|Mostra como adicionar a seguinte funcionalidade à sua solução assíncrona:<br /><br /> -   [Cancelar uma tarefa assíncrona ou uma lista de tarefas \(c\#\)](../../../../visual-basic/programming-guide/concepts/async/cancel-an-async-task-or-a-list-of-tasks.md)<br />-   [Cancelar tarefas assíncronas após um período de tempo \(c\#\)](../../../../csharp/programming-guide/concepts/async/cancel-async-tasks-after-a-period-of-time.md)<br />-   [Cancelar as demais tarefas assíncronas depois que uma for concluída \(c\#\)](../../../../csharp/programming-guide/concepts/async/cancel-remaining-async-tasks-after-one-is-complete.md)<br />-   [Iniciar várias tarefas assíncronas e processá\-las na conclusão \(c\#\)](../../../../csharp/programming-guide/concepts/async/start-multiple-async-tasks-and-process-them-as-they-complete.md)|[Exemplo de assincronia: Ajustando seu aplicativo](http://go.microsoft.com/fwlink/p/?LinkID=255046&clcid=0x409)|  
|[Tratando a reentrada em aplicativos assíncronos \(c\#\)](../../../../csharp/programming-guide/concepts/async/handling-reentrancy-in-async-apps.md)|Mostra como manipular casos em que uma operação assíncrona ativa é reiniciada enquanto ele é executado.||  
|[WhenAny: Bridging between the .NET Framework and the Windows Runtime \(C\#\)](../Topic/WhenAny:%20Bridging%20between%20the%20.NET%20Framework%20and%20the%20Windows%20Runtime%20\(C%23\).md)|Mostra como criar uma ponte entre tipos de tarefa no .NET Framework e IAsyncOperations no [!INCLUDE[wrt](../../../../csharp/includes/wrt_md.md)] para que você possa usar <xref:System.Threading.Tasks.Task.WhenAny%2A> com um [!INCLUDE[wrt](../../../../csharp/includes/wrt_md.md)] método.|[Exemplo de assincronia: Ponte entre o .NET e o tempo de execução do Windows \(AsTask e WhenAny\)](http://go.microsoft.com/fwlink/p/?LinkID=260638)|  
|[Async Cancellation: Bridging between the .NET Framework and the Windows Runtime \(C\#\)](../Topic/Async%20Cancellation:%20Bridging%20between%20the%20.NET%20Framework%20and%20the%20Windows%20Runtime%20\(C%23\).md)|Mostra como criar uma ponte entre tipos de tarefa no .NET Framework e IAsyncOperations no [!INCLUDE[wrt](../../../../csharp/includes/wrt_md.md)] para que você possa usar <xref:System.Threading.CancellationTokenSource> com um [!INCLUDE[wrt](../../../../csharp/includes/wrt_md.md)] método.|[Exemplo de assincronia: Ponte entre o .NET e o tempo de execução do Windows \(AsTask & Cancellation\)](http://go.microsoft.com/fwlink/p/?LinkId=263004)|  
|[Usando o Async para acesso a arquivos \(c\#\)](../../../../csharp/programming-guide/concepts/async/using-async-for-file-access.md)|Lista e demonstra os benefícios do uso de async e await para acessar os arquivos.||  
||||  
|[Task\-based Asynchronous Pattern \(TAP\)](../Topic/Task-based%20Asynchronous%20Pattern%20\(TAP\).md)|Descreve um novo padrão de assincronia no .NET Framework. O padrão se baseia o <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> tipos.||  
|[Vídeos sobre assincronia no Channel 9](http://go.microsoft.com/fwlink/p/?LinkID=267466)|Fornece links para uma variedade de vídeos sobre programação assíncrona.||  
  
##  <a name="BKMK_CompleteExample"></a> Exemplo completo  
 O código a seguir é o arquivo de MainWindow.xaml.cs do aplicativo Windows Presentation Foundation \(WPF\) que aborda esse tópico. Você pode baixar o exemplo de [exemplo de assincronia: exemplo de "Programação assíncrona com Async e Await"](http://go.microsoft.com/fwlink/p/?LinkID=261549).  
  
```c#  
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
                String.Format("\r\nLength of the downloaded string: {0}.\r\n", contentLength);  
        }  
  
        // Three things to note in the signature:  
        //  - The method has an async modifier.   
        //  - The return type is Task or Task<T>. (See "Return Types" section.)  
        //    Here, it is Task<int> because the return statement returns an integer.  
        //  - The method name ends in "Async."  
        async Task<int> AccessTheWebAsync()  
        {   
            // You need to add a reference to System.Net.Http to declare client.  
            HttpClient client = new HttpClient();  
  
            // GetStringAsync returns a Task<string>. That means that when you await the  
            // task you'll get a string (urlContents).  
            Task<string> getStringTask = client.GetStringAsync("http://msdn.microsoft.com");  
  
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
  
        void DoIndependentWork()  
        {  
            resultsTextBox.Text += "Working . . . . . . .\r\n";  
        }  
    }  
}  
  
// Sample Output:  
  
// Working . . . . . . .  
  
// Length of the downloaded string: 41564.  
```  
  
## Consulte também  
 [async](../../../../visual-basic/language-reference/modifiers/async.md)   
 [await](../../../../csharp/language-reference/keywords/await.md)