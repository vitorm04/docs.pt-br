---
title: 'Como: Criar controles em um ToolBar'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: d81aa227eb1ffcb3dbaa119c41d561cbb066b704
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57364444"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Como: Criar controles em um ToolBar
O <xref:System.Windows.Controls.ToolBar> define <xref:System.Windows.ResourceKey> objetos para especificar o estilo dos controles dentro de <xref:System.Windows.Controls.ToolBar>.  Para definir o estilo de um controle em um <xref:System.Windows.Controls.ToolBar>, defina a `x:key` atributo do estilo a um <xref:System.Windows.ResourceKey> definidos no <xref:System.Windows.Controls.ToolBar>.  
  
 O <xref:System.Windows.Controls.ToolBar> define os seguintes <xref:System.Windows.ResourceKey> objetos:  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir define estilos para controles dentro de um <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Consulte também
- [Estilo e modelagem](styling-and-templating.md)
