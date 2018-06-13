---
title: Como adicionar uma marca d'água a um TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: 962d6958de0811863393f930d8672769a50e8265
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33550053"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Como adicionar uma marca d'água a um TextBox
O exemplo a seguir mostra como auxiliar usabilidade de um <xref:System.Windows.Controls.TextBox> ao exibir uma imagem de plano de fundo explicativos dentro do <xref:System.Windows.Controls.TextBox> até que o usuário insere texto, no ponto em que a imagem será removida. Além disso, a imagem de plano de fundo é restaurada novamente se o usuário remove suas entradas. Consulte a ilustração a seguir.  
  
 ![Uma caixa de texto com uma imagem de plano de fundo](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  O motivo pelo qual uma imagem de plano de fundo é usada neste exemplo, em vez de simplesmente manipular o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade <xref:System.Windows.Controls.TextBox>, é que uma imagem de plano de fundo não interferirá na associação de dados.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
