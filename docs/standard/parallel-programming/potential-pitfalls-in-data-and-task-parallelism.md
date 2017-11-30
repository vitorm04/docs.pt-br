---
title: Armadilhas em potencial em dados e paralelismo da tarefa
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: parallel programming, pitfalls
ms.assetid: 1e357177-e699-4b8f-9e49-56d3513ed128
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 54fd201bd4eaef607f8917ea693876aec7fa2923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="potential-pitfalls-in-data-and-task-parallelism"></a>Armadilhas em potencial em dados e paralelismo da tarefa
Em muitos casos, <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> pode oferecer melhorias significativas no desempenho ao longo de loops sequenciais comuns. No entanto, o trabalho de paralelização do loop apresenta complexidade que pode levar a problemas que, no código sequencial, não são tão comum ou não são encontrados. Este tópico lista algumas práticas recomendadas para evitar quando você escreve loops paralelos.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Não suponha que paralelo é sempre mais rápido  
 Em certos casos um loop paralelo pode ser executado mais lentamente do que seu equivalente sequencial. A regra de ouro básica é que loops paralelos que têm alguns iterações e delegados rápida de usuário são improvável de aumento de velocidade muito. No entanto, como muitos fatores estão envolvidos no desempenho, recomendamos que você sempre pode medir os resultados reais.  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Evitar gravar em locais de memória compartilhada  
 No código sequencial, não é incomum para ler ou gravar em variáveis estáticas ou campos de classe. No entanto, sempre que vários threads acessam simultaneamente essas variáveis, há um grande potencial de condições de corrida. Embora você possa usar bloqueios para sincronizar o acesso à variável, o custo da sincronização pode prejudicar o desempenho. Portanto, é recomendável que você evite, ou pelo menos limita, acesso ao estado em um loop paralelo tanto quanto possível compartilhado. A melhor maneira de fazer isso é usar as sobrecargas de <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> que usam um <xref:System.Threading.ThreadLocal%601?displayProperty=nameWithType> variável para armazenar o estado de local de thread durante a execução do loop. Para obter mais informações, consulte [Como escrever um loop Parallel.For com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-for-loop-with-thread-local-variables.md) e [Como escrever um loop Parallel.ForEach com variáveis locais de thread](../../../docs/standard/parallel-programming/how-to-write-a-parallel-foreach-loop-with-thread-local-variables.md).  
  
## <a name="avoid-over-parallelization"></a>Evitar excesso de paralelização  
 Usando loops paralelos, incorre em dos custos indiretos de particionamento a coleção de origem e a sincronização de threads de trabalho. Os benefícios de paralelização ainda estão limitados pelo número de processadores no computador. Não há nenhum aumento de velocidade a ser obtido executando vários threads vinculada à computação em apenas um processador. Portanto, você deve ser cuidado para não sobrescrever paralelizar um loop.  
  
 O cenário mais comum no qual paralelização excessiva pode ocorrer é em loops aninhados. Na maioria dos casos, é melhor paralelizar apenas o loop externo, a menos que uma ou mais das seguintes condições se aplicam:  
  
-   O loop interno é conhecido por ser muito longos.  
  
-   Você está executando uma computação cara em cada pedido. (A operação mostrada no exemplo não é cara).  
  
