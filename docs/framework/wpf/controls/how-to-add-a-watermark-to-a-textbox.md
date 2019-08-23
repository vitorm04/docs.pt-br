---
title: "Como: Adicionar uma marca-d'água a um TextBox"
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923570"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Como: Adicionar uma marca-d'água a um TextBox
O exemplo a seguir mostra como auxiliar a usabilidade de <xref:System.Windows.Controls.TextBox> um exibindo uma imagem de tela <xref:System.Windows.Controls.TextBox> de fundo explicativa dentro do até que o usuário entradas de texto, no ponto em que a imagem é removida. Além disso, a imagem de plano de fundo será restaurada novamente se o usuário remover sua entrada. Consulte a ilustração abaixo.  
  
 ![Uma caixa de texto com uma imagem de plano de fundo](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
> O motivo pelo qual uma imagem de plano de fundo é usada neste exemplo em vez <xref:System.Windows.Controls.TextBox.Text%2A> de simplesmente <xref:System.Windows.Controls.TextBox>manipular a propriedade de, é que uma imagem de plano de fundo não interfere na vinculação de dados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
