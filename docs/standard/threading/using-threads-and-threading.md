---
title: Usando threads e threading
ms.date: 08/08/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- threading [.NET Framework], about threading
- managed threading
ms.assetid: 9b5ec2cd-121b-4d49-b075-222cf26f2344
ms.openlocfilehash: 14159ff9a6ca39108aec14b0ad46004e95fa3cf2
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588428"
---
# <a name="using-threads-and-threading"></a>Usando threads e threading

Com o .NET, você pode escrever aplicativos que executam várias operações ao mesmo tempo. As operações com o potencial de atrasar outras operações podem ser executadas em threads separados, um processo conhecido como *multithreading* ou *free threading*.  
  
Aplicativos que usam multithreading são mais responsivos a entradas do usuário porque a interface do usuário permanece ativa, enquanto tarefas com uso intensivo do processador são executadas em threads separados. O multithreading também é útil quando você cria aplicativos escalonáveis, porque você pode adicionar threads conforme a carga de trabalho aumenta.

> [!NOTE]
> Se precisar de mais controle sobre o comportamento dos threads de seu aplicativo, você poderá gerenciar os threads por conta própria. No entanto, começando no .NET Framework 4, a programação multi-threaded ficou bastante simplificada com as classes <xref:System.Threading.Tasks.Parallel?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Task?displayProperty=nameWithType>, o [PLINQ (LINQ paralelo)](../parallel-programming/introduction-to-plinq.md), as novas classes de coleção simultânea no namespace <xref:System.Collections.Concurrent?displayProperty=nameWithType> e um novo modelo de programação que se baseia no conceito de tarefas e não em threads. Para obter mais informações, confira [Programação paralela](../parallel-programming/index.md) e [TPL (biblioteca de paralelismo de tarefas)](../parallel-programming/task-parallel-library-tpl.md).

## <a name="how-to-create-and-start-a-new-thread"></a>Como criar e iniciar um thread

Crie um thread criando uma nova instância da classe <xref:System.Threading.Thread?displayProperty=nameWithType> e fornecendo o nome do método que você deseja executar em um novo thread para o construtor. Para iniciar um thread criado, chame o método <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType>. Para obter mais informações e exemplos, confira o artigo [Criando threads e passando dados na hora de início](creating-threads-and-passing-data-at-start-time.md) e a referência da API <xref:System.Threading.Thread>.

## <a name="how-to-stop-a-thread"></a>Como interromper um thread

Para terminar a execução de <xref:System.Threading.CancellationToken?displayProperty=nameWithType>um segmento, use o . Ele fornece uma maneira unificada de parar os fios cooperativamente. Para saber mais, confira [Cancelamento em threads gerenciados](cancellation-in-managed-threads.md).

Às vezes não é possível parar um segmento cooperativamente, porque ele executa código de terceiros não projetado para cancelamento cooperativo. Neste caso, você pode querer terminar sua execução à força. Para encerrar a execução de um segmento à força, no .NET Framework você pode usar o <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> método. Esse método gera uma <xref:System.Threading.ThreadAbortException> no thread em que é invocado. Para obter mais informações, confira [Destruindo threads](destroying-threads.md). O <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> método não é suportado no .NET Core. Se você precisar encerrar a execução do código de terceiros à força no <xref:System.Diagnostics.Process.Kill%2A?displayProperty=nameWithType>.NET Core, execute-o no processo separado e use .

O <xref:System.Threading.CancellationToken?displayProperty=nameWithType> não está disponível antes do .NET Framework 4. Para parar um segmento nas versões mais antigas do .NET Framework, você deve implementar o cancelamento cooperativo manualmente usando as técnicas de sincronização de segmentos. Por exemplo, você pode criar `shouldStop` o campo booleano volátil e usá-lo para solicitar que o código executado pelo segmento pare. Para obter mais [volatile](../../csharp/language-reference/keywords/volatile.md) informações, consulte <xref:System.Threading.Volatile?displayProperty=nameWithType>volátil em C# Referência e .

Use <xref:System.Threading.Thread.Join%2A?displayProperty=nameWithType> o método para fazer com que o segmento de chamada aguarde o término do segmento sendo interrompido.

## <a name="how-to-pause-or-interrupt-a-thread"></a>Como pausar ou interromper um thread

Use o método <xref:System.Threading.Thread.Sleep%2A?displayProperty=nameWithType> para pausar o thread atual por um período de tempo especificado. Você pode interromper um thread bloqueado chamando o método <xref:System.Threading.Thread.Interrupt%2A?displayProperty=nameWithType>. Para obter mais informações, confira [Pausando e interrompendo threads](pausing-and-resuming-threads.md).

## <a name="thread-properties"></a>Propriedades do thread

A tabela a seguir apresenta algumas das propriedades do <xref:System.Threading.Thread>:  
  
|Propriedade|Descrição|  
|--------------|-----------|  
|<xref:System.Threading.Thread.IsAlive%2A>|Retorna `true` quando um thread foi iniciado e ainda não foi encerrado normalmente ou anulado.|  
|<xref:System.Threading.Thread.IsBackground%2A>|Obtém ou define um valor booliano que indica se um thread é um thread em segundo plano. Os threads em segundo plano são como threads em primeiro plano, mas um thread em segundo plano não impede que um processo pare. Após todos os threads de primeiro plano que pertencem a um processo serem parados, o Common Language Runtime finaliza o processo chamando o método <xref:System.Threading.Thread.Abort%2A> em threads em segundo plano que ainda estão ativos. Para obter mais informações, confira [Threads em primeiro plano e em segundo plano](foreground-and-background-threads.md).|  
|<xref:System.Threading.Thread.Name%2A>|Obtém ou define o nome de um thread. Usado com mais frequência para descobrir threads individuais quando você depura.|  
|<xref:System.Threading.Thread.Priority%2A>|Obtém ou define um valor de <xref:System.Threading.ThreadPriority> que é usado pelo sistema operacional para priorizar agendamentos de thread. Para obter mais informações, confira [Agendando threads](scheduling-threads.md) e a referência de <xref:System.Threading.ThreadPriority>.|  
|<xref:System.Threading.Thread.ThreadState%2A>|Obtém um valor <xref:System.Threading.ThreadState> que contém os estados atuais de um thread.|  

## <a name="see-also"></a>Confira também

- <xref:System.Threading.Thread?displayProperty=nameWithType>
- [Linhas e Roscas](threads-and-threading.md)
- [Programação Paralela](../parallel-programming/index.md)
