---
title: 'Como: Cancelar uma consulta PLINQ'
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bce6616d576263db7dce6cf7e52582ee3400d80d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962529"
---
# <a name="how-to-cancel-a-plinq-query"></a>Como: Cancelar uma consulta PLINQ
Os exemplos a seguir mostram duas maneiras de cancelar uma consulta PLINQ. O primeiro exemplo mostra como cancelar uma consulta composta principalmente de travessia de dados. O segundo exemplo mostra como cancelar uma consulta que contém uma função de usuário que gasta muitos recursos de computação.  
  
> [!NOTE]
> Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio interromperá na linha que gerou a exceção e exibirá a mensagem de erro "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir. Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.  
>   
>  Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
 [!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]  
  
 A estrutura do PLINQ não implementa um único <xref:System.OperationCanceledException> em uma <xref:System.AggregateException?displayProperty=nameWithType>; o <xref:System.OperationCanceledException> deve ser tratado em um bloco catch separado. Se um ou mais delegados de usuário gerar uma OperationCanceledException(externalCT) (usando um <xref:System.Threading.CancellationToken?displayProperty=nameWithType> externo), mas nenhuma outra exceção, e a consulta tiver sido definida como `AsParallel().WithCancellation(externalCT)`, PLINQ emitirá uma única <xref:System.OperationCanceledException> (externalCT) em vez de uma <xref:System.AggregateException?displayProperty=nameWithType>. No entanto, se um delegado de usuário lançar uma <xref:System.OperationCanceledException>, e outro delegado lançar outro tipo de exceção, as duas exceções serão transferidas para um <xref:System.AggregateException>.  
  
 A orientação geral sobre o cancelamento é a seguinte:  
  
1. Se você executar o cancelamento do delegado-usuário, deverá informar ao PLINQ sobre o <xref:System.Threading.CancellationToken> externo e lançar uma <xref:System.OperationCanceledException>(externalCT).  
  
2. Se o cancelamento ocorrer e nenhum outra exceção for gerada, você deverá tratar uma <xref:System.OperationCanceledException> em vez de uma <xref:System.AggregateException>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como tratar o cancelamento quando você tem uma função que consome muitos recursos de computação no código do usuário.  
  
 [!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
 [!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]  
  
 Quando você processa o cancelamento no código do usuário, não precisa usar <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> na definição da consulta. No entanto, recomendamos que você faça isso, pois <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> não tem nenhum efeito sobre o desempenho da consulta e permite que o cancelamento seja tratado por operadores de consulta e pelo código do usuário.  
  
 Para garantir a capacidade de resposta do sistema, recomendamos que você verifique o cancelamento uma vez a cada milissegundo; no entanto, qualquer período de até 10 milissegundos é considerado aceitável. Essa frequência não deve ter um impacto negativo no desempenho do seu código.  
  
 Quando um enumerador é descartado, por exemplo, quando o código foge de um loop foreach (For Each no Visual Basic) que está iterando sobre os resultados da consulta, a consulta é cancelada, mas nenhuma exceção é lançada.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Linq.ParallelEnumerable>
- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
- [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
