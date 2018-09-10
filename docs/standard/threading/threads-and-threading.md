---
title: Threads e threading
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- multiple threads
- threading [.NET Framework]
- threading [.NET Framework], multiple threads
ms.assetid: 5baac3aa-e603-4fa6-9f89-0f2c1084e6b1
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ef464b0d4c22d04d42f9b6f953abefe7582b4957
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/09/2018
ms.locfileid: "44188534"
---
# <a name="threads-and-threading"></a>Threads e threading
Os sistemas operacionais usam processos para separar os diferentes aplicativos que eles estão executando. Os threads são a unidade básica à qual um sistema operacional aloca tempo de processador, e mais de um thread pode estar executando código dentro desse processo. Cada thread mantém manipuladores de exceção, uma prioridade de agendamento e um conjunto de estruturas que o sistema usa para salvar o contexto do thread até que ele seja agendado. O contexto de thread inclui todas as informações que o thread precisa para continuar a execução perfeitamente, incluindo o conjunto de registros de CPU e pilha do thread, no espaço de endereço do processo de host do thread.  
  
 O .NET Framework subdivide mais ainda um processo do sistema operacional em subprocessos gerenciados leves, chamados de domínios de aplicativo, representados por <xref:System.AppDomain?displayProperty=nameWithType>. Um ou mais threads gerenciados (representados por <xref:System.Threading.Thread?displayProperty=nameWithType>) podem ser executados em uma ou qualquer número de domínios de aplicativo dentro do mesmo processo gerenciado. Embora cada domínio do aplicativo seja iniciado com um único thread, o código nesse domínio do aplicativo pode criar domínios do aplicativo adicionais e threads adicionais. O resultado é que um thread gerenciado pode se mover livremente entre domínios do aplicativo no mesmo processo gerenciado. Você pode ter apenas um thread se movendo entre vários domínios de aplicativo.  
  
 Um sistema operacional que dá suporte à multitarefa preemptiva cria o efeito da execução simultânea de vários threads de vários processos. Ele faz isso dividindo o tempo do processador disponível entre os threads que precisam dele, alocar uma fatia de tempo do processador a cada thread após o outro. O thread em execução no momento é suspenso quando sua fração de tempo se passa, e outro thread retoma a execução. Quando o sistema muda de um thread para outro, salva o contexto do thread de preempção e recarrega o contexto do thread salvo do próximo thread na fila de threads.  
  
 A duração da fração de tempo depende do sistema operacional e do processador. Como cada fração de tempo é pequena, vários threads parecem estar em execução ao mesmo tempo, mesmo se houver apenas um processador. É esse o caso em sistemas de multiprocessador, em que os threads executáveis são distribuídos entre os processadores disponíveis.  
  
