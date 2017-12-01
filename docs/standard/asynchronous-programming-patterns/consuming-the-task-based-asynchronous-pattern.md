---
title: "Consumindo o padrão assíncrono baseado em tarefa"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- .NET Framework, and TAP
- asynchronous design patterns, .NET Framework
- TAP, .NET Framework support for
- Task-based Asynchronous Pattern, .NET Framework support for
- .NET Framework, asynchronous design patterns
ms.assetid: 033cf871-ae24-433d-8939-7a3793e547bf
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 90b2a36f0e6bf06b0fefe2191d5b17c9c07d1588
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="consuming-the-task-based-asynchronous-pattern"></a>Consumindo o padrão assíncrono baseado em tarefa
Quando você usa o TAP (padrão assíncrono baseado em tarefa) para trabalhar com operações assíncronas, você pode usar retornos de chamada para obter uma espera sem bloqueio.  Para tarefas, isso é conseguido por meio de métodos como <xref:System.Threading.Tasks.Task.ContinueWith%2A?displayProperty=nameWithType>. O suporte assíncrono baseado em linguagem oculta retornos de chamada ao permitir que operações assíncronas sejam colocadas em espera no fluxo de controle normal, sendo que o código gerado pelo compilador fornece esse mesmo suporte de nível de API.  
  
## <a name="suspending-execution-with-await"></a>Suspendendo a execução com Await  
 Começando com o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], você pode usar o [await](~/docs/csharp/language-reference/keywords/await.md) palavra-chave em c# e o [operador Await](~/docs/visual-basic/language-reference/operators/await-operator.md) no Visual Basic para aguardar assincronamente <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> objetos. Quando você está aguardando uma <xref:System.Threading.Tasks.Task>, o `await` expressão é do tipo `void`. Quando você está aguardando uma <xref:System.Threading.Tasks.Task%601>, o `await` expressão é do tipo `TResult`. Uma expressão `await` deve ocorrer dentro do corpo de um método assíncrono. Para obter mais informações sobre suporte às linguagens C# e Visual Basic no [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], consulte as especificações das linguagens C# e Visual Basic.  
  
 Nos bastidores, a funcionalidade await instala um retorno de chamada na tarefa pelo uso de uma continuação.  Esse retorno de chamada retoma o método assíncrono no ponto de suspensão. Quando o método assíncrono é reiniciado, se a operação em espera foi concluída com êxito e foi um <xref:System.Threading.Tasks.Task%601>, sua `TResult` é retornado.  Se o <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> que era esperada terminou no <xref:System.Threading.Tasks.TaskStatus.Canceled> estado, uma <xref:System.OperationCanceledException> exceção será lançada.  Se o <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> que era esperada terminou no <xref:System.Threading.Tasks.TaskStatus.Faulted> de estado, a exceção que causou a falha é gerada. Uma `Task` pode falhar como resultado de várias exceções, mas apenas uma dessas exceções é propagada. No entanto, o <xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType> propriedade retorna um <xref:System.AggregateException> exceção que contém todos os erros.  
  
 Se um contexto de sincronização (<xref:System.Threading.SynchronizationContext> objeto) é associada ao thread que estava executando o método assíncrono no momento da suspensão (por exemplo, se o <xref:System.Threading.SynchronizationContext.Current%2A?displayProperty=nameWithType> propriedade não é `null`), o método assíncrono é retomada no que mesmo contexto de sincronização usando o contexto <xref:System.Threading.SynchronizationContext.Post%2A> método. Caso contrário, ele se baseia no Agendador de tarefas (<xref:System.Threading.Tasks.TaskScheduler> objeto) que era atual no momento da suspensão. Normalmente, isso é que o Agendador de tarefas padrão (<xref:System.Threading.Tasks.TaskScheduler.Default%2A?displayProperty=nameWithType>), que tem como alvo o pool de threads. O Agendador de Tarefas determina se a operação assíncrona aguardada deve continuar do ponto em que foi concluída ou se a retomada deve ser agendada. O agendador padrão geralmente permite que a continuação seja executada no thread em que a operação aguardada foi concluída.  
  
 Quando um método assíncrono é chamado, ele executa o corpo da função de modo síncrono até a primeira expressão await em uma instância aguardável que ainda não tenha foi concluída, no ponto em que a invocação retorna ao chamador. Se o método assíncrono não retornar `void`, um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> objeto é retornado para representar o cálculo em andamento. Um método assíncrono não nulo, se uma instrução de retorno é encontrada ou o final do corpo do método é atingido, a tarefa é concluída no <xref:System.Threading.Tasks.TaskStatus.RanToCompletion> estado final. Se uma exceção sem tratamento faz com que o controle sair do corpo de método assíncrono, a tarefa termina no <xref:System.Threading.Tasks.TaskStatus.Faulted> estado. Se essa exceção é um <xref:System.OperationCanceledException>, a tarefa terminará em vez disso, o <xref:System.Threading.Tasks.TaskStatus.Canceled> estado. Dessa maneira, a exceção ou o resultado é eventualmente publicado.  
  
 Há diversas variações importantes desse comportamento.  Por motivos de desempenho, se uma tarefa já foi concluída até o momento em que a tarefa é aguardada, o controle não é suspenso e a função continua a executar.  Além disso, retornar para o contexto original nem sempre é o comportamento desejado e pode ser alterado; isso é descrito mais detalhadamente na próxima seção.  
  
