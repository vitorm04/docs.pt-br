---
title: Como detectar quando o texto em um TextBox foi alterado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552946"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Como detectar quando o texto em um TextBox foi alterado
Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento para executar um método sempre que o texto em uma <xref:System.Windows.Controls.TextBox> controle foi alterado.  
  
 Na classe por trás do código para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar as alterações, insira um método a ser chamado sempre que o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento ser acionado.  Esse método deve ter uma assinatura que corresponde a esperada pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegate.  
  
 O manipulador de eventos é chamado sempre que o conteúdo do <xref:System.Windows.Controls.TextBox> controle for alterado, por um usuário ou programaticamente.  
  
 **Observação:** esse evento é acionado quando o <xref:System.Windows.Controls.TextBox> controle é criado e preenchido inicialmente com o texto.  
  
## <a name="example"></a>Exemplo  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que define seu <xref:System.Windows.Controls.TextBox> controlar, especifique o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributo com um valor que corresponda ao nome de método do manipulador de eventos.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Exemplo  
 Na classe por trás do código para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar as alterações, insira um método a ser chamado sempre que o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento ser acionado.  Esse método deve ter uma assinatura que corresponde a esperada pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegate.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 O manipulador de eventos é chamado sempre que o conteúdo do <xref:System.Windows.Controls.TextBox> controle for alterado, por um usuário ou programaticamente.  
  
 **Observação:** esse evento é acionado quando o <xref:System.Windows.Controls.TextBox> controle é criado e preenchido inicialmente com o texto.  
  
 Comentários  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
