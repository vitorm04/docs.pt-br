---
title: Particionadores personalizados para PLINQ e TPL
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
helpviewer_keywords: tasks, partitioners
ms.assetid: 96153688-9a01-47c4-8430-909cee9a2887
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12d234b86b0067178d54d2fdcb5d37ceaee6109d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="custom-partitioners-for-plinq-and-tpl"></a>Particionadores personalizados para PLINQ e TPL
Para paralelizar a uma operação em uma fonte de dados, uma das etapas essenciais é *partição* a fonte em várias seções que podem ser acessadas simultaneamente por vários threads. PLINQ e o biblioteca paralela de tarefas (TPL) fornecem particionadores padrão que funcionam de forma transparente quando você escreve uma consulta paralela ou <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop. Para cenários mais avançados, você pode conectar seu próprios particionador.  
  
## <a name="kinds-of-partitioning"></a>Tipos de particionamento  
 Há muitas maneiras de uma fonte de dados de partição. As abordagens mais eficiente, vários threads cooperam para processo de sequência de origem original, em vez de separar fisicamente a fonte em várias subsequências. Para matrizes e outras fontes indexadas como <xref:System.Collections.IList> coleções onde o tamanho é conhecido com antecedência, *o particionamento range* é o tipo mais simples de particionamento. Cada thread recebe exclusivo de abertura e fechamento índices, para que ele possa processar seu intervalo de origem sem substituição ou que está sendo substituído por qualquer outro thread. Somente sobrecarga envolvida no intervalo de particionamento é um trabalho inicial de criação de intervalos; Nenhuma sincronização adicional é necessária depois disso. Portanto, ele pode fornecer bom desempenho, desde que a carga de trabalho é dividida igualmente. Uma desvantagem de particionamento de intervalo é que se um thread termina no início, ele não pode ajudar os outros threads concluir seu trabalho.  
  
 Para listas vinculadas ou outras coleções cujo comprimento não é conhecido, você pode usar *parte particionamento*. Na parte de particionamento, cada thread ou tarefa em uma consulta ou um loop paralelo consome um número de elementos de origem em um bloco, processa-os e volta para recuperar os elementos adicionais. O particionador garante que todos os elementos são distribuídos e que não há nenhuma duplicata. Uma parte pode ser de qualquer tamanho. Por exemplo, o que é demonstrado particionador [como: implementar as partições dinâmicas](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md) cria blocos que contêm apenas um elemento. Como as partes não são muito grandes, esse tipo de particionamento é inerentemente balanceamento de carga porque a atribuição de elementos threads não é predeterminada. No entanto, o particionador sobrecarregar a sincronização sempre que o thread precisa obter outro bloco. A quantidade de sincronização incorrida nesses casos é inversamente proporcional ao tamanho das partes.  
  
 Em geral, a partição de intervalo só é mais rápido quando o tempo de execução do representante é pequeno a médio e a origem tem um grande número de elementos e o trabalho total de cada partição é aproximadamente equivalente. Particionamento de bloco, portanto, é geralmente mais rápido na maioria dos casos. Em fontes com um pequeno número de elementos ou tempos de execução do representante, em seguida, o desempenho de bloco e particionamento de intervalo é sobre igual.  
  
 Particionadores a TPL também oferecem suporte a um número dinâmico de partições. Isso significa que eles podem criar partições em interrupções, por exemplo, quando o <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop gera uma nova tarefa. Esse recurso permite que o particionador dimensionar junto com o próprio loop. Particionadores dinâmicos também são inerentemente balanceamento de carga. Quando você criar um particionador personalizado, você deve dar suporte o particionamento dinâmico para ser consumível a partir de um <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop.  
  
