---
title: Como escrever um loop arallel.ForEach simples
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
helpviewer_keywords:
- foreach, parallel version
- parallel programming, foreach
ms.assetid: cb5fab92-1c19-499e-ae91-8b7525dd875f
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 16d8cd3c3c01c2f9d83786e78f0eb1c45a38a49b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-a-simple-parallelforeach-loop"></a>Como escrever um loop arallel.ForEach simples
Este exemplo mostra como usar um <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> loop para permitir o paralelismo de dados em relação a qualquer <xref:System.Collections.IEnumerable?displayProperty=nameWithType> ou <xref:System.Collections.Generic.IEnumerable%601?displayProperty=nameWithType> fonte de dados.  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir representantes na PLINQ. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL_Parallel#03](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/simpleforeach.cs#03)]
 [!code-vb[TPL_Parallel#03](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/simpleforeach.vb#03)]  
  
 Um <xref:System.Threading.Tasks.Parallel.ForEach%2A> loop funciona como um <xref:System.Threading.Tasks.Parallel.For%2A> loop. A coleção de origem está particionada e o trabalho agendado em vários segmentos, com base no ambiente do sistema. Quanto mais processadores no sistema, é executado mais rápido do método paralelo. Para alguns conjuntos de origem, um loop sequencial pode ser mais rápido, dependendo do tamanho de origem e o tipo de trabalho que está sendo executado. Para obter mais informações sobre o desempenho, consulte [armadilhas em potencial em dados e paralelismo da tarefa](../../../docs/standard/parallel-programming/potential-pitfalls-in-data-and-task-parallelism.md)  
  
 Para obter mais informações sobre loops paralelos, consulte [como: gravar um Loop Parallel. for simples](../../../docs/standard/parallel-programming/how-to-write-a-simple-parallel-for-loop.md).  
  
 Para usar <xref:System.Threading.Tasks.Parallel.ForEach%2A> com uma coleção não genérica, você pode usar o <xref:System.Linq.Enumerable.Cast%2A> método de extensão para converter a coleção para uma coleção genérica, conforme mostrado no exemplo a seguir:  
  
 [!code-csharp[TPL_Parallel#07](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/nongeneric.cs#07)]
 [!code-vb[TPL_Parallel#07](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/nongeneric.vb#07)]  
  
 Você também pode usar o LINQ paralelo (PLINQ) para efetuar a paralelização de processamento de <xref:System.Collections.Generic.IEnumerable%601> fontes de dados. PLINQ permite que você use a sintaxe de consulta declarativa para expressar o comportamento de loop. Para obter mais informações, consulte [PLINQ (Parallel LINQ)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md).  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Copie e cole este código em um [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] 2010 projeto de aplicativo de Console.  
  
-   Adicione uma referência ao System.Drawing.dll  
  
-   Pressione F5  
  
## <a name="see-also"></a>Consulte também  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
