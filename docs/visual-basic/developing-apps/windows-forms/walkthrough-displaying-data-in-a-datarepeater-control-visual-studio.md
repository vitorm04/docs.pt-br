---
title: 'Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
ms.openlocfilehash: 8e64a819e9670a29e97140a32c81f5ff9006f83e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388546"
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="5371c-102">Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5371c-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="5371c-103">Este passo a passo fornece um cenário básico do início ao fim para exibir dados associados em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="5371c-104">Pré-requisito</span><span class="sxs-lookup"><span data-stu-id="5371c-104">Prerequisite</span></span>  
 <span data-ttu-id="5371c-105">Este passo a passo requer o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="5371c-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="5371c-106">Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do Microsoft Download Center.</span><span class="sxs-lookup"><span data-stu-id="5371c-106">If you do not have this database on your development computer, you can download it from the Microsoft Download Center.</span></span> <span data-ttu-id="5371c-107">Para obter instruções, consulte [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="5371c-107">For instructions, see [Downloading Sample Databases](../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="5371c-108">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5371c-108">Overview</span></span>  
 <span data-ttu-id="5371c-109">A primeira parte deste passo a passo consiste em quatro tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="5371c-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="5371c-110">Criando uma solução.</span><span class="sxs-lookup"><span data-stu-id="5371c-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="5371c-111">Adicionando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="5371c-112">Adicionando uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="5371c-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="5371c-113">Adicionando controles ligados a dados.</span><span class="sxs-lookup"><span data-stu-id="5371c-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="5371c-114">Criando uma solução do DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="5371c-115">Na primeira etapa, você pode criar um projeto e solução.</span><span class="sxs-lookup"><span data-stu-id="5371c-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="5371c-116">Para criar uma solução do DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="5371c-117">No Visual Studio **arquivo** menu, clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="5371c-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="5371c-118">No **tipos de projeto** painel na **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**e, em seguida, clique em **Windows**.</span><span class="sxs-lookup"><span data-stu-id="5371c-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="5371c-119">No **modelos** painel, clique em **aplicativo de formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="5371c-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="5371c-120">Na caixa **Nome**, digite `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="5371c-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="5371c-121">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5371c-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="5371c-122">O Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="5371c-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="5371c-123">Selecione o formulário no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="5371c-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="5371c-124">No **propriedades** janela, defina as **tamanho** propriedade `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="5371c-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="5371c-125">Adicionando um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="5371c-126">Nesta etapa, você adiciona um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle ao formulário.</span><span class="sxs-lookup"><span data-stu-id="5371c-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="5371c-127">Para adicionar um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="5371c-128">Sobre o **modo de exibição** menu, clique em **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5371c-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="5371c-129">O **caixa de ferramentas** é aberta.</span><span class="sxs-lookup"><span data-stu-id="5371c-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="5371c-130">Selecione o **Visual Basic PowerPacks** guia.</span><span class="sxs-lookup"><span data-stu-id="5371c-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="5371c-131">Arraste uma <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para **Form1**.</span><span class="sxs-lookup"><span data-stu-id="5371c-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="5371c-132">Na janela Propriedades, defina as **local** propriedade `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="5371c-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="5371c-133">Defina as **tamanho** propriedade `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="5371c-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="5371c-134">Adicionando uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="5371c-134">Adding a Data Source</span></span>  
 <span data-ttu-id="5371c-135">Nesta etapa, você adiciona uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="5371c-136">Para adicionar uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="5371c-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="5371c-137">Sobre o **dados** menu, clique em **Show Data Sources**.</span><span class="sxs-lookup"><span data-stu-id="5371c-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="5371c-138">No **fontes de dados** janela, clique em **Add New Data Source**.</span><span class="sxs-lookup"><span data-stu-id="5371c-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="5371c-139">Selecione **banco de dados** sobre o **escolher um tipo de fonte de dados** página e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="5371c-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="5371c-140">Sobre o **escolha sua Conexão de dados** , execute uma das seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="5371c-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="5371c-141">Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nela.</span><span class="sxs-lookup"><span data-stu-id="5371c-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="5371c-142">-ou-</span><span class="sxs-lookup"><span data-stu-id="5371c-142">-or-</span></span>  
  
    -   <span data-ttu-id="5371c-143">Clique em **nova Conexão** para configurar uma nova conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="5371c-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="5371c-144">Para obter mais informações, consulte [adicionar novas conexões](/visualstudio/data-tools/add-new-connections).</span><span class="sxs-lookup"><span data-stu-id="5371c-144">For more information, see [Add new connections](/visualstudio/data-tools/add-new-connections).</span></span>  
  
5.  <span data-ttu-id="5371c-145">Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="5371c-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="5371c-146">Se uma caixa de diálogo for exibida, clique em **Sim** para salvar o arquivo ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="5371c-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="5371c-147">Clique em **próxima** sobre o **salvar a cadeia de Conexão para o arquivo de configuração de aplicativo** página.</span><span class="sxs-lookup"><span data-stu-id="5371c-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="5371c-148">Expanda o **tabelas** nó na **Choose Your Database Objects** página.</span><span class="sxs-lookup"><span data-stu-id="5371c-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="5371c-149">Marque as caixas de seleção ao lado de **clientes** e **pedidos** tabelas e clique **concluir**.</span><span class="sxs-lookup"><span data-stu-id="5371c-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="5371c-150">**NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** as tabelas aparecem no **fontes de dados** janela.</span><span class="sxs-lookup"><span data-stu-id="5371c-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="5371c-151">Adicionando controles ligados a dados</span><span class="sxs-lookup"><span data-stu-id="5371c-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="5371c-152">Nesta etapa, você adiciona controles ligados a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="5371c-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="5371c-153">Para adicionar controles de associação de dados</span><span class="sxs-lookup"><span data-stu-id="5371c-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="5371c-154">No **fontes de dados** janela, selecione o nó de nível superior para o **clientes** tabela.</span><span class="sxs-lookup"><span data-stu-id="5371c-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="5371c-155">Alterar o tipo de tabela para descarte **detalhes** clicando **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="5371c-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="5371c-156">Selecione o **clientes** nó de tabela e arraste-o para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5371c-157">Um <xref:System.Windows.Forms.BindingNavigator> controle é adicionado ao formulário e o **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, e **CustomersBindingNavigator** componentes são adicionados à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="5371c-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="5371c-158">Selecione todos os campos e seus rótulos associados e posicioná-los próximo à borda esquerda da região de modelo de item.</span><span class="sxs-lookup"><span data-stu-id="5371c-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="5371c-159">Selecione os últimos cinco campos (**região**, **CEP**, **país**, **Phone**, e **Fax**) e os rótulos associados e movê-los até e à direita dos seis primeiros campos.</span><span class="sxs-lookup"><span data-stu-id="5371c-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="5371c-160">Selecione o modelo de item (região superior do controle).</span><span class="sxs-lookup"><span data-stu-id="5371c-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="5371c-161">Na janela Propriedades, defina as **tamanho** propriedade `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="5371c-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="5371c-162">Neste ponto, você tem um aplicativo funcional que exibirá uma lista de repetição de clientes.</span><span class="sxs-lookup"><span data-stu-id="5371c-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="5371c-163">Você pode pressionar F5 para executar o aplicativo, alterar os dados e adicionar ou excluir registros de cliente.</span><span class="sxs-lookup"><span data-stu-id="5371c-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="5371c-164">As próximas etapas opcionais, você aprenderá como personalizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="5371c-165">Próximas etapas (opcionais)</span><span class="sxs-lookup"><span data-stu-id="5371c-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="5371c-166">Esta parte do passo a passo consiste em quatro tarefas opcionais:</span><span class="sxs-lookup"><span data-stu-id="5371c-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="5371c-167">Alterando a aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="5371c-168">Impedindo que os usuários adicionem ou excluam registros.</span><span class="sxs-lookup"><span data-stu-id="5371c-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="5371c-169">Adicionar o recurso de pesquisa para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="5371c-170">Adicionando uma tabela mestre e de detalhes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="5371c-171">Alterando a aparência do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="5371c-172">Esta etapa opcional, você altera a `BackColor` do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="5371c-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="5371c-173">Você também adicionar código para exibir linhas alternando as cores e para alterar um rótulo `ForeColor` condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="5371c-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="5371c-174">Para alterar a aparência do controle</span><span class="sxs-lookup"><span data-stu-id="5371c-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="5371c-175">No Designer de formulários do Windows, selecione a região principal (inferior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="5371c-176">Na janela Propriedades, defina o `BackColor` propriedade em branco.</span><span class="sxs-lookup"><span data-stu-id="5371c-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="5371c-177">Clique duas vezes o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="5371c-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="5371c-178">No Editor de código, lista suspensa de eventos, clique em **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="5371c-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="5371c-179">No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o seguinte código para alternar o `BackColor`:</span><span class="sxs-lookup"><span data-stu-id="5371c-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="5371c-180">No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o seguinte código para alterar o `ForeColor` de um rótulo, dependendo de uma condição:</span><span class="sxs-lookup"><span data-stu-id="5371c-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="5371c-181">Pressione F5 para executar o aplicativo e ver as personalizações.</span><span class="sxs-lookup"><span data-stu-id="5371c-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="5371c-182">Impedindo que os usuários adicionem ou excluam registros</span><span class="sxs-lookup"><span data-stu-id="5371c-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="5371c-183">Esta etapa opcional, você adiciona código que impede que os usuários adicionem ou excluam registros no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="5371c-184">Para impedir que os usuários adicionando e excluindo registros</span><span class="sxs-lookup"><span data-stu-id="5371c-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="5371c-185">No Designer de formulários do Windows, clique duas vezes no formulário para abrir o Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="5371c-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="5371c-186">Adicione o seguinte código para o `Form_Load` evento:</span><span class="sxs-lookup"><span data-stu-id="5371c-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="5371c-187">Na lista suspensa nome de classe, clique em **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="5371c-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="5371c-188">Na lista suspensa Nome do método, clique em **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="5371c-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="5371c-189">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="5371c-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="5371c-190">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> permitirá que o **DeleteItem** botão sempre que o registro atual é alterado.</span><span class="sxs-lookup"><span data-stu-id="5371c-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="5371c-191">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5371c-191">Press F5 to run the application.</span></span> <span data-ttu-id="5371c-192">Observe que o **DeleteItem** botão será desabilitado e você não pode excluir itens, pressionando a tecla DELETE.</span><span class="sxs-lookup"><span data-stu-id="5371c-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="5371c-193">Adicionando funcionalidade de pesquisa ao controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="5371c-194">Esta etapa opcional, você implementa a capacidade de pesquisar um valor no <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5371c-195">Se a cadeia de caracteres de pesquisa for encontrada, o controle seleciona o item que contém o valor e rola o item na exibição.</span><span class="sxs-lookup"><span data-stu-id="5371c-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="5371c-196">Para adicionar a funcionalidade de pesquisa</span><span class="sxs-lookup"><span data-stu-id="5371c-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="5371c-197">Arraste uma <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5371c-198">Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="5371c-199">Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="5371c-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="5371c-200">Arraste uma <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="5371c-201">Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="5371c-202">Na janela Propriedades, altere o **nome** propriedade **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="5371c-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="5371c-203">Alterar o **texto** propriedade **pesquisa**.</span><span class="sxs-lookup"><span data-stu-id="5371c-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="5371c-204">Clique duas vezes o <xref:System.Windows.Forms.Button> para abrir o Editor de códigos de controle e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="5371c-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="5371c-205">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5371c-205">Press F5 to run the application.</span></span> <span data-ttu-id="5371c-206">Digite uma ID de cliente no **SearchTextBox** e clique no **pesquisa** botão.</span><span class="sxs-lookup"><span data-stu-id="5371c-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="5371c-207">Adicionando um mestre e a tabela de detalhes para DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="5371c-208">Esta etapa opcional, você adiciona um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para exibir os pedidos relacionados para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="5371c-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="5371c-209">Para adicionar uma tabela mestre e de detalhes</span><span class="sxs-lookup"><span data-stu-id="5371c-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="5371c-210">Arraste uma segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="5371c-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="5371c-211">Na janela Propriedades, defina as **local** propriedade `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="5371c-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="5371c-212">Defina as **tamanho** propriedade `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="5371c-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="5371c-213">No **fontes de dados** janela, expanda o **clientes** nó de tabela e selecione o nó de detalhe para o **pedidos** tabela.</span><span class="sxs-lookup"><span data-stu-id="5371c-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="5371c-214">Altere o tipo subjacente deste **pedidos** tabela detalhes clicando **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="5371c-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="5371c-215">Arraste esta **pedidos** nó da tabela para a área do modelo de item (região superior) do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="5371c-216">Uma **OrdersBindingSource** componente e uma **OrdersTableAdapter** componente é adicionado à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="5371c-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="5371c-217">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5371c-217">Press F5 to run the application.</span></span> <span data-ttu-id="5371c-218">Quando você seleciona cada cliente no primeiro <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar, os pedidos para aquele cliente são exibidos na segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="5371c-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5371c-219">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5371c-219">See Also</span></span>  
 [<span data-ttu-id="5371c-220">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-221">Como exibir dados associados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-222">Como exibir controles não associados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-223">Como alterar o layout de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-224">Como exibir cabeçalhos de item em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-225">Como pesquisar dados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-226">Como: criar um formulário mestre/detalhes usando dois controles DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="5371c-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="5371c-227">Como alterar a aparência de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="5371c-228">Como desabilitar a adição e a exclusão de itens DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="5371c-229">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="5371c-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
