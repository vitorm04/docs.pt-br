---
title: Arquitetura de controle DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 2e1884383cca87f8d4ff84f486e2b29761a0c55d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742535"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="dd359-102">Arquitetura do controle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="dd359-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="dd359-103">O controle de <xref:System.Windows.Forms.DataGridView> e suas classes relacionadas são projetados para ser um sistema flexível e extensível para exibir e editar dados tabulares.</span><span class="sxs-lookup"><span data-stu-id="dd359-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="dd359-104">Essas classes estão todas contidas no namespace <xref:System.Windows.Forms?displayProperty=nameWithType>, e elas são todas nomeadas com o prefixo "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="dd359-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="dd359-105">Elementos de arquitetura</span><span class="sxs-lookup"><span data-stu-id="dd359-105">Architecture Elements</span></span>  
 <span data-ttu-id="dd359-106">As classes principais do <xref:System.Windows.Forms.DataGridView> Companion derivam de <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="dd359-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="dd359-107">O modelo de objeto a seguir ilustra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="dd359-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia de modelo de objeto DataGridViewelement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="dd359-109">A classe <xref:System.Windows.Forms.DataGridViewElement> fornece uma referência ao controle de <xref:System.Windows.Forms.DataGridView> pai e tem uma propriedade <xref:System.Windows.Forms.DataGridViewElement.State%2A>, que contém um valor que representa uma combinação de valores da enumeração <xref:System.Windows.Forms.DataGridViewElementStates>.</span><span class="sxs-lookup"><span data-stu-id="dd359-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="dd359-110">As seções a seguir descrevem as classes <xref:System.Windows.Forms.DataGridView> complementares mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="dd359-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="dd359-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="dd359-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="dd359-112">A enumeração <xref:System.Windows.Forms.DataGridViewElementStates> contém os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="dd359-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
- <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="dd359-113">Os valores dessa enumeração podem ser combinados com os operadores lógicos de bit-a, para que a propriedade <xref:System.Windows.Forms.DataGridViewElement.State%2A> possa expressar mais de um estado de uma vez.</span><span class="sxs-lookup"><span data-stu-id="dd359-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="dd359-114">Por exemplo, um <xref:System.Windows.Forms.DataGridViewElement> pode ser <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>e <xref:System.Windows.Forms.DataGridViewElementStates.Visible>simultaneamente.</span><span class="sxs-lookup"><span data-stu-id="dd359-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="dd359-115">Células e faixas</span><span class="sxs-lookup"><span data-stu-id="dd359-115">Cells and Bands</span></span>  
 <span data-ttu-id="dd359-116">O controle <xref:System.Windows.Forms.DataGridView> consiste em dois tipos fundamentais de objetos: células e faixas.</span><span class="sxs-lookup"><span data-stu-id="dd359-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="dd359-117">Todas as células derivam da classe base <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="dd359-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="dd359-118">Os dois tipos de bandas, <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewRow>derivam da classe base <xref:System.Windows.Forms.DataGridViewBand>.</span><span class="sxs-lookup"><span data-stu-id="dd359-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="dd359-119">O controle de <xref:System.Windows.Forms.DataGridView> interopera com várias classes, mas as mais comumente encontradas são <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>e <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="dd359-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="dd359-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="dd359-120">DataGridViewCell</span></span>  
 <span data-ttu-id="dd359-121">A célula é a unidade fundamental de interação para o <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="dd359-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="dd359-122">A exibição é centralizada das células e entrada de dados geralmente é realizada por meio das células.</span><span class="sxs-lookup"><span data-stu-id="dd359-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="dd359-123">Você pode acessar células usando a coleção de <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> da classe <xref:System.Windows.Forms.DataGridViewRow> e pode acessar as células selecionadas usando a coleção <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> do controle <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="dd359-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="dd359-124">O modelo de objeto a seguir ilustra esse uso e mostra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="dd359-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia de modelo de objeto DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="dd359-126">O tipo de <xref:System.Windows.Forms.DataGridViewCell> é uma classe base abstrata, da qual todos os tipos de célula derivam.</span><span class="sxs-lookup"><span data-stu-id="dd359-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="dd359-127"><xref:System.Windows.Forms.DataGridViewCell> e seus tipos derivados não são Windows Forms controles, mas alguns controles de Windows Forms do host.</span><span class="sxs-lookup"><span data-stu-id="dd359-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="dd359-128">Qualquer funcionalidade de edição com suporte de uma célula normalmente é manipulada por um controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="dd359-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="dd359-129"><xref:System.Windows.Forms.DataGridViewCell> objetos não controlam seus próprios recursos de aparência e pintura da mesma maneira que Windows Forms controles.</span><span class="sxs-lookup"><span data-stu-id="dd359-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="dd359-130">Em vez disso, o <xref:System.Windows.Forms.DataGridView> é responsável pela aparência de seus objetos <xref:System.Windows.Forms.DataGridViewCell>.</span><span class="sxs-lookup"><span data-stu-id="dd359-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="dd359-131">Você pode afetar significativamente a aparência e o comportamento das células interagindo com as propriedades e os eventos do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="dd359-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="dd359-132">Quando você tem requisitos especiais para personalizações que estão além dos recursos do controle de <xref:System.Windows.Forms.DataGridView>, você pode implementar sua própria classe que deriva de <xref:System.Windows.Forms.DataGridViewCell> ou de uma de suas classes filhas.</span><span class="sxs-lookup"><span data-stu-id="dd359-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="dd359-133">A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="dd359-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
