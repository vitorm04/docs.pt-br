---
title: "Sincroniza&#231;&#227;o de thread (c#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: e42b1be6-c93c-479f-a148-be0759f1a4e1
caps.latest.revision: 3
caps.handback.revision: 3
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Sincroniza&#231;&#227;o de thread (c#)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

As seções a seguir descrevem os recursos e classes que podem ser usados para sincronizar o acesso a recursos em aplicativos multithread.  
  
 Um dos benefícios do uso de vários threads em um aplicativo é que cada thread executa de forma assíncrona. Para aplicativos do Windows, isso permite tarefas demoradas ser executada em segundo plano enquanto a janela do aplicativo e os controles permaneçam responsivos. Servidor de aplicativos, multithreading fornece a capacidade de lidar com cada solicitação de entrada com um thread diferente. Caso contrário, cada nova solicitação não obter atendida antes que a solicitação anterior tinha sido totalmente satisfeita.  
  
 No entanto, a natureza assíncrona dos meios de threads que o acesso aos recursos, como identificadores de arquivos, conexões de rede e memória deve ser coordenada. Caso contrário, dois ou mais threads podem acessar o mesmo recurso ao mesmo tempo, cada ciente das ações do outro. O resultado é a corrupção de dados imprevisível.  
  
 Para operações simples em tipos de dados numéricos integral, o sincronização de threads pode ser realizado com membros de <xref:System.Threading.Interlocked> classe. Para todos os outros dados de tipos e recursos não thread\-safe, multithreading só podem ser com segurança executados usando as construções neste tópico.  
  
 Para obter informações sobre a programação multithreaded, consulte:  
  
-   [Noções básicas de threading gerenciado](../Topic/Managed%20Threading%20Basics.md)  
  
-   [Usando threads e threading](../Topic/Using%20Threads%20and%20Threading.md)  
  
-   [Práticas recomendadas de threading gerenciado](../Topic/Managed%20Threading%20Best%20Practices.md)  
  
## A palavra\-chave de bloqueio  
 O c\# `lock` instrução pode ser usada para garantir que um bloco de código seja executada até a conclusão sem interrupção por outros threads. Isso é feito obtendo um bloqueio de exclusão mútua para um determinado objeto para a duração do bloco de código.  
  
 Um `lock` instrução é dado um objeto como um argumento e é seguida por um bloco de código que deve ser executado por apenas um thread por vez. Por exemplo:  
  
