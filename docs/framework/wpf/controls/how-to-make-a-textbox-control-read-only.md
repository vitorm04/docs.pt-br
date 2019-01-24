---
title: 'Como: Tornar um controle TextBox somente leitura'
ms.date: 03/30/2017
helpviewer_keywords:
- read-only TextBox controls [WPF]
- TextBox control read-only
ms.assetid: e707ec59-8b22-473e-b77c-3060a237517a
ms.openlocfilehash: 1e9d333f22099d9593e58b4087f185b2988215ce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54517169"
---
# <a name="how-to-make-a-textbox-control-read-only"></a>Como: Tornar um controle TextBox somente leitura
Este exemplo mostra como configurar um <xref:System.Windows.Controls.TextBox> controle por não permitir a entrada do usuário ou modificação.  
  
## <a name="example"></a>Exemplo  
 Para impedir que usuários modifiquem o conteúdo de um <xref:System.Windows.Controls.TextBox> , defina a <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo **verdadeiro**.  
  
 [!code-xaml[TextBox_MiscCode#_ReadOnlyTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_readonlytextboxxaml)]  
  
 O <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> atributo afeta somente a entrada do usuário, ela não afeta o texto definido na [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] descrição de uma <xref:System.Windows.Controls.TextBox> controle ou definida programaticamente através de texto o <xref:System.Windows.Controls.TextBox.Text%2A> propriedade.  
  
 O valor padrão de <xref:System.Windows.Controls.Primitives.TextBoxBase.IsReadOnly%2A> está **falso**.  
  
## <a name="see-also"></a>Consulte também
- [Visão geral de TextBox](../../../../docs/framework/wpf/controls/textbox-overview.md)
- [Visão geral de RichTextBox](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
