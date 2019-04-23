---
title: 'Como: Criar uma caixa de diálogo de interface do usuário padrão usando grade'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149520"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a><span data-ttu-id="d06ea-102">Como: Criar uma caixa de diálogo de interface do usuário padrão usando grade</span><span class="sxs-lookup"><span data-stu-id="d06ea-102">How to: Build a Standard UI Dialog Box by Using Grid</span></span>
<span data-ttu-id="d06ea-103">Este exemplo mostra como criar um padrão [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] caixa de diálogo usando o <xref:System.Windows.Controls.Grid> elemento.</span><span class="sxs-lookup"><span data-stu-id="d06ea-103">This example shows how to create a standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialog box by using the <xref:System.Windows.Controls.Grid> element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d06ea-104">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d06ea-104">Example</span></span>  
 <span data-ttu-id="d06ea-105">O exemplo a seguir cria uma caixa de diálogo como a caixa de diálogo **Executar** no sistema operacional [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d06ea-105">The following example creates a dialog box like the **Run** dialog box in the [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operating system.</span></span>  
  
 <span data-ttu-id="d06ea-106">O exemplo cria um <xref:System.Windows.Controls.Grid> e usa o <xref:System.Windows.Controls.ColumnDefinition> e <xref:System.Windows.Controls.RowDefinition> classes para definir cinco colunas e quatro linhas.</span><span class="sxs-lookup"><span data-stu-id="d06ea-106">The example creates a <xref:System.Windows.Controls.Grid> and uses the <xref:System.Windows.Controls.ColumnDefinition> and <xref:System.Windows.Controls.RowDefinition> classes to define five columns and four rows.</span></span>  
  
 <span data-ttu-id="d06ea-107">O exemplo então adiciona e posiciona um <xref:System.Windows.Controls.Image>, `RunIcon.png`, para representar a imagem que é encontrada na caixa de diálogo.</span><span class="sxs-lookup"><span data-stu-id="d06ea-107">The example then adds and positions an <xref:System.Windows.Controls.Image>, `RunIcon.png`, to represent the image that is found in the dialog box.</span></span> <span data-ttu-id="d06ea-108">A imagem é colocada na primeira coluna e linha do <xref:System.Windows.Controls.Grid> (canto superior esquerdo).</span><span class="sxs-lookup"><span data-stu-id="d06ea-108">The image is placed in the first column and row of the <xref:System.Windows.Controls.Grid> (the upper-left corner).</span></span>  
  
 <span data-ttu-id="d06ea-109">Em seguida, o exemplo adiciona um <xref:System.Windows.Controls.TextBlock> elemento para a primeira coluna, que abrange as colunas restantes da primeira linha.</span><span class="sxs-lookup"><span data-stu-id="d06ea-109">Next, the example adds a <xref:System.Windows.Controls.TextBlock> element to the first column, which spans the remaining columns of the first row.</span></span> <span data-ttu-id="d06ea-110">Ele adiciona outro <xref:System.Windows.Controls.TextBlock> elemento à segunda linha na primeira coluna, para representar o **aberto** caixa de texto.</span><span class="sxs-lookup"><span data-stu-id="d06ea-110">It adds another <xref:System.Windows.Controls.TextBlock> element to the second row in the first column, to represent the **Open** text box.</span></span> <span data-ttu-id="d06ea-111">Um <xref:System.Windows.Controls.TextBlock> segue, que representa a área de entrada de dados.</span><span class="sxs-lookup"><span data-stu-id="d06ea-111">A <xref:System.Windows.Controls.TextBlock> follows, which represents the data entry area.</span></span>  
  
 <span data-ttu-id="d06ea-112">Por fim, o exemplo adiciona três <xref:System.Windows.Controls.Button> elementos para a linha final, que representam os **Okey**, **Cancelar**, e **procurar** eventos.</span><span class="sxs-lookup"><span data-stu-id="d06ea-112">Finally, the example adds three <xref:System.Windows.Controls.Button> elements to the final row, which represent the **OK**, **Cancel**, and **Browse** events.</span></span>  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="d06ea-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d06ea-113">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [<span data-ttu-id="d06ea-114">Visão geral de painéis</span><span class="sxs-lookup"><span data-stu-id="d06ea-114">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="d06ea-115">Tópicos de instruções</span><span class="sxs-lookup"><span data-stu-id="d06ea-115">How-to Topics</span></span>](grid-how-to-topics.md)
