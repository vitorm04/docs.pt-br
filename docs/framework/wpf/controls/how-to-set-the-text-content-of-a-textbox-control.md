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
ms.openlocfilehash: 6c0e6e53518d382a2052efa43993d418e35fa0f2
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364119"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Como: Definir o conteúdo de texto de um controle TextBox
Este exemplo mostra como usar o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade para definir o conteúdo de texto inicial de um <xref:System.Windows.Controls.TextBox> controle.  
  
 **Observação** Embora o [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] poderia usar a versão do exemplo de `<TextBox.Text>` marcas ao redor do texto de cada botão <xref:System.Windows.Controls.TextBox> conteúdo, não é necessário porque o <xref:System.Windows.Controls.TextBox> aplica-se o <xref:System.Windows.Markup.ContentPropertyAttribute> de atributo para o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade. Para obter mais informações, consulte [visão geral de XAML (WPF)](../advanced/xaml-overview-wpf.md).  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]  
  
## <a name="example"></a>Exemplo  
 [!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
 [!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
