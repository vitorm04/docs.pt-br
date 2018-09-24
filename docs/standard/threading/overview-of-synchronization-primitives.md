---
title: Visão geral dos primitivos de sincronização
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- synchronization, threads
- threading [.NET Framework],synchronizing threads
- managed threading
ms.assetid: b782bcb8-da6a-4c6a-805f-2eb46d504309
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 37abcb6b3a8fdf4ef91d5e946a97db7ca1428ce8
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2018
ms.locfileid: "46532727"
---
# <a name="overview-of-synchronization-primitives"></a>Visão geral dos primitivos de sincronização
<a name="top"></a>O .NET Framework fornece uma variedade de primitivos de sincronização para controlar as interações de threads e evitar condições de corrida. Eles podem ser divididos em três categorias: operações interliconectadas, sinalização e bloqueio.  
  
 As categorias não estão claramente definidas nem organizadas. Alguns mecanismos de sincronização têm características de várias categorias; eventos que liberam um único thread em um momento são funcionalmente como bloqueios; a versão de qualquer bloqueio pode ser considerada como um sinal; e operações interconectadas podem ser usadas para construir bloqueios. No entanto, as categorias ainda são úteis.  
  
 É importante lembrar que a sincronização de threads é cooperativa. Se um thread ignora um mecanismo de sincronização e acessa diretamente o recurso protegido, esse mecanismo de sincronização não pode ser eficaz.  
  
 Esta visão geral contém as seguintes seções:  
  