- <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
- <xref:System.Windows.Forms.DataGridViewImageCell>  
  
- <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
- <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
- <span data-ttu-id="dd359-134">Seus tipos de célula personalizados</span><span class="sxs-lookup"><span data-stu-id="dd359-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="dd359-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="dd359-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="dd359-136">O esquema do armazenamento de dados anexado do controle de <xref:System.Windows.Forms.DataGridView> é expresso nas colunas do controle de <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="dd359-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="dd359-137">Você pode acessar as colunas do controle de <xref:System.Windows.Forms.DataGridView> usando a coleção <xref:System.Windows.Forms.DataGridView.Columns%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd359-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="dd359-138">Você pode acessar as colunas selecionadas usando a coleção de <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd359-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="dd359-139">O modelo de objeto a seguir ilustra esse uso e mostra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="dd359-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia do modelo de objeto DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="dd359-141">Alguns dos principais tipos de células têm tipos de colunas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="dd359-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="dd359-142">Eles são derivados da classe base <xref:System.Windows.Forms.DataGridViewColumn>.</span><span class="sxs-lookup"><span data-stu-id="dd359-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="dd359-143">A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="dd359-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
- <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
- <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
- <span data-ttu-id="dd359-144">Seus tipos de colunas personalizadas</span><span class="sxs-lookup"><span data-stu-id="dd359-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="dd359-145">Controles de edição de DataGridView</span><span class="sxs-lookup"><span data-stu-id="dd359-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="dd359-146">Células que dão suporte a recursos de edição avançados normalmente usam um controle hospedado que é derivado de um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="dd359-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="dd359-147">Esses controles também implementam a interface <xref:System.Windows.Forms.IDataGridViewEditingControl>.</span><span class="sxs-lookup"><span data-stu-id="dd359-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="dd359-148">O modelo de objeto a seguir ilustra o uso desses controles.</span><span class="sxs-lookup"><span data-stu-id="dd359-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagrama que mostra a hierarquia de modelo de objeto do controle de edição do DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="dd359-150">Os seguintes controles de edição são fornecidos com o controle de <xref:System.Windows.Forms.DataGridView>:</span><span class="sxs-lookup"><span data-stu-id="dd359-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
- <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
- <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="dd359-151">Para obter informações sobre como criar seus próprios controles de edição, consulte [Como hospedar controles em células DataGridView dos Windows Forms](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="dd359-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="dd359-152">A tabela a seguir ilustra o relacionamento entre tipos de células, tipos de colunas e controles de edição.</span><span class="sxs-lookup"><span data-stu-id="dd359-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="dd359-153">Tipo de célula</span><span class="sxs-lookup"><span data-stu-id="dd359-153">Cell type</span></span>|<span data-ttu-id="dd359-154">Controle hospedado</span><span class="sxs-lookup"><span data-stu-id="dd359-154">Hosted control</span></span>|<span data-ttu-id="dd359-155">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="dd359-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="dd359-156">N/D</span><span class="sxs-lookup"><span data-stu-id="dd359-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="dd359-157">N/D</span><span class="sxs-lookup"><span data-stu-id="dd359-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="dd359-158">N/D</span><span class="sxs-lookup"><span data-stu-id="dd359-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="dd359-159">N/D</span><span class="sxs-lookup"><span data-stu-id="dd359-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="dd359-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="dd359-160">DataGridViewRow</span></span>  
 <span data-ttu-id="dd359-161">A classe <xref:System.Windows.Forms.DataGridViewRow> exibe os campos de dados de um registro do armazenamento de dados ao qual o controle de <xref:System.Windows.Forms.DataGridView> está anexado.</span><span class="sxs-lookup"><span data-stu-id="dd359-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="dd359-162">Você pode acessar as linhas do controle de <xref:System.Windows.Forms.DataGridView> usando a coleção <xref:System.Windows.Forms.DataGridView.Rows%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd359-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="dd359-163">Você pode acessar as linhas selecionadas usando a coleção de <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd359-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="dd359-164">O modelo de objeto a seguir ilustra esse uso e mostra a hierarquia de herança do <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="dd359-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia do modelo de objeto DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="dd359-166">Você pode derivar seus próprios tipos da classe <xref:System.Windows.Forms.DataGridViewRow>, embora isso normalmente não será necessário.</span><span class="sxs-lookup"><span data-stu-id="dd359-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="dd359-167">O controle <xref:System.Windows.Forms.DataGridView> tem vários eventos e propriedades relacionados à linha para personalizar o comportamento de seus objetos <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="dd359-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="dd359-168">Se você habilitar a propriedade <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> do controle de <xref:System.Windows.Forms.DataGridView>, uma linha especial para adicionar novas linhas será exibida como a última linha.</span><span class="sxs-lookup"><span data-stu-id="dd359-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="dd359-169">Essa linha faz parte da coleção de <xref:System.Windows.Forms.DataGridView.Rows%2A>, mas tem uma funcionalidade especial que pode exigir sua atenção.</span><span class="sxs-lookup"><span data-stu-id="dd359-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="dd359-170">Para obter mais informações, consulte [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="dd359-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd359-171">Veja também</span><span class="sxs-lookup"><span data-stu-id="dd359-171">See also</span></span>

- [<span data-ttu-id="dd359-172">Visão geral do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="dd359-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="dd359-173">Personalizando o controle DataGridView do Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dd359-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="dd359-174">Usando a linha para novos registros no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dd359-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
