---
title: Como criar um elemento de grade
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
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30fdd89a46e5d2027e9c525b0ca8cfcfb1d11ed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="20c35-102">Como criar um elemento de grade</span><span class="sxs-lookup"><span data-stu-id="20c35-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="20c35-103">Exemplo</span><span class="sxs-lookup"><span data-stu-id="20c35-103">Example</span></span>  
 <span data-ttu-id="20c35-104">O exemplo a seguir mostra como criar e usar uma instância de <xref:System.Windows.Controls.Grid> usando [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] ou código.</span><span class="sxs-lookup"><span data-stu-id="20c35-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="20c35-105">Este exemplo usa três <xref:System.Windows.Controls.ColumnDefinition> objetos e três <xref:System.Windows.Controls.RowDefinition> objetos criar uma grade que tem nove células, como em uma planilha.</span><span class="sxs-lookup"><span data-stu-id="20c35-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="20c35-106">Cada célula contém um <xref:System.Windows.Controls.TextBlock> elemento que representa a data e a linha superior contém um <xref:System.Windows.Controls.TextBlock> com o <xref:System.Windows.Controls.Grid.ColumnSpan%2A> propriedade aplicada.</span><span class="sxs-lookup"><span data-stu-id="20c35-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="20c35-107">Para mostrar os limites de cada célula, o <xref:System.Windows.Controls.Grid.ShowGridLines%2A> propriedade está habilitada.</span><span class="sxs-lookup"><span data-stu-id="20c35-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="20c35-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="20c35-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="20c35-109">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="20c35-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
