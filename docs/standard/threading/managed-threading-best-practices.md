---
title: "Práticas recomendadas de threading gerenciado"
ms.custom: 
ms.date: 11/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- threading [.NET Framework], design guidelines
- threading [.NET Framework], best practices
- managed threading
ms.assetid: e51988e7-7f4b-4646-a06d-1416cee8d557
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e396bb1f6a710e49e311ca1526a7aae9bca7bf90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="managed-threading-best-practices"></a>Práticas recomendadas de threading gerenciado
Multithreading requer programação cuidadosa. Para a maioria das tarefas, você pode reduzir a complexidade por solicitações de enfileiramento de mensagens para execução por threads de pool. Este tópico aborda as situações mais difíceis, como coordenar o trabalho de vários threads ou manipular threads esse bloco.  
  
> [!NOTE]
> Começando com o .NET Framework 4, a biblioteca de tarefas paralelas e em PLINQ fornecem APIs que reduza alguns a complexidade e os riscos de programação multithread. Para obter mais informações, consulte [programação paralela no .NET](../../../docs/standard/parallel-programming/index.md).  
  
## <a name="deadlocks-and-race-conditions"></a>Deadlocks e condições de corrida  
 Multithreading soluciona problemas com a taxa de transferência e a capacidade de resposta, mas isso introduz novos problemas: deadlocks e condições de corrida.  
  
### <a name="deadlocks"></a>Deadlocks  
 Um deadlock ocorre quando cada um dos dois threads tenta bloquear um recurso que já bloqueado por outro. Nenhum thread pode tornar qualquer progresso adicional.  
  
 Muitos métodos das classes de threading gerenciados fornecem tempos limite para ajudá-lo a detectar deadlocks. Por exemplo, o código a seguir tenta adquirir um bloqueio em um objeto denominado `lockObject`. Se o bloqueio não é obtido em 300 milissegundos, <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> retorna `false`.  
  
```vb  
If Monitor.TryEnter(lockObject, 300) Then  
    Try  
        ' Place code protected by the Monitor here.  
    Finally  
        Monitor.Exit(lockObject)  
    End Try  
Else  
    ' Code to execute if the attempt times out.  
End If  
```  
  
```csharp  
if (Monitor.TryEnter(lockObject, 300)) {  
    try {  
        // Place code protected by the Monitor here.  
    }  
    finally {  
        Monitor.Exit(lockObject);  
    }  
}  
else {  
    // Code to execute if the attempt times out.  
}  
```  
  