### <a name="configuring-load-balancing-partitioners-for-plinq"></a>Configurando Particionadores para PLINQ de balanceamento de carga  
 Algumas sobrecargas do <xref:System.Collections.Concurrent.Partitioner.Create%2A?displayProperty=nameWithType> método permitem que você criar um particionador para uma matriz ou <xref:System.Collections.IList> de origem e especificar se ele deve tentar equilibrar a carga de trabalho entre os threads. Quando o particionador está configurado para balanceamento de carga, o particionamento de parte é usado e os elementos são enviados para cada partição em pequenas partes conforme forem solicitados. Essa abordagem ajuda a garantir que todas as partições têm elementos para processar até que o loop inteiro ou consulta é concluída. Uma sobrecarga adicional pode ser usada para fornecer balanceamento de carga de particionamento de qualquer <xref:System.Collections.IEnumerable> fonte.  
  
 Em geral, o balanceamento de carga requer as partições para solicitar elementos relativamente com frequência do que o particionador. Por outro lado, um particionador que faz o particionamento estático pode atribuir os elementos a cada particionador todos de uma vez usando o intervalo ou bloco de particionamento. Isso requer menos sobrecarga de balanceamento de carga, mas pode levar mais tempo para ser executado se um thread pode acabar com significativamente mais trabalho do que os outros. Por padrão quando ele é passado IList ou uma matriz, PLINQ sempre usa o particionamento range sem balanceamento de carga. Para habilitar o balanceamento de carga para PLINQ, use o `Partitioner.Create` método, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[TPL_Partitioners#02](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioners.cs#02)]
 [!code-vb[TPL_Partitioners#02](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionsnippets_vb.vb#02)]  
  
 A melhor maneira de determinar se usar carga balanceamento em qualquer determinado cenário é testá-las e medir o tempo de operações sejam concluídas em cargas de representante e configurações do computador. Por exemplo, particionamento estático pode fornecer aumento de velocidade significativo em um computador com vários núcleo que tem apenas alguns núcleos, mas pode resultar em lentidão em computadores que têm relativamente muitos núcleos.  
  
 A tabela a seguir lista as sobrecargas disponíveis do <xref:System.Collections.Concurrent.Partitioner.Create%2A> método. Essas particionadores não estão limitados a usar somente com PLINQ ou <xref:System.Threading.Tasks.Task>. Eles também podem ser usados com qualquer construção paralela personalizada.  
  
|Sobrecarga|Usa o balanceamento de carga|  
|--------------|-------------------------|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>|Sempre|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28%60%600%5B%5D%2CSystem.Boolean%29>|Quando o argumento booleano é especificado como true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%60%601%28System.Collections.Generic.IList%7B%60%600%7D%2CSystem.Boolean%29>|Quando o argumento booleano é especificado como true|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%29>|Nunca|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int32%2CSystem.Int32%2CSystem.Int32%29>|Nunca|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%29>|Nunca|  
|<xref:System.Collections.Concurrent.Partitioner.Create%28System.Int64%2CSystem.Int64%2CSystem.Int64%29>|Nunca|  
  
### <a name="configuring-static-range-partitioners-for-parallelforeach"></a>Configurando intervalo estático Particionadores para Parallel. ForEach  
 Em um <xref:System.Threading.Tasks.Parallel.For%2A> loop, o corpo do loop é fornecido para o método como um representante. O custo de invocar esse delegado é quase o mesmo que uma chamada de método virtual. Em alguns cenários, o corpo de um loop paralelo pode ser pequeno o suficiente para que o custo da invocação do delegado em cada iteração do loop se tornar significativo. Em tais situações, você pode usar uma da <xref:System.Collections.Concurrent.Partitioner.Create%2A> sobrecargas para criar um <xref:System.Collections.Generic.IEnumerable%601> de partições de intervalo sobre os elementos de origem. Em seguida, você pode passar essa coleção de intervalos para uma <xref:System.Threading.Tasks.Parallel.ForEach%2A> cujo corpo consiste em uma expressão de método `for` loop. A vantagem dessa abordagem é que o custo de invocação do delegado é incorrido apenas uma vez por intervalo, em vez de uma vez por elemento. O exemplo a seguir demonstra o padrão básico.  
  
 [!code-csharp[TPL_Partitioners#01](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_partitioners/cs/partitioner01.cs#01)]
 [!code-vb[TPL_Partitioners#01](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_partitioners/vb/partitionercreate01.vb#01)]  
  
 Cada thread no loop recebe seu próprio <xref:System.Tuple%602> que contém os valores inicial e final índice no intervalo especificado de subtipo. Interna `for` loop usa o `fromInclusive` e `toExclusive` valores para executar um loop sobre a matriz ou o <xref:System.Collections.IList> diretamente.  
  
 Uma da <xref:System.Collections.Concurrent.Partitioner.Create%2A> sobrecargas lhe permite especificar o tamanho de partições e o número de partições. Essa sobrecarga pode ser usada em cenários em que o trabalho por elemento é tão baixo que até mesmo um método virtual chamada por elemento tem um impacto significativo no desempenho.  
  
## <a name="custom-partitioners"></a>Particionadores Personalizados  
 Em alguns cenários, talvez seja útil ou até mesmo necessárias para implementar seu próprio particionador. Por exemplo, você pode ter uma classe de coleção personalizada que você pode particionar de forma mais eficiente que o padrão particionadores pode, com base em seu conhecimento sobre a estrutura interna da classe. Ou, você talvez queira criar partições de intervalo de tamanhos variados com base no seu conhecimento de quanto tempo levará para elementos do processo em locais diferentes na coleção de origem.  
  
 Para criar um particionador personalizado básico, derive uma classe de <xref:System.Collections.Concurrent.Partitioner%601?displayProperty=nameWithType> e substituir os métodos virtuais, conforme descrito na tabela a seguir.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>|Este método é chamado uma vez pelo thread principal e retorna um IList(IEnumerator(TSource)). Cada thread de trabalho na consulta ou de loop pode chamar `GetEnumerator` na lista para recuperar um <xref:System.Collections.Generic.IEnumerator%601> uma partição distintos.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retornar `true` se você implementar <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, caso contrário, `false`.|  
|<xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>|Se <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> é `true`, esse método pode ser chamado, opcionalmente, em vez de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 Se os resultados devem ser classificáveis ou exigem acesso indexado nos elementos, em seguida, derive de <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> e substituir seus métodos virtuais, conforme descrito na tabela a seguir.  
  
|||  
|-|-|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetPartitions%2A>|Este método é chamado uma vez pelo thread principal e retorna um `IList(IEnumerator(TSource))`. Cada thread de trabalho na consulta ou de loop pode chamar `GetEnumerator` na lista para recuperar um <xref:System.Collections.Generic.IEnumerator%601> uma partição distintos.|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retornar `true` se você implementar <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>; caso contrário, false.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetDynamicPartitions%2A>|Normalmente, isso apenas chama <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A>|Se <xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A> é `true`, esse método pode ser chamado, opcionalmente, em vez de <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>.|  
  
 A tabela a seguir fornece detalhes adicionais sobre como os três tipos de balanceamento de carga particionadores implementar o <xref:System.Collections.Concurrent.OrderablePartitioner%601> classe.  
  
|Método/propriedade|IList / matriz sem balanceamento de carga|IList / matriz com balanceamento de carga|IEnumerable|  
|----------------------|-------------------------------------------|----------------------------------------|-----------------|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>|Usa o particionamento range|Usa a parte particionamento otimizado para listas para o partitionCount especificado|Usa parte particionamento por meio da criação de um número estático de partições.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A?displayProperty=nameWithType>|Exceção lança não suportada|Usa a parte particionamento otimizado para listas e partições dinâmicas|Usa parte particionamento por meio da criação de um número dinâmico de partições.|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedInEachPartition%2A>|Retorna `true`|Retorna `true`|Retorna `true`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysOrderedAcrossPartitions%2A>|Retorna `true`|Retorna `false`|Retorna `false`|  
|<xref:System.Collections.Concurrent.OrderablePartitioner%601.KeysNormalized%2A>|Retorna `true`|Retorna `true`|Retorna `true`|  
|<xref:System.Collections.Concurrent.Partitioner%601.SupportsDynamicPartitions%2A>|Retorna `false`|Retorna `true`|Retorna `true`|  
  
### <a name="dynamic-partitions"></a>Partições dinâmicas  
 Se você pretende particionador para ser usado em um <xref:System.Threading.Tasks.Parallel.ForEach%2A> método, você deve ser capaz de retornar um número dinâmico de partições. Isso significa que o particionador pode fornecer um enumerador para uma nova partição sob demanda a qualquer momento durante a execução do loop. Basicamente, sempre que o loop adiciona uma nova tarefa paralela, ele solicitará uma nova partição para a tarefa. Se você precisar de dados para ser solicitado, em seguida, derivam <xref:System.Collections.Concurrent.OrderablePartitioner%601?displayProperty=nameWithType> para que cada item em cada partição é atribuído a um índice exclusivo.  
  
 Para obter mais informações e um exemplo, consulte [como: implementar as partições dinâmicas](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md).  
  
### <a name="contract-for-partitioners"></a>Contrato para Particionadores  
 Ao implementar um particionador personalizado, siga estas diretrizes para ajudar a garantir a interação correta com PLINQ e <xref:System.Threading.Tasks.Parallel.ForEach%2A> na TPL:  
  
-   Se <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A> é chamado com um argumento de zero ou menos para `partitionsCount`, gerar <xref:System.ArgumentOutOfRangeException>. Embora o PLINQ e TPL nunca passará um `partitionCount` igual a 0, mesmo assim, recomendamos que você se protege contra a possibilidade.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>e <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A> deve retornar sempre `partitionsCount` número de partições. Se o particionador fica sem dados e não é possível criar quantas partições solicitada, o método deve retornar um enumerador vazio para cada uma das partições restantes. Caso contrário, PLINQ e TPL lançará um <xref:System.InvalidOperationException>.  
  
-   <xref:System.Collections.Concurrent.Partitioner%601.GetPartitions%2A>, <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderablePartitions%2A>, <xref:System.Collections.Concurrent.Partitioner%601.GetDynamicPartitions%2A>, e <xref:System.Collections.Concurrent.OrderablePartitioner%601.GetOrderableDynamicPartitions%2A> nunca deve retornar `null` (`Nothing` no Visual Basic). Se isso ocorrer, PLINQ / TPL lançará um <xref:System.InvalidOperationException>.  
  
-   Métodos que retornam partições devem retornar sempre partições que podem totalmente e exclusivamente enumerar a fonte de dados. Não deve haver nenhuma duplicação na fonte de dados ou itens ignorados a menos que especificamente necessário para o design do particionador. Se essa regra não for efetivada, a ordem de saída pode ser embaralhada.  
  
-   As seguir getters boolianos sempre com precisão devem retornar os seguintes valores para que a ordem de saída não está embaralhada:  
  
    -   `KeysOrderedInEachPartition`: Cada partição retorna elementos com o aumento da chave índices.  
  
    -   `KeysOrderedAcrossPartitions`: Para todas as partições que são retornados, os índices de chave na partição *,* são maiores do que o índice de chave na partição *,*-1.  
  
    -   `KeysNormalized`: Todos os índices de chave são monotônica sem espaços, a partir do zero.  
  
-   Todos os índices devem ser exclusivos. Pode não haver índices duplicados. Se essa regra não for efetivada, a ordem de saída pode ser embaralhada.  
  
-   Todos os índices devem ser não negativos. Se essa regra não for efetivada, PLINQ/TPL podem ocasionar exceções.  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [Como implementar partições dinâmicas](../../../docs/standard/parallel-programming/how-to-implement-dynamic-partitions.md)  
 [Como implementar um particionador para particionamento estático](../../../docs/standard/parallel-programming/how-to-implement-a-partitioner-for-static-partitioning.md)
