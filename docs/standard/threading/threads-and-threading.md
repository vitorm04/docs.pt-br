---
title: Threads e threading
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b57cac34009e13c27c6d34a0ab402f9ecbe08305
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="threads-and-threading"></a>Threads e threading
Sistemas operacionais use processos para separar os diferentes aplicativos que estão sendo executados. Threads são a unidade básica para o qual um sistema operacional aloca tempo do processador e mais de um thread pode estar executando o código dentro desse processo. Cada thread mantém um conjunto de estruturas que o sistema usa para salvar o contexto do thread até que ela esteja agendada, uma prioridade de agendamento e manipuladores de exceção. O contexto do thread inclui todas as informações que o thread precisa perfeitamente continuar execução, incluindo o conjunto do thread de registros de CPU e a pilha, no espaço de endereço de processo do host do thread.  
  
 O .NET Framework mais subdivide um processo do sistema operacional em subprocessos gerenciados leves, chamados de domínios de aplicativo, representados pelo <xref:System.AppDomain?displayProperty=nameWithType>. Um ou mais threads gerenciados (representado por <xref:System.Threading.Thread?displayProperty=nameWithType>) podem ser executados em uma ou qualquer número de domínios do aplicativo dentro do mesmo processo gerenciado. Embora cada domínio de aplicativo é iniciado com um único thread, o código no domínio de aplicativo pode criar domínios de aplicativo adicionais e threads adicionais. O resultado é que um thread gerenciado pode ser movidos livremente entre domínios de aplicativo no mesmo processo gerenciado; Você pode ter apenas um thread movendo entre vários domínios de aplicativo.  
  
 Um sistema operacional que dá suporte a multitarefa preemptiva cria o efeito da execução simultânea de vários threads de vários processos. Ele faz isso dividindo o tempo do processador disponível entre os threads que precisam dela, alocar um intervalo de tempo do processador para cada thread após o outro. O thread atualmente em execução será suspensa quando o tempo decorrido de fatia e outro thread em execução é retomada. Quando o sistema muda de um thread para outro, ele salva o contexto do thread do thread admitiu preempção e recarrega o contexto do thread salvo do próximo segmento na fila de thread.  
  
 O comprimento da fração de tempo depende do sistema operacional e o processador. Como cada intervalo de tempo é pequeno, vários threads aparecem em execução ao mesmo tempo, mesmo se houver apenas um processador. Isso é realmente o caso em sistemas de multiprocessador, em que os threads executável são distribuídos entre os processadores disponíveis.  
  
