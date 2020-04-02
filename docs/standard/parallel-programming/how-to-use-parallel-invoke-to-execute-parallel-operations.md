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
ms.openlocfilehash: 7189c478e132a41971a364b833f0fabda6ff84d4
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588405"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Como usar Parallel.Invoke para executar operações em paralelo

Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas. Três operações são executadas em uma fonte de dados compartilhada. Como nenhuma das operações modifica a fonte, elas podem ser executadas em paralelo de uma maneira simples.

> [!NOTE]
> Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [Expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Exemplo

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Observe que, com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressa quais ações quer executar simultaneamente, e o runtime trata todos os detalhes de agendamento do thread, incluindo o dimensionamento automaticamente para o número de núcleos no computador host.

Este exemplo paraleliza as operações, não os dados. Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência. Como alternativa, você poderia paralelizar os dados usando o PLINQ. Outra opção é paralelizar as consultas e as tarefas. Embora a sobrecarga resultante possa degradar o desempenho em computadores de host com poucos processadores, ela será dimensionada muito melhor em computadores com vários processadores.

## <a name="compile-the-code"></a>Compile o código

Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio e pressione **F5**.

## <a name="see-also"></a>Confira também

- [Programação Paralela](../../../docs/standard/parallel-programming/index.md)
- [Como cancelar uma tarefa e seus filhos](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