```c#  
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
  
 O argumento fornecido para o `lock` palavra\-chave deve ser um objeto com base em um tipo de referência e é usado para definir o escopo do bloqueio. No exemplo acima, o escopo de bloqueio é limitado para essa função porque nenhuma referência ao objeto `lockThis` existir fora da função. Se tal referência existisse, escopo de bloqueio se estende para o objeto. Estritamente falando, o objeto fornecido é usado exclusivamente para identificar exclusivamente o recurso seja compartilhado entre vários threads, assim ela pode ser uma instância da classe arbitrário. Na prática, no entanto, esse objeto normalmente representa o recurso para o qual o segmento de sincronização é necessária. Por exemplo, se um objeto contêiner deve ser usado por vários threads, em seguida, o contêiner pode ser passado para bloquear e bloco sincronizado após o bloqueio poderia acessar o contêiner. Enquanto outros threads bloqueia no mesmo conter para acessá\-lo, e com segurança o acesso ao objeto é sincronizado.  
  
 Geralmente, é melhor evitar o bloqueio em um `public` tipo, ou em instâncias de objeto além do controle do seu aplicativo. Por exemplo, `lock(this)` pode ser problemático se a instância pode ser acessada publicamente, porque o código fora de seu controle, poderá bloquear o objeto. Isso pode criar situações de deadlock, onde dois ou mais threads esperam para a versão do mesmo objeto. O bloqueio em um tipo de dados públicos, em vez de um objeto, pode causar problemas pelo mesmo motivo. O bloqueio em cadeias de caracteres literal é arriscado especialmente como cadeias de caracteres literais são *interned* pelo common language runtime \(CLR\). Isso significa que há uma instância de determinada cadeia de caracteres literal para todo o programa, o mesmo objeto exato representa o literal em todas executando domínios de aplicativo, em todos os threads. Como resultado, um bloqueio colocado em uma cadeia de caracteres com o mesmo conteúdo em qualquer lugar em que os bloqueios de processo do aplicativo todas as instâncias dessa cadeia de caracteres no aplicativo. Como resultado, é melhor bloquear um membro particular ou protegido que não é interned. Algumas classes fornecem aos membros especificamente para o bloqueio. O <xref:System.Array> tipo, por exemplo, fornece <xref:System.Array.SyncRoot%2A>. Muitos tipos de coleção fornecem um `SyncRoot` membro também.  
  
 Para obter mais informações sobre o `lock` instrução, consulte os seguintes tópicos:  
  
-   [Instrução lock](../../../../csharp/language-reference/keywords/lock-statement.md)  
  
-   [Monitores](../Topic/Monitors.md)  
  
## Monitores  
 Como o `lock` palavra\-chave, monitores impedir blocos de código de execução simultaneamente por vários threads. O <xref:System.Threading.Monitor.Enter%2A> método permite que apenas um thread prosseguir para as seguintes instruções; todos os outros threads são bloqueados até que as chamadas do thread executando <xref:System.Threading.Monitor.Exit%2A>. Isso é como usar o `lock` palavra\-chave. Por exemplo:  
  
```c#  
lock (x)  
{  
    DoSomething();  
}  
```  
  
 Isso é equivalente a:  
  
```c#  
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
  
 Usando o `lock`palavra\-chave é geralmente preferível usar o <xref:System.Threading.Monitor> classe diretamente, ambos, porque `lock` é mais conciso e porque `lock` assegura que o monitor subjacente é liberado, mesmo que o código protegido lança uma exceção. Isso é feito com o `finally` palavra\-chave, que executa o bloco de código associado independentemente se uma exceção é lançada.  
  
## Eventos de sincronização e identificadores de espera  
 Usar um monitor ou um bloqueio é útil para evitar a execução simultânea de thread diferencia blocos de código, mas essas construções não permitem que um thread para se comunicar um evento para outro. Isso requer *eventos de sincronização*, que são objetos que possuem um de dois estados, signaled e não sinalizado, que pode ser usado para ativar e suspender os threads. Segmentos podem ser suspensa por sendo feitas para aguardar um evento de sincronização é sinalizado e podem ser ativados pela alteração do estado do evento para sinalizar. Se um thread tentar aguardar um evento que já é sinalizado, em seguida, o segmento continua a executar sem atraso.  
  
 Há dois tipos de eventos de sincronização: <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.ManualResetEvent>. Eles diferem apenas em que <xref:System.Threading.AutoResetEvent> as alterações do sinalizado para sinalizado automaticamente sempre que ele ativa um thread. Por outro lado, um <xref:System.Threading.ManualResetEvent> permite que qualquer número de threads para ser ativado por estado sinalizado e só será revertido para um sinalizado estado quando seu <xref:System.Threading.EventWaitHandle.Reset%2A> método é chamado.  
  
 Threads podem ser feitos para esperar por eventos chamando um dos métodos de espera, como <xref:System.Threading.WaitHandle.WaitOne%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A>, ou <xref:System.Threading.WaitHandle.WaitAll%2A>.<xref:System.Threading.WaitHandle.WaitOne%2A?displayProperty=fullName> faz com que o thread a esperar até que um único evento se torna sinalizado, <xref:System.Threading.WaitHandle.WaitAny%2A?displayProperty=fullName> bloqueia um thread até que um ou mais eventos indicados tornou\-se sinalizado, e <xref:System.Threading.WaitHandle.WaitAll%2A?displayProperty=fullName> bloqueia o thread até que todos os eventos indicados tornou\-se sinalizado. Um evento se torna sinalizado quando seu <xref:System.Threading.EventWaitHandle.Set%2A> método é chamado.  
  
 No exemplo a seguir, um thread é criado e iniciado pelo `Main` função. O novo thread aguarda em um evento usando o <xref:System.Threading.WaitHandle.WaitOne%2A> método. O thread está suspenso até que o evento torna\-se sinalizado pelo thread principal que está executando o `Main` função. Depois que o evento torna\-se sinalizado, retorna o thread auxiliar. Nesse caso, como o evento só é usado para ativação de um thread, ou o <xref:System.Threading.AutoResetEvent> ou <xref:System.Threading.ManualResetEvent> classes pode ser usadas.  
  
