---
title: Personalizando o controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 92bbace4d0869aca67025f1e4ac8c451fe073219
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="4e29a-102">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="4e29a-103">O controle `DataGridView` fornece várias propriedades que podem ser usadas para ajustar a aparência e o comportamento básico (visual) das células, linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="4e29a-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="4e29a-104">Se você tiver necessidades especiais que vão além dos recursos da <xref:System.Windows.Forms.DataGridViewCellStyle> da classe, no entanto, você também pode implementar o controle de desenho do proprietário ou estender seus recursos, criando personalizadas células, colunas e linhas.</span><span class="sxs-lookup"><span data-stu-id="4e29a-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="4e29a-105">Para pintar linhas e células por conta própria, você pode manipular vários eventos de pintura `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="4e29a-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="4e29a-106">Para modificar a funcionalidade existente ou fornecer novas funcionalidades, crie seus próprios tipos derivados dos tipos `DataGridViewCell`, `DataGridViewColumn` e `DataGridViewRow` existentes.</span><span class="sxs-lookup"><span data-stu-id="4e29a-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="4e29a-107">Você também pode fornecer novos recursos de edição criando tipos derivados que exibem um controle de sua escolha quando uma célula está em modo de edição.</span><span class="sxs-lookup"><span data-stu-id="4e29a-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e29a-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="4e29a-108">In This Section</span></span>  
 [<span data-ttu-id="4e29a-109">Como personalizar a aparência de células no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="4e29a-110">Descreve como tratar o <xref:System.Windows.Forms.DataGridView.CellPainting> evento para pintar células manualmente.</span><span class="sxs-lookup"><span data-stu-id="4e29a-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="4e29a-111">Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="4e29a-112">Descreve como tratar o <xref:System.Windows.Forms.DataGridView.RowPrePaint> e <xref:System.Windows.Forms.DataGridView.RowPostPaint> eventos para desenhar linhas com um plano de fundo personalizado, gradiente e conteúdo que se estende por várias colunas.</span><span class="sxs-lookup"><span data-stu-id="4e29a-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="4e29a-113">Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência</span><span class="sxs-lookup"><span data-stu-id="4e29a-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](../../../../docs/framework/winforms/controls/customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="4e29a-114">Descreve como criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para realçar células ao posicionar o ponteiro do mouse sobre elas.</span><span class="sxs-lookup"><span data-stu-id="4e29a-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="4e29a-115">Como desabilitar botões em uma coluna de botão no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="4e29a-116">Descreve como criar tipos personalizados derivados de <xref:System.Windows.Forms.DataGridViewButtonCell> e <xref:System.Windows.Forms.DataGridViewButtonColumn> para exibir botões desabilitados em uma coluna de botão.</span><span class="sxs-lookup"><span data-stu-id="4e29a-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="4e29a-117">Como hospedar controles em células DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="4e29a-118">Descreve como implementar o `IDataGridViewEditingControl` de interface e criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para exibir um <xref:System.Windows.Forms.DateTimePicker> controlar quando uma célula está em modo de edição.</span><span class="sxs-lookup"><span data-stu-id="4e29a-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4e29a-119">Referência</span><span class="sxs-lookup"><span data-stu-id="4e29a-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="4e29a-120">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="4e29a-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="4e29a-121">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewCell> classe.</span><span class="sxs-lookup"><span data-stu-id="4e29a-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="4e29a-122">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewRow> classe.</span><span class="sxs-lookup"><span data-stu-id="4e29a-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="4e29a-123">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridViewColumn> classe.</span><span class="sxs-lookup"><span data-stu-id="4e29a-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="4e29a-124">Fornece documentação de referência para o <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span><span class="sxs-lookup"><span data-stu-id="4e29a-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="4e29a-125">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="4e29a-125">Related Sections</span></span>  
 [<span data-ttu-id="4e29a-126">Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="4e29a-127">Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.</span><span class="sxs-lookup"><span data-stu-id="4e29a-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e29a-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4e29a-128">See Also</span></span>  
 [<span data-ttu-id="4e29a-129">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="4e29a-129">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="4e29a-130">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4e29a-130">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
