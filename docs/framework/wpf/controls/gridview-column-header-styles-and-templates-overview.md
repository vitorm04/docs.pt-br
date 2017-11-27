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
# <a name="gridview-column-header-styles-and-templates-overview"></a><span data-ttu-id="56c1a-102">Visão geral dos estilos e dos modelos de cabeçalho da coluna GridView</span><span class="sxs-lookup"><span data-stu-id="56c1a-102">GridView Column Header Styles and Templates Overview</span></span>
<span data-ttu-id="56c1a-103">Esta visão geral discute a ordem de precedência para as propriedades que você usar para personalizar um cabeçalho de coluna no <xref:System.Windows.Controls.GridView> modo de exibição de um <xref:System.Windows.Controls.ListView> controle.</span><span class="sxs-lookup"><span data-stu-id="56c1a-103">This overview discusses the order of precedence for properties that you use to customize a column header in the <xref:System.Windows.Controls.GridView> view mode of a <xref:System.Windows.Controls.ListView> control.</span></span>  
  
## <a name="customizing-a-column-header-in-a-gridview"></a><span data-ttu-id="56c1a-104">Personalizando um cabeçalho da coluna em GridView</span><span class="sxs-lookup"><span data-stu-id="56c1a-104">Customizing a Column Header in a GridView</span></span>  
 <span data-ttu-id="56c1a-105">As propriedades que definem o conteúdo, layout e estilo de um cabeçalho de coluna em um <xref:System.Windows.Controls.GridView> são encontradas em muitas classes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="56c1a-105">The properties that define the content, layout, and style of a column header in a <xref:System.Windows.Controls.GridView> are found on many related classes.</span></span> <span data-ttu-id="56c1a-106">Algumas dessas propriedades tem funcionalidades parecidas ou iguais.</span><span class="sxs-lookup"><span data-stu-id="56c1a-106">Some of these properties have functionality that is similar or the same.</span></span>  
  
 <span data-ttu-id="56c1a-107">As linhas na tabela a seguir mostram grupos de propriedades que desempenham a mesma função.</span><span class="sxs-lookup"><span data-stu-id="56c1a-107">The rows in the following table show groups of properties that perform the same function.</span></span> <span data-ttu-id="56c1a-108">Você pode usar essas propriedades para personalizar os cabeçalhos de coluna em um <xref:System.Windows.Controls.GridView>.</span><span class="sxs-lookup"><span data-stu-id="56c1a-108">You can use these properties to customize the column headers in a <xref:System.Windows.Controls.GridView>.</span></span> <span data-ttu-id="56c1a-109">A ordem de precedência para propriedades relacionadas é da direita para a esquerda, em que a propriedade na coluna mais à direita tem a mais alta precedência.</span><span class="sxs-lookup"><span data-stu-id="56c1a-109">The order of precedence for related properties is from right to left where the property in the farthest right column has the highest precedence.</span></span> <span data-ttu-id="56c1a-110">Por exemplo, se um <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> é ativada a <xref:System.Windows.Controls.GridViewColumnHeader> objeto e o <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> é definido em associado <xref:System.Windows.Controls.GridViewColumn>, o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> terá precedência.</span><span class="sxs-lookup"><span data-stu-id="56c1a-110">For example, if a <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> is set on the <xref:System.Windows.Controls.GridViewColumnHeader> object and the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> is set on the associated <xref:System.Windows.Controls.GridViewColumn>, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> takes precedence.</span></span> <span data-ttu-id="56c1a-111">Nesse cenário, o <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> não tem nenhum efeito.</span><span class="sxs-lookup"><span data-stu-id="56c1a-111">In this scenario, the <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A> has no effect.</span></span>  
  
 <span data-ttu-id="56c1a-112">**Propriedades relacionadas para cabeçalho da coluna em GridView**</span><span class="sxs-lookup"><span data-stu-id="56c1a-112">**Related properties for column headers in a GridView**</span></span>  
  
