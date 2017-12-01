---
title: Como cancelar uma consulta PLINQ
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
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d8031758462df45c030b8b75a3507f1bfb44bfd0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-cancel-a-plinq-query"></a>Como cancelar uma consulta PLINQ
Os exemplos a seguir mostram dois modos para cancelar uma consulta PLINQ. O primeiro exemplo mostra como cancelar uma consulta que consiste principalmente a passagem de dados. O segundo exemplo mostra como cancelar uma consulta que contém uma função de usuário é cara.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.  
>   
>  Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 A estrutura do PLINQ não será revertida para um único <xref:System.OperationCanceledException> em uma <xref:System.AggregateException?displayProperty=nameWithType>; o <xref:System.OperationCanceledException> devem ser tratados em um bloco catch separado. Se um ou mais representantes de usuário gera um OperationCanceledException(externalCT) (usando externo <xref:System.Threading.CancellationToken?displayProperty=nameWithType>), mas nenhuma outra exceção e a consulta foi definido como `AsParallel().WithCancellation(externalCT)`, em seguida, PLINQ emitirá um único <xref:System.OperationCanceledException> (externalCT) em vez de um <xref:System.AggregateException?displayProperty=nameWithType>. No entanto, se um usuário delegar lança um <xref:System.OperationCanceledException>e outro representante gerará outro tipo de exceção, as duas exceções serão transferidas para um <xref:System.AggregateException>.  
  
 A orientação geral sobre o cancelamento é o seguinte:  
  
1.  Se você executar o cancelamento de usuário delegado deve informar o PLINQ sobre externo <xref:System.Threading.CancellationToken> e lançar um <xref:System.OperationCanceledException>(externalCT).  
  
2.  Se o cancelamento ocorrerá e nenhum outras exceções são geradas, em seguida, você deve tratar uma <xref:System.OperationCanceledException> em vez de um <xref:System.AggregateException>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como tratar o cancelamento quando você tem uma função de computação dispendiosa no código do usuário.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Quando você processa o cancelamento no código do usuário, você não precisa usar <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> na definição de consulta. No entanto, é recomendável que você faça isso porque <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> não tem nenhum efeito no desempenho da consulta e permite o cancelamento ser tratada pelo código do usuário e de operadores de consulta.  
  
 Para garantir a capacidade de resposta do sistema, é recomendável que você verificar o cancelamento em torno de uma vez por milissegundo; No entanto, qualquer período de até 10 milissegundos é considerado aceitável. Essa frequência não deve ter um impacto negativo no desempenho do seu código.  
  
 Quando um enumerador é descartado, por exemplo quando código quebra fora de um loop foreach (para cada um no Visual Basic) que estiver iterando sobre resultados de consulta, em seguida, a consulta foi cancelada, mas nenhuma exceção é lançada.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable>  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
