---
title: 'Como: abrir uma caixa de mensagem'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1754fa190a638c1a200805e339f91bd582d27c4c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-open-a-message-box"></a>Como: abrir uma caixa de mensagem
Este exemplo mostra como abrir uma caixa de mensagem.  
  
## <a name="example"></a>Exemplo  
 Uma caixa de mensagem é uma caixa de diálogo modal pré-fabricada para exibir informações aos usuários. Uma caixa de mensagem é aberta chamando estático <xref:System.Windows.MessageBox.Show%2A> método o <xref:System.Windows.MessageBox> classe. Quando <xref:System.Windows.MessageBox.Show%2A> é chamado, a mensagem será passada usando um parâmetro de cadeia de caracteres. Várias sobrecargas de <xref:System.Windows.MessageBox.Show%2A> permitem que você configure como uma caixa de mensagem será exibida (consulte <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Consulte também  
 [Exemplo de MessageBox](http://go.microsoft.com/fwlink/?LinkID=160023)
