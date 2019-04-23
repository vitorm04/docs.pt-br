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
ms.openlocfilehash: ef2536f03ba6ed08e27d2fcf30cd1f72df2cf460
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142409"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Como: Adicionar uma marca-d'água a um TextBox
O exemplo a seguir mostra como a usabilidade de auxílio de uma <xref:System.Windows.Controls.TextBox> exibindo uma imagem em segundo plano explicativo dentro do <xref:System.Windows.Controls.TextBox> até que o usuário insere texto, no ponto em que a imagem será removida. Além disso, a imagem de plano de fundo é restaurada novamente se o usuário remove suas entradas. Consulte a ilustração a seguir.  
  
 ![Uma caixa de texto com uma imagem de plano de fundo](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  O motivo pelo qual uma imagem de plano de fundo é usada neste exemplo em vez de simplesmente manipular as <xref:System.Windows.Controls.TextBox.Text%2A> propriedade de <xref:System.Windows.Controls.TextBox>, é que uma imagem de plano de fundo não interferirá na associação de dados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
