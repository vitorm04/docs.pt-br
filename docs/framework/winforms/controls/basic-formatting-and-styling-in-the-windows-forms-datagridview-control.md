---
title: Formatação básica e estilos no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: d38620c321fb12b9f489fd086e222b7780337ab3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528789"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="206dd-102">Formatação básica e estilos no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="206dd-103">O controle `DataGridView` facilita a tarefa de definir a aparência básica de células e a formatação da exibição dos valores de célula.</span><span class="sxs-lookup"><span data-stu-id="206dd-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="206dd-104">Você pode definir os estilos de aparência e formatação de células individuais, para células em linhas e colunas específicas ou para todas as células no controle definindo as propriedades dos objetos `DataGridViewCellStyle` acessados por meio de várias propriedades do controle `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="206dd-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="206dd-105">Além disso, é possível modificar esses estilos dinamicamente com base em fatores como o valor da célula manipulando o evento `CellFormatting`.</span><span class="sxs-lookup"><span data-stu-id="206dd-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="206dd-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="206dd-106">In This Section</span></span>  
 [<span data-ttu-id="206dd-107">Como alterar os estilos de borda e de guia da linha de grade no tempo de execução no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="206dd-108">Descreve como configurar as propriedades `DataGridView` que definem a aparência da borda do controle e as linhas de limite entre células.</span><span class="sxs-lookup"><span data-stu-id="206dd-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="206dd-109">Estilos de célula no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="206dd-110">Descreve a classe `DataGridViewCellStyle` e como propriedades desse tipo interagem para definir como as células são exibidas no controle.</span><span class="sxs-lookup"><span data-stu-id="206dd-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="206dd-111">Como definir estilos de célula padrão para o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="206dd-112">Descreve como usar propriedades `DataGridViewCellStyle` para definir a aparência padrão de células em linhas e colunas específicas e em todo o controle.</span><span class="sxs-lookup"><span data-stu-id="206dd-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="206dd-113">Como formatar dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="206dd-114">Descreve como formatar valores de exibição de célula usando propriedades `DataGridViewCellStyle`.</span><span class="sxs-lookup"><span data-stu-id="206dd-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="206dd-115">Como definir estilos de fonte e cor no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="206dd-116">Descreve como usar a propriedade `DefaultCellStyle` para definir as características de exibição básicas para todas as células no controle.</span><span class="sxs-lookup"><span data-stu-id="206dd-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="206dd-117">Como definir estilos de linha alternada para o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="206dd-118">Descreve como criar um efeito semelhante à razão no controle usando linhas alternadas são exibidas de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="206dd-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="206dd-119">Como usar o modelo da linha para personalizar linhas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="206dd-120">Descreve como usar a propriedade `RowTemplate` para definir as propriedades de linha que serão usadas para todas as linhas no controle.</span><span class="sxs-lookup"><span data-stu-id="206dd-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="206dd-121">Referência</span><span class="sxs-lookup"><span data-stu-id="206dd-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="206dd-122">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="206dd-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="206dd-123">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewCellStyle> classe.</span><span class="sxs-lookup"><span data-stu-id="206dd-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="206dd-124">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.CellFormatting> evento.</span><span class="sxs-lookup"><span data-stu-id="206dd-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="206dd-125">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="206dd-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="206dd-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="206dd-126">Related Sections</span></span>  
 [<span data-ttu-id="206dd-127">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-127">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="206dd-128">Fornece tópicos que descrevem a pintura personalizada de células e linhas <xref:System.Windows.Forms.DataGridView>, bem como a criação de tipos de célula, coluna e linha derivados.</span><span class="sxs-lookup"><span data-stu-id="206dd-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="206dd-129">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="206dd-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="206dd-130">Fornece tópicos que descrevem as propriedades da célula, linha e coluna mais usados.</span><span class="sxs-lookup"><span data-stu-id="206dd-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="206dd-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="206dd-131">See Also</span></span>  
 [<span data-ttu-id="206dd-132">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="206dd-132">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)
