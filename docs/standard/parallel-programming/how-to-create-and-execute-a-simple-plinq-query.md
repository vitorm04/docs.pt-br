---
title: Como criar e executar uma consulta PLINQ simples
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to create
ms.assetid: 983b4213-bddd-4a44-9262-cbe59186df4c
ms.openlocfilehash: 349cc8d78e9a080d720e09a7e3e5e314752605c7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "73106953"
---
# <a name="how-to-create-and-execute-a-simple-plinq-query"></a>Como criar e executar uma consulta PLINQ simples
O exemplo a seguir mostra como criar uma consulta Parallel LINQ simples usando o método de extensão <xref:System.Linq.ParallelEnumerable.AsParallel%2A> na sequência de origem e executando a consulta usando o método <xref:System.Linq.ParallelEnumerable.ForAll%2A>.  
  
> [!NOTE]
> Esta documentação usa expressões lambda para definir representantes na PLINQ. Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [Expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PLINQ#11](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/create1.cs#11)]
 [!code-vb[PLINQ#11](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/create1.vb#11)]  
  
 Este exemplo demonstra o padrão básico para criar e executar qualquer consulta Parallel LINQ quando a ordenação da sequência de resultado não é importante. Geralmente, as consultas não ordenadas são mais rápidas que as ordenadas. A consulta particiona a origem em tarefas executadas de maneira assíncrona em vários threads. A ordem em que cada tarefa é concluída depende não apenas da quantidade de trabalho envolvido para processar os elementos na partição, mas também de fatores externos como a maneira que o sistema operacional agenda cada thread. Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md). Para saber mais sobre como preservar a ordenação de elementos em uma consulta, consulte [Como controlar a ordem em uma consulta PLINQ](../../../docs/standard/parallel-programming/how-to-control-ordering-in-a-plinq-query.md).  
  
## <a name="see-also"></a>Confira também

- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
