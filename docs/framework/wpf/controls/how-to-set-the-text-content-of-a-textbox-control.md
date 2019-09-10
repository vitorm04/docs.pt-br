---
title: 'Como: Definir o conteúdo de texto de um controle TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856116"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Como: Definir o conteúdo de texto de um controle TextBox

Este exemplo mostra como usar a <xref:System.Windows.Controls.TextBox.Text%2A> propriedade para definir o conteúdo de texto inicial de um <xref:System.Windows.Controls.TextBox> controle.

> [!NOTE]
> Embora a [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] versão do exemplo possa usar as `<TextBox.Text>` marcas em volta do <xref:System.Windows.Controls.TextBox> texto do conteúdo de cada botão, isso não é <xref:System.Windows.Controls.TextBox.Text%2A> necessário porque o <xref:System.Windows.Controls.TextBox> aplica o <xref:System.Windows.Markup.ContentPropertyAttribute> atributo à propriedade . Para obter mais informações, consulte [visão geral de XAML (WPF)](../advanced/xaml-overview-wpf.md).

## <a name="example"></a>Exemplo

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Exemplo

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Consulte também

- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
