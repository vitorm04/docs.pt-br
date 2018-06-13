---
title: Como associar um ListBox a dados
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 186d25750c5ce196a5e46c02f0f56e2440ea3a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552825"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Como associar um ListBox a dados
Um desenvolvedor de aplicativos pode criar <xref:System.Windows.Controls.ListBox> controles sem especificar o conteúdo de cada <xref:System.Windows.Controls.ListBoxItem> separadamente. Você pode usar a associação de dados para associar dados aos itens individuais.  
  
 O exemplo a seguir mostra como criar um <xref:System.Windows.Controls.ListBox> que preenche a <xref:System.Windows.Controls.ListBoxItem> elementos de associação de dados a uma fonte de dados chamada *cores*. Nesse caso não é necessário usar <xref:System.Windows.Controls.ListBoxItem> marcas para especificar o conteúdo de cada item.  
  
## <a name="example"></a>Exemplo  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [Controles](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
