---
title: "Como usar Parallel.Invoke para executar operações em paralelo"
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
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
caps.latest.revision: "22"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 8a51f180a394c1baa2ecb0620279ea15c62e1edc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Como usar Parallel.Invoke para executar operações em paralelo
Este exemplo mostra como a paralelização de operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na biblioteca de tarefas paralelas. Três operações são executadas em uma fonte de dados compartilhada. Como nenhuma das operações de modificar a fonte, eles podem ser executados em paralelo de uma maneira simples.  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Observe que, com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressar quais ações você deseja executar simultaneamente e o tempo de execução trata todos os threads agendamento detalhes, incluindo dimensionamento automaticamente para o número de núcleos no computador host.  
  
 Este exemplo parallelizes as operações, não os dados. Como uma abordagem alternativa, você pode paralelizar consultas LINQ usando PLINQ e executar as consultas em sequência. Como alternativa, você poderia paralelizar os dados usando o PLINQ. Outra opção é paralelizar as consultas e as tarefas. Embora resultante sobrecarga pode degradar o desempenho em computadores de host com processadores relativamente poucas, ele será dimensionado muito melhor em computadores com vários processadores.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio 2010 e pressione F5.  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [Como cancelar uma tarefa e seus filhos](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
