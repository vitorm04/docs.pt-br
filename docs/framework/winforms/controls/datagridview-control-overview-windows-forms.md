---
title: "Visão geral do controle DataGridView (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- DataGridView
helpviewer_keywords:
- DataGridView control [Windows Forms], about DataGridView control
- grid controls [Windows Forms]
- tables [Windows Forms], displaying in DataGridView control
- tables [Windows Forms], binding to DataGridView control
- columns [Windows Forms], DataGridView control
- bound controls [Windows Forms], dataGridView control
- datasets [Windows Forms], binding to DataGridView control
- data grids [Windows Forms], about data grids
- data [Windows Forms], resorting
- data [Windows Forms], navigating
- grids [Windows Forms]
- data binding [Windows Forms], DataGridView control
- data sources [Windows Forms], binding to DataGridView control
- DataGridView control [Windows Forms], data binding
ms.assetid: 0a45c661-89dc-4390-9cc6-c47eee501488
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6d9cc6568813af866acaf20696b870bedc3099be
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="datagridview-control-overview-windows-forms"></a><span data-ttu-id="ef6e4-102">Visão geral do controle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="ef6e4-102">DataGridView Control Overview (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="ef6e4-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle <xref:System.Windows.Forms.DataGrid>, no entanto, o controle <xref:System.Windows.Forms.DataGrid> é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the <xref:System.Windows.Forms.DataGrid> control; however, the <xref:System.Windows.Forms.DataGrid> control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="ef6e4-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ef6e4-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="ef6e4-105">Com o <xref:System.Windows.Forms.DataGridView> controle, você pode exibir e editar dados tabulares de muitos tipos diferentes de fontes de dados.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-105">With the <xref:System.Windows.Forms.DataGridView> control, you can display and edit tabular data from many different kinds of data sources.</span></span>  
  
 <span data-ttu-id="ef6e4-106">Associação de dados para o <xref:System.Windows.Forms.DataGridView> controle é simples e intuitiva e, em muitos casos, ele é tão simple quanto a configuração do <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-106">Binding data to the <xref:System.Windows.Forms.DataGridView> control is straightforward and intuitive, and in many cases it is as simple as setting the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span> <span data-ttu-id="ef6e4-107">Quando você associa a uma fonte de dados que contém várias listas ou tabelas, defina o <xref:System.Windows.Forms.DataGridView.DataMember%2A> uma cadeia de caracteres que especifica a lista ou tabela para associar à propriedade.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-107">When you bind to a data source that contains multiple lists or tables, set the <xref:System.Windows.Forms.DataGridView.DataMember%2A> property to a string that specifies the list or table to bind to.</span></span>  
  
 <span data-ttu-id="ef6e4-108">O <xref:System.Windows.Forms.DataGridView> controle oferece suporte para o modelo de associação de dados formulários do Windows padrão, portanto ele associará a instâncias das classes descritas na lista a seguir:</span><span class="sxs-lookup"><span data-stu-id="ef6e4-108">The <xref:System.Windows.Forms.DataGridView> control supports the standard Windows Forms data binding model, so it will bind to instances of classes described in the following list:</span></span>  
  
-   <span data-ttu-id="ef6e4-109">Qualquer classe que implementa o <xref:System.Collections.IList> interface, inclusive matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-109">Any class that implements the <xref:System.Collections.IList> interface, including one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="ef6e4-110">Qualquer classe que implementa o <xref:System.ComponentModel.IListSource> interface, como o <xref:System.Data.DataTable> e <xref:System.Data.DataSet> classes.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-110">Any class that implements the <xref:System.ComponentModel.IListSource> interface, such as the <xref:System.Data.DataTable> and <xref:System.Data.DataSet> classes.</span></span>  
  
-   <span data-ttu-id="ef6e4-111">Qualquer classe que implementa o <xref:System.ComponentModel.IBindingList> interface, como o <xref:System.ComponentModel.BindingList%601> classe.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-111">Any class that implements the <xref:System.ComponentModel.IBindingList> interface, such as the <xref:System.ComponentModel.BindingList%601> class.</span></span>  
  
-   <span data-ttu-id="ef6e4-112">Qualquer classe que implementa o <xref:System.ComponentModel.IBindingListView> interface, como o <xref:System.Windows.Forms.BindingSource> classe.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-112">Any class that implements the <xref:System.ComponentModel.IBindingListView> interface, such as the <xref:System.Windows.Forms.BindingSource> class.</span></span>  
  
 <span data-ttu-id="ef6e4-113">O <xref:System.Windows.Forms.DataGridView> controle oferece suporte à associação de dados para as propriedades públicas de objetos retornados por essas interfaces ou à coleção de propriedades retornado por um <xref:System.ComponentModel.ICustomTypeDescriptor> interface, se implementado em objetos retornados.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-113">The <xref:System.Windows.Forms.DataGridView> control supports data binding to the public properties of the objects returned by these interfaces or to the properties collection returned by an <xref:System.ComponentModel.ICustomTypeDescriptor> interface, if implemented on the returned objects.</span></span>  
  
 <span data-ttu-id="ef6e4-114">Normalmente, você associará a uma <xref:System.Windows.Forms.BindingSource> componente e vincular o <xref:System.Windows.Forms.BindingSource> componente para outra fonte de dados ou preenchê-la com objetos de negócios.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-114">Typically, you will bind to a <xref:System.Windows.Forms.BindingSource> component and bind the <xref:System.Windows.Forms.BindingSource> component to another data source or populate it with business objects.</span></span> <span data-ttu-id="ef6e4-115">O <xref:System.Windows.Forms.BindingSource> componente é a fonte de dados preferencial porque ele pode ser associado a uma ampla variedade de fontes de dados e pode resolver vários problemas de associação de dados automaticamente.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-115">The <xref:System.Windows.Forms.BindingSource> component is the preferred data source because it can bind to a wide variety of data sources and can resolve many data binding issues automatically.</span></span> <span data-ttu-id="ef6e4-116">Para obter mais informações, consulte [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span><span class="sxs-lookup"><span data-stu-id="ef6e4-116">For more information, see [BindingSource Component](../../../../docs/framework/winforms/controls/bindingsource-component.md).</span></span>  
  
 <span data-ttu-id="ef6e4-117">O <xref:System.Windows.Forms.DataGridView> controle também pode ser usado em *desassociado* modo, com nenhum armazenamento de dados subjacente.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-117">The <xref:System.Windows.Forms.DataGridView> control can also be used in *unbound* mode, with no underlying data store.</span></span> <span data-ttu-id="ef6e4-118">Para obter um exemplo de código que usa um desassociado <xref:System.Windows.Forms.DataGridView> , consulte [passo a passo: Criando um controle DataGridView do Windows Forms não associados](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="ef6e4-118">For a code example that uses an unbound <xref:System.Windows.Forms.DataGridView> control, see [Walkthrough: Creating an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
 <span data-ttu-id="ef6e4-119">O <xref:System.Windows.Forms.DataGridView> controle é altamente configurável e extensível, e fornece muitas propriedades, métodos e eventos para personalizar sua aparência e comportamento.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-119">The <xref:System.Windows.Forms.DataGridView> control is highly configurable and extensible, and it provides many properties, methods, and events to customize its appearance and behavior.</span></span> <span data-ttu-id="ef6e4-120">Quando você quiser que seu aplicativo do Windows Forms para exibir dados de tabela, considere o uso de <xref:System.Windows.Forms.DataGridView> controle antes de outros (por exemplo, <xref:System.Windows.Forms.DataGrid>).</span><span class="sxs-lookup"><span data-stu-id="ef6e4-120">When you want your Windows Forms application to display tabular data, consider using the <xref:System.Windows.Forms.DataGridView> control before others (for example, <xref:System.Windows.Forms.DataGrid>).</span></span> <span data-ttu-id="ef6e4-121">Se você estiver exibindo uma pequena grade valores somente leitura, ou se você estiver habilitando um usuário editar uma tabela com milhões de registros, o <xref:System.Windows.Forms.DataGridView> controle fornece uma solução eficiente de memória prontamente programável.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-121">If you are displaying a small grid of read-only values, or if you are enabling a user to edit a table with millions of records, the <xref:System.Windows.Forms.DataGridView> control will provide you with a readily programmable, memory-efficient solution.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ef6e4-122">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="ef6e4-122">In This Section</span></span>  
 [<span data-ttu-id="ef6e4-123">Resumo de tecnologia do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef6e4-123">DataGridView Control Technology Summary</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-technology-summary-windows-forms.md)  
 <span data-ttu-id="ef6e4-124">Resume <xref:System.Windows.Forms.DataGridView> controlar o uso de classes relacionadas e conceitos.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-124">Summarizes <xref:System.Windows.Forms.DataGridView> control concepts and the use of related classes.</span></span>  
  
 [<span data-ttu-id="ef6e4-125">Arquitetura de controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef6e4-125">DataGridView Control Architecture</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-architecture-windows-forms.md)  
 <span data-ttu-id="ef6e4-126">Descreve a arquitetura do <xref:System.Windows.Forms.DataGridView> controle, explicando sua estrutura de hierarquia e herança de tipo.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-126">Describes the architecture of the <xref:System.Windows.Forms.DataGridView> control, explaining its type hierarchy and inheritance structure.</span></span>  
  
 [<span data-ttu-id="ef6e4-127">Cenários do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef6e4-127">DataGridView Control Scenarios</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-scenarios-windows-forms.md)  
 <span data-ttu-id="ef6e4-128">Descreve os cenários mais comuns no qual <xref:System.Windows.Forms.DataGridView> controles são usados.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-128">Describes the most common scenarios in which <xref:System.Windows.Forms.DataGridView> controls are used.</span></span>  
  
 [<span data-ttu-id="ef6e4-129">Diretório de código do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef6e4-129">DataGridView Control Code Directory</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-code-directory-windows-forms.md)  
 <span data-ttu-id="ef6e4-130">Fornece links para exemplos de código na documentação para vários <xref:System.Windows.Forms.DataGridView> tarefas.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-130">Provides links to code examples in the documentation for various <xref:System.Windows.Forms.DataGridView> tasks.</span></span> <span data-ttu-id="ef6e4-131">Esses exemplos são categorizados por tipo de tarefa.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-131">These examples are categorized by task type.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ef6e4-132">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="ef6e4-132">Related Sections</span></span>  
 [<span data-ttu-id="ef6e4-133">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef6e4-133">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ef6e4-134">Descreve os tipos de coluna em Windows Forms <xref:System.Windows.Forms.DataGridView> usado para exibir informações e permitir que os usuários modificar ou adicionar informações de controle.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-134">Discusses the column types in the Windows Forms <xref:System.Windows.Forms.DataGridView> control used to display information and allow users to modify or add information.</span></span>  
  
 [<span data-ttu-id="ef6e4-135">Exibindo dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef6e4-135">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ef6e4-136">Fornece tópicos que descrevem como preencher o controle com os dados manualmente ou de uma fonte de dados externa.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-136">Provides topics that describe how to populate the control with data either manually, or from an external data source.</span></span>  
  
 [<span data-ttu-id="ef6e4-137">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef6e4-137">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ef6e4-138">Fornece tópicos que descrevem a pintura personalizada de células e linhas <xref:System.Windows.Forms.DataGridView>, bem como a criação de tipos de célula, coluna e linha derivados.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-138">Provides topics that describe custom painting <xref:System.Windows.Forms.DataGridView> cells and rows, and creating derived cell, column, and row types.</span></span>  
  
 [<span data-ttu-id="ef6e4-139">Ajuste de desempenho no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef6e4-139">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="ef6e4-140">Apresenta tópicos que descrevem como usar o controle com eficiência para evitar problemas de desempenho ao trabalhar com grandes volumes de dados.</span><span class="sxs-lookup"><span data-stu-id="ef6e4-140">Provides topics that describe how to use the control efficiently to avoid performance problems when working with large amounts of data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef6e4-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ef6e4-141">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="ef6e4-142">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="ef6e4-142">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="ef6e4-143">Funcionalidade padrão no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef6e4-143">Default Functionality in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-functionality-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="ef6e4-144">Tratamento de teclado e mouse padrão no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ef6e4-144">Default Keyboard and Mouse Handling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/default-keyboard-and-mouse-handling-in-the-windows-forms-datagridview-control.md)