|||||  
|-|-|-|-|  
|<span data-ttu-id="56c1a-113">**Classes**</span><span class="sxs-lookup"><span data-stu-id="56c1a-113">**Classes**</span></span>|<xref:System.Windows.Controls.GridView>|<xref:System.Windows.Controls.GridViewColumn>|<xref:System.Windows.Controls.GridViewColumnHeader>|  
|<span data-ttu-id="56c1a-114">**Propriedades do menu de contexto**</span><span class="sxs-lookup"><span data-stu-id="56c1a-114">**Context Menu Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContextMenu%2A>|<span data-ttu-id="56c1a-115">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="56c1a-115">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ContextMenu%2A>|  
|<span data-ttu-id="56c1a-116">**ToolTip**</span><span class="sxs-lookup"><span data-stu-id="56c1a-116">**ToolTip**</span></span><br /><br /> <span data-ttu-id="56c1a-117">**Propriedades**</span><span class="sxs-lookup"><span data-stu-id="56c1a-117">**Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderToolTip%2A>|<span data-ttu-id="56c1a-118">Não aplicável</span><span class="sxs-lookup"><span data-stu-id="56c1a-118">Not applicable</span></span>|<xref:System.Windows.FrameworkElement.ToolTip%2A>|  
|<span data-ttu-id="56c1a-119">**Modelo de Cabeçalho**</span><span class="sxs-lookup"><span data-stu-id="56c1a-119">**Header Template**</span></span><br /><br /> <span data-ttu-id="56c1a-120">**Propriedades**</span><span class="sxs-lookup"><span data-stu-id="56c1a-120">**Properties**</span></span>|<span data-ttu-id="56c1a-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="56c1a-121"><xref:System.Windows.Controls.GridView.ColumnHeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridView.ColumnHeaderTemplateSelector%2A>|<span data-ttu-id="56c1a-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="56c1a-122"><xref:System.Windows.Controls.GridViewColumn.HeaderTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.GridViewColumn.HeaderTemplateSelector%2A>|<span data-ttu-id="56c1a-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span><span class="sxs-lookup"><span data-stu-id="56c1a-123"><xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <sup>1</sup>/</span></span><br /><br /> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>|  
|<span data-ttu-id="56c1a-124">**Propriedades do estilo**</span><span class="sxs-lookup"><span data-stu-id="56c1a-124">**Style Properties**</span></span>|<xref:System.Windows.Controls.GridView.ColumnHeaderContainerStyle%2A>|<xref:System.Windows.Controls.GridViewColumn.HeaderContainerStyle%2A>|<xref:System.Windows.FrameworkElement.Style%2A>|  
  
 <span data-ttu-id="56c1a-125"><sup>1</sup>Para **Propriedades de modelo de cabeçalho**, se as propriedades do modelo e do seletor de modelo forem definidas, a propriedade do modelo terá precedência.</span><span class="sxs-lookup"><span data-stu-id="56c1a-125"><sup>1</sup>For **Header Template Properties**, if you set both the template and template selector properties, the template property takes precedence.</span></span> <span data-ttu-id="56c1a-126">Por exemplo, se você definir ambos os <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> e <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> propriedades, o <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> propriedade terá precedência.</span><span class="sxs-lookup"><span data-stu-id="56c1a-126">For example, if you set both the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> and <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> properties, the <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> property takes precedence.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56c1a-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56c1a-127">See Also</span></span>  
 [<span data-ttu-id="56c1a-128">Tópicos explicativos</span><span class="sxs-lookup"><span data-stu-id="56c1a-128">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [<span data-ttu-id="56c1a-129">Visão geral de ListView</span><span class="sxs-lookup"><span data-stu-id="56c1a-129">ListView Overview</span></span>](../../../../docs/framework/wpf/controls/listview-overview.md)  
 [<span data-ttu-id="56c1a-130">Visão geral de GridView</span><span class="sxs-lookup"><span data-stu-id="56c1a-130">GridView Overview</span></span>](../../../../docs/framework/wpf/controls/gridview-overview.md)