### <a name="configuring-suspension-and-resumption-with-yield-and-configureawait"></a>Configurando a suspensão e retomada com Yield e ConfigureAwait  
 Vários métodos fornecem mais controle sobre a execução de um método assíncrono. Por exemplo, você pode usar o <xref:System.Threading.Tasks.Task.Yield%2A?displayProperty=nameWithType> método introduzir um ponto de rendimento para o método assíncrono:  
  
```csharp  
public class Task : …  
{  
    public static YieldAwaitable Yield();  
    …  
}  
```  
  
 Isso é equivalente a postar assincronamente ou agendar de volta para o contexto atual.  
  
```csharp  
Task.Run(async delegate  
{  
    for(int i=0; i<1000000; i++)  
    {  
        await Task.Yield(); // fork the continuation into a separate work item  
        ...  
    }  
});  
```  
  
 Você também pode usar o <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> método para melhor controle sobre a suspensão e retomada de um método assíncrono.  Conforme mencionado anteriormente, por padrão, o contexto atual é capturado no momento em que um método assíncrono é suspenso e esse contexto capturado é usado para invocar a continuação do método assíncrono após a retomada.  Em muitos casos, esse é o comportamento exato desejado.  Em outros casos, você pode não se importar com o contexto de continuação e pode obter o melhor desempenho ao evitar essas postagens de volta para o contexto original.  Para habilitar isso, use o <xref:System.Threading.Tasks.Task.ConfigureAwait%2A?displayProperty=nameWithType> método para informar a operação de espera não capturar e retomar no contexto, mas para continuar a execução sempre que a operação assíncrona que estava sendo aguardada concluída:  
  
```csharp  
await someTask.ConfigureAwait(continueOnCapturedContext:false);  
```  
  
## <a name="canceling-an-asynchronous-operation"></a>Cancelando uma operação assíncrona  
 Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], toque em métodos que oferece suporte ao cancelamento fornecem pelo menos uma sobrecarga que aceita um token de cancelamento (<xref:System.Threading.CancellationToken> objeto).  
  
 Um token de cancelamento é criado por meio de uma origem de token de cancelamento (<xref:System.Threading.CancellationTokenSource> objeto).  A fonte <xref:System.Threading.CancellationTokenSource.Token%2A> propriedade retorna o token de cancelamento que sinalizará quando a fonte <xref:System.Threading.CancellationTokenSource.Cancel%2A> método é chamado.  Por exemplo, se você deseja fazer download de uma única página da Web e você deseja cancelar a operação, você cria um <xref:System.Threading.CancellationTokenSource> do objeto, passe seu token para o método de toque e chame a fonte <xref:System.Threading.CancellationTokenSource.Cancel%2A> método quando você estiver pronto para cancelar a operação:  
  
```csharp  
var cts = new CancellationTokenSource();  
string result = await DownloadStringAsync(url, cts.Token);  
… // at some point later, potentially on another thread  
cts.Cancel();  
```  
  
 Para cancelar várias invocações assíncronas, você pode passar o mesmo token para todas as invocações:  
  
```csharp  
var cts = new CancellationTokenSource();  
    IList<string> results = await Task.WhenAll(from url in urls select DownloadStringAsync(url, cts.Token));  
    // at some point later, potentially on another thread  
    …  
    cts.Cancel();  
```  
  
 Ou então, você pode passar o mesmo token para um subconjunto seletivo de operações:  
  
```csharp  
var cts = new CancellationTokenSource();  
    byte [] data = await DownloadDataAsync(url, cts.Token);  
    await SaveToDiskAsync(outputPath, data, CancellationToken.None);  
    … // at some point later, potentially on another thread  
    cts.Cancel();  
```  
  
 Solicitações de cancelamento podem ser iniciadas de qualquer thread.  
  
 Você pode passar o <xref:System.Threading.CancellationToken.None%2A?displayProperty=nameWithType> valor para qualquer método que aceite um token de cancelamento para indicar que o cancelamento nunca será solicitado.  Isso faz com que o <xref:System.Threading.CancellationToken.CanBeCanceled%2A?displayProperty=nameWithType> propriedade para retornar `false`, e o método chamado pode otimizar adequadamente.  Para fins de teste, você também pode passar um token de cancelamento previamente cancelado que é instanciado pelo uso do construtor que aceita um valor booliano para indicar se o token deve iniciar em um estado não cancelável ou já cancelado.  
  
 Essa abordagem para o cancelamento tem várias vantagens:  
  
-   Você pode passar o mesmo token de cancelamento para qualquer número de operações síncronas e assíncronas.  
  
-   A mesma solicitação de cancelamento pode ser proliferada para qualquer número de ouvintes.  
  
-   O desenvolvedor da API assíncrona tem total controle com relação ao cancelamento poder ou não ser solicitado e a quando isso pode entrar em vigor.  
  
-   O código que consome a API pode, seletivamente, determinar as invocações assíncronas para as quais as solicitações de cancelamento serão propagadas.  
  
## <a name="monitoring-progress"></a>Monitorando o progresso  
 Alguns métodos assíncronos expõem progresso através de uma interface de progresso passada para o método assíncrono.  Por exemplo, considere uma função que baixa de forma assíncrona uma cadeia de caracteres de texto e, durante esse processo, emite atualizações de progresso que incluem o percentual de download concluído até o momento.  Tal método poderia ser consumido em um aplicativo do WPF (Windows Presentation Foundation) da seguinte maneira:  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)    
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtResult.Text = await DownloadStringAsync(txtUrl.Text,   
            new Progress<int>(p => pbDownloadProgress.Value = p));  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
