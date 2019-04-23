---
title: Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView
ms.date: 03/30/2017
helpviewer_keywords:
- column headers [WPF], customizing
- ListView controls [WPF], GridView column header styles
- controls [WPF], ListView
- headers [WPF], customizing
- GridView view mode [WPF], customizing column headers
ms.assetid: 74835674-a39e-4ab5-9418-ad7f6ab7b956
ms.openlocfilehash: 83643d8acea706bad439683702e4228d240b97bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59090286"
---
# <a name="gridview-column-header-styles-and-templates-overview"></a>Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView
Esta visão geral discute a ordem de precedência para propriedades que você pode usar para personalizar um cabeçalho de coluna na <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.  
  
## <a name="customizing-a-column-header-in-a-gridview"></a>Personalizando um cabeçalho da coluna em GridView  
 As propriedades que definem o conteúdo, layout e estilo de um cabeçalho de coluna em um <xref:System.Windows.Controls.GridView> são encontradas em muitas classes relacionadas. Algumas dessas propriedades tem funcionalidades parecidas ou iguais.  
  
 As linhas na tabela a seguir mostram grupos de propriedades que desempenham a mesma função. Você pode usar essas propriedades para personalizar os cabeçalhos de coluna em um <xref:System.Windows.Controls.GridView>. A ordem de precedência para propriedades relacionadas é da direita para a esquerda, em que a propriedade na coluna mais à direita tem a mais alta precedência. Por exemplo, se um <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> é definida na <xref:System.Windows.Controls.GridViewColumnHeader> objeto e o <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> estiver definido no associado <xref:System.Windows.Controls.GridViewColumn>, o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> terá precedência. Nesse cenário, o <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> não tem nenhum efeito.  
  
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

- [Tópicos de instruções](listview-how-to-topics.md)
- [Visão geral de ListView](listview-overview.md)
- [Visão geral de GridView](gridview-overview.md)
