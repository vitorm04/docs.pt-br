---
title: Sincronização de thread (C#)
ms.date: 07/20/2015
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
ms.openlocfilehash: 138b94ef8ae5fc54e42277127f9b22f88803457f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="thread-synchronization-c"></a>Sincronização de thread (C#)
As seções a seguir descrevem recursos e classes que podem ser usados para sincronizar o acesso a recursos em aplicativos multi-threaded.  
  
 Um dos benefícios do usar vários threads em um aplicativo é que cada thread é executado de forma assíncrona. Para aplicativos do Windows, isso permite que tarefas demoradas sejam executadas em segundo plano enquanto a janela e os controles do aplicativo permanecem responsivos. Para aplicativos de servidor, o multithreading possibilita lidar com cada solicitação de entrada com um thread diferente. Caso contrário, cada nova solicitação não seria atendida antes que a solicitação anterior fosse totalmente satisfeita.  
  
 No entanto, a natureza assíncrona dos threads significa que o acesso a recursos, como identificadores de arquivos, conexões de rede e memória, deve ser coordenado. Caso contrário, dois ou mais threads poderiam acessar o mesmo recurso ao mesmo tempo, cada um deles sem conhecimento das ações do outro. O resultado são dados corrompidos de forma imprevisível.  
  
 Para operações simples em tipos de dados numéricos integrais, os threads de sincronização podem ser realizados com membros da classe <xref:System.Threading.Interlocked>. Para todos os outros tipos de dados e recursos não thread-safe, o multithreading só pode ser realizado com segurança usando os constructos neste tópico.  
  
 Para obter informações gerais sobre a programação multi-threaded, consulte:  
  
-   [Noções básicas de threading gerenciado](../../../../standard/threading/managed-threading-basics.md)  
  
-   [Usando threads e threading](../../../../standard/threading/using-threads-and-threading.md)  
  
-   [Práticas recomendadas de threading gerenciado](../../../../standard/threading/managed-threading-best-practices.md)  
  
## <a name="the-lock-keyword"></a>A palavra-chave lock  
 A instrução `lock` de C# pode ser usada para garantir que um bloco de código seja executado até a conclusão sem interrupção por outros threads. Isso é feito obtendo um bloqueio de exclusão mútua para um determinado objeto pela duração do bloco de código.  
  
 Uma instrução `lock` recebe um objeto como argumento e é seguida por um bloco de código que deve ser executado por apenas um thread por vez. Por exemplo:  
  
```csharp  
public class TestThreading  
{  
    private System.Object lockThis = new System.Object();  
  
    public void Process()  
    {  
  
        lock (lockThis)  
        {  
            // Access thread-sensitive resources.  
        }  
    }  
  
}  
```  
  
 O argumento fornecido à palavra-chave `lock` deve ser um objeto baseado em um tipo de referência e é usado para definir o escopo do bloqueio. No exemplo acima, o escopo do bloqueio é limitado a essa função porque não há referências ao objeto `lockThis` fora da função. Se tal referência existisse, o escopo do bloqueio se estenderia a esse objeto. Falando rigorosamente, o objeto fornecido é usado apenas para identificar de forma exclusiva o recurso compartilhado entre vários threads, então ele pode ser uma instância de classe arbitrária. Na prática, no entanto, esse objeto normalmente representa o recurso para o qual a sincronização de threads é necessária. Por exemplo, se um objeto de contêiner for usado por vários threads, o contêiner poderá ser passado para o bloqueio e o bloco de código sincronizado após o bloqueio acessaria o contêiner. Desde que outros threads bloqueiem o mesmo contêiner antes de acessá-lo, o acesso ao objeto é sincronizado com segurança.  
  
 Geralmente, é melhor evitar bloquear um tipo `public` ou instâncias de objeto além do controle do seu aplicativo. Por exemplo, `lock(this)` pode ser problemático se a instância puder ser acessada publicamente, porque o código fora do seu controle também poderá bloquear o objeto. Isso pode criar situações de deadlock, em que dois ou mais threads esperam a liberação do mesmo objeto. Bloquear um tipo de dados público, em vez de um objeto, pode causar problemas pelo mesmo motivo. Bloquear cadeias de caracteres literais é especialmente arriscado porque cadeias de caracteres literais são *internos* ao CLR (Common Language Runtime). Isso significa que há uma instância de um determinado literal de cadeia de caracteres para todo o programa, o mesmo objeto exato representa o literal em todos os domínios de aplicativo em execução, em todos os threads. Como resultado, um bloqueio colocado em uma cadeia de caracteres com o mesmo conteúdo em qualquer parte do processo do aplicativo bloqueia todas as instâncias dessa cadeia de caracteres no aplicativo. Sendo assim, é melhor bloquear um membro particular ou protegido que não é interno. Algumas classes fornecem membros especificamente para o bloqueio. O tipo <xref:System.Array>, por exemplo, fornece <xref:System.Array.SyncRoot%2A>. Muitos tipos de coleção fornecem também fornecem um membro `SyncRoot`.  
  
 Para obter mais informações sobre a instrução `lock`, consulte os tópicos a seguir:  
  
-   [Instrução lock](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   <xref:System.Threading.Monitor>  
  
## <a name="monitors"></a>Monitores  
 Assim como a palavra-chave `lock`, os monitores impedem que blocos de código sejam executados simultaneamente por vários threads. O método <xref:System.Threading.Monitor.Enter%2A> permite que apenas um thread prossiga para as instruções seguintes, todos os outros threads são bloqueados até que o thread em execução chame <xref:System.Threading.Monitor.Exit%2A>. É como usar a palavra-chave `lock`. Por exemplo:  
  
```csharp  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Isso é equivalente a:  
  
```csharp  
System.Object obj = (System.Object)x;  
System.Threading.Monitor.Enter(obj);  
try  
{  
    DoSomething();  
}  
finally  
{  
    System.Threading.Monitor.Exit(obj);  
}  
```  
  
 Usar a palavra-chave `lock` geralmente é preferível a usar a classe <xref:System.Threading.Monitor> diretamente, porque `lock` é mais conciso e porque `lock` garante que o monitor subjacente seja liberado, mesmo que o código protegido gere uma exceção. Isso é feito com a palavra-chave `finally`, que executa o bloco de código associado independentemente de uma exceção ser lançada.  
  
## <a name="synchronization-events-and-wait-handles"></a>Eventos de sincronização e identificadores de espera  
 Usar um monitor ou um bloqueio é útil para evitar a execução simultânea de blocos de código sensíveis ao thread, mas esses constructos não permitem que um thread comunique um evento a outro. Isso requer *eventos de sincronização*, que são objetos que têm um de dois estados, sinalizado e não sinalizado, que podem ser usados para ativar e suspender os threads. Threads podem ser suspensos tendo que aguardar um evento de sincronização não sinalizado e podem ser ativados alterando o estado do evento para sinalizado. Se um thread tentar aguardar um evento que já é sinalizado, então o thread continua sendo executado sem atraso.  
  
 Há dois tipos de eventos de sincronização: <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent>. A única diferença entre eles é que <xref:System.Threading.AutoResetEvent> muda de sinalizado para não sinalizado automaticamente sempre que ele ativar um thread. Por outro lado, um <xref:System.Threading.ManualResetEvent> permite que qualquer número de threads seja ativado por seu estado sinalizado e será revertido apenas para estado não sinalizado quando seu método <xref:System.Threading.EventWaitHandle.Reset%2A> for chamado.  
  
 É possível fazer os threads esperarem por eventos chamando um dos métodos de espera, como <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A> ou <xref:System.Threading.WaitHandle.WaitAll%2A>. <xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=nameWithType> faz com que o thread espere até que um único evento se torne sinalizado, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=nameWithType> bloqueia um thread até que um ou mais eventos indicados se tornem sinalizados e <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=nameWithType> bloqueia o thread até que todos os eventos indicados ser tornem sinalizados. Um evento se torna sinalizado quando seu método <xref:System.Threading.EventWaitHandle.Set%2A> é chamado.  
  
 No exemplo a seguir, um thread é criado e iniciado pela função `Main`. O novo thread aguarda um evento usando o método <xref:System.Threading.WaitHandle.WaitOne%2A>. O thread é suspenso até que o evento seja sinalizado pelo thread principal que está executando a função `Main`. Após o evento ser sinalizado, o thread auxiliar é retornado. Nesse caso, como o evento é usado apenas para uma ativação de thread, as classes <xref:System.Threading.AutoResetEvent> ou <xref:System.Threading.ManualResetEvent> podem ser usadas.  
  
```csharp  
using System;  
using System.Threading;  
  
class ThreadingExample  
{  
    static AutoResetEvent autoEvent;  
  
    static void DoWork()  
    {  
        Console.WriteLine("   worker thread started, now waiting on event...");  
        autoEvent.WaitOne();  
        Console.WriteLine("   worker thread reactivated, now exiting...");  
    }  
  
    static void Main()  
    {  
        autoEvent = new AutoResetEvent(false);  
  
        Console.WriteLine("main thread starting worker thread...");  
        Thread t = new Thread(DoWork);  
        t.Start();  
  
        Console.WriteLine("main thread sleeping for 1 second...");  
        Thread.Sleep(1000);  
  
        Console.WriteLine("main thread signaling worker thread...");  
        autoEvent.Set();  
    }  
}  
```  
  
## <a name="mutex-object"></a>Objeto mutex  
 Um *mutex* é semelhante a um monitor; ele impede a execução simultânea de um bloco de código por mais de um thread por vez. Na verdade, o nome "mutex" é uma forma abreviada do termo "mutuamente exclusivo". No entanto, diferente dos monitores, um mutex pode ser usado para sincronizar threads entre processos. Um mutex é representado pela classe <xref:System.Threading.Mutex>.  
  
 Quando usado para sincronização entre processos, um mutex é chamado de *mutex nomeado* porque deve ser usado em outro aplicativo e, portanto, não pode ser compartilhado por meio de uma variável global ou estática. Ele deve receber um nome para que ambos os aplicativos possam acessar o mesmo objeto de mutex.  
  
 Embora um mutex possa ser usado para sincronização de threads dentro do processo, o uso de <xref:System.Threading.Monitor> normalmente é preferível, pois os monitores foram criados especificamente para o .NET Framework e, portanto, utilizam melhor os recursos. Por outro lado, a classe <xref:System.Threading.Mutex> é um wrapper para um constructo de Win32. Embora seja mais eficiente do que um monitor, um mutex requer transições de interoperabilidade que são mais dispendiosas em termos computacionais do que aquelas necessárias para a classe <xref:System.Threading.Monitor>. Para obter um exemplo de como usar um mutex, consulte [Mutexes](../../../../standard/threading/mutexes.md).  
  
## <a name="interlocked-class"></a>Classe Interlocked  
 É possível usar os métodos da classe <xref:System.Threading.Interlocked> para evitar problemas que podem ocorrer quando vários threads tentam atualizar ou comparar simultaneamente o mesmo valor. Os métodos dessa classe permitem incrementar, decrementar, trocar e comparar de forma segura os valores de qualquer thread.  
  
## <a name="readerwriter-locks"></a>Bloqueios ReaderWriter  
 Em alguns casos, talvez você queira bloquear um recurso somente quando dados estiverem sendo gravados e permitir que vários clientes leiam simultaneamente os dados quando eles não estiverem sendo atualizados. A classe <xref:System.Threading.ReaderWriterLock> força o acesso exclusivo a um recurso enquanto um thread está modificando o recurso, mas permite acesso não exclusivo ao ler o recurso. Bloqueios ReaderWriter são uma alternativa útil a bloqueios exclusivos, fazem outros segmentos esperar, mesmo quando esses threads não precisam atualizar dados.  
  
## <a name="deadlocks"></a>Deadlocks  
 A sincronização de threads tem valor incalculável em aplicativos multi-threaded, mas sempre há o perigo de criar um `deadlock`, em que vários segmentos estão aguardando uns aos outros e o aplicativo é interrompido. Um deadlock é semelhante a uma situação em que carros estão parados em uma parada de quatro vias e cada pessoa está aguardando a outra prosseguir. Evitar deadlocks é importante; a chave é um planejamento cuidadoso. Geralmente, você pode prever situações de deadlock diagramando aplicativos multi-threaded antes de iniciar a codificação.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.Thread>  
 <xref:System.Threading.WaitHandle.WaitOne%2A>  
 <xref:System.Threading.WaitHandle.WaitAny%2A>  
 <xref:System.Threading.WaitHandle.WaitAll%2A>  
 <xref:System.Threading.Thread.Join%2A>  
 <xref:System.Threading.Thread.Start%2A>  
 <xref:System.Threading.Thread.Sleep%2A>  
 <xref:System.Threading.Monitor>  
 <xref:System.Threading.Mutex>  
 <xref:System.Threading.AutoResetEvent>  
 <xref:System.Threading.ManualResetEvent>  
 <xref:System.Threading.Interlocked>  
 <xref:System.Threading.WaitHandle>  
 <xref:System.Threading.EventWaitHandle>  
 <xref:System.Threading>  
 <xref:System.Threading.EventWaitHandle.Set%2A>  
 <xref:System.Threading.Monitor>  
 [Aplicativos com multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)  
 [Instrução lock](../../../../csharp/language-reference/keywords/lock-statement.md)  
 [Mutexes](../../../../standard/threading/mutexes.md)  
 [Operações interconectadas](../../../../standard/threading/interlocked-operations.md)  
 [AutoResetEvent](../../../../standard/threading/autoresetevent.md)  
 [Sincronizando dados para multithreading](../../../../standard/threading/synchronizing-data-for-multithreading.md)
