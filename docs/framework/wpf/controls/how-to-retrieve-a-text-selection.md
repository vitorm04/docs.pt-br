---
title: Como recuperar uma seleção de texto
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], retrieving
- TextBox control [WPF], retrieving text
- retrieving text [WPF]
ms.assetid: d5793172-1e11-4a39-9be0-73f336ed858d
ms.openlocfilehash: 6b25c555d5e6cac93b2e1518b25e7880ab77c866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552006"
---
# <a name="how-to-retrieve-a-text-selection"></a>Como recuperar uma seleção de texto
Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.TextBox.SelectedText%2A> propriedade para recuperar o texto que o usuário selecionou em uma <xref:System.Windows.Controls.TextBox> controle.  
  
## <a name="example"></a>Exemplo  
 O seguinte [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] exemplo mostra a definição de um <xref:System.Windows.Controls.TextBox> controle que contém algum texto para selecionar, e um <xref:System.Windows.Controls.Button> controle com um especificado <xref:System.Windows.Controls.Button.OnClick%2A> método.  
  
 Neste exemplo, um botão com um tipo de <xref:System.Windows.Controls.Primitives.ButtonBase.Click> manipulador de eventos é usado para recuperar a seleção de texto. Quando o usuário clica no botão, o <xref:System.Windows.Controls.Button.OnClick%2A> método copia qualquer texto selecionado na caixa de texto em uma cadeia de caracteres. As circunstâncias específicas pelas quais a seleção de texto é recuperada (clicando em um botão), bem como a ação tomada com essa seleção (copiar a seleção de texto para uma cadeia de caracteres), podem facilmente ser modificadas para acomodar uma grande variedade de cenários.  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxSelectTextXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxselecttextxaml)]  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir c# mostra um <xref:System.Windows.Controls.Button.OnClick%2A> manipulador de eventos para o botão definido no [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] para este exemplo.  
  
 [!code-csharp[TextBox_MiscCode#_SelectText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_selecttext)]
 [!code-vb[TextBox_MiscCode#_SelectText](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_selecttext)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
