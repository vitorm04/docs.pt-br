---
title: "Como registrar retornos de chamada para solicitações de cancelamento"
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
helpviewer_keywords: cancellation, how to register callbacks
ms.assetid: 8838dd75-18ed-4b8b-b322-cd4531faac64
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 85b15ed610d80958ac9d7e3762ac8ea7b781b8d0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-register-callbacks-for-cancellation-requests"></a>Como registrar retornos de chamada para solicitações de cancelamento
O exemplo a seguir mostra como registrar um delegado que será invocado quando uma <xref:System.Threading.CancellationToken.IsCancellationRequested%2A> propriedade torna-se verdadeiro devido a uma chamada para <xref:System.Threading.CancellationTokenSource.Cancel%2A> no objeto que criou o token. Use essa técnica para cancelar operações assíncronas que não suportam nativamente o framework de cancelamento unificada e para métodos de desbloqueio que podem estar aguardando para uma operação assíncrona concluir.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Net.WebClient.CancelAsync%2A> método é registrado como o método a ser invocado quando o cancelamento for solicitado por meio do token de cancelamento.  
  
 [!code-csharp[Conceptual.Cancellation.Callback#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.cancellation.callback/cs/howtoexample1.cs#1)]
 [!code-vb[Conceptual.Cancellation.Callback#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.cancellation.callback/vb/howtoexample1.vb#1)]  
  
 Se o cancelamento já foi solicitado quando o retorno de chamada for registrado, o retorno de chamada ainda é garantido para ser chamado. Nesse caso específico, o <xref:System.Net.WebClient.CancelAsync%2A> método não fará nada se nenhuma operação assíncrona está em andamento, portanto, é sempre seguro chamar o método.  
  
## <a name="see-also"></a>Consulte também  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
