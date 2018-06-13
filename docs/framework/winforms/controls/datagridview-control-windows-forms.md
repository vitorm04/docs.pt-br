---
title: Controle DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- tables [Windows Forms]
- data grids [Windows Forms
- data [Windows Forms], displaying in tabular format
- grid controls [Windows Forms]
- datasets [Windows Forms], user interface
- Windows Forms, displaying data
- data presentation
- tabular data [Windows Forms], displaying on Windows Forms
- datasets [Windows Forms], displaying in DataGridView control
- DataGridView control [Windows Forms]
ms.assetid: dbee73f2-bba6-4874-9389-cd21d44309be
ms.openlocfilehash: 3c642a2a0eccc5a2b08cee71ca719515b115b2f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529919"
---
# <a name="datagridview-control-windows-forms"></a><span data-ttu-id="67ace-102">Controle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="67ace-102">DataGridView Control (Windows Forms)</span></span>
<span data-ttu-id="67ace-103">O controle de `DataGridView` fornece uma maneira poderosa e flexível para exibir dados em um formato de tabela.</span><span class="sxs-lookup"><span data-stu-id="67ace-103">The `DataGridView` control provides a powerful and flexible way to display data in a tabular format.</span></span> <span data-ttu-id="67ace-104">Você pode usar o controle `DataGridView` para mostrar as exibições somente leitura de uma pequena quantidade de dados ou pode ajustar a escala para mostrar exibições editáveis de grandes conjuntos de dados.</span><span class="sxs-lookup"><span data-stu-id="67ace-104">You can use the `DataGridView` control to show read-only views of a small amount of data, or you can scale it to show editable views of very large sets of data.</span></span>  
  
 <span data-ttu-id="67ace-105">Você pode estender o controle `DataGridView` de várias maneiras para compilar comportamentos personalizados em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="67ace-105">You can extend the `DataGridView` control in a number of ways to build custom behaviors into your applications.</span></span> <span data-ttu-id="67ace-106">Por exemplo, você pode especificar seus próprios algoritmos de classificação com programação, podendo também criar seus próprios tipos de células.</span><span class="sxs-lookup"><span data-stu-id="67ace-106">For example, you can programmatically specify your own sorting algorithms, and you can create your own types of cells.</span></span> <span data-ttu-id="67ace-107">É possível personalizar facilmente a aparência do controle `DataGridView` escolhendo dentre várias propriedades.</span><span class="sxs-lookup"><span data-stu-id="67ace-107">You can easily customize the appearance of the `DataGridView` control by choosing among several properties.</span></span> <span data-ttu-id="67ace-108">Muitos tipos de armazenamentos de dados podem ser usados como uma fonte de dados ou o controle `DataGridView` pode operar sem nenhuma fonte de dados associada a ele.</span><span class="sxs-lookup"><span data-stu-id="67ace-108">Many types of data stores can be used as a data source, or the `DataGridView` control can operate with no data source bound to it.</span></span>  
  
 <span data-ttu-id="67ace-109">Os tópicos nesta seção descrevem os conceitos e técnicas que você pode usar para compilar recursos `DataGridView` em seus aplicativos.</span><span class="sxs-lookup"><span data-stu-id="67ace-109">The topics in this section describe the concepts and techniques that you can use to build `DataGridView` features into your applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="67ace-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="67ace-110">In This Section</span></span>  
 [<span data-ttu-id="67ace-111">Visão geral do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="67ace-111">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 <span data-ttu-id="67ace-112">Fornece tópicos que descrevem as arquitetura e os principais conceitos do controle `DataGridView` do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="67ace-112">Provides topics that describe the architecture and core concepts of the Windows Forms `DataGridView` control.</span></span>  
  
 [<span data-ttu-id="67ace-113">Funcionalidade padrão no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-113">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-114">Descreve a aparência padrão e o comportamento do controle `DataGridView` do Windows Forms quando ele é associado a uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="67ace-114">Describes the default appearance and behavior of the Windows Forms `DataGridView` control when it is bound to a data source.</span></span>  
  
 [<span data-ttu-id="67ace-115">Tipos de coluna no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-115">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-116">Descreve os tipos de coluna no controle `DataGridView` do Windows Forms usado para exibir dados e permitir que os usuários modifiquem ou adicionem dados.</span><span class="sxs-lookup"><span data-stu-id="67ace-116">Describes the column types in the Windows Forms `DataGridView` control used to display data and allow users to modify or add data.</span></span>  
  
 [<span data-ttu-id="67ace-117">Funcionalidades de coluna, linha e célula básicas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 <span data-ttu-id="67ace-118">Fornece tópicos que descrevem as propriedades da célula, linha e coluna mais usados.</span><span class="sxs-lookup"><span data-stu-id="67ace-118">Provides topics that describe commonly-used cell, row, and column properties.</span></span>  
  
 [<span data-ttu-id="67ace-119">Formatação e estilos básicos no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-119">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-120">Fornece tópicos que descrevem como modificar a aparência básica do controle e a formatação de exibição de dados da célula.</span><span class="sxs-lookup"><span data-stu-id="67ace-120">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="67ace-121">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-121">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-122">Fornece tópicos que descrevem como preencher o controle com os dados manualmente ou de uma fonte de dados externa.</span><span class="sxs-lookup"><span data-stu-id="67ace-122">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="67ace-123">Redimensionamento de colunas e linhas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-123">Resizing Columns and Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-124">Fornece tópicos que descrevem como o tamanho de linhas e colunas pode ser ajustado automaticamente para caber no conteúdo da célula ou para ajustar à largura do controle disponível.</span><span class="sxs-lookup"><span data-stu-id="67ace-124">Provides topics that describe how the size of rows and columns can be adjusted automatically to fit cell content or to fit the available width of the control.</span></span>  
  
 [<span data-ttu-id="67ace-125">Classificando dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-125">Sorting Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/sorting-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-126">Fornece tópicos que descrevem os recursos de classificação no controle.</span><span class="sxs-lookup"><span data-stu-id="67ace-126">Provides topics that describe the sorting features in the control.</span></span>  
  
 [<span data-ttu-id="67ace-127">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-127">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-128">Fornece tópicos que descrevem como alterar os maneira como os usuários adicionam e modificam dados no controle.</span><span class="sxs-lookup"><span data-stu-id="67ace-128">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
 [<span data-ttu-id="67ace-129">Seleção e uso da Área de Transferência com o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-129">Selection and Clipboard Use with the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-130">Fornece tópicos que descrevem os recursos de seleção de célula, linha e coluna no controle.</span><span class="sxs-lookup"><span data-stu-id="67ace-130">Provides topics that describe the cell, row, and column selection features in the control.</span></span>  
  
 [<span data-ttu-id="67ace-131">Programando com células, linhas e colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-131">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="67ace-132">Fornece tópicos que descrevem como programar com objetos de célula, linha e coluna.</span><span class="sxs-lookup"><span data-stu-id="67ace-132">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
 [<span data-ttu-id="67ace-133">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-133">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-134">Fornece tópicos que descrevem a pintura personalizada de células e linhas `DataGridView`, bem como a criação de tipos de célula, coluna e linha derivados.</span><span class="sxs-lookup"><span data-stu-id="67ace-134">Provides topics that describe custom painting `DataGridView` cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="67ace-135">Ajuste de desempenho no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-135">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-136">Fornece tópicos que descrevem como usar o controle com eficiência para evitar problemas de desempenho ao trabalhar com grandes volumes de dados.</span><span class="sxs-lookup"><span data-stu-id="67ace-136">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
 [<span data-ttu-id="67ace-137">Tratamento de teclado e mouse padrão no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-137">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="67ace-138">Descreve como os usuários podem interagir com o controle `DataGridView` por meio de um teclado e mouse.</span><span class="sxs-lookup"><span data-stu-id="67ace-138">Describes how users can interact with the `DataGridView` control through a keyboard and a mouse.</span></span>  
  
 [<span data-ttu-id="67ace-139">Diferenças entre os controles DataGridView e DataGrid dos Windows Forms </span><span class="sxs-lookup"><span data-stu-id="67ace-139">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)  
 <span data-ttu-id="67ace-140">Descreve como o `DataGridView` controle aprimora e substitui o <xref:System.Windows.Forms.DataGrid> controle.</span><span class="sxs-lookup"><span data-stu-id="67ace-140">Describes how the `DataGridView` control improves upon and replaces the <xref:System.Windows.Forms.DataGrid> control.</span></span>  
  
 <span data-ttu-id="67ace-141">Consulte também [Usando o designer com o controle DataGridView do Windows Forms](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="67ace-141">Also see [Using the Designer with the Windows Forms DataGridView Control](http://msdn.microsoft.com/library/ms171593\(v=vs.110\)).</span></span>  
  
## <a name="reference"></a><span data-ttu-id="67ace-142">Referência</span><span class="sxs-lookup"><span data-stu-id="67ace-142">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="67ace-143">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="67ace-143">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="67ace-144">Fornece documentação de referência para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="67ace-144">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="67ace-145">O <xref:System.Windows.Forms.DataGridView> controle e o <xref:System.Windows.Forms.BindingSource> componente são projetados para trabalhar juntos.</span><span class="sxs-lookup"><span data-stu-id="67ace-145">The <xref:System.Windows.Forms.DataGridView> control and the <xref:System.Windows.Forms.BindingSource> component are designed to work closely together.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="67ace-146">Consulte também</span><span class="sxs-lookup"><span data-stu-id="67ace-146">See Also</span></span>  
 [<span data-ttu-id="67ace-147">Controles a serem usados nos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="67ace-147">Controls to Use on Windows Forms</span></span>](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)
