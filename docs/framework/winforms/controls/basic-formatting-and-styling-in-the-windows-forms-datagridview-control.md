---
title: Formatação básica e estilos no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting and styling
- data grids [Windows Forms], formatting
ms.assetid: b9b90836-1f56-4aa9-8db8-edc78fe830e8
ms.openlocfilehash: 5e967c1bbe54095cc11e48b014600158da7fe6a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189867"
---
# <a name="basic-formatting-and-styling-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="8657f-102">Formatação básica e estilos no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-102">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="8657f-103">O controle `DataGridView` facilita a tarefa de definir a aparência básica de células e a formatação da exibição dos valores de célula.</span><span class="sxs-lookup"><span data-stu-id="8657f-103">The `DataGridView` control makes it easy to define the basic appearance of cells and the display formatting of cell values.</span></span> <span data-ttu-id="8657f-104">Você pode definir os estilos de aparência e formatação de células individuais, para células em linhas e colunas específicas ou para todas as células no controle definindo as propriedades dos objetos `DataGridViewCellStyle` acessados por meio de várias propriedades do controle `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="8657f-104">You can define appearance and formatting styles for individual cells, for cells in specific columns and rows, or for all cells in the control by setting the properties of the `DataGridViewCellStyle` objects accessed through various `DataGridView` control properties.</span></span> <span data-ttu-id="8657f-105">Além disso, é possível modificar esses estilos dinamicamente com base em fatores como o valor da célula manipulando o evento `CellFormatting`.</span><span class="sxs-lookup"><span data-stu-id="8657f-105">Additionally, you can modify these styles dynamically based on factors such as the cell value by handling the `CellFormatting` event.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8657f-106">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="8657f-106">In This Section</span></span>  
 [<span data-ttu-id="8657f-107">Como: Alterar a borda e os estilos da linha de grade no tempo de execução no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-107">How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control</span></span>](change-the-border-and-gridline-styles-in-the-datagrid.md)  
 <span data-ttu-id="8657f-108">Descreve como configurar as propriedades `DataGridView` que definem a aparência da borda do controle e as linhas de limite entre células.</span><span class="sxs-lookup"><span data-stu-id="8657f-108">Describes how to set `DataGridView` properties that define the appearance of the control border and the boundary lines between cells.</span></span>  
  
 [<span data-ttu-id="8657f-109">Estilos de célula no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-109">Cell Styles in the Windows Forms DataGridView Control</span></span>](cell-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8657f-110">Descreve a classe `DataGridViewCellStyle` e como propriedades desse tipo interagem para definir como as células são exibidas no controle.</span><span class="sxs-lookup"><span data-stu-id="8657f-110">Describes the `DataGridViewCellStyle` class and how properties of that type interact to define how cells are displayed in the control.</span></span>  
  
 [<span data-ttu-id="8657f-111">Como: Definir estilos de célula padrão para o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-111">How to: Set Default Cell Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8657f-112">Descreve como usar propriedades `DataGridViewCellStyle` para definir a aparência padrão de células em linhas e colunas específicas e em todo o controle.</span><span class="sxs-lookup"><span data-stu-id="8657f-112">Describes how to use `DataGridViewCellStyle` properties to define the default appearance of cells in specific rows and columns and in the entire control.</span></span>  
  
 [<span data-ttu-id="8657f-113">Como: Formatar dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-113">How to: Format Data in the Windows Forms DataGridView Control</span></span>](how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8657f-114">Descreve como formatar valores de exibição de célula usando propriedades `DataGridViewCellStyle`.</span><span class="sxs-lookup"><span data-stu-id="8657f-114">Describes how to format cell display values using `DataGridViewCellStyle` properties.</span></span>  
  
 [<span data-ttu-id="8657f-115">Como: Definir estilos de fonte e cor no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-115">How to: Set Font and Color Styles in the Windows Forms DataGridView Control</span></span>](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8657f-116">Descreve como usar a propriedade `DefaultCellStyle` para definir as características de exibição básicas para todas as células no controle.</span><span class="sxs-lookup"><span data-stu-id="8657f-116">Describes how to use the `DefaultCellStyle` property to set basic display characteristics for all cells in the control.</span></span>  
  
 [<span data-ttu-id="8657f-117">Como: Definir estilos de linha alternados para o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-117">How to: Set Alternating Row Styles for the Windows Forms DataGridView Control</span></span>](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8657f-118">Descreve como criar um efeito semelhante à razão no controle usando linhas alternadas são exibidas de maneira diferente.</span><span class="sxs-lookup"><span data-stu-id="8657f-118">Describes how to create a ledger-like effect in the control using alternating rows that are displayed differently.</span></span>  
  
 [<span data-ttu-id="8657f-119">Como: Usar o modelo da linha para personalizar linhas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-119">How to: Use the Row Template to Customize Rows in the Windows Forms DataGridView Control</span></span>](use-the-row-template-to-customize-rows-in-the-datagrid.md)  
 <span data-ttu-id="8657f-120">Descreve como usar a propriedade `RowTemplate` para definir as propriedades de linha que serão usadas para todas as linhas no controle.</span><span class="sxs-lookup"><span data-stu-id="8657f-120">Describes how to use the `RowTemplate` property to set row properties that will be used for all rows in the control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="8657f-121">Referência</span><span class="sxs-lookup"><span data-stu-id="8657f-121">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="8657f-122">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="8657f-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <span data-ttu-id="8657f-123">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewCellStyle> classe.</span><span class="sxs-lookup"><span data-stu-id="8657f-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCellStyle> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>  
 <span data-ttu-id="8657f-124">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.CellFormatting> eventos.</span><span class="sxs-lookup"><span data-stu-id="8657f-124">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.RowTemplate%2A>  
 <span data-ttu-id="8657f-125">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="8657f-125">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.RowTemplate%2A> property.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="8657f-126">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="8657f-126">Related Sections</span></span>  
 [<span data-ttu-id="8657f-127">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-127">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="8657f-128">Fornece tópicos que descrevem a pintura personalizada de células e linhas <xref:System.Windows.Forms.DataGridView>, bem como a criação de tipos de célula, coluna e linha derivados.</span><span class="sxs-lookup"><span data-stu-id="8657f-128">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="8657f-129">Funcionalidades de coluna, linha e célula básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8657f-129">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="8657f-130">Fornece tópicos que descrevem as propriedades da célula, linha e coluna mais usados.</span><span class="sxs-lookup"><span data-stu-id="8657f-130">Provides topics that describe commonly used cell, row, and column properties.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8657f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8657f-131">See also</span></span>

- [<span data-ttu-id="8657f-132">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="8657f-132">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