<a name="combinators"></a>   
## <a name="using-the-built-in-task-based-combinators"></a>Usando os combinadores baseados em tarefas internos  
 O <xref:System.Threading.Tasks> namespace inclui vários métodos para compor e trabalhar com tarefas.  
  
### <a name="taskrun"></a>Task.Run  
 O <xref:System.Threading.Tasks.Task> classe inclui vários <xref:System.Threading.Tasks.Task.Run%2A> métodos que permitem a fácil descarregar o trabalho como um <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> ao pool de threads, por exemplo:  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    textBox1.Text = await Task.Run(() =>  
    {  
        // … do compute-bound work here  
        return answer;  
    });  
}  
```  
  
 Algumas dessas <xref:System.Threading.Tasks.Task.Run%2A> métodos, como o <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType> sobrecarga, existe como um atalho para o <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> método.  Outras sobrecargas, como <xref:System.Threading.Tasks.Task.Run%28System.Func%7BSystem.Threading.Tasks.Task%7D%29?displayProperty=nameWithType>, permitem que você use await ao trabalho descarregados, por exemplo:  
  
```csharp  
public async void button1_Click(object sender, EventArgs e)  
{  
    pictureBox1.Image = await Task.Run(async() =>  
    {  
        using(Bitmap bmp1 = await DownloadFirstImageAsync())  
        using(Bitmap bmp2 = await DownloadSecondImageAsync())  
        return Mashup(bmp1, bmp2);  
    });  
}  
```  
  
 Essas sobrecargas são logicamente equivalentes a usar o <xref:System.Threading.Tasks.TaskFactory.StartNew%2A?displayProperty=nameWithType> método junto com o <xref:System.Threading.Tasks.TaskExtensions.Unwrap%2A> método de extensão na biblioteca de tarefas paralelas.  
  
### <a name="taskfromresult"></a>Task.FromResult  
 Use o <xref:System.Threading.Tasks.Task.FromResult%2A> método em cenários onde dados já podem estar disponível e apenas precisa ser retornado de um método de retorno foi eliminado em um <xref:System.Threading.Tasks.Task%601>:  
  
```csharp  
public Task<int> GetValueAsync(string key)  
{  
    int cachedValue;  
    return TryGetCachedValue(out cachedValue) ?  
        Task.FromResult(cachedValue) :  
        GetValueAsyncInternal();  
}  
  
private async Task<int> GetValueAsyncInternal(string key)  
{  
    …  
}  
```  
  
### <a name="taskwhenall"></a>Task.WhenAll  
 Use o <xref:System.Threading.Tasks.Task.WhenAll%2A> método de forma assíncrona espera em várias operações assíncronas que são representadas como tarefas.  O método tem várias sobrecargas que dão suporte a um conjunto de tarefas não genéricas ou um conjunto não uniforme de tarefas genéricas (por exemplo, aguardar de forma assíncrona várias operações que retornam nulo ou aguardar vários métodos que retornam um valor em que cada valor pode ter um tipo diferente) e dão suporte a um conjunto uniforme de tarefas genéricas (como aguardar de forma assíncrona vários métodos que retornam `TResult`).  
  
 Digamos que você deseja enviar mensagens de email para vários clientes. Você pode sobrepor o envio de mensagens de modo que você não aguarde a conclusão de uma mensagem antes de enviar a próxima. Você também pode descobrir quando as operações de envio foram concluídas e se ocorreu algum erro:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
await Task.WhenAll(asyncOps);  
```  
  
 Esse código explicitamente não lidar com exceções que podem ocorrer, mas permite exceções propagar do `await` na tarefa resultante de <xref:System.Threading.Tasks.Task.WhenAll%2A>.  Para tratar as exceções, você pode usar código como o seguinte:  
  
```csharp  
IEnumerable<Task> asyncOps = from addr in addrs select SendMailAsync(addr);  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    ...  
}  
```  
  
 Nesse caso, se qualquer operação assíncrona falhar, todas as exceções serão consolidadas em um <xref:System.AggregateException> exceção, que é armazenada no <xref:System.Threading.Tasks.Task> que é retornado o <xref:System.Threading.Tasks.Task.WhenAll%2A> método.  No entanto, apenas uma dessas exceções é propagada pela palavra-chave `await`.  Se você quiser examinar todas as exceções, poderá reescrever o código anterior da seguinte maneira:  
  
```csharp  
Task [] asyncOps = (from addr in addrs select SendMailAsync(addr)).ToArray();  
try  
{  
    await Task.WhenAll(asyncOps);  
}  
catch(Exception exc)  
{  
    foreach(Task faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
 Vamos considerar um exemplo em que baixamos vários arquivos da Web de forma assíncrona.  Nesse caso, todas as operações assíncronas têm tipos de resultado homogêneos e é fácil acessar os resultados:  
  
```csharp  
string [] pages = await Task.WhenAll(  
    from url in urls select DownloadStringAsync(url));  
```  
  
 Você pode usar as mesmas técnicas de tratamento de exceções discutidas no cenário anterior, em que nulo é retornado:  
  
```csharp  
Task [] asyncOps =   
    (from url in urls select DownloadStringAsync(url)).ToArray();  