## <a name="when-to-use-multiple-threads"></a>Quando usar vários Threads  
 Software que requer interação do usuário deve reagir às atividades do usuário mais rápido possível para fornecer uma experiência de usuário. No entanto, ao mesmo tempo, ele deve fazer cálculos necessários para apresentar os dados para o usuário mais rápido possível. Se seu aplicativo usa apenas um thread de execução, você pode combinar [programação assíncrona](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) com[comunicação remota do .NET Framework](http://msdn.microsoft.com/en-us/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) ou [os XML Web services](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c) criados usando ASP .NET para usar o tempo de processamento de outros computadores Além disso, para que seus próprios para aumentar a capacidade de resposta para o usuário e diminuir o tempo de processamento de dados do seu aplicativo. Se você estiver fazendo um trabalho de entrada/saída intensivo, você também pode usar as portas de conclusão de e/s para aumentar a capacidade de resposta do seu aplicativo.  
  
### <a name="advantages-of-multiple-threads"></a>Vantagens de vários Threads  
 No entanto, usar mais de um thread é a técnica mais avançada disponível para aumentar a capacidade de resposta para o usuário e processar os dados necessários para realizar o trabalho quase simultaneamente. Em um computador com um processador, vários threads podem criar esse efeito, aproveitando os pequenos períodos de tempo entre eventos de usuário para processar os dados em segundo plano. Por exemplo, um usuário pode editar uma planilha enquanto outro thread está recalculando outras partes da planilha dentro do mesmo aplicativo.  
  
 Sem modificação, o mesmo aplicativo seria aumentar a satisfação do usuário quando executado em um computador com mais de um processador. O único domínio de aplicativo pode usar vários threads para realizar as seguintes tarefas:  
  
-   Se comunicar pela rede, em um servidor Web e um banco de dados.  
  
-   Execute as operações que levam a uma grande quantidade de tempo.  
  
-   Diferenciar as tarefas de prioridade diferentes. Por exemplo, um thread de alta prioridade gerencia as tarefas críticas e um thread de baixa prioridade executa outras tarefas.  
  
-   Permitir que a interface do usuário continuar responsiva, durante a alocação de tempo para tarefas em segundo plano.  
  
### <a name="disadvantages-of-multiple-threads"></a>Desvantagens de vários Threads  
 É recomendável que você use o menor número de threads, minimizando, assim, o uso de recursos do sistema operacional e melhorar o desempenho. Threading também tem requisitos de recursos e possíveis conflitos a serem considerados ao criar seu aplicativo. Os requisitos de recursos são os seguintes:  
  
-   O sistema consome memória para as informações de contexto exigidas por processos, **AppDomain** objetos e threads. Portanto, o número de processos, **AppDomain** objetos e os threads que podem ser criados é limitado pela memória disponível.  
  
-   Manter o controle de um grande número de threads consome muito tempo do processador. Se houver muitos threads, a maioria deles não fará grande progresso. Se a maioria dos threads atuais for em um processo, threads em outros processos agendados com menos frequência.  
  
-   Controlando a execução de código com o número de threads é complexo e pode ser uma fonte de muitos erros.  
  
-   Destruindo threads requer saber o que poderia acontecer e manipulação desses problemas.  
  
 Acesso compartilhado a recursos pode criar conflitos. Para evitar conflitos, você deve sincronizar ou controlar o acesso aos recursos compartilhados. Falha ao sincronizar o acesso corretamente (nos domínios de aplicativo igual ou diferente) pode causar problemas, como deadlocks (no qual dois threads parar de responder enquanto aguarda a cada um do outro concluir) e condições de corrida (quando ocorre um resultado anômalo devido a uma inesperado crítica dependência de tempo dos dois eventos). O sistema fornece objetos de sincronização que podem ser usados para coordenar entre vários threads de compartilhamento de recursos. Reduzir o número de threads torna mais fácil sincronizar os recursos.  
  
 Os recursos que requerem sincronização incluem:  
  
-   Recursos do sistema (como portas de comunicação).  
  
-   Recursos compartilhados por vários processos (como identificadores de arquivos).  
  
-   Os recursos de um único domínio de aplicativo (como global, estático e campos de instância) acessados por vários threads.  
  
### <a name="threading-and-application-design"></a>Design de aplicativo e Threading  
 Em geral, usando o <xref:System.Threading.ThreadPool> classe é a maneira mais fácil de lidar com vários threads para tarefas relativamente curtos, que não impede que outros threads e quando você não espera agendamento específico das tarefas. No entanto, há vários motivos para criar seus próprios threads:  
  
-   Se você precisar de uma tarefa com uma prioridade específica.  
  
-   Se você tiver uma tarefa que talvez um longo tempo de execução (e, portanto, bloquear outras tarefas).  
  
-   Se você precisa colocar os threads em um single-threaded apartment (todos os **ThreadPool** threads estão no multi-threaded apartment).  
  
-   Se você precisa de uma identidade estável associada ao segmento. Por exemplo, você deve usar um thread dedicado para anular o thread, suspendê-las ou descobri-lo por nome.  
  
-   Se você precisar executar threads em segundo plano que interagem com a interface do usuário, o .NET Framework versão 2.0 fornece um <xref:System.ComponentModel.BackgroundWorker> componente que se comunicam por meio de eventos, com entre threads marshaling para o thread de interface do usuário.  
  
### <a name="threading-and-exceptions"></a>Threading e exceções  
 Manipule exceções em threads. Exceções sem tratamento em threads, threads de plano de fundo até mesmo, geralmente encerrar o processo. Há três exceções a essa regra:  
  
-   Um <xref:System.Threading.ThreadAbortException> é gerada em um thread porque <xref:System.Threading.Thread.Abort%2A> foi chamado.  
  
-   Um <xref:System.AppDomainUnloadedException> é gerada em um thread porque o domínio de aplicativo está sendo descarregado.  
  
-   O common language runtime ou um processo de host encerra o thread.  
  
 Para obter mais informações, consulte [exceções em Threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, o common language runtime silenciosamente intercepta algumas exceções, por exemplo, em threads de pool. Isso pode corromper o estado do aplicativo e, eventualmente, fazer com que aplicativos de suspensão, que podem ser muito difícil de depurar.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Threading.ThreadPool>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
 [O pool de threads gerenciados](../../../docs/standard/threading/the-managed-thread-pool.md)