## <a name="when-to-use-multiple-threads"></a>Quando usar vários threads  
 Os softwares que requerem interação do usuário devem reagir às atividades do usuário o mais rápido possível para fornecer uma rica experiência ao usuário. No entanto, ao mesmo tempo, ele deve fazer os cálculos necessários para apresentar os dados ao usuário o mais rápido possível. Caso seu aplicativo só use um thread de execução, você poderá combinar a [programação assíncrona](../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md) com a[comunicação remota do .NET Framework](https://msdn.microsoft.com/library/eccb1d31-0a22-417a-97fd-f4f1f3aa4462) ou os [serviços Web XML](https://msdn.microsoft.com/library/1e64af78-d705-4384-b08d-591a45f4379c) criados com o ASP.NET para usar o tempo de processamento de outros computadores, além do tempo do seu próprio computador, para aumentar a capacidade de resposta ao usuário e diminuir o tempo de processamento de dados do seu aplicativo. Se você estiver fazendo um trabalho de entrada/saída intensivo, também poderá usar as portas de conclusão de E/S para aumentar a capacidade de resposta do seu aplicativo.  
  
### <a name="advantages-of-multiple-threads"></a>Vantagens dos vários threads  
 No entanto, usar mais de um thread é a técnica mais avançada disponível para aumentar a capacidade de resposta ao usuário e processar os dados necessários para realizar o trabalho quase simultaneamente. Em um computador com um processador, vários threads podem criar esse efeito, aproveitando os pequenos períodos de tempo entre os eventos de usuário para processar os dados em segundo plano. Por exemplo, um usuário pode editar uma planilha enquanto outro thread está recalculando outras partes da planilha dentro do mesmo aplicativo.  
  
 Sem modificação, o mesmo aplicativo aumentaria drasticamente a satisfação do usuário quando executado em um computador com mais de um processador. Seu domínio de aplicativo único pode usar vários threads para realizar as seguintes tarefas:  
  
-   Comunicar-se pela rede, para um servidor Web e para um banco de dados.  
  
-   Executar operações que demorem muito.  
  
-   Diferenciar as tarefas de prioridade variada. Por exemplo, um thread de alta prioridade gerencia tarefas cujo tempo é algo crítico e um thread de baixa prioridade executa outras tarefas.  
  
-   Permitir que a interface do usuário continue responsiva, durante a alocação de tempo a tarefas em segundo plano.  
  
### <a name="disadvantages-of-multiple-threads"></a>Desvantagens dos vários threads  
 Recomendamos que use o menor número de threads possível, minimizando, assim, o uso de recursos do sistema operacional e melhorando o desempenho. O threading também tem requisitos de recursos e possíveis conflitos a serem considerados durante a criação de seu aplicativo. Os requisitos de recurso são os seguintes:  
  
-   O sistema consome memória para as informações de contexto exigidas por processos, objetos **AppDomain** e threads. Portanto, o número de processos, objetos **AppDomain** e threads que podem ser criados é limitado pela memória disponível.  
  
-   Manter o controle de um grande número de threads consome muito tempo do processador. Se houver muitos threads, a maioria deles não fará progresso significativo. Se a maioria dos threads atuais estiver em um processo, os threads em outros processos serão agendados com menos frequência.  
  
-   O controlando da execução de código com muitos threads é complexo e pode ser uma fonte de muitos erros.  
  
-   A destruição de threads requer o conhecimento do que poderia acontecer e o tratamento desses problemas.  
  
 Fornecer acesso compartilhado a recursos pode criar conflitos. Para evitar conflitos, você deve sincronizar ou controlar o acesso aos recursos compartilhados. A não possibilidade de sincronizar o acesso corretamente (nos domínios de aplicativo iguais ou diferentes) pode causar problemas, como deadlocks (no qual dois threads param de responder enquanto cada um aguarda a conclusão do outro) e condições de corrida (quando ocorre um resultado anômalo devido a uma inesperada dependência crítica do tempo dos dois eventos). O sistema fornece objetos de sincronização que podem ser usados para coordenar compartilhamento de recursos entre vários threads. Reduzir o número de threads torna mais fácil a sincronização de recursos.  
  
 Os recursos que requerem sincronização são:  
  
-   Recursos do sistema (como portas de comunicação).  
  
-   Recursos compartilhados por vários processos (como identificadores de arquivos).  
  
-   Os recursos de um único domínio do aplicativo (como os campos global, estático e de instância) acessados por vários threads.  
  
### <a name="threading-and-application-design"></a>Design de aplicativo e threading  
 Em geral, usar a classe <xref:System.Threading.ThreadPool> é a maneira mais fácil de lidar com vários threads para tarefas relativamente curtas, que não bloquearão outros threads e quando você não espera nenhum agendamento específico das tarefas. No entanto, há vários motivos para criar seus próprios threads:  
  
-   Se você precisar de uma tarefa para ter uma prioridade específica.  
  
-   Se você tiver uma tarefa que pode executar por muito tempo (e, portanto, bloquear outras tarefas).  
  
-   Se você precisar colocar os threads em um apartment de thread único (todos os threads **ThreadPool** estão no apartament de vários threads).  
  
-   Se você precisa de uma identidade estável associada ao thread. Por exemplo, você deve usar um thread dedicado para anular aquele thread, suspendê-lo ou descobri-lo por nome.  
  
-   Se você precisar executar threads em segundo plano que interagem com a interface do usuário, o .NET Framework versão 2.0 fornece um componente <xref:System.ComponentModel.BackgroundWorker> que se comunica por meio de eventos, com marshaling entre threads para o thread da interface do usuário.  
  
### <a name="threading-and-exceptions"></a>Threading e exceções  
 Não se esqueça de tratar as exceções nos threads. As exceções sem tratamento nos threads, até threads em segundo plano, geralmente encerram o processo. Há três exceções a essa regra:  
  
-   Uma <xref:System.Threading.ThreadAbortException> é gerada em um thread porque <xref:System.Threading.Thread.Abort%2A> foi chamado.  
  
-   Uma <xref:System.AppDomainUnloadedException> é gerada em um thread porque o domínio de aplicativo está sendo descarregado.  
  
-   O CLR ou um processo de host encerra o thread.  
  
 Para saber mais, veja [Exceções em threads gerenciados](../../../docs/standard/threading/exceptions-in-managed-threads.md).  
  
> [!NOTE]
>  Nas versões do .NET Framework 1.0 e 1.1, o CLR intercepta silenciosamente algumas exceções, por exemplo, em threads de pool de threads. Isso pode corromper o estado do aplicativo e, eventualmente, fazer com que aplicativos sejam suspensos, o que pode ser muito difícil de depurar.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Threading.ThreadPool>  
- <xref:System.ComponentModel.BackgroundWorker>  
- [Sincronizando dados para multithreading](../../../docs/standard/threading/synchronizing-data-for-multithreading.md)  
- [O pool de threads gerenciados](../../../docs/standard/threading/the-managed-thread-pool.md)