try  
{  
    string [] pages = await Task.WhenAll(asyncOps);  
    ...  
}  
catch(Exception exc)  
{  
    foreach(Task<string> faulted in asyncOps.Where(t => t.IsFaulted))  
    {  
        … // work with faulted and faulted.Exception  
    }  
}  
```  
  
### <a name="taskwhenany"></a>Task.WhenAny  
 Você pode usar o <xref:System.Threading.Tasks.Task.WhenAny%2A> método de forma assíncrona espera para apenas uma das várias operações assíncronas são representadas como tarefas para concluir.  Esse método tem quatro casos de uso principais:  
  
-   Redundância: executar uma operação várias vezes e selecionar aquela que é concluída primeiro (por exemplo, entrando em contato com vários serviços Web de cotação de ações que produzirão um único resultado e selecionar aquele que termina mais rápido).  
  
-   Intercalação: iniciar várias operações e aguardar que todas eles sejam concluídas, mas processando-as conforme são concluídas.  
  
-   Limitação: permitir que operações adicionais comecem conforme outras forem concluídas.  Essa é uma extensão do cenário de intercalação.  
  
-   Esgotamento de início: por exemplo, uma operação representada pela tarefa t1 pode ser agrupada em uma <xref:System.Threading.Tasks.Task.WhenAny%2A> tarefa com outra tarefa t2 e você pode esperar o <xref:System.Threading.Tasks.Task.WhenAny%2A> tarefa. A tarefa t2 poderiam representar um tempo limite, ou cancelamento ou alguns outros sinal que faz com que o <xref:System.Threading.Tasks.Task.WhenAny%2A> tarefa seja concluída antes de t1 é concluída.  
  
#### <a name="redundancy"></a>Redundância  
 Considere um caso em que você deseja tomar uma decisão sobre a possibilidade de comprar uma ação.  Há diversos serviços Web de recomendação de compra de ações nos quais você confia, mas dependendo da carga diária, cada serviço pode acabar sendo lento em horários diferentes.  Você pode usar o <xref:System.Threading.Tasks.Task.WhenAny%2A> método para receber uma notificação quando qualquer operação for concluída:  
  
```csharp  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol),   
    GetBuyRecommendation2Async(symbol),  
    GetBuyRecommendation3Async(symbol)  
};  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
if (await recommendation) BuyStock(symbol);  
```  
  
 Ao contrário de <xref:System.Threading.Tasks.Task.WhenAll%2A>, que retorna os resultados não encapsulados de todas as tarefas concluídas com êxito, <xref:System.Threading.Tasks.Task.WhenAny%2A> retorna a tarefa foi concluída. Se uma tarefa falhar, será importante saber que ela falhou e, se uma tarefa for bem-sucedida, será importante saber a qual tarefa o valor retornado é associado.  Portanto, você precisa acessar o resultado da tarefa retornada ou aguardá-la ainda mais, conforme mostra este exemplo.  
  
 Assim como acontece com <xref:System.Threading.Tasks.Task.WhenAll%2A>, você precisa ser capaz de acomodar as exceções.  Devido a você receber novamente a tarefa concluída, você poderá esperar a tarefa retornada para então propagar os erros e aplicar `try/catch` a eles adequadamente; por exemplo:  
  
```csharp  
Task<bool> [] recommendations = …;  
while(recommendations.Count > 0)  
{   
    Task<bool> recommendation = await Task.WhenAny(recommendations);      
    try  
    {  
        if (await recommendation) BuyStock(symbol);  
        break;  
    }  
    catch(WebException exc)  
    {  
        recommendations.Remove(recommendation);  
    }  
}  
```  
  
 Além disso, mesmo que uma primeira tarefa seja concluída com êxito, as tarefas subsequentes poderão falhar.  Neste ponto, você tem várias opções para lidar com exceções: você pode esperar até que tem concluído todas as tarefas iniciadas, caso em que você pode usar o <xref:System.Threading.Tasks.Task.WhenAll%2A> método, ou você pode decidir que todas as exceções são importantes e devem estar conectadas.  Para isso, você pode usar as continuações para receber uma notificação quando tarefas foram concluídas de forma assíncrona:  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => { if (t.IsFaulted) Log(t.Exception); });  
}  
```  
  
 ou:  
  
```csharp  
foreach(Task recommendation in recommendations)  
{  
    var ignored = recommendation.ContinueWith(  
        t => Log(t.Exception), TaskContinuationOptions.OnlyOnFaulted);  
}  
```  
  
 ou até mesmo:  
  
```  
private static async void LogCompletionIfFailed(IEnumerable<Task> tasks)  
{  
    foreach(var task in tasks)  
    {  
        try { await task; }  
        catch(Exception exc) { Log(exc); }  
    }  
}  
…  
LogCompletionIfFailed(recommendations);  
```  
  
 Finalmente, você talvez queira cancelar todas as operações restantes:  
  
```csharp  
var cts = new CancellationTokenSource();  
var recommendations = new List<Task<bool>>()   
{   
    GetBuyRecommendation1Async(symbol, cts.Token),   
    GetBuyRecommendation2Async(symbol, cts.Token),  
    GetBuyRecommendation3Async(symbol, cts.Token)  
};  
  
Task<bool> recommendation = await Task.WhenAny(recommendations);  
cts.Cancel();  
if (await recommendation) BuyStock(symbol);  
```  
  
