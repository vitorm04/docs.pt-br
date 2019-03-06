---
title: 'Como: Abrir uma caixa de mensagem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: fa371b62c78a08e25de815fa44360230b6156008
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57369598"
---
# <a name="how-to-open-a-message-box"></a>Como: Abrir uma caixa de mensagem
Este exemplo mostra como abrir uma caixa de mensagem.  
  
## <a name="example"></a>Exemplo  
 Uma caixa de mensagem é uma caixa de diálogo modal pré-fabricada para exibir informações aos usuários. Uma caixa de mensagem é aberta chamando estático <xref:System.Windows.MessageBox.Show%2A> método da <xref:System.Windows.MessageBox> classe. Quando <xref:System.Windows.MessageBox.Show%2A> é chamado, a mensagem é passada usando um parâmetro de cadeia de caracteres. Várias sobrecargas de <xref:System.Windows.MessageBox.Show%2A> permitem que você configure como uma caixa de mensagem será exibida (consulte <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Consulte também
- [Amostra de MessageBox](https://go.microsoft.com/fwlink/?LinkID=160023)
