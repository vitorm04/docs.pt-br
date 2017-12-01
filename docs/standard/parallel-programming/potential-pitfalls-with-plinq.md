---
title: Armadilhas em potencial com PLINQ
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
helpviewer_keywords: PLINQ queries, pitfalls
ms.assetid: 75a38b55-4bc4-488a-87d5-89dbdbdc76a2
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f7c971d2c039e6441669108e966eba472819fde5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="potential-pitfalls-with-plinq"></a>Armadilhas em potencial com PLINQ
Em muitos casos, PLINQ pode oferecer melhorias significativas no desempenho ao longo de LINQ sequencial para consultas de objetos. No entanto, o trabalho de paralelizar a execução da consulta apresenta complexidade que pode levar a problemas que, no código sequencial, não são tão comum ou não são encontrados. Este tópico lista algumas práticas recomendadas para evitar ao escrever consultas PLINQ.  
  
## <a name="do-not-assume-that-parallel-is-always-faster"></a>Não suponha que paralelo é sempre mais rápido  
 Paralelização às vezes faz com que uma consulta PLINQ executar mais lentamente do que o LINQ em equivalentes de objetos. O princípio básico é que as consultas que têm alguns elementos de origem e delegados rápida de usuário são improvável de aumento de velocidade muito. No entanto, como muitos fatores estão envolvidos no desempenho, é recomendável medir os resultados reais antes de decidir se deseja usar PLINQ. Para saber mais, veja [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="avoid-writing-to-shared-memory-locations"></a>Evitar gravar em locais de memória compartilhada  
 No código sequencial, não é incomum para ler ou gravar em variáveis estáticas ou campos de classe. No entanto, sempre que vários threads acessam simultaneamente essas variáveis, há um grande potencial de condições de corrida. Embora você possa usar bloqueios para sincronizar o acesso à variável, o custo da sincronização pode prejudicar o desempenho. Portanto, é recomendável que você evite, ou pelo menos limita, acesso ao estado em uma consulta PLINQ tanto quanto possível compartilhado.  
  
## <a name="avoid-over-parallelization"></a>Evitar excesso de paralelização  
 Usando o `AsParallel` operador, você provoca dos custos indiretos de particionamento a coleção de origem e a sincronização de threads de trabalho. Os benefícios de paralelização ainda estão limitados pelo número de processadores no computador. Não há nenhum aumento de velocidade a ser obtido executando vários threads vinculada à computação em apenas um processador. Portanto, você deve ser cuidado para não sobrescrever paralelizar uma consulta.  
  
 O cenário mais comum no qual paralelização excessiva pode ocorrer é em consultas aninhadas, conforme mostrado no trecho a seguir.  
  
 [!code-csharp[PLINQ#20](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#20)]
 [!code-vb[PLINQ#20](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#20)]  
  
 Nesse caso, é melhor paralelizar somente a fonte de dados externa (clientes), a menos que uma ou mais das seguintes condições se aplicam:  
  
-   A fonte de dados interna (cust. Pedidos) é conhecido por ser muito longos.  
  
-   Você está executando uma computação cara em cada pedido. (A operação mostrada no exemplo não é cara).  
  
-   O sistema de destino é conhecido por ter processadores suficientes para controlar o número de threads que será produzido pela paralelizar a consulta em `cust.Orders`.  
  
 Em todos os casos, a melhor maneira de determinar a forma de consulta ideal é testar e medidas. Para obter mais informações, consulte [como: desempenho de consulta PLINQ medida](../../../docs/standard/parallel-programming/how-to-measure-plinq-query-performance.md).  
  
## <a name="avoid-calls-to-non-thread-safe-methods"></a>Evite chamadas para métodos de Non-Thread-Safe  
 Gravar em métodos de instância non-thread-safe de um PLINQ consulta pode levar à corrupção de dados que podem ou não pode ser detectados em seu programa. Isso também poderá resultar em exceções. No exemplo a seguir, vários threads é tentar chamar o `Filestream.Write` método simultaneamente, que não é compatível com a classe.  
  
```vb  
Dim fs As FileStream = File.OpenWrite(…)  
a.Where(...).OrderBy(...).Select(...).ForAll(Sub(x) fs.Write(x))  
```  
  
```csharp  
FileStream fs = File.OpenWrite(...);  
a.Where(...).OrderBy(...).Select(...).ForAll(x => fs.Write(x));  
```  
  
## <a name="limit-calls-to-thread-safe-methods"></a>Limite de chamadas para métodos de Thread-Safe  
 Os métodos mais estáticos no .NET Framework são thread-safe e podem ser chamados de vários threads simultaneamente. No entanto, até mesmo nesses casos, a sincronização envolvidos pode levar a diminuição significativa na consulta.  
  
> [!NOTE]
>  Você pode testar isso por conta própria, inserindo algumas chamadas para <xref:System.Console.WriteLine%2A> em suas consultas. Embora esse método é usado nos exemplos a documentação para fins de demonstração, não a use em consultas PLINQ.  
  
## <a name="avoid-unnecessary-ordering-operations"></a>Evite operações de classificação desnecessária  
 Quando o PLINQ executa uma consulta em paralelo, divide a sequência de origem em partições que podem ser operadas simultaneamente em vários threads. Por padrão, a ordem na qual as partições são processadas e os resultados são fornecidos não é previsível (exceto para operadores como `OrderBy`). Você pode instruir o PLINQ para preservar a ordenação de qualquer sequência de origem, mas isso tem um impacto negativo no desempenho. A prática recomendada, sempre que possível, é estruturar consultas para que eles não confiam na preservação da ordem. Para saber mais, veja [Preservação da ordem em PLINQ](../../../docs/standard/parallel-programming/order-preservation-in-plinq.md).  
  
## <a name="prefer-forall-to-foreach-when-it-is-possible"></a>Preferir ForAll ForEach quando é possível  
 Embora o PLINQ executa uma consulta em vários threads, se você consumir os resultados em uma `foreach` loop (`For Each` no Visual Basic), em seguida, os resultados da consulta devem ser mesclados novamente em um thread e acessados em série pelo enumerador. Em alguns casos, isso é inevitável; No entanto, sempre que possível, use o `ForAll` método para habilitar cada thread gerar seus próprio resultados, por exemplo, gravando em uma coleção thread-safe, como <xref:System.Collections.Concurrent.ConcurrentBag%601?displayProperty=nameWithType>.  
  
 O mesmo problema se aplica a <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> em outras palavras, `source.AsParallel().Where().ForAll(...)` devem ser fortemente preferidos para  
  
 `Parallel.ForEach(source.AsParallel().Where(), ...)`.  
  
## <a name="be-aware-of-thread-affinity-issues"></a>Estar ciente das questões de afinidade de Thread  
 Algumas tecnologias, por exemplo, a interoperabilidade COM para componentes de Single-Threaded Apartment (STA), formulários do Windows e Windows Presentation Foundation (WPF), impõem restrições de afinidade de thread que exigem o código para executar em um thread específico. Por exemplo, no Windows Forms e WPF, um controle só pode ser acessado no thread no qual ele foi criado. Se você tentar acessar o estado compartilhado de um controle de formulários do Windows em uma consulta PLINQ, uma exceção é gerada se você estiver executando o depurador. (Essa configuração pode ter sido desligado). No entanto, se sua consulta é consumida no thread da interface do usuário, em seguida, você pode acessar o controle do `foreach` loop que enumera a consulta resultante porque esse código é executado em apenas um thread.  
  
## <a name="do-not-assume-that-iterations-of-foreach-for-and-forall-always-execute-in-parallel"></a>Não suponha que iterações de ForEach, para e ForAll sempre executar em paralelo  
 É importante ter em mente que iterações individuais em um <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> ou <xref:System.Linq.ParallelEnumerable.ForAll%2A> pode executar um loop, mas não é necessário que executar em paralelo. Portanto, você deve evitar gravar qualquer código que depende de correção de execução paralela de iterações ou na execução de iterações em nenhuma ordem específica.  
  
 Por exemplo, esse código é provavelmente um deadlock:  
  
```vb  
Dim mre = New ManualResetEventSlim()  
    Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll(Sub(j)   
  
                                                     If j = Environment.ProcessorCount Then  
  
                                                         Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Set()  
  
                                                     Else  
  
                                                         Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j)  
                                                         mre.Wait()  
                                                     End If  
    End Sub) ' deadlocks  
```  
  
```csharp  
ManualResetEventSlim mre = new ManualResetEventSlim();  
            Enumerable.Range(0, ProcessorCount * 100).AsParallel().ForAll((j) =>  
            {  
                if (j == Environment.ProcessorCount)  
                {  
                    Console.WriteLine("Set on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Set();  
                }  
                else  
                {  
                    Console.WriteLine("Waiting on {0} with value of {1}", Thread.CurrentThread.ManagedThreadId, j);  
                    mre.Wait();  
                }  
            }); //deadlocks  
```  
  
 Neste exemplo, uma iteração define um evento, e todas as outras iterações esperar o evento. Nenhuma das iterações espera pode concluir até que a iteração de configuração de evento foi concluída. No entanto, é possível que as iterações espera bloqueiam todos os threads que são usados para executar o loop paralelo, antes da iteração de configuração de evento teve a chance de executar. Isso resulta em um deadlock – a iteração de configuração de evento nunca será executado e as iterações espera nunca serão ativada.  
  
 Em particular, uma iteração de um loop paralelo nunca deve aguardar outra iteração do loop para tornar o progresso. Se o loop paralelo decidir agendar as iterações sequencialmente, mas em ordem oposta, ocorrerá um deadlock.  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
