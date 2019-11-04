---
title: Como definir o conteúdo de texto de um controle TextBox
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459307"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Como definir o conteúdo de texto de um controle TextBox

Este exemplo mostra como usar a propriedade <xref:System.Windows.Controls.TextBox.Text%2A> para definir o conteúdo de texto inicial de um controle de <xref:System.Windows.Controls.TextBox>.

> [!NOTE]
> Embora a versão [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] do exemplo possa usar as marcas de `<TextBox.Text>` ao texto do conteúdo de cada botão <xref:System.Windows.Controls.TextBox>, não é necessário porque o <xref:System.Windows.Controls.TextBox> aplica o atributo <xref:System.Windows.Markup.ContentPropertyAttribute> à propriedade <xref:System.Windows.Controls.TextBox.Text%2A>. Para obter mais informações, consulte [visão geral de XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Exemplo

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Exemplo

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Consulte também

- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
