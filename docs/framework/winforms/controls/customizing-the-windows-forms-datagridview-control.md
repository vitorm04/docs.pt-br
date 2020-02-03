---
title: Personalizar controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data grids [Windows Forms], customization
- DataGridView control [Windows Forms], customization
ms.assetid: 01ea5d4c-a736-4596-b0e9-a67a1b86e15f
ms.openlocfilehash: 348c78d091679418f2452326555d49229bd2a8ea
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744026"
---
# <a name="customizing-the-windows-forms-datagridview-control"></a><span data-ttu-id="e0daa-102">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-102">Customizing the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e0daa-103">O controle `DataGridView` fornece várias propriedades que podem ser usadas para ajustar a aparência e o comportamento básico (visual) das células, linhas e colunas.</span><span class="sxs-lookup"><span data-stu-id="e0daa-103">The `DataGridView` control provides several properties that you can use to adjust the appearance and basic behavior (look and feel) of its cells, rows, and columns.</span></span> <span data-ttu-id="e0daa-104">No entanto, se você tiver necessidades especiais que vão além dos recursos da classe <xref:System.Windows.Forms.DataGridViewCellStyle>, também poderá implementar o desenho do proprietário para o controle ou estender seus recursos Criando células, colunas e linhas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="e0daa-104">If you have special needs that go beyond the capabilities of the <xref:System.Windows.Forms.DataGridViewCellStyle> class, however, you can also implement owner drawing for the control or extend its capabilities by creating custom cells, columns, and rows.</span></span>  
  
 <span data-ttu-id="e0daa-105">Para pintar linhas e células por conta própria, você pode manipular vários eventos de pintura `DataGridView`.</span><span class="sxs-lookup"><span data-stu-id="e0daa-105">To paint cells and rows yourself, you can handle various `DataGridView` painting events.</span></span> <span data-ttu-id="e0daa-106">Para modificar a funcionalidade existente ou fornecer novas funcionalidades, crie seus próprios tipos derivados dos tipos `DataGridViewCell`, `DataGridViewColumn` e `DataGridViewRow` existentes.</span><span class="sxs-lookup"><span data-stu-id="e0daa-106">To modify existing functionality or provide new functionality, you can create your own types derived from the existing `DataGridViewCell`, `DataGridViewColumn`, and `DataGridViewRow` types.</span></span> <span data-ttu-id="e0daa-107">Você também pode fornecer novos recursos de edição criando tipos derivados que exibem um controle de sua escolha quando uma célula está em modo de edição.</span><span class="sxs-lookup"><span data-stu-id="e0daa-107">You can also provide new editing capabilities by creating derived types that display a control of your choosing when a cell is in edit mode.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0daa-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="e0daa-108">In This Section</span></span>  
 [<span data-ttu-id="e0daa-109">Como personalizar a aparência de células no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-109">How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-cells-in-the-datagrid.md)  
 <span data-ttu-id="e0daa-110">Descreve como manipular o evento <xref:System.Windows.Forms.DataGridView.CellPainting> para pintar células manualmente.</span><span class="sxs-lookup"><span data-stu-id="e0daa-110">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellPainting> event in order to paint cells manually.</span></span>  
  
 [<span data-ttu-id="e0daa-111">Como personalizar a aparência de linhas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-111">How to: Customize the Appearance of Rows in the Windows Forms DataGridView Control</span></span>](customize-the-appearance-of-rows-in-the-datagrid.md)  
 <span data-ttu-id="e0daa-112">Descreve como lidar com os eventos <xref:System.Windows.Forms.DataGridView.RowPrePaint> e <xref:System.Windows.Forms.DataGridView.RowPostPaint> para pintar linhas com um plano de fundo personalizado, gradiente e conteúdo que abrange várias colunas.</span><span class="sxs-lookup"><span data-stu-id="e0daa-112">Describes how to handle the <xref:System.Windows.Forms.DataGridView.RowPrePaint> and <xref:System.Windows.Forms.DataGridView.RowPostPaint> events in order to paint rows with a custom, gradient background and content that spans multiple columns.</span></span>  
  
 [<span data-ttu-id="e0daa-113">Como personalizar células e colunas no controle DataGridView dos Windows Forms estendendo o comportamento e a aparência</span><span class="sxs-lookup"><span data-stu-id="e0daa-113">How to: Customize Cells and Columns in the Windows Forms DataGridView Control by Extending Their Behavior and Appearance</span></span>](customize-cells-and-columns-in-the-datagrid-by-extending-behavior.md)  
 <span data-ttu-id="e0daa-114">Descreve como criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para realçar células ao posicionar o ponteiro do mouse sobre elas.</span><span class="sxs-lookup"><span data-stu-id="e0daa-114">Describes how to create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to highlight cells when the mouse pointer rests on them.</span></span>  
  
 [<span data-ttu-id="e0daa-115">Como desabilitar botões em uma coluna de botão no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-115">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>](disable-buttons-in-a-button-column-in-the-datagrid.md)  
 <span data-ttu-id="e0daa-116">Descreve como criar tipos personalizados derivados de <xref:System.Windows.Forms.DataGridViewButtonCell> e <xref:System.Windows.Forms.DataGridViewButtonColumn> para exibir botões desabilitados em uma coluna de botão.</span><span class="sxs-lookup"><span data-stu-id="e0daa-116">Describes how to create custom types derived from <xref:System.Windows.Forms.DataGridViewButtonCell> and <xref:System.Windows.Forms.DataGridViewButtonColumn> in order to display disabled buttons in a button column.</span></span>  
  
 [<span data-ttu-id="e0daa-117">Como hospedar controles em células DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-117">How to: Host Controls in Windows Forms DataGridView Cells</span></span>](how-to-host-controls-in-windows-forms-datagridview-cells.md)  
 <span data-ttu-id="e0daa-118">Descreve como implementar a interface `IDataGridViewEditingControl` e criar tipos personalizados derivados de `DataGridViewCell` e `DataGridViewColumn` para exibir um controle de <xref:System.Windows.Forms.DateTimePicker> quando uma célula estiver no modo de edição.</span><span class="sxs-lookup"><span data-stu-id="e0daa-118">Describes how to implement the `IDataGridViewEditingControl` interface and create custom types derived from `DataGridViewCell` and `DataGridViewColumn` in order to display a <xref:System.Windows.Forms.DateTimePicker> control when a cell is in edit mode.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e0daa-119">Referência</span><span class="sxs-lookup"><span data-stu-id="e0daa-119">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="e0daa-120">Fornece documentação de referência para o controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="e0daa-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewCell>  
 <span data-ttu-id="e0daa-121">Fornece documentação de referência para a classe <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="e0daa-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewCell> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewRow>  
 <span data-ttu-id="e0daa-122">Fornece documentação de referência para a classe <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="e0daa-122">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewRow> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <span data-ttu-id="e0daa-123">Fornece documentação de referência para a classe <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="e0daa-123">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn> class.</span></span>  
  
 <xref:System.Windows.Forms.IDataGridViewEditingControl>  
 <span data-ttu-id="e0daa-124">Fornece documentação de referência para a interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="e0daa-124">Provides reference documentation for the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e0daa-125">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="e0daa-125">Related Sections</span></span>  
 [<span data-ttu-id="e0daa-126">Formatação e definição de estilos básicas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="e0daa-127">Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.</span><span class="sxs-lookup"><span data-stu-id="e0daa-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0daa-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e0daa-128">See also</span></span>

- [<span data-ttu-id="e0daa-129">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="e0daa-129">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="e0daa-130">Tipos de coluna no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e0daa-130">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