#### <a name="interleaving"></a>Intercalação  
 Considere um caso em que você está baixando imagens da Web e processando cada imagem (por exemplo, adicionando a imagem a um controle de interface do usuário).  Você precisa fazer o processamento sequencialmente no thread da interface do usuário, mas você quer baixar as imagens tão simultaneamente quanto possível. Além disso, você não deseja esperar para adicionar as imagens à interface do usuário após elas serem todas baixadas – você deseja adicioná-las conforme o download de cada uma delas é concluído:  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
 Você também pode aplicar de intercalação para o cenário que envolve o processamento de computação intensivo no <xref:System.Threading.ThreadPool> das imagens baixadas; por exemplo:  
  
```csharp  
List<Task<Bitmap>> imageTasks =   
    (from imageUrl in urls select GetBitmapAsync(imageUrl)  
         .ContinueWith(t => ConvertImage(t.Result)).ToList();  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch{}  
}  
```  
  
#### <a name="throttling"></a>Limitação  
 Considere o exemplo de intercalação, exceto que o usuário está baixando um número tão grande de imagens que os downloads precisam ser limitados; por exemplo, você deseja que apenas um número específico de downloads ocorram simultaneamente. Para conseguir isso, você pode iniciar um subconjunto das operações assíncronas.  Conforme as operações forem concluídas, você pode iniciar operações adicionais para assumir o lugar delas:  
  
```csharp  
const int CONCURRENCY_LEVEL = 15;  
Uri [] urls = …;  
int nextIndex = 0;  
var imageTasks = new List<Task<Bitmap>>();  
while(nextIndex < CONCURRENCY_LEVEL && nextIndex < urls.Length)  
{  
    imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
    nextIndex++;  
}  
  
while(imageTasks.Count > 0)  
{  
    try  
    {  
        Task<Bitmap> imageTask = await Task.WhenAny(imageTasks);  
        imageTasks.Remove(imageTask);  
  
        Bitmap image = await imageTask;  
        panel.AddImage(image);  
    }  
    catch(Exception exc) { Log(exc); }  
  
    if (nextIndex < urls.Length)  
    {  
        imageTasks.Add(GetBitmapAsync(urls[nextIndex]));  
        nextIndex++;  
    }  
}  
```  
  
#### <a name="early-bailout"></a>Saída precoce  
 Considere a possibilidade de que você está aguardando de forma assíncrona que uma operação seja concluída e, simultaneamente, respondendo a uma solicitação de cancelamento do usuário (por exemplo, o usuário clicou em um botão para cancelar). O código a seguir ilustra esse cenário:  
  
```csharp  
private CancellationTokenSource m_cts;   
  
public void btnCancel_Click(object sender, EventArgs e)  
{  
    if (m_cts != null) m_cts.Cancel();  
}  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        if (imageDownload.IsCompleted)  
        {  
            Bitmap image = await imageDownload;  
            panel.AddImage(image);  
        }  
        else imageDownload.ContinueWith(t => Log(t));  
    }  
    finally { btnRun.Enabled = true; }  
}  
  
private static async Task UntilCompletionOrCancellation(  
    Task asyncOp, CancellationToken ct)  
{  
    var tcs = new TaskCompletionSource<bool>();  
    using(ct.Register(() => tcs.TrySetResult(true)))  
        await Task.WhenAny(asyncOp, tcs.Task);  
    return asyncOp;  
}  
```  
  
 Essa implementação reabilita a interface do usuário assim que você decide sair, mas não as cancela as operações assíncronas subjacentes.  Outra alternativa seria cancelar as operações pendentes quando você decide sair, mas não restabelecer a interface do usuário até que as operações sejam realmente concluídas, possivelmente devido a um encerramento precoce devido à solicitação de cancelamento:  
  
```csharp  
private CancellationTokenSource m_cts;  
  
public async void btnRun_Click(object sender, EventArgs e)  
{  
    m_cts = new CancellationTokenSource();  
  
    btnRun.Enabled = false;  
    try  
    {  
        Task<Bitmap> imageDownload = GetBitmapAsync(txtUrl.Text, m_cts.Token);   
        await UntilCompletionOrCancellation(imageDownload, m_cts.Token);  
        Bitmap image = await imageDownload;  
        panel.AddImage(image);  
    }  
    catch(OperationCanceledException) {}  
    finally { btnRun.Enabled = true; }  
}  
```  
  
 Outro exemplo de esgotamento antecipado envolve o uso de <xref:System.Threading.Tasks.Task.WhenAny%2A> método junto com o <xref:System.Threading.Tasks.Task.Delay%2A> método, conforme discutido na próxima seção.  
  
