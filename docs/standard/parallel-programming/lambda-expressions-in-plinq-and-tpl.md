---
title: "Expressões lambda em PLINQ e TPL"
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
- Func delegate, creating with lambda expression
- Action delegate, creating with lambda expression
- lambda expressions, with Action and Func
ms.assetid: 645b2c17-29d0-4ffa-8684-430743cc2f2d
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 79ab0f4427e0f37259f88cd3ec0762d1582481f1
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="lambda-expressions-in-plinq-and-tpl"></a>Expressões lambda em PLINQ e TPL
O biblioteca paralela de tarefas (TPL) contém vários métodos que usam uma da <xref:System.Func%601?displayProperty=nameWithType> ou <xref:System.Action?displayProperty=nameWithType> família de delegados como parâmetros de entrada. Você pode usar esses delegados para transmitir sua lógica de programa personalizado para o loop paralelo, a tarefa ou a consulta. Os exemplos de código para TPL, bem como o PLINQ usam expressões lambda para criar instâncias desses representantes como blocos de código embutido. Este tópico fornece uma breve introdução ao Func e Action e mostra como usar expressões lambda no PLINQ e biblioteca paralela de tarefas.  
  
 **Observação** para obter mais informações sobre delegados em geral, consulte [delegados](../../csharp/programming-guide/delegates/index.md) e [delegados](../../visual-basic/programming-guide/language-features/delegates/index.md). Para obter mais informações sobre expressões lambda em c# e [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)], consulte [expressões Lambda](~/docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) e [expressões Lambda](~/docs/visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
## <a name="func-delegate"></a>Delegado de função  
 Um `Func` delegado encapsula um método que retorna um valor. Em uma assinatura de função, o parâmetro de tipo do último ou mais à direita sempre Especifica o tipo de retorno. Uma causa comum de erros do compilador é tentar passar dois parâmetros de entrada para um <xref:System.Func%602?displayProperty=nameWithType>; na verdade, esse tipo usa somente um parâmetro de entrada. A biblioteca de classes do Framework define 17 versões do `Func`: <xref:System.Func%601?displayProperty=nameWithType>, <xref:System.Func%602?displayProperty=nameWithType>, <xref:System.Func%603?displayProperty=nameWithType>, e assim por diante até por meio de <xref:System.Func%6017?displayProperty=nameWithType>.  
  
## <a name="action-delegate"></a>Delegado de ação  
 Um <xref:System.Action?displayProperty=nameWithType> delegado encapsula um método (Sub no [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) que não retorna um valor ou retorna [void](~/docs/csharp/language-reference/keywords/void.md). Uma assinatura de tipo de ação, os parâmetros de tipo representam apenas os parâmetros de entrada. Como Func, a biblioteca de classes do Framework define 17 versões de ação, de uma versão que não tem nenhum parâmetro de tipo por meio de uma versão que tenha 16 parâmetros de tipo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir para o <xref:System.Threading.Tasks.Parallel.ForEach%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%601%7D%2CSystem.Func%7B%60%600%2CSystem.Threading.Tasks.ParallelLoopState%2C%60%601%2C%60%601%7D%2CSystem.Action%7B%60%601%7D%29?displayProperty=nameWithType> método mostra como express delegados Func e Action usando expressões lambda.  
  
 [!code-csharp[System.Threading.Tasks.Parallel#02](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.threading.tasks.parallel/cs/parallelforeach.cs#02)]
 [!code-vb[System.Threading.Tasks.Parallel#02](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.threading.tasks.parallel/vb/parallelforeach.vb#02)]  
  
## <a name="see-also"></a>Consulte também  
 [Programação paralela](../../../docs/standard/parallel-programming/index.md)
