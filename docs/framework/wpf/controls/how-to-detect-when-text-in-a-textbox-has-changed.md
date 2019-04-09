---
title: 'Como: Detectar quando o texto em um TextBox foi alterado'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091142"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Como: Detectar quando o texto em um TextBox foi alterado
Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento para executar um método sempre que o texto em um <xref:System.Windows.Controls.TextBox> controle foi alterado.  
  
 Em que a classe code-behind para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar alterações, inserir um método a ser chamado sempre que o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento é acionado.  Esse método deve ter uma assinatura que corresponde ao que é esperado pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegar.  
  
 O manipulador de eventos é chamado sempre que o conteúdo do <xref:System.Windows.Controls.TextBox> controle for alterado, por um usuário ou programaticamente.  
  
 **Observação:** Esse evento é acionado quando o <xref:System.Windows.Controls.TextBox> controle é criado e preenchido inicialmente com texto.  
  
## <a name="example"></a>Exemplo  
 No [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] que define seu <xref:System.Windows.Controls.TextBox> controlar, especifique o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributo com um valor que corresponda ao nome de método do manipulador de eventos.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Exemplo  
 Em que a classe code-behind para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar alterações, inserir um método a ser chamado sempre que o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento é acionado.  Esse método deve ter uma assinatura que corresponde ao que é esperado pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegar.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 O manipulador de eventos é chamado sempre que o conteúdo do <xref:System.Windows.Controls.TextBox> controle for alterado, por um usuário ou programaticamente.  
  
 **Observação:** Esse evento é acionado quando o <xref:System.Windows.Controls.TextBox> controle é criado e preenchido inicialmente com texto.  
  
 Comentários  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