### <a name="taskdelay"></a>Task.Delay  
 Você pode usar o <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> método apresentar faz uma pausa na execução de um método assíncrono.  Isso é útil para muitos tipos de funcionalidades, incluindo o build de loops de sondagem e o atraso da manipulação da entrada do usuário por um período de tempo predeterminado.  O <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> método também pode ser útil em combinação com <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> para implementação de tempos limite em espera.  
  
 Se uma tarefa que for parte de uma operação assíncrona maior (por exemplo, um serviço Web ASP.NET) levar muito tempo para concluir, a operação geral poderá ser afetada, especialmente se ela falhar e nunca for concluída.  Por esse motivo, é importante ser capaz de atingir o tempo limite ao aguardar uma operação assíncrona.  Síncronos <xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.WaitAll%2A?displayProperty=nameWithType>, e <xref:System.Threading.Tasks.Task.WaitAny%2A?displayProperty=nameWithType> métodos aceitam valores de tempo limite, mas correspondente <xref:System.Threading.Tasks.TaskFactory.ContinueWhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> e mencionadas anteriormente <xref:System.Threading.Tasks.Task.WhenAll%2A?displayProperty=nameWithType> / <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType>métodos não.  Em vez disso, você pode usar <xref:System.Threading.Tasks.Task.Delay%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task.WhenAny%2A?displayProperty=nameWithType> em conjunto para implementar um tempo limite.  
  
 Por exemplo, em seu aplicativo de interface do usuário, digamos que você deseja baixar uma imagem e desabilitar a interface do usuário durante esse download. No entanto, se o download levar muito tempo, você desejará reabilitar a interface do usuário e descartar o download:  
  
```csharp  
public async void btnDownload_Click(object sender, EventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap> download = GetBitmapAsync(url);  
        if (download == await Task.WhenAny(download, Task.Delay(3000)))  
        {  
            Bitmap bmp = await download;  
            pictureBox.Image = bmp;  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            pictureBox.Image = null;  
            status.Text = "Timed out";  
            var ignored = download.ContinueWith(  
                t => Trace("Task finally completed"));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
 O mesmo se aplica a vários downloads, porque <xref:System.Threading.Tasks.Task.WhenAll%2A> retorna uma tarefa:  
  
```csharp  
public async void btnDownload_Click(object sender, RoutedEventArgs e)  
{  
    btnDownload.Enabled = false;  
    try  
    {  
        Task<Bitmap[]> downloads =   
            Task.WhenAll(from url in urls select GetBitmapAsync(url));  
        if (downloads == await Task.WhenAny(downloads, Task.Delay(3000)))  
        {  
            foreach(var bmp in downloads) panel.AddImage(bmp);  
            status.Text = "Downloaded";  
        }  
        else  
        {  
            status.Text = "Timed out";  
            downloads.ContinueWith(t => Log(t));  
        }  
    }  
    finally { btnDownload.Enabled = true; }  
}  
```  
  
## <a name="building-task-based-combinators"></a>Compilando combinadores baseados em tarefa  
 Já que uma tarefa é capaz de representar totalmente uma operação assíncrona e fornecer recursos síncronos e assíncronos para ingressar na operação, recuperar seus resultados e assim por diante, você pode compilar bibliotecas úteis de combinadores que compõem tarefas para compilar padrões maiores.  Conforme discutido na seção anterior, o .NET Framework inclui vários combinadores internos, mas você também pode compilar os seus próprios combinadores. As seções a seguir fornecem vários exemplos de tipos e métodos combinadores potenciais.  
  
### <a name="retryonfault"></a>RetryOnFault  
 Em muitas situações, talvez você queira repetir uma operação se uma tentativa anterior falhar.  Para código síncrono, você pode compilar um método auxiliar como `RetryOnFault` no exemplo a seguir para fazer isso:  
  
```csharp  
public static T RetryOnFault<T>(  
    Func<T> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return function(); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 Você pode compilar um método auxiliar quase idêntico para operações assíncronas implementadas com TAP e, assim, retornar tarefas:  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
    }  
    return default(T);  
}  
```  
  
 Você pode usar este combinador para codificar repetições na lógica do aplicativo, por exemplo:  
  
```csharp  
// Download the URL, trying up to three times in case of failure  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3);  
```  
  
 Você pode estender ainda mais a função `RetryOnFault`. Por exemplo, a função poderá aceitar outro `Func<Task>` que será invocado entre as tentativas para determinar quando tentar novamente a operação, por exemplo:  
  
```csharp  
public static async Task<T> RetryOnFault<T>(  
    Func<Task<T>> function, int maxTries, Func<Task> retryWhen)  
{  
    for(int i=0; i<maxTries; i++)  
    {  
        try { return await function().ConfigureAwait(false); }  
        catch { if (i == maxTries-1) throw; }  
        await retryWhen().ConfigureAwait(false);  
    }  
    return default(T);  
}  
```  
  
 Você pode então usar a função da seguinte maneira, para aguardar um segundo antes de repetir a operação:  
  
```csharp  
// Download the URL, trying up to three times in case of failure,  
// and delaying for a second between retries  
string pageContents = await RetryOnFault(  
    () => DownloadStringAsync(url), 3, () => Task.Delay(1000));  
