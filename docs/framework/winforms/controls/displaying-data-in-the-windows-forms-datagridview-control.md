---
title: Exibindo dados no controle DataGridView dos Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: c153d422470ff20491567aed70557e461dc2b4e6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168630"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="5165e-102">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-102">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5165e-103">O controle `DataGridView` é usado para exibir dados de uma variedade de fontes de dados externas.</span><span class="sxs-lookup"><span data-stu-id="5165e-103">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="5165e-104">Como alternativa, você pode adicionar linhas e colunas ao controle e populá-lo manualmente com os dados.</span><span class="sxs-lookup"><span data-stu-id="5165e-104">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="5165e-105">Ao associar o controle a uma fonte de dados, você pode gerar colunas automaticamente com base no esquema da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5165e-105">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="5165e-106">Se essas colunas não aparecerem como você deseja, você poderá ocultar, remover ou reorganizá-las.</span><span class="sxs-lookup"><span data-stu-id="5165e-106">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="5165e-107">Também é possível adicionar colunas desassociadas para exibir dados complementares que não vêm da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5165e-107">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="5165e-108">Além disso, você pode exibir seus dados usando os formatos padrão (como o formato de moeda) ou personalizar a formatação da exibição para apresentar os dados como desejar (como alterar a cor da tela de fundo para números negativos ou substituir os valores de cadeia de caracteres por imagens correspondentes).</span><span class="sxs-lookup"><span data-stu-id="5165e-108">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5165e-109">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="5165e-109">In This Section</span></span>  
 [<span data-ttu-id="5165e-110">Modos de exibição dos dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-110">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-111">Descreve as opções para popular o controle com os dados.</span><span class="sxs-lookup"><span data-stu-id="5165e-111">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="5165e-112">Formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-112">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-113">Descreve as opções de formatação de valores de exibição de célula.</span><span class="sxs-lookup"><span data-stu-id="5165e-113">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="5165e-114">Passo a passo: Criar um controle não associado DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-114">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-115">Descreve como popular manualmente o controle com os dados.</span><span class="sxs-lookup"><span data-stu-id="5165e-115">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="5165e-116">Como: Associar dados ao controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-116">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-117">Descreve como popular o controle com os dados associando-o a um `BindingSource` que contém informações extraídas de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5165e-117">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="5165e-118">Como: Gerar automaticamente colunas em um controle DataGridView associado a dados do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-118">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="5165e-119">Descreve como gerar automaticamente colunas com base em uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="5165e-119">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="5165e-120">Como: Remover colunas geradas automaticamente de um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-120">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="5165e-121">Descreve como ocultar ou excluir colunas geradas automaticamente de uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="5165e-121">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="5165e-122">Como: Alterar a ordem de colunas no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-122">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-123">Descreve como reorganizar colunas geradas automaticamente de uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="5165e-123">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="5165e-124">Como: Adicionar uma coluna não associada a um controle DataGridView do Windows Forms associado a dados</span><span class="sxs-lookup"><span data-stu-id="5165e-124">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="5165e-125">Descreve como complementar dados de uma fonte de dados associada exibindo colunas não associadas adicionais.</span><span class="sxs-lookup"><span data-stu-id="5165e-125">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="5165e-126">Como: Associar objetos a controles DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-126">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="5165e-127">Descreve como associar o controle a uma coleção de objetos arbitrários para que cada objeto seja exibido em sua própria linha.</span><span class="sxs-lookup"><span data-stu-id="5165e-127">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="5165e-128">Como: Acessar objetos associados às linhas de DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-128">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="5165e-129">Descreve como recuperar um objeto associado a uma linha específica do controle.</span><span class="sxs-lookup"><span data-stu-id="5165e-129">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="5165e-130">Passo a passo: Criar um formulário mestre/de detalhes usando dois controles DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-130">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="5165e-131">Descreve como exibir dados de duas tabelas de banco de dados relacionadas para que os valores mostrados em um controle `DataGridView` dependam da linha selecionada no momento em um outro controle.</span><span class="sxs-lookup"><span data-stu-id="5165e-131">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="5165e-132">Como: Personalizar a formatação de dados no controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-132">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-133">Descreve como manipular o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> evento para alterar a aparência de células dependendo dos seus valores.</span><span class="sxs-lookup"><span data-stu-id="5165e-133">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5165e-134">Referência</span><span class="sxs-lookup"><span data-stu-id="5165e-134">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="5165e-135">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="5165e-135">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="5165e-136">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="5165e-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="5165e-137">Fornece documentação de referência para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="5165e-137">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5165e-138">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="5165e-138">Related Sections</span></span>  
 [<span data-ttu-id="5165e-139">Entrada de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-139">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="5165e-140">Fornece tópicos que descrevem como alterar os maneira como os usuários adicionam e modificam dados no controle.</span><span class="sxs-lookup"><span data-stu-id="5165e-140">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5165e-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5165e-141">See also</span></span>

- [<span data-ttu-id="5165e-142">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="5165e-142">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="5165e-143">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="5165e-143">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
