---
title: Definir estilos de célula padrão para controle DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744873"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="46ea6-102">Como definir estilos de célula padrão para o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46ea6-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="46ea6-103">Com o controle <xref:System.Windows.Forms.DataGridView>, você pode especificar estilos de célula padrão para todo o controle e para colunas e linhas específicas.</span><span class="sxs-lookup"><span data-stu-id="46ea6-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="46ea6-104">Esses padrões filtram do nível do controle até o nível de coluna e depois até o nível de linha e o nível da célula.</span><span class="sxs-lookup"><span data-stu-id="46ea6-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="46ea6-105">Se uma determinada propriedade de <xref:System.Windows.Forms.DataGridViewCellStyle> não for definida no nível de célula, a configuração de propriedade padrão no nível de linha será usada.</span><span class="sxs-lookup"><span data-stu-id="46ea6-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="46ea6-106">Se a propriedade também não estiver definida no nível de linha, a configuração de coluna padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="46ea6-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="46ea6-107">Por fim, se a propriedade também não estiver definida no nível de coluna, a configuração de <xref:System.Windows.Forms.DataGridView> padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="46ea6-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="46ea6-108">Com essa configuração, você pode evitar precisar duplicar as configurações de propriedade em vários níveis.</span><span class="sxs-lookup"><span data-stu-id="46ea6-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="46ea6-109">Em cada nível, basta especifica os estilos que são diferentes dos níveis acima.</span><span class="sxs-lookup"><span data-stu-id="46ea6-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="46ea6-110">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="46ea6-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="46ea6-111">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="46ea6-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="46ea6-112">Consulte também [Como definir estilos de célula padrão e formatos de dados para o controle DataGridView dos Windows Forms usando o designer](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="46ea6-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="46ea6-113">Definir estilos de célula padrão com programação</span><span class="sxs-lookup"><span data-stu-id="46ea6-113">To set the default cell styles programmatically</span></span>  
  
1. <span data-ttu-id="46ea6-114">Defina as propriedades do <xref:System.Windows.Forms.DataGridViewCellStyle> recuperado por meio da propriedade <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46ea6-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. <span data-ttu-id="46ea6-115">Crie e Inicialize novos objetos de <xref:System.Windows.Forms.DataGridViewCellStyle> para uso por várias linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="46ea6-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. <span data-ttu-id="46ea6-116">Defina a propriedade `DefaultCellStyle` de linhas e colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="46ea6-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="46ea6-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="46ea6-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="46ea6-118">Compilando o Código</span><span class="sxs-lookup"><span data-stu-id="46ea6-118">Compiling the Code</span></span>  
 <span data-ttu-id="46ea6-119">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="46ea6-119">This example requires:</span></span>  
  
- <span data-ttu-id="46ea6-120">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="46ea6-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="46ea6-121">Referências aos assemblies <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>e <xref:System.Windows.Forms?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46ea6-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="46ea6-122">Programação Robusta</span><span class="sxs-lookup"><span data-stu-id="46ea6-122">Robust Programming</span></span>  
 <span data-ttu-id="46ea6-123">Para obter a escalabilidade máxima ao trabalhar com conjuntos de dados muito grandes, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para elementos individuais separadamente.</span><span class="sxs-lookup"><span data-stu-id="46ea6-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="46ea6-124">Além disso, você deve criar linhas compartilhadas e acessá-las usando a propriedade <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="46ea6-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="46ea6-125">Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView do Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="46ea6-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46ea6-126">Veja também</span><span class="sxs-lookup"><span data-stu-id="46ea6-126">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [<span data-ttu-id="46ea6-127">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46ea6-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="46ea6-128">Estilos de Célula no Controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46ea6-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="46ea6-129">Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46ea6-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="46ea6-130">Como definir estilos de linha alternados para o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="46ea6-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