-   O sistema de destino é conhecido por ter processadores suficientes para controlar o número de threads que será produzido pela paralelizar a consulta em `cust.Orders`.  
  
 Em todos os casos, a melhor maneira de determinar a forma de consulta ideal é testar e medidas.  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Evite chamadas para métodos de Non-Thread-Safe  
 Gravando para métodos de instância non-thread-safe de um loop paralelo pode levar à corrupção de dados que podem ou não pode ser detectados em seu programa. Isso também poderá resultar em exceções. No exemplo a seguir, vários threads é tentar chamar o <xref:System.IO.FileStream.WriteByte%2A?displayProperty=nameWithType> método simultaneamente, que não é compatível com a classe.  
  
 [!code-csharp[TPL_Pitfalls#04](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#04)]
 [!code-vb[TPL_Pitfalls#04](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#04)]  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limite de chamadas para métodos de Thread-Safe  
 Os métodos mais estáticos no .NET Framework são thread-safe e podem ser chamados de vários threads simultaneamente. No entanto, até mesmo nesses casos, a sincronização envolvidos pode levar a diminuição significativa na consulta.  
  
> [!NOTE]
>  Você pode testar isso por conta própria, inserindo algumas chamadas para <xref:System.Console.WriteLine%2A> em suas consultas. Embora esse método é usado nos exemplos a documentação para fins de demonstração, não usá-lo em loops paralelos, a menos que necessário.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Estar ciente das questões de afinidade de Thread  
 Algumas tecnologias, por exemplo, a interoperabilidade COM para componentes de Single-Threaded Apartment (STA), formulários do Windows e Windows Presentation Foundation (WPF), impõem restrições de afinidade de thread que exigem o código para executar em um thread específico. Por exemplo, no Windows Forms e WPF, um controle só pode ser acessado no thread no qual ele foi criado. Por exemplo, isso significa que você não pode atualizar um controle de lista de um loop paralelo, a menos que você configurar o Agendador de thread para agendar o trabalho somente no thread da interface do usuário. Para obter mais informações, consulte [como: agenda de trabalho no Thread da Interface do usuário (UI)](http://msdn.microsoft.com/library/32a846a5-d628-4933-907b-4888ff72c663).  
  
## <a name="use-caution-when-waiting-in-delegates-that-are-called-by-parallelinvoke"></a>Tenha cuidado quando aguardando delegados que são chamados pelo Parallel. Invoke  
 Em determinadas circunstâncias, a biblioteca paralela de tarefas será embutido uma tarefa, o que significa que ele é executado na tarefa no thread em execução no momento. (Para obter mais informações, consulte [agendadores de tarefa](http://msdn.microsoft.com/library/638f8ea5-21db-47a2-a934-86e1e961bf65).) Essa otimização de desempenho pode resultar em deadlock em determinados casos. Por exemplo, duas tarefas podem executar o mesmo delegado código, que indica quando ocorre um evento, e, em seguida, aguarda a outra tarefa sinalizar. Se a segunda tarefa é embutida no mesmo thread que o primeiro e o primeiro entra em um estado de espera, a segunda tarefa nunca poderá sinalizar o evento. Para evitar tal uma ocorrência, você pode especificar um tempo limite na operação de espera ou construtores de thread explícita de uso para ajudar a garantir que uma tarefa não podem bloquear a outra.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Não suponha que iterações de ForEach, para e ForAll sempre executar em paralelo  
 É importante ter em mente que iterações individuais em um <xref:System.Threading.Tasks.Parallel.For%2A>, <xref:System.Threading.Tasks.Parallel.ForEach%2A> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> pode executar um loop, mas não é necessário que executar em paralelo. Portanto, você deve evitar gravar qualquer código que depende de correção de execução paralela de iterações ou na execução de iterações em nenhuma ordem específica. Por exemplo, esse código é provavelmente um deadlock:  
  
 [!code-csharp[TPL_Pitfalls#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#01)]
 [!code-vb[TPL_Pitfalls#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#01)]  
  
 Neste exemplo, uma iteração define um evento, e todas as outras iterações esperar o evento. Nenhuma das iterações espera pode concluir até que a iteração de configuração de evento foi concluída. No entanto, é possível que as iterações espera bloqueiam todos os threads que são usados para executar o loop paralelo, antes da iteração de configuração de evento teve a chance de executar. Isso resulta em um deadlock – a iteração de configuração de evento nunca será executado e as iterações espera nunca serão ativada.  
  
 Em particular, uma iteração de um loop paralelo nunca deve aguardar outra iteração do loop para tornar o progresso. Se o loop paralelo decidir agendar as iterações sequencialmente, mas em ordem oposta, ocorrerá um deadlock.  
  
## <a name="avoid-executing-parallel-loops-on-the-ui-thread"></a>Evitar Loops paralelos em execução no Thread da interface do usuário  
 É importante manter a interface do usuário do aplicativo (UI) responsiva. Se uma operação contém suficiente trabalho para garantir a paralelização, em seguida, ele provavelmente não deve ser executado essa operação no thread da interface do usuário.  Em vez disso, ele deve descarregar essa operação para ser executado em um thread em segundo plano. Por exemplo, se você quiser usar um loop paralelo para calcular alguns dados que devem ser renderizados em um controle de interface do usuário, convém executar o loop dentro de uma instância de tarefa, em vez de diretamente em um manipulador de eventos de interface do usuário.  Somente quando o cálculo Central foi concluída deve você, em seguida, empacotar a atualização de interface do usuário para o thread de interface do usuário.  
  
 Se você executar loops paralelos no thread da interface do usuário, tenha cuidado para evitar a atualização de controles de interface do usuário de dentro do loop. Controles de dentro de um loop paralelo que está em execução no thread da interface do usuário tentando atualizar a interface do usuário podem levar a corrupção de estado, exceções, atualizações atrasadas e até mesmo deadlocks, dependendo de como a atualização de interface do usuário é chamada. No exemplo a seguir, o loop paralelo bloqueia o thread de interface do usuário no qual ele está em execução até que todas as iterações sejam concluídas. No entanto, se uma iteração do loop está em execução em um thread em segundo plano (como <xref:System.Threading.Tasks.Parallel.For%2A> pode fazer), a chamada a Invoke faz com que uma mensagem a ser enviado para o thread de interface do usuário e a blocos aguardando a mensagem a ser processado. Desde que o thread de interface do usuário é bloqueado executando o <xref:System.Threading.Tasks.Parallel.For%2A>, a mensagem nunca pode ser processada e os deadlocks de thread de interface do usuário.  
  
 [!code-csharp[TPL_Pitfalls#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#02)]
 [!code-vb[TPL_Pitfalls#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#02)]  
  
 O exemplo a seguir mostra como evitar o deadlock, executando o loop dentro de uma instância de tarefa. O thread de interface do usuário não é bloqueado pelo loop e a mensagem pode ser processada.  
  
 [!code-csharp[TPL_Pitfalls#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_pitfalls/cs/pitfalls.cs#03)]
 [!code-vb[TPL_Pitfalls#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_pitfalls/vb/pitfalls_vb.vb#03)]  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [Possíveis armadilhas com PLINQ](../../../docs/standard/parallel-programming/potential-pitfalls-with-plinq.md)  
 [Padrões de programação paralela: compreender e aplicar paralela padrões com o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkID=185142)
