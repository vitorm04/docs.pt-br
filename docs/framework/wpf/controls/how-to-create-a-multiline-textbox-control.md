---
title: Como criar um controle TextBox multilinha
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 9f4c9e637b686c82b4ec8a4a5d6d3a78d46f97c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Como criar um controle TextBox multilinha
Este exemplo mostra como usar [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] para definir um <xref:System.Windows.Controls.TextBox> controle expandirá automaticamente para acomodar várias linhas de texto.  
  
## <a name="example"></a>Exemplo  
 Definindo o <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributo **Wrap** fará com que o texto passe para uma nova linha quando a borda do <xref:System.Windows.Controls.TextBox> controle é alcançado, expandindo automaticamente o <xref:System.Windows.Controls.TextBox> controle para incluir espaço para uma nova linha, se é necessário.  
  
 Definindo o <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributo **true** faz com que uma nova linha seja inserida quando a tecla é pressionada, outra vez automaticamente expandindo o <xref:System.Windows.Controls.TextBox> para incluir espaço para uma nova linha, se necessário.  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> atributo adiciona uma barra de rolagem para o <xref:System.Windows.Controls.TextBox>, de modo que o conteúdo do <xref:System.Windows.Controls.TextBox> pode ser rolado por meio de se o <xref:System.Windows.Controls.TextBox> expande além do tamanho do quadro ou janela que inclui-lo.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.TextWrapping>  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
