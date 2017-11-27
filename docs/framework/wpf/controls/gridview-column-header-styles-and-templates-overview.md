---
title: "Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ad0f7cacc8256e060bb12611bd1818b694e1e6dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView
Esta visão geral discute a ordem de precedência para as propriedades que você usar para personalizar um cabeçalho de coluna no <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>Personalizando um cabeçalho da coluna em GridView  
 As propriedades que definem o conteúdo, layout e estilo de um cabeçalho de coluna em um <xref:System.Windows.Controls.GridView> são encontradas em muitas classes relacionadas. Algumas dessas propriedades tem funcionalidades parecidas ou iguais.  
  
 As linhas na tabela a seguir mostram grupos de propriedades que desempenham a mesma função. Você pode usar essas propriedades para personalizar os cabeçalhos de coluna em um <xref:System.Windows.Controls.GridView>. A ordem de precedência para propriedades relacionadas é da direita para a esquerda, em que a propriedade na coluna mais à direita tem a mais alta precedência. Por exemplo, se um <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> é ativada a <xref:System.Windows.Controls.GridViewColumnHeader> objeto e o <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> é definido em associado <xref:System.Windows.Controls.GridViewColumn>, o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> terá precedência. Nesse cenário, o <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> não tem nenhum efeito.  
  
 **Propriedades relacionadas para cabeçalho da coluna em GridView**  
  
|||||  
|-|-|-|-|  
|**Classes**|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|**Propriedades do menu de contexto**|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|Não aplicável|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|**ToolTip**<br /><br /> **Propriedades**|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|Não aplicável|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|**Modelo de Cabeçalho**<br /><br /> **Propriedades**|<xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/<br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|**Propriedades do estilo**|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <sup>1</sup>Para **Propriedades de modelo de cabeçalho**, se as propriedades do modelo e do seletor de modelo forem definidas, a propriedade do modelo terá precedência. Por exemplo, se você definir ambos os <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> e <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> propriedades, o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriedade terá precedência.  
  
## <a name="see-also"></a>Consulte também  
 [Tópicos explicativos](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Visão geral de ListView](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [Visão geral de GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