```  
  
### <a name="needonlyone"></a>NeedOnlyOne  
 Às vezes, você pode tirar proveito da redundância para melhorar a latência e as chances de sucesso de uma operação.  Considere vários serviços Web que fornecem cotações de ações, mas em diferentes horas do dia, cada serviço pode fornecer diferentes níveis de qualidade e tempos de resposta.  Para lidar com essas flutuações, você poderá emitir solicitações para todos os serviços Web e, assim que você obtiver uma resposta de um deles, cancelar as solicitações restantes.  Você pode implementar uma função auxiliar para facilitar a implementação desse padrão comum de inicialização de várias operações, aguardar uma delas e, em seguida, cancelar o restante. A função `NeedOnlyOne` no exemplo a seguir ilustra esse cenário:  
  
```csharp  
public static async Task<T> NeedOnlyOne(  
    params Func<CancellationToken,Task<T>> [] functions)  
{  
    var cts = new CancellationTokenSource();  
    var tasks = (from function in functions  
                 select function(cts.Token)).ToArray();  
    var completed = await Task.WhenAny(tasks).ConfigureAwait(false);  
    cts.Cancel();  
    foreach(var task in tasks)   
    {  
        var ignored = task.ContinueWith(  
            t => Log(t), TaskContinuationOptions.OnlyOnFaulted);  
    }  
    return completed;  
}  
```  
  
 Você pode então usar essa função conforme demonstrado a seguir:  
  
```csharp  
double currentPrice = await NeedOnlyOne(  
    ct => GetCurrentPriceFromServer1Async("msft", ct),  
    ct => GetCurrentPriceFromServer2Async("msft", ct),  
    ct => GetCurrentPriceFromServer3Async("msft", ct));  
```  
  
### <a name="interleaved-operations"></a>Operações intercaladas  
 Há um problema de desempenho potencial com o uso de <xref:System.Threading.Tasks.Task.WhenAny%2A> método para dar suporte a um cenário intercalado quando você estiver trabalhando com grandes conjuntos de tarefas.  Todas as chamadas para <xref:System.Threading.Tasks.Task.WhenAny%2A> resulta em uma continuação que está sendo registrada em cada tarefa. Para um número N de tarefas, isso resulta em O(N2) continuações criadas durante o tempo de vida da operação de intercalação.  Se você estiver trabalhando com um grande conjunto de tarefas, você poderá usar um combinador (`Interleaved` no exemplo a seguir) para solucionar o problema de desempenho:  
  
```csharp  
static IEnumerable<Task<T>> Interleaved<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputTasks = tasks.ToList();  
    var sources = (from _ in Enumerable.Range(0, inputTasks.Count)   
                   select new TaskCompletionSource<T>()).ToList();  
    int nextTaskIndex = -1;  
    foreach (var inputTask in inputTasks)  
    {  
        inputTask.ContinueWith(completed =>  
        {  
            var source = sources[Interlocked.Increment(ref nextTaskIndex)];  
            if (completed.IsFaulted)   
                source.TrySetException(completed.Exception.InnerExceptions);  
            else if (completed.IsCanceled)   
                source.TrySetCanceled();  
            else   
                source.TrySetResult(completed.Result);  
        }, CancellationToken.None,   
           TaskContinuationOptions.ExecuteSynchronously,   
           TaskScheduler.Default);  
    }  
    return from source in sources   
           select source.Task;  
}  
```  
  
 Você poderá usar o combinador para processar os resultados das tarefas conforme elas forem concluídas, por exemplo:  
  
```csharp  
IEnumerable<Task<int>> tasks = ...;  
foreach(var task in Interleaved(tasks))  
{  
    int result = await task;  
    …  
}  
```  
  
### <a name="whenallorfirstexception"></a>WhenAllOrFirstException  
 Em determinados cenários de dispersão/coleta, convém esperar por todas as tarefas em um conjunto, a menos que uma delas falhe, caso em que você desejará interromper a espera assim que a exceção ocorrer.  Você pode realizar isso com um método combinador tal como `WhenAllOrFirstException` no exemplo a seguir:  
  
```csharp  
public static Task<T[]> WhenAllOrFirstException<T>(IEnumerable<Task<T>> tasks)  
{  
    var inputs = tasks.ToList();  
    var ce = new CountdownEvent(inputs.Count);  
    var tcs = new TaskCompletionSource<T[]>();  
  
    Action<Task> onCompleted = (Task completed) =>  
    {  
        if (completed.IsFaulted)   
            tcs.TrySetException(completed.Exception.InnerExceptions);  
        if (ce.Signal() && !tcs.Task.IsCompleted)  
            tcs.TrySetResult(inputs.Select(t => t.Result).ToArray());  
    };  
  
    foreach (var t in inputs) t.ContinueWith(onCompleted);  
    return tcs.Task;  
}  
```  
  
## <a name="building-task-based-data-structures"></a>Compilando estruturas de dados com base em tarefa  
 Além da capacidade para criar combinadores personalizados baseado em tarefa, ter uma estrutura de dados em <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> que representa os dois os resultados de uma operação assíncrona e a sincronização necessária para unir com ele facilita muito poderoso Digite no qual criar estruturas de dados personalizado a ser usado em cenários assíncronos.  
  
### <a name="asynccache"></a>AsyncCache  
 Um aspecto importante de uma tarefa é que ele pode ser enviado para vários consumidores, todos os quais podem esperar, registrar continuações com ele, obter seus resultados ou exceções (no caso de <xref:System.Threading.Tasks.Task%601>), e assim por diante.  Isso torna <xref:System.Threading.Tasks.Task> e <xref:System.Threading.Tasks.Task%601> perfeito para ser usado em uma infraestrutura de cache assíncrona.  Aqui está um exemplo de uma pequena, mas eficiente cache assíncrono criado na parte superior do <xref:System.Threading.Tasks.Task%601>:  
  
```csharp  
public class AsyncCache<TKey, TValue>  
{  
    private readonly Func<TKey, Task<TValue>> _valueFactory;  
    private readonly ConcurrentDictionary<TKey, Lazy<Task<TValue>>> _map;  
  
