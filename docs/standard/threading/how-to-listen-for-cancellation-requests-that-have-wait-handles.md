---
title: "Como ouvir solicitações de cancelamento que têm identificadores de espera"
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
helpviewer_keywords: cancellation, waiting with wait handles
ms.assetid: 6e2aa49b-fc84-4bcf-962b-17db98b7edcb
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e1eaa84d924fde63e94c36fab50a809c7c03f075
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-cancellation-requests-that-have-wait-handles"></a>Como ouvir solicitações de cancelamento que têm identificadores de espera
Se um método é bloqueado enquanto ele está aguardando um evento a ser sinalizada, ele não pode verificar o valor do token de cancelamento e responder de maneira oportuna. O primeiro exemplo mostra como resolver esse problema quando você estiver trabalhando com eventos, como <xref:System.Threading.ManualResetEvent?displayProperty=nameWithType> que não suportam nativamente o framework de cancelamento unificada. O segundo exemplo mostra uma abordagem mais simples que usa <xref:System.Threading.ManualResetEventSlim?displayProperty=nameWithType>, que dá suporte a Unificação cancelamento.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Threading.ManualResetEvent> para demonstrar como desbloquear identificadores de espera que dão suporte ao cancelamento unificado.  
  
 [!code-csharp[Cancellation#9](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex9.cs#9)]
 [!code-vb[Cancellation#9](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex9.vb#9)]  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir usa um <xref:System.Threading.ManualResetEventSlim> para demonstrar como desbloquear coordenação primitivos que dão suporte a Unificação cancelamento. A mesma abordagem pode ser usada com outros primitivos de coordenação leves, como <xref:System.Threading.Semaphore> `Slim` e <xref:System.Threading.CountdownEvent>.  
  
 [!code-csharp[Cancellation#10](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex10.cs#10)]
 [!code-vb[Cancellation#10](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex10.vb#10)]  
  
## <a name="see-also"></a>Consulte também  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
