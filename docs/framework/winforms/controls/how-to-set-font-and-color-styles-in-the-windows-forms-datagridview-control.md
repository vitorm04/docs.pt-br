---
title: 'Como: Definir estilos de fonte e cor no controle DataGridView do Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: 737a4b943125245a2916bbf6b24b8abdffa8e371
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215333"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="bc6e4-102">Como: Definir estilos de fonte e cor no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc6e4-102">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="bc6e4-103">Você pode especificar a aparência visual de células dentro de uma <xref:System.Windows.Forms.DataGridView> controle definindo propriedades do <xref:System.Windows.Forms.DataGridViewCellStyle> classe.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-103">You can specify the visual appearance of cells within a <xref:System.Windows.Forms.DataGridView> control by setting properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span> <span data-ttu-id="bc6e4-104">Você pode recuperar as instâncias dessa classe de várias propriedades do <xref:System.Windows.Forms.DataGridView> classe e suas classes complementares ou você pode instanciar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos para atribuição a essas propriedades.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-104">You can retrieve instances of this class from various properties of the <xref:System.Windows.Forms.DataGridView> class and its companion classes, or you can instantiate <xref:System.Windows.Forms.DataGridViewCellStyle> objects for assignment to these properties.</span></span>  
  
 <span data-ttu-id="bc6e4-105">Os procedimentos a seguir demonstram a personalização básica da aparência de célula usando a <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-105">The following procedures demonstrate basic customization of cell appearance using the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> property.</span></span> <span data-ttu-id="bc6e4-106">Todas as células no controle herdam os estilos especificados por essa propriedade, a menos que eles sejam substituídos no nível da célula, linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-106">Every cell in the control inherits the styles specified through this property unless they are overridden at the column, row, or cell level.</span></span> <span data-ttu-id="bc6e4-107">Para obter um exemplo de herança de estilo, consulte [como: Definir estilos de célula padrão para o Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-107">For an example of style inheritance, see [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span> <span data-ttu-id="bc6e4-108">Para obter informações sobre usos adicionais do <xref:System.Windows.Forms.DataGridViewCellStyle> de classe, consulte os tópicos listados na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-108">For information about additional uses of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, see the topics listed in the See Also section.</span></span>  
  
 <span data-ttu-id="bc6e4-109">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-109">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="bc6e4-110">Consulte também [como: Definir estilos de célula padrão e formatos de dados para o Windows Forms usando o Designer de controle de DataGridView](default-cell-styles-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-110">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](default-cell-styles-datagridview.md).</span></span>  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a><span data-ttu-id="bc6e4-111">Para especificar a fonte usada pelas células DataGridView</span><span class="sxs-lookup"><span data-stu-id="bc6e4-111">To specify the font used by DataGridView cells</span></span>  
  
-   <span data-ttu-id="bc6e4-112">Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> propriedade de um <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-112">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> property of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="bc6e4-113">O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir a fonte para todo o controle.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-113">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set the font for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a><span data-ttu-id="bc6e4-114">Para especificar as cores de primeiro plano e de tela de fundo das células DataGridView</span><span class="sxs-lookup"><span data-stu-id="bc6e4-114">To specify the foreground and background colors of DataGridView cells</span></span>  
  
-   <span data-ttu-id="bc6e4-115">Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> propriedades de um <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-115">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="bc6e4-116">O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir esses estilos para todo o controle.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-116">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a><span data-ttu-id="bc6e4-117">Para especificar as cores de primeiro plano e de tela de fundo das células DataGridView selecionadas</span><span class="sxs-lookup"><span data-stu-id="bc6e4-117">To specify the foreground and background colors of selected DataGridView cells</span></span>  
  
-   <span data-ttu-id="bc6e4-118">Defina as <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> e <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> propriedades de um <xref:System.Windows.Forms.DataGridViewCellStyle>.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-118">Set the <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> and <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> properties of a <xref:System.Windows.Forms.DataGridViewCellStyle>.</span></span> <span data-ttu-id="bc6e4-119">O seguinte exemplo de código usa o <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade para definir esses estilos para todo o controle.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-119">The following code example uses the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property to set these styles for the entire control.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a><span data-ttu-id="bc6e4-120">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bc6e4-120">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc6e4-121">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="bc6e4-121">Compiling the Code</span></span>  
 <span data-ttu-id="bc6e4-122">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="bc6e4-122">This example requires:</span></span>  
  
-   <span data-ttu-id="bc6e4-123">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-123">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="bc6e4-124">Referências para o <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-124">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="bc6e4-125">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="bc6e4-125">Robust Programming</span></span>  
 <span data-ttu-id="bc6e4-126">Para obter escalabilidade máxima, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para cada elemento separadamente.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-126">For maximum scalability, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than setting the style properties for each element separately.</span></span> <span data-ttu-id="bc6e4-127">Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-127">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc6e4-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bc6e4-128">See also</span></span>

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [<span data-ttu-id="bc6e4-129">Formatação básica e estilos no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc6e4-129">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="bc6e4-130">Estilos de célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc6e4-130">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)
