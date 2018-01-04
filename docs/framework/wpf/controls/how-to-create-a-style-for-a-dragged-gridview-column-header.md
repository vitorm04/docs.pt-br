---
title: "Como criar um estilo para um cabeçalho de coluna GridView arrastado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: ListView controls [WPF], styling
ms.assetid: 0b999645-0313-4b33-80b9-19ece08b5459
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 001d0ec45ad990ef366e7fc1216a7370aade9cb7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-style-for-a-dragged-gridview-column-header"></a>Como criar um estilo para um cabeçalho de coluna GridView arrastado
Este exemplo mostra como alterar a aparência de um arrastado <xref:System.Windows.Controls.GridViewColumnHeader> quando o usuário altera a posição de uma coluna.  
  
## <a name="example"></a>Exemplo  
 Quando você arrasta um cabeçalho de coluna para outro local em um <xref:System.Windows.Controls.ListView> que usa <xref:System.Windows.Controls.GridView> seu modo de exibição, a coluna é movida para a nova posição. Enquanto você estiver arrastando o cabeçalho da coluna, uma cópia flutuante do cabeçalho é exibida além do cabeçalho original. Um cabeçalho de coluna em uma <xref:System.Windows.Controls.GridView> é representado por um <xref:System.Windows.Controls.GridViewColumnHeader> objeto.  
  
 Para personalizar a aparência de cabeçalhos flutuantes e originais, você pode definir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> para modificar o <xref:System.Windows.Controls.GridViewColumnHeader> <xref:System.Windows.Style>. Essas <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> são aplicadas quando o <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> é o valor da propriedade `true` e <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> é o valor da propriedade <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 Quando o usuário pressiona o botão do mouse e mantiver enquanto faz uma pausa o mouse sobre o <xref:System.Windows.Controls.GridViewColumnHeader>, o <xref:System.Windows.Controls.Primitives.ButtonBase.IsPressed%2A> altera o valor da propriedade para `true`. Da mesma forma, quando o usuário começa a operação de arrastar o <xref:System.Windows.Controls.GridViewColumnHeader.Role%2A> alteração na propriedade <xref:System.Windows.Controls.GridViewColumnHeaderRole.Floating>.  
  
 O exemplo a seguir mostra como definir <xref:System.Windows.Controls.ControlTemplate.Triggers%2A> para alterar o <xref:System.Windows.Controls.Control.Foreground%2A> e <xref:System.Windows.Controls.Control.Background%2A> cores dos cabeçalhos originais e flutuantes quando o usuário arrasta uma coluna para uma nova posição.  
  
 [!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplatestart)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersstart)]  
[!code-xaml[ListViewHeaderRoleStyle#IsPressed](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#ispressed)]  
[!code-xaml[ListViewHeaderRoleStyle#Floating](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#floating)]  
[!code-xaml[ListViewHeaderRoleStyle#ControlTemplateTriggersEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#controltemplatetriggersend)]  
[!code-xaml[ListViewHeaderRoleStyle#GVCHControlTemplateEnd](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHeaderRoleStyle/CS/Window1.xaml#gvchcontroltemplateend)]  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Controls.GridViewColumnHeader>  
 <xref:System.Windows.Controls.GridViewColumnHeaderRole>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.GridView>  
 [Tópicos de instruções](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
