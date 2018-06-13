---
title: Como usar Parallel.Invoke para executar operações em paralelo
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- task parallelism in .NET
- parallel programming, task parallelism
ms.assetid: 6b3ecd79-dec9-4ce1-abf4-62e5392a59c6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 4ad4b5e005ddd7bbd598a9da3032574eb2ba7dd1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33580878"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Como usar Parallel.Invoke para executar operações em paralelo
Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas. Três operações são executadas em uma fonte de dados compartilhada. Como nenhuma das operações modifica a fonte, elas podem ser executadas em paralelo de uma maneira simples.  
  
> [!NOTE]
>  Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda no C# ou no Visual Basic, veja [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
 [!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]  
  
 Observe que, com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressa quais ações quer executar simultaneamente, e o tempo de execução trata todos os detalhes de agendamento do thread, incluindo o dimensionamento automaticamente para o número de núcleos no computador host.  
  
 Este exemplo paraleliza as operações, não os dados. Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência. Como alternativa, você poderia paralelizar os dados usando o PLINQ. Outra opção é paralelizar as consultas e as tarefas. Embora a sobrecarga resultante possa degradar o desempenho em computadores de host com poucos processadores, ela será dimensionada muito melhor em computadores com vários processadores.  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio 2010 e pressione F5.  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)  
 [Como cancelar uma tarefa e seus filhos](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
