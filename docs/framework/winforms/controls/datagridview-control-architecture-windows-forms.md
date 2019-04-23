---
title: Arquitetura do controle DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: 892168ec282fbf168c43515e0718fe5486a345a8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59130254"
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="d2ba8-102">Arquitetura do controle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="d2ba8-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="d2ba8-103">O <xref:System.Windows.Forms.DataGridView> controle e suas classes relacionadas foram projetados para ser um sistema flexível e extensível para exibir e editar dados tabulares.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="d2ba8-104">Essas classes estão contidas no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace e eles são nomeados com o prefixo "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="d2ba8-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="d2ba8-105">Elementos de arquitetura</span><span class="sxs-lookup"><span data-stu-id="d2ba8-105">Architecture Elements</span></span>  
 <span data-ttu-id="d2ba8-106">O principal <xref:System.Windows.Forms.DataGridView> derivam de classes complementares <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="d2ba8-107">O modelo de objeto a seguir ilustra o <xref:System.Windows.Forms.DataGridViewElement> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia do objeto Datagridviewelement.](./media/datagridview-control-architecture-windows-forms/datagridviewelement-object-model.gif)  
  
 <span data-ttu-id="d2ba8-109">O <xref:System.Windows.Forms.DataGridViewElement> classe fornece uma referência ao pai <xref:System.Windows.Forms.DataGridView> controlar e tem um <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriedade, que contém um valor que representa uma combinação de valores da <xref:System.Windows.Forms.DataGridViewElementStates> enumeração.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-109">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="d2ba8-110">As seções a seguir descrevem o <xref:System.Windows.Forms.DataGridView> complementar classes mais detalhadamente.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-110">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="d2ba8-111">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="d2ba8-111">DataGridViewElementStates</span></span>  
 <span data-ttu-id="d2ba8-112">O <xref:System.Windows.Forms.DataGridViewElementStates> enumeração contém os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="d2ba8-112">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="d2ba8-113">Os valores dessa enumeração podem ser combinados com os operadores lógicos bit a bit, portanto, o <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriedade pode expressar mais de um estado de uma só vez.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-113">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="d2ba8-114">Por exemplo, uma <xref:System.Windows.Forms.DataGridViewElement> podem ser simultaneamente <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, e <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-114">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="d2ba8-115">Células e faixas</span><span class="sxs-lookup"><span data-stu-id="d2ba8-115">Cells and Bands</span></span>  
 <span data-ttu-id="d2ba8-116">O <xref:System.Windows.Forms.DataGridView> controle consiste em dois tipos de objetos fundamentais: células e faixas.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-116">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="d2ba8-117">Todas as células derivam o <xref:System.Windows.Forms.DataGridViewCell> classe base.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-117">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="d2ba8-118">Os dois tipos de faixas, <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewRow>, ambos derivam o <xref:System.Windows.Forms.DataGridViewBand> classe base.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-118">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="d2ba8-119">O <xref:System.Windows.Forms.DataGridView> controle interopera com várias classes, mas são mais comumente encontrados <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, e <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-119">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="d2ba8-120">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="d2ba8-120">DataGridViewCell</span></span>  
 <span data-ttu-id="d2ba8-121">A célula é a unidade fundamental de interação para o <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-121">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="d2ba8-122">A exibição é centralizada das células e entrada de dados geralmente é realizada por meio das células.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-122">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="d2ba8-123">Você pode acessar as células usando o <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> coleção do <xref:System.Windows.Forms.DataGridViewRow> classe e você pode acessar as células selecionadas usando a <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> coleção do <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-123">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="d2ba8-124">O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewCell> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-124">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia de modelo do objeto DataGridViewCell.](./media/datagridview-control-architecture-windows-forms/datagridviewcell-object-model.gif)  
  
 <span data-ttu-id="d2ba8-126">O <xref:System.Windows.Forms.DataGridViewCell> tipo é uma classe base abstrata da qual derivam todos os tipos de célula.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-126">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="d2ba8-127"><xref:System.Windows.Forms.DataGridViewCell> e seus tipos derivados não são controles dos Windows Forms, mas alguns controles de formulários do Windows do host.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-127"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="d2ba8-128">Qualquer funcionalidade de edição com suporte de uma célula normalmente é manipulada por um controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-128">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="d2ba8-129"><xref:System.Windows.Forms.DataGridViewCell> objetos não controlam sua aparência e seus recursos de pintura da mesma forma que os controles de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-129"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="d2ba8-130">Em vez disso, o <xref:System.Windows.Forms.DataGridView> é responsável pela aparência de seu <xref:System.Windows.Forms.DataGridViewCell> objetos.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-130">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="d2ba8-131">Você pode afetar significativamente a aparência e comportamento das células interagindo com o <xref:System.Windows.Forms.DataGridView> propriedades e eventos do controle.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-131">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="d2ba8-132">Quando você tiver requisitos especiais para personalizações que estão além dos recursos do <xref:System.Windows.Forms.DataGridView> controle, você pode implementar sua própria classe que deriva de <xref:System.Windows.Forms.DataGridViewCell> ou uma de suas classes filho.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-132">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="d2ba8-133">A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="d2ba8-133">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonCell>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkCell>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxCell>  
  
-   <xref:System.Windows.Forms.DataGridViewImageCell>  
  
-   <xref:System.Windows.Forms.DataGridViewHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewRowHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewColumnHeaderCell>  
  
-   <xref:System.Windows.Forms.DataGridViewTopLeftHeaderCell>  
  
