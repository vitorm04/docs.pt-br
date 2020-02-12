---
title: Como abrir uma caixa de mensagem
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- message boxes [WPF], opening
- opening message boxes [WPF]
ms.assetid: acaad17f-af43-4eca-a004-f1c9e7c6f292
ms.openlocfilehash: bd2c4dce78e46163eb4628cb3aab829fc0173edf
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77123721"
---
# <a name="how-to-open-a-message-box"></a>Como abrir uma caixa de mensagem
Este exemplo mostra como abrir uma caixa de mensagem.  
  
## <a name="example"></a>{1&gt;Exemplo&lt;1}  
 Uma caixa de mensagem é uma caixa de diálogo modal Prefabricated para exibir informações aos usuários. Uma caixa de mensagem é aberta chamando o método estático <xref:System.Windows.MessageBox.Show%2A> da classe <xref:System.Windows.MessageBox>. Quando <xref:System.Windows.MessageBox.Show%2A> é chamado, a mensagem é passada usando um parâmetro de cadeia de caracteres. Várias sobrecargas de <xref:System.Windows.MessageBox.Show%2A> permitem que você configure como uma caixa de mensagem será exibida (consulte <xref:System.Windows.MessageBox>).  
  
 [!code-csharp[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/csharp/VS_Snippets_Wpf/MessageBoxSnippets/CSharp/Show1Window.xaml.cs#messageboxshow1code)]
 [!code-vb[MessageBoxSnippets#MessageBoxShow1CODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/MessageBoxSnippets/visualbasic/show1window.xaml.vb#messageboxshow1code)]  
  
## <a name="see-also"></a>Consulte também

- [Exemplo de MessageBox](https://github.com/Microsoft/WPF-Samples/tree/master/Windows/MessageBox)
