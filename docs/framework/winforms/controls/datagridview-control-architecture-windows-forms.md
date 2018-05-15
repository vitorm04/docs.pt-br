---
title: Arquitetura do controle DataGridView (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], architecture
ms.assetid: 1c6cabf0-02ee-4bbc-9574-b54bb7f5b19e
ms.openlocfilehash: a9fc1707b1691266d1844c411a08e7e8f35514ce
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="datagridview-control-architecture-windows-forms"></a><span data-ttu-id="2226d-102">Arquitetura do controle DataGridView (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="2226d-102">DataGridView Control Architecture (Windows Forms)</span></span>
<span data-ttu-id="2226d-103">O <xref:System.Windows.Forms.DataGridView> controle e suas classes relacionadas são projetados para ser um sistema flexível e extensível para exibir e editar dados tabulares.</span><span class="sxs-lookup"><span data-stu-id="2226d-103">The <xref:System.Windows.Forms.DataGridView> control and its related classes are designed to be a flexible, extensible system for displaying and editing tabular data.</span></span> <span data-ttu-id="2226d-104">Essas classes são contidas no <xref:System.Windows.Forms?displayProperty=nameWithType> namespace e eles são nomeados com o prefixo "DataGridView".</span><span class="sxs-lookup"><span data-stu-id="2226d-104">These classes are all contained in the <xref:System.Windows.Forms?displayProperty=nameWithType> namespace, and they are all named with the "DataGridView" prefix.</span></span>  
  
## <a name="architecture-elements"></a><span data-ttu-id="2226d-105">Elementos de arquitetura</span><span class="sxs-lookup"><span data-stu-id="2226d-105">Architecture Elements</span></span>  
 <span data-ttu-id="2226d-106">O principal <xref:System.Windows.Forms.DataGridView> complementar derivam de <xref:System.Windows.Forms.DataGridViewElement>.</span><span class="sxs-lookup"><span data-stu-id="2226d-106">The primary <xref:System.Windows.Forms.DataGridView> companion classes derive from <xref:System.Windows.Forms.DataGridViewElement>.</span></span> <span data-ttu-id="2226d-107">O modelo de objeto a seguir ilustra o <xref:System.Windows.Forms.DataGridViewElement> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="2226d-107">The following object model illustrates the <xref:System.Windows.Forms.DataGridViewElement> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="2226d-108">![Modelo de objeto DataGridViewElement](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span><span class="sxs-lookup"><span data-stu-id="2226d-108">![DataGridViewElement Object Model](../../../../docs/framework/winforms/controls/media/datagridviewelement.gif "DataGridViewElement")</span></span>  
<span data-ttu-id="2226d-109">Modelo do objeto DataGridViewElement</span><span class="sxs-lookup"><span data-stu-id="2226d-109">DataGridViewElement object model</span></span>  
  
 <span data-ttu-id="2226d-110">O <xref:System.Windows.Forms.DataGridViewElement> classe fornece uma referência ao pai <xref:System.Windows.Forms.DataGridView> controlar e tem um <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriedade, que contém um valor que representa uma combinação de valores da <xref:System.Windows.Forms.DataGridViewElementStates> enumeração.</span><span class="sxs-lookup"><span data-stu-id="2226d-110">The <xref:System.Windows.Forms.DataGridViewElement> class provides a reference to the parent <xref:System.Windows.Forms.DataGridView> control and has a <xref:System.Windows.Forms.DataGridViewElement.State%2A> property, which holds a value that represents a combination of values from the <xref:System.Windows.Forms.DataGridViewElementStates> enumeration.</span></span>  
  
 <span data-ttu-id="2226d-111">As seções a seguir descrevem o <xref:System.Windows.Forms.DataGridView> complementar classes em mais detalhes.</span><span class="sxs-lookup"><span data-stu-id="2226d-111">The following sections describe the <xref:System.Windows.Forms.DataGridView> companion classes in more detail.</span></span>  
  
### <a name="datagridviewelementstates"></a><span data-ttu-id="2226d-112">DataGridViewElementStates</span><span class="sxs-lookup"><span data-stu-id="2226d-112">DataGridViewElementStates</span></span>  
 <span data-ttu-id="2226d-113">O <xref:System.Windows.Forms.DataGridViewElementStates> enumeração contém os seguintes valores:</span><span class="sxs-lookup"><span data-stu-id="2226d-113">The <xref:System.Windows.Forms.DataGridViewElementStates> enumeration contains the following values:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.None>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ReadOnly>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Resizable>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.ResizableSet>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Selected>  
  
-   <xref:System.Windows.Forms.DataGridViewElementStates.Visible>  
  
 <span data-ttu-id="2226d-114">Os valores da enumeração podem ser combinados com os operadores lógicos, portanto, o <xref:System.Windows.Forms.DataGridViewElement.State%2A> propriedade pode expressar mais de um estado de uma vez.</span><span class="sxs-lookup"><span data-stu-id="2226d-114">The values of this enumeration can be combined with the bitwise logical operators, so the <xref:System.Windows.Forms.DataGridViewElement.State%2A> property can express more than one state at once.</span></span> <span data-ttu-id="2226d-115">Por exemplo, um <xref:System.Windows.Forms.DataGridViewElement> podem ser simultaneamente <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, e <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span><span class="sxs-lookup"><span data-stu-id="2226d-115">For example, a <xref:System.Windows.Forms.DataGridViewElement> can be simultaneously <xref:System.Windows.Forms.DataGridViewElementStates.Frozen>, <xref:System.Windows.Forms.DataGridViewElementStates.Selected>, and <xref:System.Windows.Forms.DataGridViewElementStates.Visible>.</span></span>  
  
### <a name="cells-and-bands"></a><span data-ttu-id="2226d-116">Células e faixas</span><span class="sxs-lookup"><span data-stu-id="2226d-116">Cells and Bands</span></span>  
 <span data-ttu-id="2226d-117">O <xref:System.Windows.Forms.DataGridView> controle consiste em dois tipos básicos de objetos: células e as faixas.</span><span class="sxs-lookup"><span data-stu-id="2226d-117">The <xref:System.Windows.Forms.DataGridView> control comprises two fundamental kinds of objects: cells and bands.</span></span> <span data-ttu-id="2226d-118">Todas as células derivam de <xref:System.Windows.Forms.DataGridViewCell> classe base.</span><span class="sxs-lookup"><span data-stu-id="2226d-118">All cells derive from the <xref:System.Windows.Forms.DataGridViewCell> base class.</span></span> <span data-ttu-id="2226d-119">Os dois tipos de faixas, <xref:System.Windows.Forms.DataGridViewColumn> e <xref:System.Windows.Forms.DataGridViewRow>, ambos derivam de <xref:System.Windows.Forms.DataGridViewBand> classe base.</span><span class="sxs-lookup"><span data-stu-id="2226d-119">The two kinds of bands, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.DataGridViewRow>, both derive from the <xref:System.Windows.Forms.DataGridViewBand> base class.</span></span>  
  
 <span data-ttu-id="2226d-120">O <xref:System.Windows.Forms.DataGridView> controle interopera com várias classes, mas são mais comumente encontrados <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, e <xref:System.Windows.Forms.DataGridViewRow>.</span><span class="sxs-lookup"><span data-stu-id="2226d-120">The <xref:System.Windows.Forms.DataGridView> control interoperates with several classes, but the most commonly encountered are <xref:System.Windows.Forms.DataGridViewCell>, <xref:System.Windows.Forms.DataGridViewColumn>, and <xref:System.Windows.Forms.DataGridViewRow>.</span></span>  
  
### <a name="datagridviewcell"></a><span data-ttu-id="2226d-121">DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="2226d-121">DataGridViewCell</span></span>  
 <span data-ttu-id="2226d-122">A célula é a unidade fundamental de interação para o <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="2226d-122">The cell is the fundamental unit of interaction for the <xref:System.Windows.Forms.DataGridView>.</span></span> <span data-ttu-id="2226d-123">A exibição é centralizada das células e entrada de dados geralmente é realizada por meio das células.</span><span class="sxs-lookup"><span data-stu-id="2226d-123">Display is centered on cells, and data entry is often performed through cells.</span></span> <span data-ttu-id="2226d-124">Você pode acessar as células usando o <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> coleção do <xref:System.Windows.Forms.DataGridViewRow> classe e você pode acessar as células selecionadas usando o <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> coleção do <xref:System.Windows.Forms.DataGridView> controle.</span><span class="sxs-lookup"><span data-stu-id="2226d-124">You can access cells by using the <xref:System.Windows.Forms.DataGridViewRow.Cells%2A> collection of the <xref:System.Windows.Forms.DataGridViewRow> class, and you can access the selected cells by using the <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> collection of the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="2226d-125">O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewCell> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="2226d-125">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewCell> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="2226d-126">![Modelo de objeto DataGridViewCell](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span><span class="sxs-lookup"><span data-stu-id="2226d-126">![DataGridViewCell Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcell.gif "DataGridViewCell")</span></span>  
<span data-ttu-id="2226d-127">Modelo do objeto DataGridViewCell</span><span class="sxs-lookup"><span data-stu-id="2226d-127">DataGridViewCell object model</span></span>  
  
 <span data-ttu-id="2226d-128">O <xref:System.Windows.Forms.DataGridViewCell> tipo é uma classe base abstrata da qual derivam todos os tipos de célula.</span><span class="sxs-lookup"><span data-stu-id="2226d-128">The <xref:System.Windows.Forms.DataGridViewCell> type is an abstract base class, from which all cell types derive.</span></span> <span data-ttu-id="2226d-129"><xref:System.Windows.Forms.DataGridViewCell> e seus tipos derivados não são controles de formulários do Windows, mas alguns controles de formulários do Windows de host.</span><span class="sxs-lookup"><span data-stu-id="2226d-129"><xref:System.Windows.Forms.DataGridViewCell> and its derived types are not Windows Forms controls, but some host Windows Forms controls.</span></span> <span data-ttu-id="2226d-130">Qualquer funcionalidade de edição com suporte de uma célula normalmente é manipulada por um controle hospedado.</span><span class="sxs-lookup"><span data-stu-id="2226d-130">Any editing functionality supported by a cell is typically handled by a hosted control.</span></span>  
  
 <span data-ttu-id="2226d-131"><xref:System.Windows.Forms.DataGridViewCell> objetos não controlam suas próprias aparência e os recursos de pintura da mesma maneira como controles de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="2226d-131"><xref:System.Windows.Forms.DataGridViewCell> objects do not control their own appearance and painting features in the same way as Windows Forms controls.</span></span> <span data-ttu-id="2226d-132">Em vez disso, o <xref:System.Windows.Forms.DataGridView> é responsável pela aparência de seu <xref:System.Windows.Forms.DataGridViewCell> objetos.</span><span class="sxs-lookup"><span data-stu-id="2226d-132">Instead, the <xref:System.Windows.Forms.DataGridView> is responsible for the appearance of its <xref:System.Windows.Forms.DataGridViewCell> objects.</span></span> <span data-ttu-id="2226d-133">Você pode afetar significativamente a aparência e comportamento de células interagindo com o <xref:System.Windows.Forms.DataGridView> propriedades e eventos do controle.</span><span class="sxs-lookup"><span data-stu-id="2226d-133">You can significantly affect the appearance and behavior of cells by interacting with the <xref:System.Windows.Forms.DataGridView> control's properties and events.</span></span> <span data-ttu-id="2226d-134">Quando você tem requisitos especiais para personalizações que estão além dos recursos da <xref:System.Windows.Forms.DataGridView> controle, você pode implementar sua própria classe que deriva de <xref:System.Windows.Forms.DataGridViewCell> ou uma de suas classes filho.</span><span class="sxs-lookup"><span data-stu-id="2226d-134">When you have special requirements for customizations that are beyond the capabilities of the <xref:System.Windows.Forms.DataGridView> control, you can implement your own class that derives from <xref:System.Windows.Forms.DataGridViewCell> or one of its child classes.</span></span>  
  
 <span data-ttu-id="2226d-135">A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewCell>:</span><span class="sxs-lookup"><span data-stu-id="2226d-135">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewCell>:</span></span>  
  
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
  
-   <span data-ttu-id="2226d-136">Seus tipos de célula personalizados</span><span class="sxs-lookup"><span data-stu-id="2226d-136">Your custom cell types</span></span>  
  
### <a name="datagridviewcolumn"></a><span data-ttu-id="2226d-137">DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="2226d-137">DataGridViewColumn</span></span>  
 <span data-ttu-id="2226d-138">O esquema do <xref:System.Windows.Forms.DataGridView> repositório de dados anexados do controle é expresso no <xref:System.Windows.Forms.DataGridView> colunas do controle.</span><span class="sxs-lookup"><span data-stu-id="2226d-138">The schema of the <xref:System.Windows.Forms.DataGridView> control's attached data store is expressed in the <xref:System.Windows.Forms.DataGridView> control's columns.</span></span> <span data-ttu-id="2226d-139">Você pode acessar o <xref:System.Windows.Forms.DataGridView> colunas do controle usando o <xref:System.Windows.Forms.DataGridView.Columns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="2226d-139">You can access the <xref:System.Windows.Forms.DataGridView> control's columns by using the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span> <span data-ttu-id="2226d-140">Você pode acessar as colunas selecionadas usando o <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="2226d-140">You can access the selected columns by using the <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> collection.</span></span> <span data-ttu-id="2226d-141">O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewColumn> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="2226d-141">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewColumn> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="2226d-142">![Modelo de objeto de DataGridViewColumn](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span><span class="sxs-lookup"><span data-stu-id="2226d-142">![DataGridViewColumn Object Model](../../../../docs/framework/winforms/controls/media/datagridviewcolumn.gif "DataGridViewColumn")</span></span>  
<span data-ttu-id="2226d-143">Modelo do objeto DataGridViewColumn</span><span class="sxs-lookup"><span data-stu-id="2226d-143">DataGridViewColumn object model</span></span>  
  
 <span data-ttu-id="2226d-144">Alguns dos principais tipos de células têm tipos de colunas correspondentes.</span><span class="sxs-lookup"><span data-stu-id="2226d-144">Some of the key cell types have corresponding column types.</span></span> <span data-ttu-id="2226d-145">Eles derivam de <xref:System.Windows.Forms.DataGridViewColumn> classe base.</span><span class="sxs-lookup"><span data-stu-id="2226d-145">These are derived from the <xref:System.Windows.Forms.DataGridViewColumn> base class.</span></span>  
  
 <span data-ttu-id="2226d-146">A lista a seguir mostra as classes derivadas de <xref:System.Windows.Forms.DataGridViewColumn>:</span><span class="sxs-lookup"><span data-stu-id="2226d-146">The following list shows the classes derived from <xref:System.Windows.Forms.DataGridViewColumn>:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewButtonColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewCheckBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewImageColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxColumn>  
  
-   <xref:System.Windows.Forms.DataGridViewLinkColumn>  
  
-   <span data-ttu-id="2226d-147">Seus tipos de colunas personalizadas</span><span class="sxs-lookup"><span data-stu-id="2226d-147">Your custom column types</span></span>  
  
### <a name="datagridview-editing-controls"></a><span data-ttu-id="2226d-148">Controles de edição de DataGridView</span><span class="sxs-lookup"><span data-stu-id="2226d-148">DataGridView Editing Controls</span></span>  
 <span data-ttu-id="2226d-149">Células que dão suporte a recursos de edição avançados normalmente usam um controle hospedado que é derivado de um controle dos Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2226d-149">Cells that support advanced editing functionality typically use a hosted control that is derived from a Windows Forms control.</span></span> <span data-ttu-id="2226d-150">Esses controles também implementam o <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span><span class="sxs-lookup"><span data-stu-id="2226d-150">These controls also implement the <xref:System.Windows.Forms.IDataGridViewEditingControl> interface.</span></span> <span data-ttu-id="2226d-151">O modelo de objeto a seguir ilustra o uso desses controles.</span><span class="sxs-lookup"><span data-stu-id="2226d-151">The following object model illustrates the usage of these controls.</span></span>  
  
 <span data-ttu-id="2226d-152">![Editar modelo de objeto de controle de DataGridView](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span><span class="sxs-lookup"><span data-stu-id="2226d-152">![DataGridView Editing Control Object Model](../../../../docs/framework/winforms/controls/media/datagridviewediting.gif "DataGridViewEditing")</span></span>  
<span data-ttu-id="2226d-153">Modelo do objeto de controle de edição de DataGridView</span><span class="sxs-lookup"><span data-stu-id="2226d-153">DataGridView editing control object model</span></span>  
  
 <span data-ttu-id="2226d-154">Os seguintes controles de edição são fornecidos com o <xref:System.Windows.Forms.DataGridView> controle:</span><span class="sxs-lookup"><span data-stu-id="2226d-154">The following editing controls are provided with the <xref:System.Windows.Forms.DataGridView> control:</span></span>  
  
-   <xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>  
  
-   <xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>  
  
 <span data-ttu-id="2226d-155">Para obter informações sobre como criar seus próprios controles de edição, consulte [Como hospedar controles em células DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span><span class="sxs-lookup"><span data-stu-id="2226d-155">For information about creating your own editing controls, see [How to: Host Controls in Windows Forms DataGridView Cells](../../../../docs/framework/winforms/controls/how-to-host-controls-in-windows-forms-datagridview-cells.md).</span></span>  
  
 <span data-ttu-id="2226d-156">A tabela a seguir ilustra o relacionamento entre tipos de células, tipos de colunas e controles de edição.</span><span class="sxs-lookup"><span data-stu-id="2226d-156">The following table illustrates the relationship among cell types, column types, and editing controls.</span></span>  
  
|<span data-ttu-id="2226d-157">Tipo de célula</span><span class="sxs-lookup"><span data-stu-id="2226d-157">Cell type</span></span>|<span data-ttu-id="2226d-158">Controle hospedado</span><span class="sxs-lookup"><span data-stu-id="2226d-158">Hosted control</span></span>|<span data-ttu-id="2226d-159">Tipo de coluna</span><span class="sxs-lookup"><span data-stu-id="2226d-159">Column type</span></span>|  
|---------------|--------------------|-----------------|  
|<xref:System.Windows.Forms.DataGridViewButtonCell>|<span data-ttu-id="2226d-160">N/D</span><span class="sxs-lookup"><span data-stu-id="2226d-160">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewButtonColumn>|  
|<xref:System.Windows.Forms.DataGridViewCheckBoxCell>|<span data-ttu-id="2226d-161">N/D</span><span class="sxs-lookup"><span data-stu-id="2226d-161">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewCheckBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewComboBoxCell>|<xref:System.Windows.Forms.DataGridViewComboBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewComboBoxColumn>|  
|<xref:System.Windows.Forms.DataGridViewImageCell>|<span data-ttu-id="2226d-162">N/D</span><span class="sxs-lookup"><span data-stu-id="2226d-162">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewImageColumn>|  
|<xref:System.Windows.Forms.DataGridViewLinkCell>|<span data-ttu-id="2226d-163">N/D</span><span class="sxs-lookup"><span data-stu-id="2226d-163">n/a</span></span>|<xref:System.Windows.Forms.DataGridViewLinkColumn>|  
|<xref:System.Windows.Forms.DataGridViewTextBoxCell>|<xref:System.Windows.Forms.DataGridViewTextBoxEditingControl>|<xref:System.Windows.Forms.DataGridViewTextBoxColumn>|  
  
### <a name="datagridviewrow"></a><span data-ttu-id="2226d-164">DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="2226d-164">DataGridViewRow</span></span>  
 <span data-ttu-id="2226d-165">O <xref:System.Windows.Forms.DataGridViewRow> classe exibe campos de dados do registro dos dados da loja para o qual o <xref:System.Windows.Forms.DataGridView> controle está anexado.</span><span class="sxs-lookup"><span data-stu-id="2226d-165">The <xref:System.Windows.Forms.DataGridViewRow> class displays a record's data fields from the data store to which the <xref:System.Windows.Forms.DataGridView> control is attached.</span></span> <span data-ttu-id="2226d-166">Você pode acessar o <xref:System.Windows.Forms.DataGridView> linhas do controle usando o <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="2226d-166">You can access the <xref:System.Windows.Forms.DataGridView> control's rows by using the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span> <span data-ttu-id="2226d-167">Você pode acessar as linhas selecionadas usando o <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> coleção.</span><span class="sxs-lookup"><span data-stu-id="2226d-167">You can access the selected rows by using the <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> collection.</span></span> <span data-ttu-id="2226d-168">O modelo de objeto a seguir ilustra esse uso e mostra o <xref:System.Windows.Forms.DataGridViewRow> hierarquia de herança.</span><span class="sxs-lookup"><span data-stu-id="2226d-168">The following object model illustrates this usage and shows the <xref:System.Windows.Forms.DataGridViewRow> inheritance hierarchy.</span></span>  
  
 <span data-ttu-id="2226d-169">![Modelo de objeto DataGridViewRow](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span><span class="sxs-lookup"><span data-stu-id="2226d-169">![DataGridViewRow Object Model](../../../../docs/framework/winforms/controls/media/datagridviewrow.gif "DataGridViewRow")</span></span>  
<span data-ttu-id="2226d-170">Modelo do objeto DataGridViewRow</span><span class="sxs-lookup"><span data-stu-id="2226d-170">DataGridViewRow object model</span></span>  
  
 <span data-ttu-id="2226d-171">Você pode derivar seus próprios tipos do <xref:System.Windows.Forms.DataGridViewRow> classe, embora isso normalmente não é necessário.</span><span class="sxs-lookup"><span data-stu-id="2226d-171">You can derive your own types from the <xref:System.Windows.Forms.DataGridViewRow> class, although this will typically not be necessary.</span></span> <span data-ttu-id="2226d-172">O <xref:System.Windows.Forms.DataGridView> controle tem vários eventos relacionados à linha e propriedades para personalizar o comportamento do seu <xref:System.Windows.Forms.DataGridViewRow> objetos.</span><span class="sxs-lookup"><span data-stu-id="2226d-172">The <xref:System.Windows.Forms.DataGridView> control has several row-related events and properties for customizing the behavior of its <xref:System.Windows.Forms.DataGridViewRow> objects.</span></span>  
  
 <span data-ttu-id="2226d-173">Se você habilitar o <xref:System.Windows.Forms.DataGridView> do controle <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> propriedade, uma linha especial para adicionar novas linhas aparece como a última linha.</span><span class="sxs-lookup"><span data-stu-id="2226d-173">If you enable the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property, a special row for adding new rows appears as the last row.</span></span> <span data-ttu-id="2226d-174">Esta linha é parte do <xref:System.Windows.Forms.DataGridView.Rows%2A> coleção, mas tem uma funcionalidade especial que pode exigir atenção.</span><span class="sxs-lookup"><span data-stu-id="2226d-174">This row is part of the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection, but it has special functionality that may require your attention.</span></span> <span data-ttu-id="2226d-175">Para obter mais informações, consulte [Usando a linha para novos registros no controle DataGridView dos Windows Forms](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="2226d-175">For more information, see [Using the Row for New Records in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2226d-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2226d-176">See Also</span></span>  
 [<span data-ttu-id="2226d-177">Visão geral do controle DataGridView</span><span class="sxs-lookup"><span data-stu-id="2226d-177">DataGridView Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-overview-windows-forms.md)  
 [<span data-ttu-id="2226d-178">Personalizando o controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2226d-178">Customizing the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/customizing-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="2226d-179">Usando a linha para novos registros no controle DataGridView dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2226d-179">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
