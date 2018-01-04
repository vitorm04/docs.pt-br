---
title: Como criar controles em um ToolBar
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: fa6c2373a9372947b1093c4dcca31f563c2a8bf9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-style-controls-on-a-toolbar"></a><span data-ttu-id="28129-102">Como criar controles em um ToolBar</span><span class="sxs-lookup"><span data-stu-id="28129-102">How to: Style Controls on a ToolBar</span></span>
<span data-ttu-id="28129-103">O <xref:System.Windows.Controls.ToolBar> define <xref:System.Windows.ResourceKey> objetos para especificar o estilo dos controles dentro de <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="28129-103">The <xref:System.Windows.Controls.ToolBar> defines <xref:System.Windows.ResourceKey> objects to specify the style of controls within the <xref:System.Windows.Controls.ToolBar>.</span></span>  <span data-ttu-id="28129-104">Para estilizar um controle em um <xref:System.Windows.Controls.ToolBar>, defina o `x:key` atributo de estilo para um <xref:System.Windows.ResourceKey> definido em <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="28129-104">To style a control in a <xref:System.Windows.Controls.ToolBar>, set the `x:key` attribute of the style to a <xref:System.Windows.ResourceKey> defined in <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 <span data-ttu-id="28129-105">O <xref:System.Windows.Controls.ToolBar> define o seguinte <xref:System.Windows.ResourceKey> objetos:</span><span class="sxs-lookup"><span data-stu-id="28129-105">The <xref:System.Windows.Controls.ToolBar> defines the following <xref:System.Windows.ResourceKey> objects:</span></span>  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a><span data-ttu-id="28129-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="28129-106">Example</span></span>  
 <span data-ttu-id="28129-107">O exemplo a seguir define estilos para o controle dentro de um <xref:System.Windows.Controls.ToolBar>.</span><span class="sxs-lookup"><span data-stu-id="28129-107">The following example defines styles for the controls within a <xref:System.Windows.Controls.ToolBar>.</span></span>  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a><span data-ttu-id="28129-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="28129-108">See Also</span></span>  
 [<span data-ttu-id="28129-109">Estilo e modelagem</span><span class="sxs-lookup"><span data-stu-id="28129-109">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)