-   <span data-ttu-id="d2ba8-134">Seus tipos de célula personalizados</span><span class="sxs-lookup"><span data-stu-id="d2ba8-134">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="d2ba8-135">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="d2ba8-135">DataGridViewColumn</span></span>  
 <span data-ttu-id="d2ba8-136">O esquema do <xref:System.Windows.Forms.DataGridView> repositório de dados anexados do controle é expresso no <xref:System.Windows.Forms.DataGridView> colunas do controle.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-136">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="d2ba8-137">Você pode acessar o <xref:System.Windows.Forms.DataGridView> colunas do controle usando o <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-137">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="d2ba8-138">Você pode acessar as colunas selecionadas usando a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-138">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="d2ba8-139">O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewColumn> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-139">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia de modelo do objeto DataGridViewColumn.](./media/datagridview-control-architecture-windows-forms/datagridviewcolumn-object-model.gif)  
  
 <span data-ttu-id="d2ba8-141">Alguns dos principais tipos de células têm tipos de colunas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-141">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="d2ba8-142">Eles derivam o <xref:System.Windows.Forms.DataGridViewColumn> classe base.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-142">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="d2ba8-143">A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="d2ba8-143">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="d2ba8-144">Seus tipos de colunas personalizadas</span><span class="sxs-lookup"><span data-stu-id="d2ba8-144">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="d2ba8-145">Controles de edição de DataGridView</span><span class="sxs-lookup"><span data-stu-id="d2ba8-145">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="d2ba8-146">Células que dão suporte a recursos de edição avançados normalmente usam um controle hospedado que é derivado de um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-146">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="d2ba8-147">Esses controles também implementam a <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-147">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="d2ba8-148">O modelo de objeto a seguir ilustra o uso desses controles.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-148">The following object model illustrates the usage of these controls.</span></span>  
  
 ![Diagrama mostrando a hierarquia de modelo de objeto de controle de edição de DataGridView.](./media/datagridview-control-architecture-windows-forms/datagridviewediting-object-model.gif)  
  
 <span data-ttu-id="d2ba8-150">Os controles de edição a seguir são fornecidos com o <xref:System.Windows.Forms.DataGridView> controle:</span><span class="sxs-lookup"><span data-stu-id="d2ba8-150">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="d2ba8-151">Para obter informações sobre como criar suas própria edição de controles, consulte [como: Hospedar controles em Windows Forms células DataGridView](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="d2ba8-151">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="d2ba8-152">A tabela a seguir ilustra o relacionamento entre tipos de células, tipos de colunas e controles de edição.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-152">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="d2ba8-153">Tipo de célula</span><span class="sxs-lookup"><span data-stu-id="d2ba8-153">Cell type</span></span>|<span data-ttu-id="d2ba8-154">Controle hospedado</span><span class="sxs-lookup"><span data-stu-id="d2ba8-154">Hosted control</span></span>|<span data-ttu-id="d2ba8-155">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="d2ba8-155">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="d2ba8-156">N/D</span><span class="sxs-lookup"><span data-stu-id="d2ba8-156">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="d2ba8-157">N/D</span><span class="sxs-lookup"><span data-stu-id="d2ba8-157">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="d2ba8-158">N/D</span><span class="sxs-lookup"><span data-stu-id="d2ba8-158">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="d2ba8-159">N/D</span><span class="sxs-lookup"><span data-stu-id="d2ba8-159">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="d2ba8-160">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="d2ba8-160">DataGridViewRow</span></span>  
 <span data-ttu-id="d2ba8-161">O <xref:System.Windows.Forms.DataGridViewRow> exibe classe campos de dados de um registro dos dados da loja para o qual o <xref:System.Windows.Forms.DataGridView> controle está anexado.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-161">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="d2ba8-162">Você pode acessar o <xref:System.Windows.Forms.DataGridView> linhas do controle usando o <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-162">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="d2ba8-163">Você pode acessar as linhas selecionadas usando a <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-163">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="d2ba8-164">O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewRow> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-164">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 ![Diagrama que mostra a hierarquia de modelo do objeto DataGridViewRow.](./media/datagridview-control-architecture-windows-forms/datagridviewrow-object-model.gif)
  
 <span data-ttu-id="d2ba8-166">Você pode derivar seus próprios tipos da <xref:System.Windows.Forms.DataGridViewRow> classe, embora isso normalmente não será necessário.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-166">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="d2ba8-167">O <xref:System.Windows.Forms.DataGridView> controle tem vários eventos relacionados à linha e propriedades para personalizar o comportamento do seu <xref:System.Windows.Forms.DataGridViewRow> objetos.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-167">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="d2ba8-168">Se você habilitar a <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriedade, uma linha especial para adicionar novas linhas aparecerá como a última linha.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-168">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="d2ba8-169">Esta linha é parte do <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção, mas ele tem uma funcionalidade especial que pode exigir sua atenção.</span><span class="sxs-lookup"><span data-stu-id="d2ba8-169">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="d2ba8-170">Para obter mais informações, consulte [Usando a linha para novos registros no controle DataGridView dos Windows Forms](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="d2ba8-170">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2ba8-171">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2ba8-171">See also</span></span>

- [<span data-ttu-id="d2ba8-172">Visão geral do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="d2ba8-172">DataGridView Control Overview</span></span>](datagridview-control-overview-windows-forms.md)
- [<span data-ttu-id="d2ba8-173">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d2ba8-173">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d2ba8-174">Usando a linha para novos registros no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d2ba8-174">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
