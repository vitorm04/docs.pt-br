---
title: "Como compilar uma caixa de diálogo de interface do usuário padrão usando grade"
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
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 69dba9b76f823e1779c4555521552b4a423c844c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="769ce-102">Como compilar uma caixa de diálogo de interface do usuário padrão usando grade</span><span class="sxs-lookup"><span data-stu-id="769ce-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="769ce-103">Este exemplo mostra como criar um padrão [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] caixa de diálogo usando o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="769ce-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="769ce-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="769ce-104">Example</span></span>  
 <span data-ttu-id="769ce-105">O exemplo a seguir cria uma caixa de diálogo como a caixa de diálogo **Executar** no sistema operacional [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].</span><span class="sxs-lookup"><span data-stu-id="769ce-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="769ce-106">O exemplo cria um <xref:System.Windows.Controls.Grid> e usa o <xref:System.Windows.Controls.ColumnDefinition> e <xref:System.Windows.Controls.RowDefinition> classes para definir cinco colunas e quatro linhas.</span><span class="sxs-lookup"><span data-stu-id="769ce-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="769ce-107">O exemplo então adiciona e posiciona um <xref:System.Windows.Controls.Image>, `RunIcon.png`, para representar a imagem que é encontrada na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="769ce-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="769ce-108">A imagem é colocada na primeira coluna e linha do <xref:System.Windows.Controls.Grid> (canto superior esquerdo).</span><span class="sxs-lookup"><span data-stu-id="769ce-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="769ce-109">Em seguida, o exemplo adiciona um <xref:System.Windows.Controls.TextBlock> elemento para a primeira coluna, que abrange as colunas restantes da primeira linha.</span><span class="sxs-lookup"><span data-stu-id="769ce-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="769ce-110">Ele adiciona outro <xref:System.Windows.Controls.TextBlock> elemento para a segunda linha na primeira coluna, para representar o **abrir** caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="769ce-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="769ce-111">Um <xref:System.Windows.Controls.TextBlock> segue, que representa a área de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="769ce-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="769ce-112">Por fim, o exemplo adiciona três <xref:System.Windows.Controls.Button> elementos para a linha final, que representam o **Okey**, **Cancelar**, e **procurar** eventos.</span><span class="sxs-lookup"><span data-stu-id="769ce-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="769ce-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="769ce-113">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [<span data-ttu-id="769ce-114">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="769ce-114">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="769ce-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="769ce-115">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
