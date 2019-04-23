---
title: 'Como: Recuperar uma seleção de texto'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: b7f0b9ee02a7ace717787fc8eeb6e15649829a49
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59224579"
---
# <a name="how-to-retrieve-a-text-selection"></a>Como: Recuperar uma seleção de texto
Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.TextBox.SelectedText%2A> propriedade para recuperar o texto que o usuário tiver selecionado em um <xref:System.Windows.Controls.TextBox> controle.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo mostra a definição de uma <xref:System.Windows.Controls.TextBox> controle que contém algum texto para selecionar, e um <xref:System.Windows.Controls.Button> controle com um especificado <xref:System.Windows.Controls.Button.OnClick%2A> método.  
  
 Neste exemplo, um botão com um tipo de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos é usado para recuperar a seleção de texto. Quando o usuário clica no botão, o <xref:System.Windows.Controls.Button.OnClick%2A> método copia o texto selecionado na caixa de texto em uma cadeia de caracteres. As circunstâncias específicas pelas quais a seleção de texto é recuperada (clicando em um botão), bem como a ação tomada com essa seleção (copiar a seleção de texto para uma cadeia de caracteres), podem facilmente ser modificadas para acomodar uma grande variedade de cenários.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Exemplo  
 O seguinte C# exemplo mostra uma <xref:System.Windows.Controls.Button.OnClick%2A> manipulador de eventos para o botão definido na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para este exemplo.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