### <a name="race-conditions"></a>Condições de corrida  
 Uma condição de corrida é um erro que ocorre quando o resultado de um programa depende de qual dos dois ou mais threads atingir um determinado bloco de código primeiro. Executar o programa muitas vezes produz resultados diferentes, e o resultado de qualquer execução especificada não pode ser previsto.  
  
 Um exemplo simples de uma condição de corrida é incrementar um campo. Suponha que uma classe tem uma particular **estático** campo (**compartilhado** no Visual Basic) que é incrementado toda vez que uma instância da classe é criada, usando um código como `objCt++;` (c#) ou `objCt += 1` ( Visual Basic). Esta operação requer a carregar o valor de `objCt` em um registro, aumentando o valor e armazená-los em `objCt`.  
  
 Em um aplicativo multithread, um thread que foi carregado e incrementado o valor pode ser impedido por outro thread que executa todas as três etapas; Quando o primeiro thread retoma a execução e armazena seu valor, ele substitui `objCt` sem levar em conta o fato de que o valor é alterado durante o processo.  
  
 Essa condição de corrida específica é evitada facilmente usando métodos do <xref:System.Threading.Interlocked> classe, como <xref:System.Threading.Interlocked.Increment%2A?displayProperty=nameWithType>. Para ler sobre outras técnicas para sincronizar dados entre vários threads, consulte [sincronizando dados para Multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md).  
  
 Condições de corrida também podem ocorrer quando você sincronizar as atividades de vários threads. Sempre que você escreve uma linha de código, você deve considerar o que poderia acontecer se um thread foram capturadas antes de executar a linha (ou antes de qualquer uma das instruções de computadores individuais que compõem a linha) e outro thread overtook-lo.  
  
## <a name="number-of-processors"></a>Número de processadores  
 A maioria dos computadores agora tem vários processadores (também chamados de núcleos), até mesmo pequenos dispositivos como tablets e telefones. Se você souber que você está desenvolvendo software também é executados em computadores com processador único, você deve estar ciente multithreading que resolve problemas diferentes para computadores com processador único e computadores com multiprocessadores.  
  
### <a name="multiprocessor-computers"></a>Computadores com multiprocessadores  
 Multithreading fornece maior taxa de transferência. Dez processadores podem fazer dez vezes o trabalho de uma, mas somente se o trabalho é dividido para que os dez podem estar trabalhando ao mesmo tempo; threads fornecem uma maneira fácil para dividir o trabalho e explorar o poder de processamento extra. Se você usar multithreading em um computador multiprocessador:  
  
-   O número de threads que podem ser executados simultaneamente é limitado pelo número de processadores.  
  
-   Um thread em segundo plano é executado somente quando o número de threads de primeiro plano em execução é menor do que o número de processadores.  
  
-   Quando você chama o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> método em um thread, o thread pode ou não pode iniciar a execução imediatamente, dependendo do número de processadores e o número de threads que estão aguardando para executar.  
  
-   Condições de corrida podem ocorrer não só porque threads são capturados inesperadamente, mas porque dois threads em execução em diferentes processadores podem ser corrida para alcançar o mesmo bloco de código.  
  
### <a name="single-processor-computers"></a>Computadores com processador único  
 Multithreading fornece maior capacidade de resposta para o usuário do computador e usa o tempo ocioso para tarefas em segundo plano. Se você usar multithreading em um computador com processador único:  
  
-   Apenas um thread é executado em qualquer momento.  
  
-   Um thread em segundo plano é executado somente quando o thread principal de usuário estiver ocioso. Um thread de primeiro plano que é executado constantemente impede threads de plano de fundo de tempo do processador.  
  
-   Quando você chama o <xref:System.Threading.Thread.Start%2A?displayProperty=nameWithType> método em um thread que thread não iniciar, executar até que o thread atual produz ou é executada pelo sistema operacional.  
  
-   Condições de corrida ocorrem normalmente porque o programador não previu o fato de que um thread pode ser impedido em um momento inadequado, às vezes, permitindo que outro thread alcançar um bloco de código primeiro.  
  
## <a name="static-members-and-static-constructors"></a>Membros estáticos e construtores estáticos  
 Uma classe não foi inicializada até que o construtor de classe (`static` construtor em c#, `Shared Sub New` no Visual Basic) concluiu a execução. Para impedir a execução de código em um tipo que não é inicializado, o common language runtime bloqueia todas as chamadas de outros threads para `static` membros da classe (`Shared` membros no Visual Basic) até que o construtor da classe concluiu a execução.  
  
 Por exemplo, se um construtor de classe inicia um novo thread, e chama o procedimento de thread um `static` membro da classe, os novos blocos de thread até que o construtor da classe seja concluída.  
  
 Isso se aplica a qualquer tipo que pode ter um `static` construtor.  
  
## <a name="general-recommendations"></a>Recomendações gerais  
 Ao usar vários threads, considere as seguintes diretrizes:  
  
-   Não use <xref:System.Threading.Thread.Abort%2A?displayProperty=nameWithType> encerrar outros threads. Chamando **anular** em outro thread equivale a gerar uma exceção que o thread, sem saber o que esse thread de ponto alcançou em seu processamento.  
  
-   Não use <xref:System.Threading.Thread.Suspend%2A?displayProperty=nameWithType> e <xref:System.Threading.Thread.Resume%2A?displayProperty=nameWithType> para sincronizar as atividades de vários threads. Use <xref:System.Threading.Mutex>, <xref:System.Threading.ManualResetEvent>, <xref:System.Threading.AutoResetEvent>, e <xref:System.Threading.Monitor>.  
  
-   Não controla a execução de threads de trabalho em seu programa principal (usando eventos, por exemplo). Em vez disso, crie seu programa para que os threads de trabalho são responsáveis por esperar até que o trabalho está disponível, executá-lo e notificar outras partes do seu programa quando terminar. Se seus threads de trabalho não bloqueiam, considere o uso de threads de pool. <xref:System.Threading.Monitor.PulseAll%2A?displayProperty=nameWithType>é útil em situações em que os threads de trabalho do bloco.  
  
-   Não use tipos como objetos de bloqueio. Isto é, evite código como `lock(typeof(X))` em c# ou `SyncLock(GetType(X))` no Visual Basic ou o uso de <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> com <xref:System.Type> objetos. Para um determinado tipo, há apenas uma instância de <xref:System.Type?displayProperty=nameWithType> por domínio de aplicativo. Se o tipo de em que usar um bloqueio for público, o código que não seja o seu próprio pode assumir bloqueios, levando a deadlocks. Para problemas adicionais, consulte [práticas recomendadas de confiabilidade](../../../docs/framework/performance/reliability-best-practices.md).  
  
-   Tenha cuidado ao bloqueio em instâncias, por exemplo `lock(this)` em c# ou `SyncLock(Me)` no Visual Basic. Se outro código no seu aplicativo externo para o tipo tem um bloqueio no objeto, podem ocorrer deadlocks.  
  
-   Certifique-se de que um thread que entrou em um monitor sempre deixa monitor, mesmo se uma exceção ocorre enquanto o thread está no monitor. C# [bloqueio](~/docs/csharp/language-reference/keywords/lock-statement.md) instrução e o Visual Basic [SyncLock](~/docs/visual-basic/language-reference/statements/synclock-statement.md) instrução fornecer esse comportamento automaticamente, empregando uma **finalmente** bloco para garantir que <xref:System.Threading.Monitor.Exit%2A?displayProperty=nameWithType> é chamado. Se você não pode garantir que **Exit** será chamado, considere alterar o design para usar **Mutex**. Um mutex é liberado automaticamente quando o thread que atualmente possui ele termina.  
  
-   Usar vários threads para tarefas que exigem recursos diferentes e evite atribuir vários threads para um único recurso. Por exemplo, se beneficia ter seu próprio thread, porque esse thread bloqueará durante as operações de e/s e assim permitir que outros threads executar qualquer tarefa que envolvem a e/s. Entrada do usuário é outro recurso que se beneficia com um thread dedicado. Em um computador com processador único, uma tarefa que envolve a computação intensiva coexiste com a entrada do usuário e tarefas que envolvem a e/s, mas várias tarefas de computação intensa conteúdo uns com os outros.  
  
-   Considere o uso de métodos do <xref:System.Threading.Interlocked> classe para alterações de estado simples, em vez de usar o `lock` instrução (`SyncLock` no Visual Basic). O `lock` instrução é uma boa ferramenta para fins gerais, mas o <xref:System.Threading.Interlocked> classe fornece um melhor desempenho para atualizações que devem ser atômica. Internamente, ele executa um prefixo único bloqueio se não houver nenhuma contenção. Em revisões de código, atente para código semelhante ao mostrado nos exemplos a seguir. No primeiro exemplo, uma variável de estado é incrementada:  
  
    ```vb  
    SyncLock lockObject  
        myField += 1  
    End SyncLock  
    ```  
  
    ```csharp  
    lock(lockObject)   
    {  
        myField++;  
    }  
    ```  
  
     Você pode melhorar o desempenho usando o <xref:System.Threading.Interlocked.Increment%2A> método em vez do `lock` instrução, da seguinte maneira:  
  
    ```vb  
    System.Threading.Interlocked.Increment(myField)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.Increment(myField);  
    ```  
  
    > [!NOTE]
    >  No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.Add%2A> método fornece atualizações atômicas em incrementos maiores do que 1.  
  
     No segundo exemplo, uma variável de tipo de referência é atualizada somente se ele for uma referência nula (`Nothing` no Visual Basic).  
  
    ```vb  
    If x Is Nothing Then  
        SyncLock lockObject  
            If x Is Nothing Then  
                x = y  
            End If  
        End SyncLock  
    End If  
    ```  
  
    ```csharp  
    if (x == null)  
    {  
        lock (lockObject)  
        {  
            if (x == null)  
            {  
                x = y;  
            }  
        }  
    }  
    ```  
  
     É possível melhorar o desempenho usando o <xref:System.Threading.Interlocked.CompareExchange%2A> método em vez disso, da seguinte maneira:  
  
    ```vb  
    System.Threading.Interlocked.CompareExchange(x, y, Nothing)  
    ```  
  
    ```csharp  
    System.Threading.Interlocked.CompareExchange(ref x, y, null);  
    ```  
  
    > [!NOTE]
    >  No .NET Framework versão 2.0, o <xref:System.Threading.Interlocked.CompareExchange%2A> método tem uma sobrecarga genérica que pode ser usada para a substituição de segurança de tipos de qualquer tipo de referência.  
  
## <a name="recommendations-for-class-libraries"></a>Recomendações para bibliotecas de classe  
 Considere as seguintes diretrizes ao criar bibliotecas de classes para multithreading:  
  
-   Evite a necessidade de sincronização, se possível. Isso é especialmente verdadeiro para o código de uso intensivo. Por exemplo, um algoritmo pode ser ajustado para tolerar uma condição de corrida em vez de eliminá-lo. Sincronização desnecessária diminui o desempenho e cria a possibilidade de deadlocks e condições de corrida.  
  
-   Verifique os dados estáticos (`Shared` no Visual Basic) thread-safe por padrão.  
  
-   Não faça instância de segmento de dados seguro por padrão. Adicionar bloqueios para criar o código de thread-safe diminui o desempenho, aumenta a contenção de bloqueio e cria a possibilidade de deadlocks ocorra. Modelos de aplicativo, em comum que apenas um thread por vez executa código do usuário, o que minimiza a necessidade de acesso thread-safe. Por esse motivo, as bibliotecas de classes do .NET Framework não são thread-safe por padrão.  
  
-   Evite fornecer métodos estáticos que alteram o estado estático. Em cenários de servidor comum, estado estático é compartilhado entre as solicitações, que significa que vários threads podem executar esse código ao mesmo tempo. Isso abre a possibilidade de threading bugs. Considere usar um padrão de design que encapsula dados em instâncias que não são compartilhadas entre solicitações. Além disso, se os dados estáticos são sincronizados, chamadas entre os métodos estáticos que alteram o estado podem resultar em deadlocks ou sincronização redundante, afetando negativamente o desempenho.  
  
## <a name="see-also"></a>Consulte também  
 [Threading](../../../docs/standard/threading/index.md)  
 [Threads e threading](../../../docs/standard/threading/threads-and-threading.md)
