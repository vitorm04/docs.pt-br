---
title: Como cancelar uma consulta PLINQ
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- PLINQ queries, how to cancel
- cancellation, PLINQ
ms.assetid: 80b14640-edfa-4153-be1b-3e003d3e9c1a
ms.openlocfilehash: 312c71b787ac7b4aa092f1517d2ed5af314a22e4
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635875"
---
# <a name="how-to-cancel-a-plinq-query"></a>Como cancelar uma consulta PLINQ
Os exemplos a seguir mostram duas maneiras de cancelar uma consulta PLINQ. O primeiro exemplo mostra como cancelar uma consulta composta principalmente de travessia de dados. O segundo exemplo mostra como cancelar uma consulta que contém uma função de usuário que gasta muitos recursos de computação.

> [!NOTE]
> Se a opção "Apenas Meu Código" estiver habilitada, o Visual Studio interromperá na linha que gerou a exceção e exibirá a mensagem de erro "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir daí e ver o comportamento de tratamento de exceção, demonstrado nos exemplos a seguir. Para impedir que o Visual Studio seja interrompido no primeiro erro, basta desmarcar a caixa de seleção "Apenas Meu Código" em **Ferramentas, Opções, Depuração, Geral**.
>
> Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para saber mais sobre agilização, confira [Noções básicas sobre agilização no PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).

## <a name="example"></a>Exemplo

[!code-csharp[PLINQ#16](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#16)]
[!code-vb[PLINQ#16](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#16)]

A estrutura do PLINQ não implementa um único <xref:System.OperationCanceledException> em uma <xref:System.AggregateException?displayProperty=nameWithType>; o <xref:System.OperationCanceledException> deve ser tratado em um bloco catch separado. Se um ou mais delegados de usuário gerar uma OperationCanceledException(externalCT) (usando um <xref:System.Threading.CancellationToken?displayProperty=nameWithType> externo), mas nenhuma outra exceção, e a consulta tiver sido definida como `AsParallel().WithCancellation(externalCT)`, PLINQ emitirá uma única <xref:System.OperationCanceledException> (externalCT) em vez de uma <xref:System.AggregateException?displayProperty=nameWithType>. No entanto, se um delegado de usuário lançar uma <xref:System.OperationCanceledException>, e outro delegado lançar outro tipo de exceção, as duas exceções serão transferidas para um <xref:System.AggregateException>.

A orientação geral sobre o cancelamento é a seguinte:

1. Se você realizar o cancelamento do usuário-delegado, <xref:System.Threading.CancellationToken> você deve <xref:System.OperationCanceledException>informar plinq sobre o externo e jogar um (externalCT).

2. Se ocorrer cancelamento e nenhuma outra exceção <xref:System.OperationCanceledException> for <xref:System.AggregateException>lançada, então manuseie um em vez de um .

## <a name="example"></a>Exemplo

O exemplo a seguir mostra como tratar o cancelamento quando você tem uma função que consome muitos recursos de computação no código do usuário.

[!code-csharp[PLINQ#17](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#17)]
[!code-vb[PLINQ#17](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#17)]

Quando você processa o cancelamento no código do usuário, não precisa usar <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> na definição da consulta. No entanto, recomendamos <xref:System.Linq.ParallelEnumerable.WithCancellation%2A>que <xref:System.Linq.ParallelEnumerable.WithCancellation%2A> você use, porque não tem efeito no desempenho da consulta e permite que o cancelamento seja tratado pelas operadoras de consulta e pelo seu código de usuário.

Para garantir a capacidade de resposta do sistema, recomendamos que você verifique o cancelamento uma vez a cada milissegundo; no entanto, qualquer período de até 10 milissegundos é considerado aceitável. Essa frequência não deve ter um impacto negativo no desempenho do seu código.

Quando um enumerador é eliminado, por exemplo, quando o código sai de um loop foreach (For Each in Visual Basic) que está iterando sobre os resultados da consulta, então a consulta é cancelada, mas nenhuma exceção é lançada.

## <a name="see-also"></a>Confira também

- <xref:System.Linq.ParallelEnumerable>
- [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/introduction-to-plinq.md)
- [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
