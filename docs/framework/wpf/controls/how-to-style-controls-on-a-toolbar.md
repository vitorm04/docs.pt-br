---
title: Como criar controles em um ToolBar
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 78b9fc505c3c9045a0ca16ddaa1361c90bcc896a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459410"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Como criar controles em um ToolBar
O <xref:System.Windows.Controls.ToolBar> define <xref:System.Windows.ResourceKey> objetos para especificar o estilo dos controles dentro do <xref:System.Windows.Controls.ToolBar>.  Para estilizar um controle em um <xref:System.Windows.Controls.ToolBar>, defina o atributo `x:key` do estilo como um <xref:System.Windows.ResourceKey> definido em <xref:System.Windows.Controls.ToolBar>.  
  
 O <xref:System.Windows.Controls.ToolBar> define os seguintes objetos <xref:System.Windows.ResourceKey>:  
  
- <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define os estilos para os controles dentro de um <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Consulte também

- [Estilo e modelagem](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
