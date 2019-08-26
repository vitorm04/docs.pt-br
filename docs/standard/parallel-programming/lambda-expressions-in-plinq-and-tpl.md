---
title: Expressões lambda em PLINQ e TPL
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e1487d3721694ae45b67ae3534c89cc62f513911
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666317"
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Expressões lambda em PLINQ e TPL
A TPL (Biblioteca de Paralelismo de Tarefas) contém vários métodos que usam uma das família de delegados <xref:System.Func%601?displayProperty=nameWithType> ou <xref:System.Action?displayProperty=nameWithType> como parâmetros de entrada. Você pode usar esses delegados para transmitir sua lógica de programa personalizada para o loop paralelo, tarefa ou consulta. Os exemplos de código para TPL, bem como o PLINQ, usam expressões lambda para criar instâncias desses delegados como blocos de código embutido. Este tópico fornece uma breve introdução a Func e Action, e mostra como usar expressões lambda no PLINQ e na Biblioteca de paralelismo de tarefas.  
  
 **Observação** Para saber mais sobre delegados em geral, consulte [Delegados](../../csharp/programming-guide/delegates/index.md) e [Delegados](../../visual-basic/programming-guide/language-features/delegates/index.md). Para saber mais sobre expressões lambda em C# e em Visual Basic, confira [Expressões lambda](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) e [Expressões lambda](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>Delegado Func  
 Um delegado `Func` encapsula um método que retorna um valor. Em uma assinatura Func, o último parâmetro de tipo, ou da extrema direita, sempre especifica o tipo de retorno. Uma causa comum de erros do compilador é tentar passar dois parâmetros de entrada para um <xref:System.Func%602?displayProperty=nameWithType>; na verdade, esse tipo usa somente um parâmetro de entrada. A Biblioteca de Classes do Framework define 17 versões do `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType> e assim por diante até <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Delegado Action  
 Um delegado <xref:System.Action?displayProperty=nameWithType> encapsula um método (Sub em Visual Basic) que não retorna um valor, ou que retorna [void](../../csharp/language-reference/keywords/void.md). Em uma assinatura de tipo Action, os parâmetros de tipo representam apenas os parâmetros de entrada. Assim como Func, a Biblioteca de Classes do Framework define 17 versões de Action, partindo de uma versão que não tem nenhum parâmetro de tipo até uma versão que tenha 16 parâmetros de tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir para o método <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> mostra como expressar delegados Func e Action usando expressões lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Consulte também

- [Programação paralela](../../../docs/standard/parallel-programming/index.md)
