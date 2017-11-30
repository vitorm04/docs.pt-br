---
title: "Opções de mesclagem em PLINQ"
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
helpviewer_keywords: PLINQ queries, merge options
ms.assetid: e8f7be3b-88de-4f33-ab14-dc008e76c1ba
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e9bf586c1805fc5b5f1cc5f96f4e6b08d80c199a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="merge-options-in-plinq"></a>Opções de mesclagem em PLINQ
Quando uma consulta está em execução como partições PLINQ paralelas, a sequência de origem para que vários threads podem trabalhar em diferentes partes simultaneamente, normalmente em threads separados. Se os resultados devem ser consumidos em um thread, por exemplo, em um `foreach` (`For Each` em [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) loop, em seguida, os resultados de cada segmento devem ser mesclados novamente em uma sequência. O tipo de mesclagem PLINQ executa depende dos operadores que estão presentes na consulta. Por exemplo, os operadores que impõem um novo pedido nos resultados devem buffer todos os elementos de todos os threads. Da perspectiva do thread de consumo (que também é que o usuário do aplicativo) uma consulta com buffer completo pode ser executado por um período significativo de tempo antes que ele produz o primeiro resultado. Outros operadores, por padrão, são parcialmente armazenada em buffer; eles geram seus resultados em lotes. Um operador, <xref:System.Linq.ParallelEnumerable.ForAll%2A> não armazenado em buffer por padrão. Ele gera todos os elementos de todos os threads imediatamente.  
  
 Usando o <xref:System.Linq.ParallelEnumerable.WithMergeOptions%2A> método, conforme mostrado no exemplo a seguir, você pode fornecer uma dica ao PLINQ que indica o tipo de mesclagem para executar.  
  
 [!code-csharp[PLINQ#26](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#26)]
 [!code-vb[PLINQ#26](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinq2_vb.vb#26)]  
  
 Para o exemplo completo, consulte [como: especificar opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md).  
  
 Se a consulta em questão não oferecer suporte a opção solicitada, a opção apenas será ignorada. Na maioria dos casos, você não precisa especificar uma opção de mesclagem para uma consulta PLINQ. No entanto, em alguns casos você pode achar Testando e medida que uma consulta é melhor executada em um modo diferente do padrão. Um uso comum dessa opção é forçar um operador de mesclagem de bloco para transmitir os resultados para fornecer uma interface de usuário mais ágil na resposta.  
  
## <a name="parallelmergeoptions"></a>ParallelMergeOptions  
 O <xref:System.Linq.ParallelMergeOptions> enumeração inclui as seguintes opções que especificam para formas de consulta com suporte, como a saída final da consulta é produzida quando os resultados são consumidos em um thread:  
  
-   `Not Buffered`  
  
     O <xref:System.Linq.ParallelMergeOptions.NotBuffered> opção faz com que cada elemento processado a ser retornado de cada thread assim que é produzida. Esse comportamento é semelhante a "transmissão" a saída. Se o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operador está presente na consulta, `NotBuffered` preserva a ordem dos elementos de origem. Embora `NotBuffered` inicia produzir resultados assim que estiverem disponíveis, o tempo total para gerar todos os resultados a ainda podem ultrapassar usando uma das opções de mesclagem.  
  
-   `Auto Buffered`  
  
     O <xref:System.Linq.ParallelMergeOptions.AutoBuffered> opção faz com que a consulta coletar os elementos em um buffer e, em seguida, gerar periodicamente o conteúdo do buffer de uma vez para o thread de consumo. Isso equivale a gerando os dados de origem de "partes" em vez de usar o comportamento "fluxo" de `NotBuffered`. `AutoBuffered`pode demorar mais do que `NotBuffered` para disponibilizar o primeiro elemento no thread de consumo. O tamanho do buffer e o comportamento de resultado exato não são configurável e podem variar, dependendo de vários fatores relacionados à consulta.  
  
-   `FullyBuffered`  
  
     O <xref:System.Linq.ParallelMergeOptions.FullyBuffered> opção faz com que a saída de toda a consulta a ser armazenado em buffer antes de qualquer um dos elementos são gerou. Quando você usar essa opção, pode levar mais tempo antes do primeiro elemento está disponível no thread de consumo, mas os resultados completos ainda podem ser produzidos mais rápido do que usando as outras opções.  
  
## <a name="query-operators-that-support-merge-options"></a>Operadores de consulta que dão suporte a opções de mesclagem  
 A tabela a seguir lista os operadores que dão suporte a todos os modos de opção de mesclagem, sujeito as restrições especificadas.  
  
|Operador|Restrições|  
|--------------|------------------|  
|<xref:System.Linq.ParallelEnumerable.AsEnumerable%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.Cast%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.Concat%2A>|Consultas não ordenado que têm apenas uma fonte de matriz ou lista.|  
|<xref:System.Linq.ParallelEnumerable.DefaultIfEmpty%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.OfType%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.Reverse%2A>|Consultas não ordenado que têm apenas uma fonte de matriz ou lista.|  
|<xref:System.Linq.ParallelEnumerable.Select%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.SelectMany%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.Skip%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.Take%2A>|Nenhum|  
|<xref:System.Linq.ParallelEnumerable.Where%2A>|Nenhum|  
  
 Todos os outros operadores de consulta PLINQ poderá ignorar opções de mesclagem fornecido pelo usuário. Alguns operadores de consulta, por exemplo, <xref:System.Linq.ParallelEnumerable.Reverse%2A> e <xref:System.Linq.ParallelEnumerable.OrderBy%2A>, não é possível gerar todos os elementos até que todos os produzido e reordenados. Portanto, quando <xref:System.Linq.ParallelMergeOptions> é usado em uma consulta que também contém um operador, como <xref:System.Linq.ParallelEnumerable.Reverse%2A>, o comportamento de mesclagem não será aplicado na consulta até depois que esse operador produziu seus resultados.  
  
 A capacidade de alguns operadores para lidar com as opções de mesclagem depende do tipo da sequência de origem e se o <xref:System.Linq.ParallelEnumerable.AsOrdered%2A> operador foi usado anteriormente na consulta. <xref:System.Linq.ParallelEnumerable.ForAll%2A>é sempre <xref:System.Linq.ParallelMergeOptions.NotBuffered> ; esse processo resulta em seus elementos imediatamente. <xref:System.Linq.ParallelEnumerable.OrderBy%2A>é sempre <xref:System.Linq.ParallelMergeOptions.FullyBuffered>; ele deve classificar a lista inteira antes que ele produz.  
  
## <a name="see-also"></a>Consulte também  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Como especificar opções de mesclagem em PLINQ](../../../docs/standard/parallel-programming/how-to-specify-merge-options-in-plinq.md)
