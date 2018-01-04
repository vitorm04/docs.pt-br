---
title: Como alterar o tipo de cursor
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c59f4c90eed00775fc9fceaf872391faa93784
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-cursor-type"></a>Como alterar o tipo de cursor
Este exemplo mostra como alterar a <xref:System.Windows.Input.Cursor> do ponteiro do mouse para um elemento específico e para o aplicativo.  
  
 Esse exemplo consiste em um arquivo [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] e um arquivo code-behind.  
  
## <a name="example"></a>Exemplo  
 A interface do usuário é criada, que consiste de um <xref:System.Windows.Controls.ComboBox> para selecionar o desejado <xref:System.Windows.Input.Cursor>, um par de <xref:System.Windows.Controls.RadioButton> objetos para determinar se a mudança de cursor se aplica a um único elemento ou se aplica a todo o aplicativo e um <xref:System.Windows.Controls.Border> qual é o elemento que o cursor novo é aplicado ao.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 O código a seguir cria um <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> manipulador de eventos que é chamado quando o tipo de cursor é alterado no <xref:System.Windows.Controls.ComboBox>.  Uma instrução switch filtros em nome do cursor e define o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade o <xref:System.Windows.Controls.Border> denominado *DisplayArea*.  
  
 Se a mudança de cursor é definida como "Aplicativo inteiro", o <xref:System.Windows.Input.Mouse.OverrideCursor%2A> está definida como o <xref:System.Windows.FrameworkElement.Cursor%2A> propriedade o <xref:System.Windows.Controls.Border> controle.  Isso força o cursor a mudar para o aplicativo inteiro.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral da entrada](../../../../docs/framework/wpf/advanced/input-overview.md)