    public AsyncCache(Func<TKey, Task<TValue>> valueFactory)  
    {  
        if (valueFactory == null) throw new ArgumentNullException("loader");  
        _valueFactory = valueFactory;  
        _map = new ConcurrentDictionary<TKey, Lazy<Task<TValue>>>();  
    }  
  
    public Task<TValue> this[TKey key]  
    {  
        get  
        {  
            if (key == null) throw new ArgumentNullException("key");  
            return _map.GetOrAdd(key, toAdd =>   
                new Lazy<Task<TValue>>(() => _valueFactory(toAdd))).Value;  
        }  
    }  
}  
```  
  
 O [AsyncCache\<TKey, TValue >](http://go.microsoft.com/fwlink/p/?LinkId=251941) classe aceita como um delegado para o construtor de uma função que usa um `TKey` e retorna um <xref:System.Threading.Tasks.Task%601>.  Quaisquer valores do cache previamente acessados são armazenados no dicionário interno e `AsyncCache` garante que apenas uma tarefa seja gerada por chave, mesmo que o cache seja acessado simultaneamente.  
  
 Por exemplo, você pode compilar um cache para páginas da Web baixadas:  
  
```csharp  
private AsyncCache<string,string> m_webPages =   
    new AsyncCache<string,string>(DownloadStringAsync);  
```  
  
 Você pode em seguida usar esse cache em métodos assíncronos sempre que precisar do conteúdo de uma página da Web. A classe `AsyncCache` garante que você esteja baixando o mínimo possível de páginas e armazena os resultados em cache.  
  
```csharp  
private async void btnDownload_Click(object sender, RoutedEventArgs e)   
{  
    btnDownload.IsEnabled = false;  
    try  
    {  
        txtContents.Text = await m_webPages["http://www.microsoft.com"];  
    }  
    finally { btnDownload.IsEnabled = true; }  
}  
```  
  
### <a name="asyncproducerconsumercollection"></a>AsyncProducerConsumerCollection  
 Você também pode usar tarefas para compilar estruturas de dados para coordenar atividades assíncronas.  Considere um dos padrões de design paralelos clássicos: produtor/consumidor.  Nesse padrão, produtores geram dados que são consumidos pelos consumidores e produtores e consumidores podem executar em paralelo. Por exemplo, o consumidor processa o item 1, que anteriormente foi gerado por um produtor que agora está produzindo o item 2.  Para o padrão de produtor/consumidor, você precisa invariavelmente que alguma estrutura de dados armazene o trabalho criado pelos produtores para que os consumidores possam ser notificados sobre novos dados e localizá-los quando disponíveis.  
  
 Eis aqui uma estrutura de dados simples criada sobre tarefas que permitem que os métodos assíncronos sejam usados como produtores e consumidores:  
  
```csharp  
public class AsyncProducerConsumerCollection<T>  
{  
    private readonly Queue<T> m_collection = new Queue<T>();  
    private readonly Queue<TaskCompletionSource<T>> m_waiting =   
        new Queue<TaskCompletionSource<T>>();  
  
    public void Add(T item)  
    {  
        TaskCompletionSource<T> tcs = null;  
        lock (m_collection)  
        {  
            if (m_waiting.Count > 0) tcs = m_waiting.Dequeue();  
            else m_collection.Enqueue(item);  
        }  
        if (tcs != null) tcs.TrySetResult(item);  
    }  
  
    public Task<T> Take()  
    {  
        lock (m_collection)  
        {  
            if (m_collection.Count > 0)   
            {  
                return Task.FromResult(m_collection.Dequeue());   
            }  
            else   
            {  
                var tcs = new TaskCompletionSource<T>();  
                m_waiting.Enqueue(tcs);  
                return tcs.Task;  
            }  
        }  
    }  
}  
```  
  
 Com essa estrutura de dados estabelecida, você pode escrever código como o seguinte:  
  
```csharp  
private static AsyncProducerConsumerCollection<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.Take();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Add(data);  
}  
```  
  
 O <xref:System.Threading.Tasks.Dataflow> namespace inclui o <xref:System.Threading.Tasks.Dataflow.BufferBlock%601> tipo, que pode ser usado de maneira semelhante, mas sem a necessidade de criar um tipo de coleção personalizados:  
  
```csharp  
private static BufferBlock<int> m_data = …;  
…  
private static async Task ConsumerAsync()  
{  
    while(true)  
    {  
        int nextItem = await m_data.ReceiveAsync();  
        ProcessNextItem(nextItem);  
    }  
}  
…  
private static void Produce(int data)  
{  
    m_data.Post(data);  
}  
```  
  
> [!NOTE]
>  O <xref:System.Threading.Tasks.Dataflow> namespace está disponível na [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] por meio de **NuGet**. Para instalar o assembly que contém o <xref:System.Threading.Tasks.Dataflow> namespace, abra seu projeto no [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], escolha **gerenciar pacotes NuGet** no menu projeto e pesquise online o pacote TPL.  
  
## <a name="see-also"></a>Consulte também  
 [TAP (Padrão Assíncrono Baseado em Tarefa)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md)  
 [Implementando o padrão assíncrono baseado em tarefa](../../../docs/standard/asynchronous-programming-patterns/implementing-the-task-based-asynchronous-pattern.md)  
 [Interoperabilidade com outros tipos e padrões assíncronos](../../../docs/standard/asynchronous-programming-patterns/interop-with-other-asynchronous-patterns-and-types.md)
