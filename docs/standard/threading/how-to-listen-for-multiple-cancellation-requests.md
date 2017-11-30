---
title: "Como ouvir várias solicitações de cancelamento"
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
- cancellation tokens, joining
- LinkedTokenSource, how to
ms.assetid: 6f4f3804-2ed7-41b4-a97a-6e32b93f6e05
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 36cf338a15ad3f7d234f902c50a2dbb1b2e95847
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-listen-for-multiple-cancellation-requests"></a>Como ouvir várias solicitações de cancelamento
Este exemplo mostra como escutar dois tokens de cancelamento simultaneamente para que você pode cancelar uma operação, se o token solicitá-lo.  
  
> [!NOTE]
>  Quando "Apenas meu código" estiver habilitado, o Visual Studio, em alguns casos quebrar a linha que lança a exceção e exibir uma mensagem de erro que diz "exceção não tratada pelo código do usuário". Esse erro é benigno. Você pode pressionar F5 para continuar a partir dele e ver o comportamento de tratamento de exceção que é demonstrado nos exemplos a seguir. Para impedir que o Visual Studio quebra no primeiro erro, simplesmente desmarque a caixa de seleção "Apenas meu código" em **ferramentas, opções, depuração, geral**.  
  
## <a name="example"></a>Exemplo  
 No exemplo a seguir, o <xref:System.Threading.CancellationTokenSource.CreateLinkedTokenSource%2A> método é usado para unir dois tokens em um token. Isso permite que o token a ser passado para métodos que usam o cancelamento apenas um token como um argumento. O exemplo demonstra um cenário comum em que um método deve observar os dois um token passado de fora da classe e um token gerado na classe.  
  
 [!code-csharp[Cancellation#13](../../../samples/snippets/csharp/VS_Snippets_Misc/cancellation/cs/cancellationex13.cs#13)]
 [!code-vb[Cancellation#13](../../../samples/snippets/visualbasic/VS_Snippets_Misc/cancellation/vb/cancellationex13.vb#13)]  
  
 Quando o token vinculado gera um <xref:System.OperationCanceledException>, o token que é passado para a exceção é o token vinculado, não a qualquer um dos tokens predecessor. Para determinar qual dos tokens foi cancelada, verifique o status dos tokens predecessor diretamente.  
  
 Neste exemplo, <xref:System.AggregateException> nunca deverá ser lançada, mas é capturado aqui porque em cenários do mundo real todas as outras exceções além <xref:System.OperationCanceledException> que são geradas pelo delegado tarefa são encapsuladas em um <xref:System.OperationCanceledException>.  
  
## <a name="see-also"></a>Consulte também  
 [Cancelamento em threads gerenciados](../../../docs/standard/threading/cancellation-in-managed-threads.md)
