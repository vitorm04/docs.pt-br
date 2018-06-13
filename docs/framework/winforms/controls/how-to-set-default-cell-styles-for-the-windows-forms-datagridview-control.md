---
title: Como definir estilos de célula padrão para o controle DataGridView dos Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: ed7ff720d8ef4aa2caa858ea61c4d38866cf50a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538673"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a><span data-ttu-id="93563-102">Como definir estilos de célula padrão para o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93563-102">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="93563-103">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode especificar os estilos de célula padrão para todo o controle em colunas e linhas específicas.</span><span class="sxs-lookup"><span data-stu-id="93563-103">With the <xref:System.Windows.Forms.DataGridView> control, you can specify default cell styles for the entire control and for specific columns and rows.</span></span> <span data-ttu-id="93563-104">Esses padrões filtram do nível do controle até o nível de coluna e depois até o nível de linha e o nível da célula.</span><span class="sxs-lookup"><span data-stu-id="93563-104">These defaults filter down from the control level to the column level, then to the row level, then to the cell level.</span></span> <span data-ttu-id="93563-105">Se um determinado <xref:System.Windows.Forms.DataGridViewCellStyle> propriedade não está definida no nível da célula, a configuração de propriedade padrão no nível de linha é usada.</span><span class="sxs-lookup"><span data-stu-id="93563-105">If a particular <xref:System.Windows.Forms.DataGridViewCellStyle> property is not set at the cell level, the default property setting at the row level is used.</span></span> <span data-ttu-id="93563-106">Se a propriedade também não estiver definida no nível de linha, a configuração de coluna padrão será usada.</span><span class="sxs-lookup"><span data-stu-id="93563-106">If the property is also not set at the row level, the default column setting is used.</span></span> <span data-ttu-id="93563-107">Por fim, se a propriedade não também é definida no nível de coluna, o padrão <xref:System.Windows.Forms.DataGridView> configuração é usada.</span><span class="sxs-lookup"><span data-stu-id="93563-107">Finally, if the property is also not set at the column level, the default <xref:System.Windows.Forms.DataGridView> setting is used.</span></span> <span data-ttu-id="93563-108">Com essa configuração, você pode evitar precisar duplicar as configurações de propriedade em vários níveis.</span><span class="sxs-lookup"><span data-stu-id="93563-108">With this setting, you can avoid having to duplicate the property settings at multiple levels.</span></span> <span data-ttu-id="93563-109">Em cada nível, basta especifica os estilos que são diferentes dos níveis acima.</span><span class="sxs-lookup"><span data-stu-id="93563-109">At each level, simply specify the styles that differ from the levels above it.</span></span> <span data-ttu-id="93563-110">Para obter mais informações, consulte [Estilos de célula no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="93563-110">For more information, see [Cell Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="93563-111">Há um suporte abrangente para esta tarefa no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="93563-111">There is extensive support for this task in Visual Studio.</span></span>  <span data-ttu-id="93563-112">Consulte também [Como definir estilos de célula padrão e formatos de dados para o controle DataGridView dos Windows Forms usando o designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="93563-112">Also see [How to: Set Default Cell Styles and Data Formats for the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).</span></span>  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a><span data-ttu-id="93563-113">Definir estilos de célula padrão com programação</span><span class="sxs-lookup"><span data-stu-id="93563-113">To set the default cell styles programmatically</span></span>  
  
1.  <span data-ttu-id="93563-114">Definir as propriedades do <xref:System.Windows.Forms.DataGridViewCellStyle> recuperados por meio de <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="93563-114">Set the properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> retrieved through the <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> property.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  <span data-ttu-id="93563-115">Criar e inicializar novos <xref:System.Windows.Forms.DataGridViewCellStyle> objetos para uso por várias linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="93563-115">Create and initialize new <xref:System.Windows.Forms.DataGridViewCellStyle> objects for use by multiple rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  <span data-ttu-id="93563-116">Defina a propriedade `DefaultCellStyle` de linhas e colunas específicas.</span><span class="sxs-lookup"><span data-stu-id="93563-116">Set the `DefaultCellStyle` property of specific rows and columns.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a><span data-ttu-id="93563-117">Exemplo</span><span class="sxs-lookup"><span data-stu-id="93563-117">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="93563-118">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="93563-118">Compiling the Code</span></span>  
 <span data-ttu-id="93563-119">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="93563-119">This example requires:</span></span>  
  
-   <span data-ttu-id="93563-120">Um controle <xref:System.Windows.Forms.DataGridView> chamado `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="93563-120">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="93563-121">Referências a <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, e <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span><span class="sxs-lookup"><span data-stu-id="93563-121">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="93563-122">Programação robusta</span><span class="sxs-lookup"><span data-stu-id="93563-122">Robust Programming</span></span>  
 <span data-ttu-id="93563-123">Para obter escalabilidade máxima ao trabalhar com grandes conjuntos de dados, você deve compartilhar <xref:System.Windows.Forms.DataGridViewCellStyle> objetos em várias linhas, colunas ou células que usam os mesmos estilos, em vez de definir as propriedades de estilo para elementos individuais separadamente.</span><span class="sxs-lookup"><span data-stu-id="93563-123">To achieve maximum scalability when you work with very large data sets, you should share <xref:System.Windows.Forms.DataGridViewCellStyle> objects across multiple rows, columns, or cells that use the same styles, rather than set the style properties for individual elements separately.</span></span> <span data-ttu-id="93563-124">Além disso, você deve criar linhas compartilhadas e acessá-los usando o <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> propriedade.</span><span class="sxs-lookup"><span data-stu-id="93563-124">Additionally, you should create shared rows and access them by using the <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="93563-125">Para obter mais informações, consulte [Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="93563-125">For more information, see [Best Practices for Scaling the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93563-126">Consulte também</span><span class="sxs-lookup"><span data-stu-id="93563-126">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="93563-127">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93563-127">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="93563-128">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93563-128">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="93563-129">Práticas recomendadas para colocação em escala do controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93563-129">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="93563-130">Como definir estilos de linha alternados para o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="93563-130">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
