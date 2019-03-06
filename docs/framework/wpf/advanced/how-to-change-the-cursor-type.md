---
title: 'Como: Alterar o tipo de cursor'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: e62658f4c4249c93bd24dffd3878dd2ec2b75029
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371135"
---
# <a name="how-to-change-the-cursor-type"></a>Como: Alterar o tipo de cursor
Este exemplo mostra como alterar o <xref:System.Windows.Input.Cursor> do ponteiro do mouse para um elemento específico e para o aplicativo.  
  
 Esse exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 A interface do usuário é criada, que consiste em uma <xref:System.Windows.Controls.ComboBox> para selecionar o desejado <xref:System.Windows.Input.Cursor>, um par de <xref:System.Windows.Controls.RadioButton> objetos para determinar se a mudança de cursor se aplica a apenas um único elemento ou se aplica a todo o aplicativo e um <xref:System.Windows.Controls.Border> qual é o elemento que o novo cursor é aplicado ao.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 O código a seguir cria uma <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> manipulador de eventos que é chamado quando o tipo de cursor é alterado no <xref:System.Windows.Controls.ComboBox>.  Uma instrução switch filtra o nome de cursor e define a <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade em de <xref:System.Windows.Controls.Border> que é denominado *DisplayArea*.  
  
 Se a mudança de cursor for definida como "Aplicativo inteiro", o <xref:System.Windows.Input.Mouse.OverrideCursor%2A> estiver definida como o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade do <xref:System.Windows.Controls.Border> controle.  Isso força o cursor a mudar para o aplicativo inteiro.  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Consulte também
- [Visão geral da entrada](input-overview.md)
