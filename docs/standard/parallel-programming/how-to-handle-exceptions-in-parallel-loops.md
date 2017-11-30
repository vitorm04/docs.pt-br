---
title: "Como manipular exceções em loops paralelos"
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
helpviewer_keywords: parallel loops, how to handle exceptions
ms.assetid: 512f0d5a-4636-4875-b766-88f20044f143
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 98e822bc148bbe5879a9ff0b7c47e9124b68e612
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-parallel-loops"></a>Como manipular exceções em loops paralelos
O <xref:System.Threading.Tasks.Parallel.For%2A?displayProperty=nameWithType> e <xref:System.Threading.Tasks.Parallel.ForEach%2A?displayProperty=nameWithType> sobrecargas não tem qualquer mecanismo especial para lidar com exceções que podem ser geradas. Nesse sentido, assemelham regular `for` e `foreach` loops (`For` e `For Each` no Visual Basic); uma exceção sem tratamento faz com que o loop encerrar imediatamente.  
  
 Quando você adicionar sua própria lógica de tratamento de exceção para paralelo loops, tratar o caso em que exceções semelhantes podem ser geradas em vários threads ao mesmo tempo e o caso em que uma exceção lançada em um thread faz com que outra exceção seja lançada em outro thread. Você pode manipular ambos os casos, quebra automática de todas as exceções de loop em um <xref:System.AggregateException?displayProperty=nameWithType>. O exemplo a seguir mostra uma abordagem possível.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado no exemplo a seguir. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.  
  
## <a name="example"></a>Exemplo  
 Neste exemplo, todas as exceções são detectadas e, em seguida, encapsuladas em um <xref:System.AggregateException?displayProperty=nameWithType> que é gerado. O chamador pode decidir quais exceções para tratar.  
  
 [!code-csharp[TPL_Exceptions#08](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_exceptions/cs/exceptions.cs#08)]
 [!code-vb[TPL_Exceptions#08](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_exceptions/vb/exceptionsinloops.vb#08)]  
  
## <a name="see-also"></a>Consulte também  
 [Paralelismo de dados](../../../docs/standard/parallel-programming/data-parallelism-task-parallel-library.md)  
 [Expressões lambda em PLINQ e TPL](../../../docs/standard/parallel-programming/lambda-expressions-in-plinq-and-tpl.md)
