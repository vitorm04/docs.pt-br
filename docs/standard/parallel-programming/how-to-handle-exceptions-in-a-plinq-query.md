---
title: "Como manipular exceções em uma consulta PLINQ"
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
helpviewer_keywords: PLINQ queries, how to handle exceptions
ms.assetid: 8d56ff9b-a571-4d31-b41f-80c0b51b70a5
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 209e0c1bf89f231d03647ae4351279bfdb172e68
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-handle-exceptions-in-a-plinq-query"></a>Como manipular exceções em uma consulta PLINQ
O primeiro exemplo neste tópico mostra como tratar o <xref:System.AggregateException?displayProperty=nameWithType> que pode ser gerada de uma consulta PLINQ quando ele é executado. O segundo exemplo mostra como colocar blocos try-catch em delegados, mais próximo possível de onde a exceção será lançada. Dessa forma, você pode capturá-los assim que eles ocorrem e possivelmente continuam a execução da consulta. Quando as exceções tiverem permissão de emergirem novamente para o thread de associação, então será possível que uma consulta continue a processar alguns itens após a geração da exceção.  
  
 Em alguns casos quando PLINQ reverterá para execução sequencial e ocorre uma exceção, a exceção pode ser propagada diretamente e não é encapsulada em um <xref:System.AggregateException>. Além disso, <xref:System.Threading.ThreadAbortException>s sempre são propagadas diretamente.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.  
>   
>  Este exemplo tem como objetivo demonstrar o uso e pode não executar tão rápido quanto a consulta LINQ to Objects sequencial equivalente. Para obter mais informações sobre velocidade, consulte [Noções básicas sobre agilização em PLINQ](../../../docs/standard/parallel-programming/understanding-speedup-in-plinq.md).  
  
## <a name="example"></a>Exemplo  
 Este exemplo mostra como colocar os blocos de try-catch no código que executa a consulta para capturar qualquer <xref:System.AggregateException?displayProperty=nameWithType>s que são geradas.  
  
 [!code-csharp[PLINQ#41](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#41)]
 [!code-vb[PLINQ#41](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#41)]  
  
 Neste exemplo, a consulta não pode continuar depois que a exceção é gerada. Quando o que código do aplicativo captura a exceção, PLINQ já foi interrompido a consulta em todos os threads.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como inserir um bloco try-catch em um representante para que seja possível capturar uma exceção e continuar com a execução da consulta.  
  
 [!code-csharp[PLINQ#42](../../../samples/snippets/csharp/VS_Snippets_Misc/plinq/cs/plinqsamples.cs#42)]
 [!code-vb[PLINQ#42](../../../samples/snippets/visualbasic/VS_Snippets_Misc/plinq/vb/plinqsnippets1.vb#42)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Para compilar e executar esses exemplos, copiá-las para o exemplo de exemplo de dados PLINQ e chame o método do principal.  
  
## <a name="robust-programming"></a>Programação robusta  
 Não captura uma exceção, a menos que você sabe como tratá-la para que o estado do programa não sejam corrompidos.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Linq.ParallelEnumerable>  
 [PLINQ (LINQ paralelo)](../../../docs/standard/parallel-programming/parallel-linq-plinq.md)
