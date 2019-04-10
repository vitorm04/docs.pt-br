---
title: 'Como: Formatar dados no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in DataGridView control
- data grids [Windows Forms], enabling wordwrap
- currency values [Windows Forms], formatting in data grids
- data grids [Windows Forms], currency values
- data grids [Windows Forms], formatting data
- data grids [Windows Forms], text alignment
- data grids [Windows Forms], date values
- cells [Windows Forms], text alignment
ms.assetid: 8c33543c-9c08-4636-a65a-fdf714a529b7
ms.openlocfilehash: 62701edfdb3cf2729cb401ad12a12ee4f524287b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59221294"
---
# <a name="how-to-format-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e73b1-102">Como: Formatar dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e73b1-102">How to: Format Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e73b1-103">Os procedimentos a seguir demonstram a formatação básica de valores de célula usando a <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade de um <xref:System.Windows.Forms.DataGridView> controle e de colunas específicas em um controle.</span><span class="sxs-lookup"><span data-stu-id="e73b1-103">The following procedures demonstrate basic formatting of cell values using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property of a <xref:System.Windows.Forms.DataGridView> control and of specific columns in a control.</span></span> <span data-ttu-id="e73b1-104">Para obter informações sobre a formatação de dados avançados, consulte [como: Personalizar a formatação de dados no controle DataGridView dos Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e73b1-104">For information about advanced data formatting, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
### <a name="to-format-currency-and-date-values"></a><span data-ttu-id="e73b1-105">Formatar os valores de moeda e datas</span><span class="sxs-lookup"><span data-stu-id="e73b1-105">To format currency and date values</span></span>  
  
-   <span data-ttu-id="e73b1-106">Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="e73b1-106">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="e73b1-107">O exemplo de código a seguir define o formato para colunas específicas usando o <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriedade das colunas.</span><span class="sxs-lookup"><span data-stu-id="e73b1-107">The following code example sets the format for specific columns using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the columns.</span></span> <span data-ttu-id="e73b1-108">Valores na coluna `UnitPrice` aparecem no formato de moeda específico da cultura atual, com valores negativos entre parênteses.</span><span class="sxs-lookup"><span data-stu-id="e73b1-108">Values in the `UnitPrice` column appear in the current culture-specific currency format, with negative values surrounded by parentheses.</span></span> <span data-ttu-id="e73b1-109">Valores na coluna `ShipDate` aparecem no formato de data curto específico da cultura atual.</span><span class="sxs-lookup"><span data-stu-id="e73b1-109">Values in the `ShipDate` column appear in the current culture-specific short date format.</span></span> <span data-ttu-id="e73b1-110">Para obter mais informações sobre <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> valores, consulte [tipos de formatação](../../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="e73b1-110">For more information about <xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A> values, see [Formatting Types](../../../standard/base-types/formatting-types.md).</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#071)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#071](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#071)]  
  
### <a name="to-customize-the-display-of-null-database-values"></a><span data-ttu-id="e73b1-111">Personalizar a exibição de valores nulos de banco de dados</span><span class="sxs-lookup"><span data-stu-id="e73b1-111">To customize the display of null database values</span></span>  
  
-   <span data-ttu-id="e73b1-112">Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="e73b1-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.NullValue%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="e73b1-113">O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para não exibir "nenhuma entrada" em todas as células que contêm valores iguais a <xref:System.DBNull.Value?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e73b1-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to display "no entry" in all cells containing values equal to <xref:System.DBNull.Value?displayProperty=nameWithType>.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#073)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#073](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#073)]  
  
### <a name="to-enable-wordwrap-in-text-based-cells"></a><span data-ttu-id="e73b1-114">Habilitar quebra automática de linha nas células de texto</span><span class="sxs-lookup"><span data-stu-id="e73b1-114">To enable wordwrap in text-based cells</span></span>  
  
-   <span data-ttu-id="e73b1-115">Defina a <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle> a um do <xref:System.Windows.Forms.DataGridViewTriState> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e73b1-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.WrapMode%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewTriState> enumeration values.</span></span> <span data-ttu-id="e73b1-116">O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir o modo de encapsulamento para todo o controle.</span><span class="sxs-lookup"><span data-stu-id="e73b1-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the wrap mode for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#074)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#074](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#074)]  
  
### <a name="to-specify-the-text-alignment-of-datagridview-cells"></a><span data-ttu-id="e73b1-117">Especificar o alinhamento de texto de células DataGridView</span><span class="sxs-lookup"><span data-stu-id="e73b1-117">To specify the text alignment of DataGridView cells</span></span>  
  
-   <span data-ttu-id="e73b1-118">Defina a <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle> a um do <xref:System.Windows.Forms.DataGridViewContentAlignment> valores de enumeração.</span><span class="sxs-lookup"><span data-stu-id="e73b1-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Alignment%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle> to one of the <xref:System.Windows.Forms.DataGridViewContentAlignment> enumeration values.</span></span> <span data-ttu-id="e73b1-119">O exemplo de código a seguir define o alinhamento de uma coluna específica usando o <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> propriedade da coluna.</span><span class="sxs-lookup"><span data-stu-id="e73b1-119">The following code example sets the alignment for a specific column using the <xref:System.Windows.Forms.DataGridViewColumn.DefaultCellStyle%2A> property of the column.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#072)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#072](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#072)]  
  
## <a name="example"></a><span data-ttu-id="e73b1-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e73b1-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#070)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#070](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#070)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e73b1-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="e73b1-121">Compiling the Code</span></span>  
 <span data-ttu-id="e73b1-122">Esses exemplos precisam de:</span><span class="sxs-lookup"><span data-stu-id="e73b1-122">These examples require:</span></span>  
  
-   <span data-ttu-id="e73b1-123">Um <xref:System.Windows.Forms.DataGridView> controle chamado `dataGridView1` que contém uma coluna denominada `UnitPrice`, uma coluna denominada `ShipDate`e uma coluna denominada `CustomerName`.</span><span class="sxs-lookup"><span data-stu-id="e73b1-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `UnitPrice`, a column named `ShipDate`, and a column named `CustomerName`.</span></span>  
  
-   <span data-ttu-id="e73b1-124">Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="e73b1-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="e73b1-125">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="e73b1-125">Robust Programming</span></span>  
 <span data-ttu-id="e73b1-126">Para obter escalabilidade máxima, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos em vez de configurar as propriedades de estilo para cada elemento separadamente.</span><span class="sxs-lookup"><span data-stu-id="e73b1-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="e73b1-127">Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="e73b1-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e73b1-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e73b1-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="e73b1-129">Formatação básica e estilos no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e73b1-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e73b1-130">Estilos de célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e73b1-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e73b1-131">Formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e73b1-131">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e73b1-132">Como: Personalizar a formatação de dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e73b1-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e73b1-133">Formatar tipos</span><span class="sxs-lookup"><span data-stu-id="e73b1-133">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)
