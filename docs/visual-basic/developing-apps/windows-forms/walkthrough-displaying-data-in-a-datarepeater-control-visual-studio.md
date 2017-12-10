---
title: "Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: DataRepeater, walkthrough
ms.assetid: 65dcdb95-6c3e-47cc-987d-190000f71653
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 6f0cf690b816d57dc4a2646eb82d649727d033a9
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/09/2017
---
# <a name="walkthrough-displaying-data-in-a-datarepeater-control-visual-studio"></a><span data-ttu-id="1722f-102">Instruções passo a passo: exibindo dados em um controle DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1722f-102">Walkthrough: Displaying Data in a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="1722f-103">Este passo a passo fornece um cenário básico do início ao fim para exibir dados associados em um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-103">This walkthrough provides a basic start-to-finish scenario for displaying bound data in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="prerequisite"></a><span data-ttu-id="1722f-104">Pré-requisito</span><span class="sxs-lookup"><span data-stu-id="1722f-104">Prerequisite</span></span>  
 <span data-ttu-id="1722f-105">Este passo a passo requer o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="1722f-105">This walkthrough requires the Northwind sample database.</span></span>  
  
 <span data-ttu-id="1722f-106">Se você não tiver esse banco de dados no computador de desenvolvimento, você pode baixá-lo do [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span><span class="sxs-lookup"><span data-stu-id="1722f-106">If you do not have this database on your development computer, you can download it from the [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=98088).</span></span> <span data-ttu-id="1722f-107">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="1722f-107">For instructions, see [Downloading Sample Databases](../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="1722f-108">Visão Geral</span><span class="sxs-lookup"><span data-stu-id="1722f-108">Overview</span></span>  
 <span data-ttu-id="1722f-109">A primeira parte deste passo a passo consiste em quatro tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="1722f-109">The first part of this walkthrough consists of four main tasks:</span></span>  
  
-   <span data-ttu-id="1722f-110">Criando uma solução.</span><span class="sxs-lookup"><span data-stu-id="1722f-110">Creating a solution.</span></span>  
  
-   <span data-ttu-id="1722f-111">Adicionando um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-111">Adding a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="1722f-112">Adicionando uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1722f-112">Adding a data source.</span></span>  
  
-   <span data-ttu-id="1722f-113">Adicionando controles associados a dados.</span><span class="sxs-lookup"><span data-stu-id="1722f-113">Adding data-bound controls.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="creating-a-datarepeater-solution"></a><span data-ttu-id="1722f-114">Criando uma solução DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-114">Creating a DataRepeater Solution</span></span>  
 <span data-ttu-id="1722f-115">Na primeira etapa, você pode criar um projeto e solução.</span><span class="sxs-lookup"><span data-stu-id="1722f-115">In the first step, you create a project and solution.</span></span>  
  
#### <a name="to-create-a-datarepeater-solution"></a><span data-ttu-id="1722f-116">Para criar uma solução DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-116">To create a DataRepeater solution</span></span>  
  
1.  <span data-ttu-id="1722f-117">No Visual Studio **arquivo** menu, clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="1722f-117">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="1722f-118">No **tipos de projeto** painel o **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**e, em seguida, clique em **Windows**.</span><span class="sxs-lookup"><span data-stu-id="1722f-118">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="1722f-119">No **modelos** painel, clique em **aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="1722f-119">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="1722f-120">Na caixa **Nome**, digite `DataRepeaterApp`.</span><span class="sxs-lookup"><span data-stu-id="1722f-120">In the **Name** box, type `DataRepeaterApp`.</span></span>  
  
5.  <span data-ttu-id="1722f-121">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="1722f-121">Click **OK**.</span></span>  
  
     <span data-ttu-id="1722f-122">O Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="1722f-122">The Windows Forms Designer opens.</span></span>  
  
6.  <span data-ttu-id="1722f-123">Selecione o formulário no Designer de formulários do Windows.</span><span class="sxs-lookup"><span data-stu-id="1722f-123">Select the form in the Windows Forms Designer.</span></span> <span data-ttu-id="1722f-124">No **propriedades** janela, defina o **tamanho** propriedade `800, 700`.</span><span class="sxs-lookup"><span data-stu-id="1722f-124">In the **Properties** window, set the **Size** property to `800, 700`.</span></span>  
  
## <a name="adding-a-datarepeater-control"></a><span data-ttu-id="1722f-125">Adicionando um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-125">Adding a DataRepeater Control</span></span>  
 <span data-ttu-id="1722f-126">Nesta etapa, você adiciona um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle no formulário.</span><span class="sxs-lookup"><span data-stu-id="1722f-126">In this step, you add a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to the form.</span></span>  
  
#### <a name="to-add-a-datarepeater-control"></a><span data-ttu-id="1722f-127">Para adicionar um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-127">To add a DataRepeater control</span></span>  
  
1.  <span data-ttu-id="1722f-128">Sobre o **exibição** menu, clique em **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="1722f-128">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="1722f-129">O **caixa de ferramentas** é aberto.</span><span class="sxs-lookup"><span data-stu-id="1722f-129">The **Toolbox** opens.</span></span>  
  
2.  <span data-ttu-id="1722f-130">Selecione o **Visual Basic PowerPacks** guia.</span><span class="sxs-lookup"><span data-stu-id="1722f-130">Select the **Visual Basic PowerPacks** tab.</span></span>  
  
3.  <span data-ttu-id="1722f-131">Arraste um <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para **Form1**.</span><span class="sxs-lookup"><span data-stu-id="1722f-131">Drag a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control onto **Form1**.</span></span>  
  
4.  <span data-ttu-id="1722f-132">Na janela Propriedades, defina o **local** propriedade `0, 25`.</span><span class="sxs-lookup"><span data-stu-id="1722f-132">In the Properties window, set the **Location** property to `0, 25`.</span></span>  
  
5.  <span data-ttu-id="1722f-133">Definir o **tamanho** propriedade `460, 600`.</span><span class="sxs-lookup"><span data-stu-id="1722f-133">Set the **Size** property to `460, 600`.</span></span>  
  
## <a name="adding-a-data-source"></a><span data-ttu-id="1722f-134">Adicionando uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="1722f-134">Adding a Data Source</span></span>  
 <span data-ttu-id="1722f-135">Nesta etapa, você adiciona uma fonte de dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-135">In this step, you add a data source for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-add-a-data-source"></a><span data-ttu-id="1722f-136">Para adicionar uma fonte de dados</span><span class="sxs-lookup"><span data-stu-id="1722f-136">To add a data source</span></span>  
  
1.  <span data-ttu-id="1722f-137">Sobre o **dados** menu, clique em **Mostrar fontes de dados**.</span><span class="sxs-lookup"><span data-stu-id="1722f-137">On the **Data** menu, click **Show Data Sources**.</span></span>  
  
2.  <span data-ttu-id="1722f-138">No **fontes de dados** janela, clique em **adicionar nova fonte de dados**.</span><span class="sxs-lookup"><span data-stu-id="1722f-138">In the **Data Sources** window, click **Add New Data Source**.</span></span>  
  
3.  <span data-ttu-id="1722f-139">Selecione **banco de dados** no **escolher um tipo de fonte de dados** página e, em seguida, clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="1722f-139">Select **Database** on the **Choose a Data Source Type** page, and then click **Next**.</span></span>  
  
4.  <span data-ttu-id="1722f-140">Sobre o **escolha sua Conexão de dados** página, execute uma das seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="1722f-140">On the **Choose Your Data Connection** page, perform one of the following steps:</span></span>  
  
    -   <span data-ttu-id="1722f-141">Se uma conexão de dados com o banco de dados de exemplo Northwind estiver disponível na lista suspensa, clique nela.</span><span class="sxs-lookup"><span data-stu-id="1722f-141">If a data connection to the Northwind sample database is available in the drop-down list, click it.</span></span>  
  
         <span data-ttu-id="1722f-142">-ou-</span><span class="sxs-lookup"><span data-stu-id="1722f-142">-or-</span></span>  
  
    -   <span data-ttu-id="1722f-143">Clique em **nova Conexão** para configurar uma nova conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="1722f-143">Click **New Connection** to configure a new data connection.</span></span> <span data-ttu-id="1722f-144">Para obter mais informações, consulte [como: criar conexões com bancos de dados do SQL Server](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span><span class="sxs-lookup"><span data-stu-id="1722f-144">For more information, see [How to: Create Connections to SQL Server Databases](http://msdn.microsoft.com/en-us/360c340d-e5a6-4a7e-a569-e95d500be43d).</span></span>  
  
5.  <span data-ttu-id="1722f-145">Se o banco de dados exigir uma senha, selecione a opção para incluir dados confidenciais e, em seguida, clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="1722f-145">If the database requires a password, select the option to include sensitive data, and then click **Next**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="1722f-146">Se uma caixa de diálogo for exibida, clique em **Sim** para salvar o arquivo ao seu projeto.</span><span class="sxs-lookup"><span data-stu-id="1722f-146">If a dialog box appears, click **Yes** to save the file to your project.</span></span>  
  
6.  <span data-ttu-id="1722f-147">Clique em **próximo** no **Salvar cadeia de caracteres de Conexão para o arquivo de configuração de aplicativo** página.</span><span class="sxs-lookup"><span data-stu-id="1722f-147">Click **Next** on the **Save Connection String to the Application Configuration file** page.</span></span>  
  
7.  <span data-ttu-id="1722f-148">Expanda o **tabelas** nó sob o **escolher seus objetos de banco de dados** página.</span><span class="sxs-lookup"><span data-stu-id="1722f-148">Expand the **Tables** node on the **Choose Your Database Objects** page.</span></span>  
  
8.  <span data-ttu-id="1722f-149">Marque as caixas de seleção ao lado de **clientes** e **pedidos** tabelas e depois clique em **concluir**.</span><span class="sxs-lookup"><span data-stu-id="1722f-149">Select the check boxes next to the **Customers** and **Orders** tables, and then click **Finish**.</span></span>  
  
     <span data-ttu-id="1722f-150">**NorthwindDataSet** é adicionado ao seu projeto e o **clientes** e **pedidos** as tabelas aparecem no **fontes de dados** janela.</span><span class="sxs-lookup"><span data-stu-id="1722f-150">**NorthwindDataSet** is added to your project and the **Customers** and **Orders** tables appear in the **Data Sources** window.</span></span>  
  
## <a name="adding-data-bound-controls"></a><span data-ttu-id="1722f-151">Adicionando controles associados a dados</span><span class="sxs-lookup"><span data-stu-id="1722f-151">Adding Data-Bound Controls</span></span>  
 <span data-ttu-id="1722f-152">Nesta etapa, você adicionar controles associados a dados para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span><span class="sxs-lookup"><span data-stu-id="1722f-152">In this step, you add data-bound controls to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>.</span></span>  
  
#### <a name="to-add-data-bound-controls"></a><span data-ttu-id="1722f-153">Para adicionar controles de associação de dados</span><span class="sxs-lookup"><span data-stu-id="1722f-153">To add data-bound controls</span></span>  
  
1.  <span data-ttu-id="1722f-154">No **fontes de dados** janela, selecione o nó de nível superior para o **clientes** tabela.</span><span class="sxs-lookup"><span data-stu-id="1722f-154">In the **Data Sources** window, select the top-level node for the **Customers** table.</span></span>  
  
2.  <span data-ttu-id="1722f-155">Altere o tipo subjacente da tabela para **detalhes** clicando **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="1722f-155">Change the drop type of the table to **Details** by clicking **Details** in the drop-down list on the table node.</span></span>  
  
3.  <span data-ttu-id="1722f-156">Selecione o **clientes** nó da tabela e arraste-o para a região de modelo de item (região superior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-156">Select the **Customers** table node and drag it onto the item template region (the upper region) of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1722f-157">Um <xref:System.Windows.Forms.BindingNavigator> controle é adicionado ao formulário e o **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**,  **TableAdapterManager**, e **CustomersBindingNavigator** componentes são adicionados à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="1722f-157">A <xref:System.Windows.Forms.BindingNavigator> control is added to the form, and the **NorthwindDataSet**, **CustomersBindingSource**, **CustomersTableAdapter**, **TableAdapterManager**, and **CustomersBindingNavigator** components are added to the Component Tray.</span></span>  
  
4.  <span data-ttu-id="1722f-158">Selecione todos os campos e seus rótulos associados e posicioná-los próximo à borda esquerda da região de modelo de item.</span><span class="sxs-lookup"><span data-stu-id="1722f-158">Select all of the fields and their associated labels and position them near the left edge of the item template region.</span></span>  
  
5.  <span data-ttu-id="1722f-159">Selecione os últimos cinco campos (**região**, **CEP**, **país**, **Phone**, e **Fax**) e os rótulos associados e movê-los até e à direita dos seis primeiros campos.</span><span class="sxs-lookup"><span data-stu-id="1722f-159">Select the last five fields (**Region**, **Postal Code**, **Country**, **Phone**, and **Fax**) and their associated labels and move them up and to the right of the first six fields.</span></span>  
  
6.  <span data-ttu-id="1722f-160">Selecione o modelo de item (região superior do controle).</span><span class="sxs-lookup"><span data-stu-id="1722f-160">Select the item template (the upper region of the control).</span></span>  
  
7.  <span data-ttu-id="1722f-161">Na janela Propriedades, defina o **tamanho** propriedade `427, 170`.</span><span class="sxs-lookup"><span data-stu-id="1722f-161">In the Properties window, set the **Size** property to `427, 170`.</span></span>  
  
 <span data-ttu-id="1722f-162">Neste ponto, você tem um aplicativo de trabalho que será exibida uma lista de repetição de clientes.</span><span class="sxs-lookup"><span data-stu-id="1722f-162">At this point, you have a working application that will display a repeating list of customers.</span></span> <span data-ttu-id="1722f-163">Você pode pressionar F5 para executar o aplicativo, alterar os dados e adicionar ou excluir registros de clientes.</span><span class="sxs-lookup"><span data-stu-id="1722f-163">You can press F5 to run the application, change the data, and add or delete customer records.</span></span>  
  
 <span data-ttu-id="1722f-164">As próximas etapas opcionais, você aprenderá a personalizar o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-164">In the next optional steps, you will learn how to customize the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="next-steps-optional"></a><span data-ttu-id="1722f-165">Próximas etapas (opcionais)</span><span class="sxs-lookup"><span data-stu-id="1722f-165">Next Steps (Optional)</span></span>  
 <span data-ttu-id="1722f-166">Esta parte do passo a passo consiste em quatro tarefas opcionais:</span><span class="sxs-lookup"><span data-stu-id="1722f-166">This part of the walkthrough consists of four optional tasks:</span></span>  
  
-   <span data-ttu-id="1722f-167">Alterando a aparência do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-167">Changing the appearance of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="1722f-168">Impedindo que os usuários adicionem ou excluam registros.</span><span class="sxs-lookup"><span data-stu-id="1722f-168">Preventing users from adding or deleting records.</span></span>  
  
-   <span data-ttu-id="1722f-169">Adicionando funcionalidade de pesquisa para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-169">Adding search capability to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
-   <span data-ttu-id="1722f-170">Adicionando uma tabela mestre e de detalhes para o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-170">Adding a master and detail table to the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="changing-the-appearance-of-the-datarepeater-control"></a><span data-ttu-id="1722f-171">Alterando a aparência do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-171">Changing the Appearance of the DataRepeater Control</span></span>  
 <span data-ttu-id="1722f-172">Nesta etapa opcional, você deve alterar o `BackColor` do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle em tempo de design.</span><span class="sxs-lookup"><span data-stu-id="1722f-172">In this optional step, you change the `BackColor` of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time.</span></span> <span data-ttu-id="1722f-173">Você também adicionar código para exibir linhas alternando as cores e para alterar um rótulo `ForeColor` condicionalmente.</span><span class="sxs-lookup"><span data-stu-id="1722f-173">You also add code to display rows in alternating colors and to change a label's `ForeColor` conditionally.</span></span>  
  
#### <a name="to-change-the-appearance-of-the-control"></a><span data-ttu-id="1722f-174">Para alterar a aparência do controle</span><span class="sxs-lookup"><span data-stu-id="1722f-174">To change the appearance of the control</span></span>  
  
1.  <span data-ttu-id="1722f-175">No Designer de formulários do Windows, selecione a região principal (inferior) do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-175">In the Windows Forms Designer, select the main (lower) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="1722f-176">Na janela Propriedades, defina o `BackColor` propriedade em branco.</span><span class="sxs-lookup"><span data-stu-id="1722f-176">In the Properties window, set the `BackColor` property to white.</span></span>  
  
3.  <span data-ttu-id="1722f-177">Clique duas vezes o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> para abrir o Editor de código.</span><span class="sxs-lookup"><span data-stu-id="1722f-177">Double-click the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> to open the Code Editor.</span></span>  
  
4.  <span data-ttu-id="1722f-178">No Editor de códigos, lista suspensa de eventos, clique em **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="1722f-178">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
5.  <span data-ttu-id="1722f-179">No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o seguinte código para alternar o `BackColor`:</span><span class="sxs-lookup"><span data-stu-id="1722f-179">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to alternate the `BackColor`:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_1.vb)]  
  
6.  <span data-ttu-id="1722f-180">No <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> manipulador de eventos, adicione o código a seguir para alterar o `ForeColor` de um rótulo, dependendo de uma condição:</span><span class="sxs-lookup"><span data-stu-id="1722f-180">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add the following code to change the `ForeColor` of a label depending on a condition:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_2.vb)]  
  
7.  <span data-ttu-id="1722f-181">Pressione F5 para executar o aplicativo e ver as personalizações.</span><span class="sxs-lookup"><span data-stu-id="1722f-181">Press F5 to run the application and see the customizations.</span></span>  
  
## <a name="preventing-users-from-adding-or-deleting-records"></a><span data-ttu-id="1722f-182">Impedindo que os usuários adicionem ou excluam registros</span><span class="sxs-lookup"><span data-stu-id="1722f-182">Preventing Users from Adding or Deleting Records</span></span>  
 <span data-ttu-id="1722f-183">Nesta etapa opcional, você adiciona o código que impede que os usuários adicionem ou excluam registros de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-183">In this optional step, you add code that prevents users from adding or deleting records in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
#### <a name="to-prevent-users-from-adding-and-deleting-records"></a><span data-ttu-id="1722f-184">Para impedir que os usuários adicionando e excluindo registros</span><span class="sxs-lookup"><span data-stu-id="1722f-184">To prevent users from adding and deleting records</span></span>  
  
1.  <span data-ttu-id="1722f-185">No Designer de formulários do Windows, clique duas vezes no formulário para abrir o Editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="1722f-185">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="1722f-186">Adicione o seguinte código para o `Form_Load` evento:</span><span class="sxs-lookup"><span data-stu-id="1722f-186">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#3](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_3.vb)]  
  
3.  <span data-ttu-id="1722f-187">Na lista suspensa Nome da classe, clique em **BindingNavigatorDeleteItem**.</span><span class="sxs-lookup"><span data-stu-id="1722f-187">In the Class Name drop-down list, click **BindingNavigatorDeleteItem**.</span></span> <span data-ttu-id="1722f-188">Na lista suspensa o nome do método, clique em **EnabledChanged**.</span><span class="sxs-lookup"><span data-stu-id="1722f-188">In the Method Name drop-down list, click **EnabledChanged**.</span></span>  
  
4.  <span data-ttu-id="1722f-189">Adicione o seguinte código ao manipulador de eventos do `BindingNavigatorDeleteItem_EnabledChanged`:</span><span class="sxs-lookup"><span data-stu-id="1722f-189">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#4](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_4.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="1722f-190">Essa etapa é necessária porque o <xref:System.Windows.Forms.BindingSource> habilitará o **DeleteItem** botão toda vez que o registro atual é alterado.</span><span class="sxs-lookup"><span data-stu-id="1722f-190">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
5.  <span data-ttu-id="1722f-191">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1722f-191">Press F5 to run the application.</span></span> <span data-ttu-id="1722f-192">Observe que o **DeleteItem** botão será desabilitado e você não pode excluir itens, pressionando a tecla DELETE.</span><span class="sxs-lookup"><span data-stu-id="1722f-192">Notice that the **DeleteItem** button is disabled and that you cannot delete items by pressing the DELETE key.</span></span>  
  
## <a name="adding-search-capability-to-the-datarepeater-control"></a><span data-ttu-id="1722f-193">Adicionando funcionalidade de pesquisa ao controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-193">Adding Search Capability to the DataRepeater Control</span></span>  
 <span data-ttu-id="1722f-194">Nesta etapa opcional, você implementar a capacidade de pesquisar para um valor de <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-194">In this optional step, you implement the capability to search for a value in the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1722f-195">Se a cadeia de caracteres for encontrada, o controle seleciona o item que contém o valor e o item é movido para a exibição.</span><span class="sxs-lookup"><span data-stu-id="1722f-195">If the search string is found, the control selects the item that contains the value and scrolls the item into view.</span></span>  
  
#### <a name="to-add-search-capability"></a><span data-ttu-id="1722f-196">Para adicionar a funcionalidade de pesquisa</span><span class="sxs-lookup"><span data-stu-id="1722f-196">To add search capability</span></span>  
  
1.  <span data-ttu-id="1722f-197">Arraste um <xref:System.Windows.Forms.TextBox> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-197">Drag a <xref:System.Windows.Forms.TextBox> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1722f-198">Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-198">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="1722f-199">Na janela Propriedades, altere o **nome** propriedade **SearchTextBox**.</span><span class="sxs-lookup"><span data-stu-id="1722f-199">In the Properties window, change the **Name** property to **SearchTextBox**.</span></span>  
  
3.  <span data-ttu-id="1722f-200">Arraste um <xref:System.Windows.Forms.Button> controlar do **caixa de ferramentas** para o formulário que contém o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-200">Drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the form that contains the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="1722f-201">Posicione-o sob o <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-201">Position it under the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
4.  <span data-ttu-id="1722f-202">Na janela Propriedades, altere o **nome** propriedade **SearchButton**.</span><span class="sxs-lookup"><span data-stu-id="1722f-202">In the Properties window, change the **Name** property to **SearchButton**.</span></span> <span data-ttu-id="1722f-203">Alterar o **texto** propriedade **pesquisa**.</span><span class="sxs-lookup"><span data-stu-id="1722f-203">Change the **Text** property to **Search**.</span></span>  
  
5.  <span data-ttu-id="1722f-204">Clique duas vezes o <xref:System.Windows.Forms.Button> de controle para abrir o Editor de código e adicione o seguinte código para o `SearchButton_Click` manipulador de eventos.</span><span class="sxs-lookup"><span data-stu-id="1722f-204">Double-click the <xref:System.Windows.Forms.Button> control to open the Code Editor, and add the following code to the `SearchButton_Click` event handler.</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.cs)]
     [!code-vb[VbPowerPacksDataRepeaterWalkthrough#5](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/walkthrough-displaying-data-in-a-datarepeater-control-visual-studio_5.vb)]  
  
6.  <span data-ttu-id="1722f-205">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1722f-205">Press F5 to run the application.</span></span> <span data-ttu-id="1722f-206">Digite uma ID de cliente **SearchTextBox** e clique no **pesquisa** botão.</span><span class="sxs-lookup"><span data-stu-id="1722f-206">Type a customer ID in **SearchTextBox** and click the **Search** button.</span></span>  
  
## <a name="adding-a-master-and-detail-table-to-the-datarepeater"></a><span data-ttu-id="1722f-207">Adicionando um mestre e a tabela de detalhes para DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-207">Adding a Master and Detail Table to the DataRepeater</span></span>  
 <span data-ttu-id="1722f-208">Nesta etapa opcional, você pode adicionar um segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle para exibir os pedidos relacionados para cada cliente.</span><span class="sxs-lookup"><span data-stu-id="1722f-208">In this optional step, you add a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control to display related orders for each customer.</span></span>  
  
#### <a name="to-add-a-master-and-detail-table"></a><span data-ttu-id="1722f-209">Para adicionar uma tabela mestre e de detalhes</span><span class="sxs-lookup"><span data-stu-id="1722f-209">To add a master and detail table</span></span>  
  
1.  <span data-ttu-id="1722f-210">Arraste uma segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar do **Visual Basic PowerPacks** guia o **caixa de ferramentas** para o formulário.</span><span class="sxs-lookup"><span data-stu-id="1722f-210">Drag a second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control from the **Visual Basic PowerPacks** tab in the **Toolbox** onto the form.</span></span>  
  
2.  <span data-ttu-id="1722f-211">Na janela Propriedades, defina o **local** propriedade `465, 25`.</span><span class="sxs-lookup"><span data-stu-id="1722f-211">In the Properties window, set the **Location** property to `465, 25`.</span></span>  
  
3.  <span data-ttu-id="1722f-212">Definir o **tamanho** propriedade `315, 600`.</span><span class="sxs-lookup"><span data-stu-id="1722f-212">Set the **Size** property to `315, 600`.</span></span>  
  
4.  <span data-ttu-id="1722f-213">No **fontes de dados** janela, expanda o **clientes** nó de tabela e selecione o nó de detalhe para o **pedidos** tabela.</span><span class="sxs-lookup"><span data-stu-id="1722f-213">In the **Data Sources** window, expand the **Customers** table node and select the detail node for the **Orders** table.</span></span>  
  
5.  <span data-ttu-id="1722f-214">Altere o tipo subjacente desse **pedidos** tabela detalhes clicando **detalhes** na lista suspensa no nó da tabela.</span><span class="sxs-lookup"><span data-stu-id="1722f-214">Change the drop type of this **Orders** table to Details by clicking **Details** in the drop-down list on the table node.</span></span>  
  
6.  <span data-ttu-id="1722f-215">Arraste esta **pedidos** nó de tabela para a área do modelo de item (região superior) do segundo <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-215">Drag this **Orders** table node onto the item template region (the upper region) of the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
     <span data-ttu-id="1722f-216">Um **OrdersBindingSource** componente e um **OrdersTableAdapter** componente são adicionados à bandeja de componentes.</span><span class="sxs-lookup"><span data-stu-id="1722f-216">An **OrdersBindingSource** component and an **OrdersTableAdapter** component are added to the Component Tray.</span></span>  
  
7.  <span data-ttu-id="1722f-217">Pressione F5 para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1722f-217">Press F5 to run the application.</span></span> <span data-ttu-id="1722f-218">Quando você seleciona cada cliente na primeira <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controlar os pedidos de cliente são exibidas na segunda <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> controle.</span><span class="sxs-lookup"><span data-stu-id="1722f-218">When you select each customer in the first <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control, the orders for that customer are displayed in the second <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1722f-219">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1722f-219">See Also</span></span>  
 [<span data-ttu-id="1722f-220">Introdução ao Controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-220">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-221">Como exibir dados associados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-221">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-222">Como exibir controles não associados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-222">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-223">Como alterar o layout de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-223">How to: Change the Layout of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-layout-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-224">Como exibir cabeçalhos de item em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-224">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-225">Como pesquisar dados em um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-225">How to: Search Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-search-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-226">Como: criar um formulário mestre/detalhado usando dois controles DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="1722f-226">How to: Create a Master/Detail Form by Using Two DataRepeater Controls (Visual Studio)</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [<span data-ttu-id="1722f-227">Como alterar a aparência de um controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-227">How to: Change the Appearance of a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="1722f-228">Como desabilitar a adição e a exclusão de itens DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-228">How to: Disable Adding and Deleting DataRepeater Items</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio.md)  
 [<span data-ttu-id="1722f-229">Solução de problemas do controle DataRepeater</span><span class="sxs-lookup"><span data-stu-id="1722f-229">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