-   [Bloqueio](#locking)  
  
-   [Sinalização](#signaling)  
  
-   [Tipos de sincronização leve](#lightweight_synchronization_types)  
  
-   [SpinWait](#spinwait)  
  
-   [Operações interconectadas](#interlocked_operations)  
  
<a name="locking"></a>   
## <a name="locking"></a>Bloqueio  
 Bloqueios oferecem controle de um recurso para um thread por vez, ou para um número especificado de threads. Um thread que solicita um bloqueio exclusivo quando o bloqueio está sendo usado permanece bloqueado até o bloqueio ficar disponível.  
  
### <a name="exclusive-locks"></a>Bloqueios exclusivos  
 A forma mais simples de bloqueio é a instrução `lock` em C# e a instrução `SyncLock` no Visual Basic, que controla o acesso a um bloco de código. Tal bloco é normalmente chamado de seção crítica. A instrução `lock` é implementada usando os métodos <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> e <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType>, e usa um bloco `try…finally` para garantir que o bloqueio será liberado.  
  
 Em geral, usar a instrução `lock` ou `SyncLock` para proteger pequenos blocos de código, sem nunca abranger mais de um único método, é a melhor maneira de usar a classe <xref:System.Threading.Monitor>. Embora poderosa, a classe <xref:System.Threading.Monitor> é propensa a deadlocks e a bloqueios órfãos.  
  
#### <a name="monitor-class"></a>Classe Monitor  
 A classe <xref:System.Threading.Monitor> fornece funcionalidade adicional, que pode ser usada em conjunto com a instrução `lock`:  
  
-   O método <xref:System.Threading.Monitor.TryEnter%2A> permite que um thread que está bloqueado aguardando o recurso desista após um intervalo especificado. Ele retorna um valor booliano que indica êxito ou falha, que pode ser usado para detectar e evitar deadlocks potenciais.  
  
-   O método <xref:System.Threading.Monitor.Wait%2A> é chamado por um thread em uma seção crítica. Ele fornece controle de recursos e blocos até que o recurso esteja disponível novamente.  
  
-   Os métodos <xref:System.Threading.Monitor.Pulse%2A> e <xref:System.Threading.Monitor.PulseAll%2A> permitem que um thread que está prestes a liberar o bloqueio ou a chamar <xref:System.Threading.Monitor.Wait%2A> coloque um ou mais threads na fila de pronto para que eles possam adquirir o bloqueio.  
  
 Os tempos limite de sobrecargas do método <xref:System.Threading.Monitor.Wait%2A> permitem que os threads em espera pulem para a fila de pronto.  
  
 A classe <xref:System.Threading.Monitor> pode fornecer o bloqueio em vários domínios de aplicativo se o objeto usado para o bloqueio for derivado de <xref:System.MarshalByRefObject>.  
  
 <xref:System.Threading.Monitor> tem afinidade de thread. Ou seja, um thread que inseriu o monitor deve sair chamando <xref:System.Threading.Monitor.Exit%2A> ou <xref:System.Threading.Monitor.Wait%2A>.  
  
 A classe <xref:System.Threading.Monitor> não está instanciada. Seus métodos são estáticos (`Shared` no Visual Basic) e afetam um objeto de bloqueio que pode ser instanciado.  
  
 Para obter uma visão conceitual, consulte [Monitores](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db).  
  
#### <a name="mutex-class"></a>Classe Mutex  
 Os threads solicitam um <xref:System.Threading.Mutex> chamando uma sobrecarga de seu método <xref:System.Threading.WaitHandle.WaitOne%2A>. Sobrecargas com tempos limite são fornecidas para permitir que os threads desistam da espera. Ao contrário da classe <xref:System.Threading.Monitor>, um mutex pode ser local ou global. Global mutexes, também chamados de mutexes nomeados, são visíveis em todo o sistema operacional e podem ser usados para sincronizar threads em vários domínios de aplicativos ou processos. Os mutexes locais derivam de <xref:System.MarshalByRefObject> e podem ser usados nos limites do domínio de aplicativo.  
  
 Além disso, <xref:System.Threading.Mutex> deriva de <xref:System.Threading.WaitHandle> e isso significa que ele pode ser usado com os mecanismos de sinalização fornecidos pelo <xref:System.Threading.WaitHandle>, como os métodos <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A> e <xref:System.Threading.WaitHandle.SignalAndWait%2A>.  
  
 Como <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> tem afinidade de thread. Ao contrário de <xref:System.Threading.Monitor>, um <xref:System.Threading.Mutex> é um objeto que pode ser instanciado.  
  
 Para obter uma visão conceitual, consulte [Mutexes](../../../docs/standard/threading/mutexes.md).  
  
#### <a name="spinlock-class"></a>Classe de SpinLock  
 Começando com o [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], você pode usar a classe <xref:System.Threading.SpinLock> quando a sobrecarga exigida por <xref:System.Threading.Monitor> prejudicar o desempenho. Quando <xref:System.Threading.SpinLock> encontra uma seção crítica bloqueada, ele simplesmente gira em um loop até o bloqueio ficar disponível. Se o bloqueio for mantido por um período muito curto, a rotação pode fornecer melhor desempenho do que o bloqueio. No entanto, se o bloqueio for mantido por mais de algumas dezenas de ciclos, o <xref:System.Threading.SpinLock> terá um desempenho tão bom quanto o <xref:System.Threading.Monitor>, mas usará mais ciclos de CPU e, portanto, poderá prejudicar o desempenho de outros processos ou threads.  
  
### <a name="other-locks"></a>Outros bloqueios  
 Os bloqueios não precisam ser exclusivos. Normalmente é útil permitir que um número limitado de threads acesse simultaneamente um recurso. Semaphores e bloqueios de leitor-gravador são criados para controlar esse tipo de acesso a recursos em pool.  
  
#### <a name="readerwriterlock-class"></a>Classe ReaderWriterLock  
 A classe <xref:System.Threading.ReaderWriterLockSlim> aborda o caso em que um thread que altera os dados, o gravador, deve ter acesso exclusivo a um recurso. Quando o gravador não está ativo, qualquer número de leitores pode acessar o recurso (por exemplo, ao chamar o método <xref:System.Threading.ReaderWriterLockSlim.EnterReadLock%2A>). Quando um thread solicita acesso exclusivo (por exemplo, ao chamar o método <xref:System.Threading.ReaderWriterLockSlim.EnterWriteLock%2A>), o leitor subsequente solicita o bloqueio até que todos os leitores existentes tenham saído do bloqueio e o gravador tenha entrado e saído do bloqueio.  
  
 <xref:System.Threading.ReaderWriterLockSlim> tem afinidade de thread.  
  
 Para obter uma visão conceitual, consulte [Bloqueios de leitor-gravador](../../../docs/standard/threading/reader-writer-locks.md).  
  
#### <a name="semaphore-class"></a>Classe Semaphore  
 A classe <xref:System.Threading.Semaphore> permite que um número especificado de threads acesse um recurso. Threads adicionais solicitam o bloqueio de um recurso até que um thread libere o semaphore.  
  
 Como a classe <xref:System.Threading.Mutex>, <xref:System.Threading.Semaphore> deriva de <xref:System.Threading.WaitHandle>. Além disso, como <xref:System.Threading.Mutex>, um <xref:System.Threading.Semaphore> pode ser local ou global. Ele pode ser usado nos limites do domínio de aplicativo.  
  
 Ao contrário de <xref:System.Threading.Monitor>, <xref:System.Threading.Mutex> e <xref:System.Threading.ReaderWriterLock>, <xref:System.Threading.Semaphore> não tem afinidade de thread. Isso significa que ele pode ser usado em cenários onde um thread adquire o semaphore e o outro o libera.  
  
 Para obter uma visão conceitual, consulte [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md).  
  
 <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> é um sinal leve para sincronização no limite de um único processo.  
  
 [Voltar ao início](#top)  
  
<a name="signaling"></a>   
## <a name="signaling"></a>Sinalização  
 A maneira mais simples de esperar por um sinal de outro thread é chamando o método <xref:System.Threading.Thread.Join%2A> que é bloqueado até o outro thread ser concluído. <xref:System.Threading.Thread.Join%2A> tem duas sobrecargas que permitem que o thread bloqueado interrompa a espera após um intervalo especificado.  
  
 Identificadores de espera fornecem um conjunto mais avançado de recursos de espera e sinalização.  
  
### <a name="wait-handles"></a>Identificadores de espera  
 Os identificadores de espera derivam da classe <xref:System.Threading.WaitHandle> que, por sua vez, deriva de <xref:System.MarshalByRefObject>. Assim, os identificadores de espera podem ser usados para sincronizar as atividades de threads entre limites de domínio de aplicativo.  
  
 Os threads bloqueiam os identificadores de espera chamando o método de instância <xref:System.Threading.WaitHandle.WaitOne%2A> ou um dos métodos estáticos <xref:System.Threading.WaitHandle.WaitAll%2A>, <xref:System.Threading.WaitHandle.WaitAny%2A> ou <xref:System.Threading.WaitHandle.SignalAndWait%2A>. Como eles são liberados depende de qual método foi chamado e do tipo de identificadores de espera.  
  
 Para obter uma visão conceitual, consulte [Identificadores de espera](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489).  
  
#### <a name="event-wait-handles"></a>Identificadores de espera de eventos  
 Os identificadores de espera de eventos incluem a classe <xref:System.Threading.EventWaitHandle> e suas classes derivadas, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent>. Os threads são liberados de um identificador de espera de eventos quando ele é sinalizado, chamando seu método <xref:System.Threading.EventWaitHandle.Set%2A> ou usando o método <xref:System.Threading.WaitHandle.SignalAndWait%2A>.  
  
 Os identificadores de espera de eventos são automaticamente redefinidos, como uma borboleta que permite que apenas um thread seja sinalizado de cada vez, ou deverão ser redefinidos manualmente, como uma entrada que é fechada até ser sinalizada e, em seguida, aberta até que alguém a feche. Como seus nomes sugerem, <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent> representam o primeiro e último, respectivamente. <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> é um evento leve para sincronização no limite de um único processo.  
  
 Um <xref:System.Threading.EventWaitHandle> pode representar qualquer tipo de evento e pode ser local ou global. As classes derivadas <xref:System.Threading.AutoResetEvent> e <xref:System.Threading.ManualResetEvent> são sempre locais.  
  
 Identificadores de espera de eventos não têm afinidade de thread. Qualquer thread pode sinalizar um identificador de espera de eventos.  
  
 Para uma visão conceitual, consulte [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md).  
  
#### <a name="mutex-and-semaphore-classes"></a>Classes Mutex e Semaphore  
 Como as classes <xref:System.Threading.Mutex> e <xref:System.Threading.Semaphore> derivam de <xref:System.Threading.WaitHandle>, elas podem ser usadas com os métodos estáticos de <xref:System.Threading.WaitHandle>. Por exemplo, um thread pode usar o método <xref:System.Threading.WaitHandle.WaitAll%2A> para aguardar até que todas as três condições a seguir forem verdadeiras: um <xref:System.Threading.EventWaitHandle> é sinalizado, um <xref:System.Threading.Mutex> é liberado e um <xref:System.Threading.Semaphore> é liberado. Da mesma forma, um thread pode usar o método <xref:System.Threading.WaitHandle.WaitAny%2A> para aguardar até que qualquer uma dessas condições seja verdadeira.  
  
 No caso de um <xref:System.Threading.Mutex> ou de um <xref:System.Threading.Semaphore>, ser sinalizado significa ser liberado. Se o tipo for usado como o primeiro argumento do método <xref:System.Threading.WaitHandle.SignalAndWait%2A>, ele será liberado. No caso de um <xref:System.Threading.Mutex>, que tem afinidade de thread, uma exceção será gerada se o thread de chamada não possuir o mutex. Conforme observado anteriormente, os semaphores não têm afinidade de thread.  
  
#### <a name="barrier"></a>Barreira  
 A classe <xref:System.Threading.Barrier> fornece uma maneira de sincronizar, de forma cíclica, vários threads para que todos sejam bloqueados no mesmo ponto e aguardem a conclusão dos outros threads. Uma barreira é útil quando um ou mais threads requerem os resultados de outro thread para poderem prosseguir para a próxima fase de um algoritmo. Para saber mais, consulte [Barreira](../../../docs/standard/threading/barrier.md).  
  
 [Voltar ao início](#top)  
  
<a name="lightweight_synchronization_types"></a>   
## <a name="lightweight-synchronization-types"></a>Tipos de sincronização leve  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], você pode usar primitivos de sincronização que fornecem desempenho rápido, evitando a dispendiosa dependência de objetos do kernel do Win32, como identificadores de espera, sempre que possível. Em geral, você deve usar esses tipos quando os tempos de espera são curtos e somente quando os tipos de sincronização originais foram usados e considerados insatisfatórios. Os tipos leves não podem ser usados em cenários que exigem a comunicação entre processos.  
  
-   <xref:System.Threading.SemaphoreSlim?displayProperty=nameWithType> é uma versão leve de <xref:System.Threading.Semaphore?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType> é uma versão leve de <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType>.  
  
-   <xref:System.Threading.CountdownEvent?displayProperty=nameWithType> representa um evento que é sinalizado quando a contagem é zero.  
  
-   <xref:System.Threading.Barrier?displayProperty=nameWithType> permite que vários threads sincronizem entre si sem exigir o controle de um thread mestre. Uma barreira impede cada thread de continuar até que todos os threads atinjam um ponto especificado.  
  
 [Voltar ao início](#top)  
  
<a name="spinwait"></a>   
## <a name="spinwait"></a>SpinWait  
 Começando com o [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], você pode usar a estrutura de <xref:System.Threading.SpinWait?displayProperty=nameWithType> quando um thread tiver de esperar pela sinalização de um evento ou por uma condição específica. No entanto, quando o tempo de espera real for menor do que o tempo necessário, use um identificador de espera ou bloqueie o thread atual. Usando o <xref:System.Threading.SpinWait>, você pode especificar um curto período de tempo para girar enquanto espera e, em seguida, gerar (por exemplo, aguardando ou em espera) somente se a condição não for atendida no tempo especificado.  
  
 [Voltar ao início](#top)  
  
<a name="interlocked_operations"></a>   
## <a name="interlocked-operations"></a>Operações interconectadas  
 As operações interconectadas são operações atômicas simples realizadas em um local de memória por métodos estáticos da classe <xref:System.Threading.Interlocked>. Essas operações atômicas incluem adição, incremento e decremento, troca, troca condicional (dependendo de uma comparação) e operações de leitura de valores de 64 bits em plataformas de 32 bits.  
  
> [!NOTE]
>  A garantia de atomicidade é limitada às operações individuais; quando várias operações devem ser executadas como uma unidade, um mecanismo de sincronização da mais alta granularidade deve ser usado.  
  
 Embora nenhuma dessas operações sejam bloqueios ou sinais, eles podem ser usadas para construir sinais e bloqueios. Como são nativas do sistema operacional Windows, as operações interconectadas são extremamente rápidas.  
  
 Operações interconectadas podem ser usadas com garantias de memória volátil para gravar aplicativos que apresentam simultaneidade eficiente sem bloqueio. No entanto, elas exigem programação sofisticada, de baixo nível, para a maioria das finalidades, portanto, bloqueios simples são uma opção melhor.  
  
 Para obter uma visão conceitual, consulte [Operações interconectadas](../../../docs/standard/threading/interlocked-operations.md).  
  
## <a name="see-also"></a>Consulte também

- [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [Monitores](https://msdn.microsoft.com/library/33fe4aef-b44b-42fd-9e72-c908e39e75db)  
- [Mutexes](../../../docs/standard/threading/mutexes.md)  
- [Semaphore e SemaphoreSlim](../../../docs/standard/threading/semaphore-and-semaphoreslim.md)  
- [EventWaitHandle, AutoResetEvent, CountdownEvent, ManualResetEvent](../../../docs/standard/threading/eventwaithandle-autoresetevent-countdownevent-manualresetevent.md)  
- [Identificadores de espera](https://msdn.microsoft.com/library/48d10b6f-5fd7-407c-86ab-0179aef72489)  
- [Operações interconectadas](../../../docs/standard/threading/interlocked-operations.md)  
- [Bloqueios de leitor-gravador](../../../docs/standard/threading/reader-writer-locks.md)  
- [Barreira](../../../docs/standard/threading/barrier.md)  
- [SpinWait](../../../docs/standard/threading/spinwait.md)  
- [SpinLock](../../../docs/standard/threading/spinlock.md)
