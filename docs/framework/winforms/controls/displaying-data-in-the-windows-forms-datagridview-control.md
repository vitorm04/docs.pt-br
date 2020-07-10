---
title: Exibindo dados no controle DataGridView
description: Saiba como usar o controle Windows Forms DataGridView para exibir dados de uma variedade de fontes de dados externas.
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], displaying in tabular format
- data grids [Windows Forms], displaying data
- displaying data [Windows Forms], data grids
- DataGridView control [Windows Forms], displaying data
ms.assetid: b170b52a-2ebd-4948-ac2f-e52d494cebb2
ms.openlocfilehash: a0f3e6627290521b8c10477c31459f1486e79162
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174569"
---
# <a name="displaying-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d48b6-103">Exibindo dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-103">Displaying Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d48b6-104">O controle `DataGridView` é usado para exibir dados de uma variedade de fontes de dados externas.</span><span class="sxs-lookup"><span data-stu-id="d48b6-104">The `DataGridView` control is used to display data from a variety of external data sources.</span></span> <span data-ttu-id="d48b6-105">Como alternativa, você pode adicionar linhas e colunas ao controle e populá-lo manualmente com os dados.</span><span class="sxs-lookup"><span data-stu-id="d48b6-105">Alternatively, you can add rows and columns to the control and manually populate it with data.</span></span>  
  
 <span data-ttu-id="d48b6-106">Ao associar o controle a uma fonte de dados, você pode gerar colunas automaticamente com base no esquema da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d48b6-106">When you bind the control to a data source, you can generate columns automatically based on the schema of the data source.</span></span> <span data-ttu-id="d48b6-107">Se essas colunas não aparecerem como você deseja, você poderá ocultar, remover ou reorganizá-las.</span><span class="sxs-lookup"><span data-stu-id="d48b6-107">If these columns do not appear just as you want them to, you can hide, remove, or rearrange them.</span></span> <span data-ttu-id="d48b6-108">Também é possível adicionar colunas desassociadas para exibir dados complementares que não vêm da fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="d48b6-108">You can also add unbound columns to display supplemental data that does not come from the data source.</span></span>  
  
 <span data-ttu-id="d48b6-109">Além disso, você pode exibir seus dados usando os formatos padrão (como o formato de moeda) ou personalizar a formatação da exibição para apresentar os dados como desejar (como alterar a cor da tela de fundo para números negativos ou substituir os valores de cadeia de caracteres por imagens correspondentes).</span><span class="sxs-lookup"><span data-stu-id="d48b6-109">Additionally, you can display your data using standard formats (such as currency format), or you can customize the display formatting to present your data however you need to (such as changing the background color for negative numbers, or replacing string values with corresponding images).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d48b6-110">Nesta seção</span><span class="sxs-lookup"><span data-stu-id="d48b6-110">In This Section</span></span>  
 [<span data-ttu-id="d48b6-111">Modos de exibição de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-111">Data Display Modes in the Windows Forms DataGridView Control</span></span>](data-display-modes-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-112">Descreve as opções para popular o controle com os dados.</span><span class="sxs-lookup"><span data-stu-id="d48b6-112">Describes the options for populating the control with data.</span></span>  
  
 [<span data-ttu-id="d48b6-113">Formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-113">Data Formatting in the Windows Forms DataGridView Control</span></span>](data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-114">Descreve as opções de formatação de valores de exibição de célula.</span><span class="sxs-lookup"><span data-stu-id="d48b6-114">Describes the options for formatting cell display values.</span></span>  
  
 [<span data-ttu-id="d48b6-115">Instruções passo a passo: criando um controle DataGridView não associado do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-115">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-116">Descreve como popular manualmente o controle com os dados.</span><span class="sxs-lookup"><span data-stu-id="d48b6-116">Describes how to manually populate the control with data.</span></span>  
  
 [<span data-ttu-id="d48b6-117">Como associar dados ao controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-117">How to: Bind Data to the Windows Forms DataGridView Control</span></span>](how-to-bind-data-to-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-118">Descreve como popular o controle com os dados associando-o a um `BindingSource` que contém informações extraídas de um banco de dados.</span><span class="sxs-lookup"><span data-stu-id="d48b6-118">Describes how to populate the control with data by binding it to a `BindingSource` that contains information pulled from a database.</span></span>  
  
 [<span data-ttu-id="d48b6-119">Como gerar automaticamente colunas em um controle DataGridView associado a dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-119">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>](autogenerate-columns-in-a-data-bound-wf-datagridview-control.md)  
 <span data-ttu-id="d48b6-120">Descreve como gerar automaticamente colunas com base em uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="d48b6-120">Describes how to automatically generate columns based on a bound data source.</span></span>  
  
 [<span data-ttu-id="d48b6-121">Como remover colunas geradas automaticamente de um controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-121">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 <span data-ttu-id="d48b6-122">Descreve como ocultar ou excluir colunas geradas automaticamente de uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="d48b6-122">Describes how to hide or delete columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="d48b6-123">Como alterar a ordem das colunas no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-123">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-124">Descreve como reorganizar colunas geradas automaticamente de uma fonte de dados associada.</span><span class="sxs-lookup"><span data-stu-id="d48b6-124">Describes how to rearrange columns generated automatically from a bound data source.</span></span>  
  
 [<span data-ttu-id="d48b6-125">Como adicionar uma coluna não associada a um controle DataGridView associado a dados dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-125">How to: Add an Unbound Column to a Data-Bound Windows Forms DataGridView Control</span></span>](unbound-column-to-a-data-bound-datagridview.md)  
 <span data-ttu-id="d48b6-126">Descreve como complementar dados de uma fonte de dados associada exibindo colunas não associadas adicionais.</span><span class="sxs-lookup"><span data-stu-id="d48b6-126">Describes how to supplement data from a bound data source by displaying additional, unbound columns.</span></span>  
  
 [<span data-ttu-id="d48b6-127">Como associar objetos a controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-127">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>](how-to-bind-objects-to-windows-forms-datagridview-controls.md)  
 <span data-ttu-id="d48b6-128">Descreve como associar o controle a uma coleção de objetos arbitrários para que cada objeto seja exibido em sua própria linha.</span><span class="sxs-lookup"><span data-stu-id="d48b6-128">Describes how to bind the control to a collection of arbitrary objects so that each object is displayed in its own row.</span></span>  
  
 [<span data-ttu-id="d48b6-129">Como acessar objetos associados às linhas de DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-129">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)  
 <span data-ttu-id="d48b6-130">Descreve como recuperar um objeto associado a uma linha específica do controle.</span><span class="sxs-lookup"><span data-stu-id="d48b6-130">Describes how to retrieve an object bound to a particular row of the control.</span></span>  
  
 [<span data-ttu-id="d48b6-131">Passo a passo: criando um formulário mestre e de detalhes usando dois controles DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-131">Walkthrough: Creating a Master/Detail Form Using Two Windows Forms DataGridView Controls</span></span>](creating-a-master-detail-form-using-two-datagridviews.md)  
 <span data-ttu-id="d48b6-132">Descreve como exibir dados de duas tabelas de banco de dados relacionadas para que os valores mostrados em um controle `DataGridView` dependam da linha selecionada no momento em um outro controle.</span><span class="sxs-lookup"><span data-stu-id="d48b6-132">Describes how to display data from two related database tables so that the values shown in one `DataGridView` control depend on the currently selected row in another control.</span></span>  
  
 [<span data-ttu-id="d48b6-133">Como personalizar a formatação de dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-133">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-134">Descreve como manipular o <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> evento para alterar a aparência de células dependendo de seus valores.</span><span class="sxs-lookup"><span data-stu-id="d48b6-134">Describes how to handle the <xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType> event to change the appearance of cells depending on their values.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d48b6-135">Referência</span><span class="sxs-lookup"><span data-stu-id="d48b6-135">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="d48b6-136">Fornece documentação de referência para o <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="d48b6-136">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataSource%2A?displayProperty=nameWithType>  
 <span data-ttu-id="d48b6-137">Fornece documentação de referência para a <xref:System.Windows.Forms.DataGridView.DataSource%2A> propriedade.</span><span class="sxs-lookup"><span data-stu-id="d48b6-137">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataSource%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.BindingSource>  
 <span data-ttu-id="d48b6-138">Fornece documentação de referência para o <xref:System.Windows.Forms.BindingSource> componente.</span><span class="sxs-lookup"><span data-stu-id="d48b6-138">Provides reference documentation for the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="d48b6-139">Seções relacionadas</span><span class="sxs-lookup"><span data-stu-id="d48b6-139">Related Sections</span></span>  
 [<span data-ttu-id="d48b6-140">Entrada de Dados no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-140">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="d48b6-141">Fornece tópicos que descrevem como alterar os maneira como os usuários adicionam e modificam dados no controle.</span><span class="sxs-lookup"><span data-stu-id="d48b6-141">Provides topics that describe how to change the way users add and modify data in the control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d48b6-142">Veja também</span><span class="sxs-lookup"><span data-stu-id="d48b6-142">See also</span></span>

- [<span data-ttu-id="d48b6-143">Controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="d48b6-143">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="d48b6-144">Tipos de coluna no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d48b6-144">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
