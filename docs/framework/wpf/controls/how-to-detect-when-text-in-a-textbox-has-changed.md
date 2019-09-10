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
ms.openlocfilehash: 8c7744e9e61b8ba796802e54435c0bf9fdbee50e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855612"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Como: Detectar quando o texto em um TextBox foi alterado

Este exemplo mostra uma maneira de usar o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> evento para executar um método sempre que o texto em <xref:System.Windows.Controls.TextBox> um controle for alterado.

Na classe code-behind para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar para as alterações, insira um método a ser chamado sempre que <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento for disparado.  Esse método deve ter uma assinatura que corresponda ao que é esperado pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegado.

O manipulador de eventos é chamado sempre que o conteúdo <xref:System.Windows.Controls.TextBox> do controle é alterado, seja por um usuário ou programaticamente.

> [!NOTE]
> Esse evento é acionado <xref:System.Windows.Controls.TextBox> quando o controle é criado e preenchido inicialmente com texto.

## <a name="example"></a>Exemplo

No que define seu <xref:System.Windows.Controls.TextBox> controle, especifique o <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributo com um valor que corresponda ao nome do método do manipulador de eventos. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]

[!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]

## <a name="example"></a>Exemplo

Na classe code-behind para o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] que contém o <xref:System.Windows.Controls.TextBox> controle que você deseja monitorar para as alterações, insira um método a ser chamado sempre que <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> o evento for disparado.  Esse método deve ter uma assinatura que corresponda ao que é esperado pelo <xref:System.Windows.Controls.TextChangedEventHandler> delegado.

[!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
[!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]

O manipulador de eventos é chamado sempre que o conteúdo <xref:System.Windows.Controls.TextBox> do controle é alterado, seja por um usuário ou programaticamente.

> [!NOTE]
> Esse evento é acionado <xref:System.Windows.Controls.TextBox> quando o controle é criado e preenchido inicialmente com texto.

Comentários

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [Visão geral de TextBox](textbox-overview.md)
- [Visão geral de RichTextBox](richtextbox-overview.md)
