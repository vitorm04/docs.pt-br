---
title: Exibindo dados no controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: d02362895d75df3735d19554bd44bb8ac443c6c2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745872"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="11eec-102">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="11eec-103">O controle `DataGridView` é usado para exibir dados de uma variedade de fontes de dados externas.</span><span class="sxs-lookup"><span data-stu-id="11eec-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="11eec-104">Como alternativa, você pode adicionar linhas e colunas ao controle e populá-lo manualmente com os dados.</span><span class="sxs-lookup"><span data-stu-id="11eec-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="11eec-105">Ao associar o controle a uma fonte de dados, você pode gerar colunas automaticamente com base no esquema da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="11eec-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="11eec-106">Se essas colunas não aparecerem como você deseja, você poderá ocultar, remover ou reorganizá-las.</span><span class="sxs-lookup"><span data-stu-id="11eec-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="11eec-107">Também é possível adicionar colunas desassociadas para exibir dados complementares que não vêm da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="11eec-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="11eec-108">Além disso, você pode exibir seus dados usando os formatos padrão (como o formato de moeda) ou personalizar a formatação da exibição para apresentar os dados como desejar (como alterar a cor da tela de fundo para números negativos ou substituir os valores de cadeia de caracteres por imagens correspondentes).</span><span class="sxs-lookup"><span data-stu-id="11eec-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="11eec-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="11eec-109">In This Section</span></span>  
 [<span data-ttu-id="11eec-110">Modos de exibição de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-111">Descreve as opções para popular o controle com os dados.</span><span class="sxs-lookup"><span data-stu-id="11eec-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="11eec-112">Formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-113">Descreve as opções de formatação de valores de exibição de célula.</span><span class="sxs-lookup"><span data-stu-id="11eec-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="11eec-114">Instruções passo a passo: criando um controle DataGridView não associado do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-115">Descreve como popular manualmente o controle com os dados.</span><span class="sxs-lookup"><span data-stu-id="11eec-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="11eec-116">Como associar dados ao controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-117">Descreve como popular o controle com os dados associando-o a um `BindingSource` que contém informações extraídas de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="11eec-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="11eec-118">Como gerar automaticamente colunas em um controle DataGridView associado a dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="11eec-119">Descreve como gerar automaticamente colunas com base em uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="11eec-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="11eec-120">Como remover colunas geradas automaticamente de um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="11eec-121">Descreve como ocultar ou excluir colunas geradas automaticamente de uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="11eec-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="11eec-122">Como alterar a ordem das colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-123">Descreve como reorganizar colunas geradas automaticamente de uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="11eec-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="11eec-124">Como adicionar uma coluna não associada a um controle DataGridView associado a dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="11eec-125">Descreve como complementar dados de uma fonte de dados associada exibindo colunas não associadas adicionais.</span><span class="sxs-lookup"><span data-stu-id="11eec-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="11eec-126">Como associar objetos a controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="11eec-127">Descreve como associar o controle a uma coleção de objetos arbitrários para que cada objeto seja exibido em sua própria linha.</span><span class="sxs-lookup"><span data-stu-id="11eec-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="11eec-128">Como acessar objetos associados às linhas de DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="11eec-129">Descreve como recuperar um objeto associado a uma linha específica do controle.</span><span class="sxs-lookup"><span data-stu-id="11eec-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="11eec-130">Passo a passo: criando um formulário mestre e de detalhes usando dois controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="11eec-131">Descreve como exibir dados de duas tabelas de banco de dados relacionadas para que os valores mostrados em um controle `DataGridView` dependam da linha selecionada no momento em um outro controle.</span><span class="sxs-lookup"><span data-stu-id="11eec-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="11eec-132">Como personalizar a formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-133">Descreve como manipular o evento <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> para alterar a aparência de células dependendo de seus valores.</span><span class="sxs-lookup"><span data-stu-id="11eec-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="11eec-134">Referência</span><span class="sxs-lookup"><span data-stu-id="11eec-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="11eec-135">Fornece documentação de referência para o controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="11eec-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="11eec-136">Fornece documentação de referência para a propriedade <xref:System.Windows.Forms.DataGridView.DataSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="11eec-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="11eec-137">Fornece documentação de referência para o componente <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="11eec-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="11eec-138">Seções Relacionadas</span><span class="sxs-lookup"><span data-stu-id="11eec-138">Related Sections</span></span>  
 [<span data-ttu-id="11eec-139">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="11eec-140">Fornece tópicos que descrevem como alterar os maneira como os usuários adicionam e modificam dados no controle.</span><span class="sxs-lookup"><span data-stu-id="11eec-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11eec-141">Veja também</span><span class="sxs-lookup"><span data-stu-id="11eec-141">See also</span></span>

- [<span data-ttu-id="11eec-142">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="11eec-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="11eec-143">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="11eec-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