```c#  
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
  
## Objeto mutex  
 Um *mutex* é semelhante a um monitor; ele impede a execução simultânea de um bloco de código por mais de um thread por vez. Na verdade, o nome "mutex" é uma forma abreviada do termo "mutuamente". Ao contrário dos monitores, no entanto, um mutex pode ser usado para sincronizar threads entre processos. Um mutex é representado pela <xref:System.Threading.Mutex> classe.  
  
 Quando usado para sincronização entre processos, um mutex é chamado um *mutex denominado* porque ele deve ser usado em outro aplicativo e, portanto, não podem ser compartilhado por meio de uma variável global ou estática. Ele deve ser dado um nome para que ambos os aplicativos podem acessar o mesmo objeto de mutex.  
  
 Embora um mutex pode ser usado para sincronização de threads de processo interno, usando <xref:System.Threading.Monitor> é geralmente preferível, pois os monitores foram projetados especificamente para o .NET Framework e, portanto, fazer melhor uso de recursos. Por outro lado, a <xref:System.Threading.Mutex> classe é um wrapper para uma construção de Win32. Embora seja mais eficiente do que um monitor, um mutex requer transições de interoperabilidade que são mais dispendiosa computacionalmente daqueles necessários para a <xref:System.Threading.Monitor> classe. Para obter um exemplo de como usar um mutex, consulte [Mutexes](../Topic/Mutexes.md).  
  
## Classe Interlocked  
 Você pode usar os métodos de <xref:System.Threading.Interlocked> classe para evitar problemas que podem ocorrer quando vários segmentos tentarem simultaneamente atualizar ou comparar o mesmo valor. Os métodos dessa classe permitem que você com segurança incremento, decremento, exchange e comparam valores de qualquer thread.  
  
## Bloqueios ReaderWriter  
 Em alguns casos, você talvez queira bloquear um recurso somente quando os dados estão sendo gravados e permitir que vários clientes simultaneamente leiam os dados quando dados não está sendo atualizados. O <xref:System.Threading.ReaderWriterLock> classe garante o acesso exclusivo a um recurso enquanto um segmento está modificando o recurso, mas ele permite acesso não\-exclusivo ao ler o recurso. Bloqueios ReaderWriter são uma alternativa útil para bloqueios exclusivos que causam outros segmentos para esperar, mesmo quando esses threads não é necessário atualizar os dados.  
  
## Deadlocks  
 Sincronização de thread não é válida em aplicativos multissegmentados, mas há sempre o perigo de criação de um `deadlock`, onde vários segmentos estão aguardando um pelo outro e o aplicativo chega a uma interrupção. Um deadlock é análogo a uma situação na qual carros são interrompidos em uma parada de quatro vias e cada pessoa está aguardando a outra para ir. Evitar deadlocks é importante; a chave é um planejamento cuidadoso. Geralmente você pode prever situações de bloqueio por diagramação de aplicativos multissegmentados antes de iniciar a codificação.  
  
## Consulte também  
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
 [Aplicativos multithread \(c\#\)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Instrução lock](../../../../csharp/language-reference/keywords/lock-statement.md)   
 [Mutexes](../Topic/Mutexes.md)   
 [Monitores](../Topic/Monitors.md)   
 [Operações interconectadas](../Topic/Interlocked%20Operations.md)   
 [AutoResetEvent](../Topic/AutoResetEvent.md)   
 [Sincronizando dados para multithreading](../Topic/Synchronizing%20Data%20for%20Multithreading.md)