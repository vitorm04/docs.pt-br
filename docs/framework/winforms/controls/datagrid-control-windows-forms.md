---
title: Controle DataGrid (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: 5f8fcd21802c52d61d354c5ba85d665bd17237db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59078909"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="7a61e-102">Controle DataGrid (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7a61e-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="7a61e-103">O controle <xref:System.Windows.Forms.DataGridView> substitui e adiciona funcionalidade ao controle `DataGrid`, no entanto, o controle `DataGrid` é mantido para compatibilidade com versões anteriores e para uso futuro, se desejado.</span><span class="sxs-lookup"><span data-stu-id="7a61e-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="7a61e-104">Para obter mais informações, consulte [Diferenças Entre o Windows Forms DataGridView e os Controles do DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7a61e-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="7a61e-105">O controle `DataGrid` do Windows Forms fornece uma interface do usuário para conjuntos de dados [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)], exibindo dados tabulares e habilitando atualizações para a fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="7a61e-105">The Windows Forms `DataGrid` control provides a user interface to [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="7a61e-106">Quando o controle `DataGrid` estiver definido como uma fonte de dados válido, o controle é preenchido automaticamente, criando colunas e linhas com base na forma dos dados.</span><span class="sxs-lookup"><span data-stu-id="7a61e-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="7a61e-107">O controle `DataGrid` pode ser usado para exibir uma única tabela ou as relações hierárquicas entre um conjunto de tabelas.</span><span class="sxs-lookup"><span data-stu-id="7a61e-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="7a61e-108">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="7a61e-108">In This Section</span></span>  
 [<span data-ttu-id="7a61e-109">Visão geral do controle DataGrid</span><span class="sxs-lookup"><span data-stu-id="7a61e-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="7a61e-110">Descreve os recursos básicos do console `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-111">Como: Adicionar tabelas e colunas do controle DataGrid do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="7a61e-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="7a61e-112">Descreve como adicionar tabelas e colunas ao controle `DataGrid` usando o designer.</span><span class="sxs-lookup"><span data-stu-id="7a61e-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="7a61e-113">Como: Adicionar tabelas e colunas ao controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="7a61e-114">Descreve como adicionar tabelas e colunas ao controle `DataGrid` com programação.</span><span class="sxs-lookup"><span data-stu-id="7a61e-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="7a61e-115">Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados usando o Designer</span><span class="sxs-lookup"><span data-stu-id="7a61e-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="7a61e-116">Descreve como associar um conjunto de dados [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ao controle `DataGrid` usando o designer.</span><span class="sxs-lookup"><span data-stu-id="7a61e-116">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="7a61e-117">Como: Associar o controle DataGrid do Windows Forms a uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="7a61e-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="7a61e-118">Descreve como associar um conjunto de dados [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] ao controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-118">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-119">Como: Alterar os dados exibidos em tempo de execução no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="7a61e-120">Descreve como alterar dados com programação no controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-121">Como: Criar listas mestre e de detalhes com o controle DataGrid do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="7a61e-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="7a61e-122">Descreve como exibir duas tabelas reunidas com uma relação pai/filho em dois controles `DataGrid` separados usando o designer.</span><span class="sxs-lookup"><span data-stu-id="7a61e-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="7a61e-123">Como: Criar listas mestre / detalhes com o controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="7a61e-124">Descreve como exibir duas tabelas reunidas com uma relação pai/filho em dois controles `DataGrid` separados.</span><span class="sxs-lookup"><span data-stu-id="7a61e-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="7a61e-125">Como: Excluir ou ocultar colunas no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="7a61e-126">Descreve como remover colunas no controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-127">Como: Formatar o controle DataGrid do Windows Forms usando o Designer</span><span class="sxs-lookup"><span data-stu-id="7a61e-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="7a61e-128">Descreve como alterar as propriedades relacionadas à aparência do controle `DataGrid` usando o designer.</span><span class="sxs-lookup"><span data-stu-id="7a61e-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="7a61e-129">Como: Formatar o controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="7a61e-130">Descreve como alterar as propriedades relacionadas à aparência do controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-131">Atalhos de teclado para o controle DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="7a61e-132">Lista atalhos para navegarem por meio do controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-133">Como: Responder a cliques no controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="7a61e-134">Descreve como determinar em qual célula um usuário clicou no controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="7a61e-135">Como: Validar a entrada com o controle DataGrid do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="7a61e-136">Descreve como validar a entrada no conjunto de dados associado ao controle `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="7a61e-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="7a61e-137">Referência</span><span class="sxs-lookup"><span data-stu-id="7a61e-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="7a61e-138">Fornece uma visão geral de <xref:System.Windows.Forms.DataGrid> classe.</span><span class="sxs-lookup"><span data-stu-id="7a61e-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="7a61e-139">Fornece detalhes sobre como usar essa propriedade para associar o <xref:System.Windows.Forms.DataGrid> controle aos dados.</span><span class="sxs-lookup"><span data-stu-id="7a61e-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7a61e-140">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="7a61e-140">Related Sections</span></span>  
 [<span data-ttu-id="7a61e-141">Associação de dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="7a61e-142">Fornece links para tópicos sobre a associação de dados no Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7a61e-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a61e-143">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a61e-143">See also</span></span>

- [<span data-ttu-id="7a61e-144">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="7a61e-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="7a61e-145">Diferenças entre os controles DataGridView e DataGrid dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7a61e-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
