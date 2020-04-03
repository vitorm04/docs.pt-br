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
ms.openlocfilehash: f61bbf10bbeef736f66710f50e621c3619355a1d
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635798"
---
# <a name="how-to-use-parallelinvoke-to-execute-parallel-operations"></a>Como usar Parallel.Invoke para executar operações em paralelo

Este exemplo mostra como paralelizar operações usando <xref:System.Threading.Tasks.Parallel.Invoke%2A> na Biblioteca de paralelismo de tarefas. Três operações são executadas em uma fonte de dados compartilhada. As operações podem ser executadas em paralelo de forma direta, porque nenhuma delas modifica a fonte.

> [!NOTE]
> Esta documentação usa expressões lambda para definir delegados na TLP. Se você não estiver familiarizado com expressões lambda em C# ou Visual Basic, consulte [Expressões Lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md).

## <a name="example"></a>Exemplo

[!code-csharp[TPL_Parallel#06](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_parallel/cs/parallelinvoke.cs#06)]
[!code-vb[TPL_Parallel#06](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_parallel/vb/parallelinvoke.vb#06)]

Com <xref:System.Threading.Tasks.Parallel.Invoke%2A>, você simplesmente expressa quais ações deseja executar simultaneamente, e o tempo de execução lida com todos os detalhes de agendamento de thread, incluindo o dimensionamento automático para o número de núcleos no computador host.

Este exemplo paraleliza as operações, não os dados. Como uma abordagem alternativa, você pode paralelizar as consultas do LINQ usando PLINQ e executar as consultas em sequência. Como alternativa, você poderia paralelizar os dados usando o PLINQ. Outra opção é paralelizar as consultas e as tarefas. Embora a sobrecarga resultante possa degradar o desempenho em computadores host com relativamente poucos processadores, ele escala melhor em computadores com muitos processadores.

## <a name="compile-the-code"></a>Compile o código

Copie e cole o exemplo inteiro em um projeto do Microsoft Visual Studio e pressione **F5**.

## <a name="see-also"></a>Confira também

- [Programação Paralela](../../../docs/standard/parallel-programming/index.md)
- [Como cancelar uma tarefa e seus filhos](../../../docs/standard/parallel-programming/how-to-cancel-a-task-and-its-children.md)
- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
