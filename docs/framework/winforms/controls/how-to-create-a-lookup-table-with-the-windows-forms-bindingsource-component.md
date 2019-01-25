---
title: 'Como: Criar uma tabela de pesquisa com o componente BindingSource dos Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- lookup tables
- tables [Windows Forms], creating lookup tables
- BindingSource component [Windows Forms], creating a lookup table
- BindingSource component [Windows Forms], examples
ms.assetid: 622fce80-879d-44be-abbf-8350ec22ca2b
ms.openlocfilehash: 79459364fba51e8e10194a5e3681d6384beb16a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54539890"
---
# <a name="how-to-create-a-lookup-table-with-the-windows-forms-bindingsource-component"></a><span data-ttu-id="1b9ac-102">Como: Criar uma tabela de pesquisa com o componente BindingSource dos Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1b9ac-102">How to: Create a Lookup Table with the Windows Forms BindingSource Component</span></span>
<span data-ttu-id="1b9ac-103">A tabela de pesquisa é uma tabela de dados que tem uma coluna que exibe dados de registros em uma tabela relacionada.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-103">A lookup table is a table of data that has a column that displays data from records in a related table.</span></span> <span data-ttu-id="1b9ac-104">Nos procedimentos a seguir, um controle <xref:System.Windows.Forms.ComboBox> é usado para exibir o campo com a relação de chave estrangeira da tabela pai para a tabela filho.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-104">In the following procedures, a <xref:System.Windows.Forms.ComboBox> control is used to display the field with the foreign-key relationship from the parent to the child table.</span></span>  
  
 <span data-ttu-id="1b9ac-105">Para ajudar a visualizar essas duas tabelas e essa relação, veja a seguir um exemplo de uma tabela pai e filho:</span><span class="sxs-lookup"><span data-stu-id="1b9ac-105">To help visualize these two tables and this relationship, here is an example of a parent and child table:</span></span>  
  
 <span data-ttu-id="1b9ac-106">CustomersTable (tabela pai)</span><span class="sxs-lookup"><span data-stu-id="1b9ac-106">CustomersTable (parent table)</span></span>  
  
|<span data-ttu-id="1b9ac-107">CustomerID</span><span class="sxs-lookup"><span data-stu-id="1b9ac-107">CustomerID</span></span>|<span data-ttu-id="1b9ac-108">CustomerName</span><span class="sxs-lookup"><span data-stu-id="1b9ac-108">CustomerName</span></span>|  
|----------------|------------------|  
|<span data-ttu-id="1b9ac-109">712</span><span class="sxs-lookup"><span data-stu-id="1b9ac-109">712</span></span>|<span data-ttu-id="1b9ac-110">Paul Koch</span><span class="sxs-lookup"><span data-stu-id="1b9ac-110">Paul Koch</span></span>|  
|<span data-ttu-id="1b9ac-111">713</span><span class="sxs-lookup"><span data-stu-id="1b9ac-111">713</span></span>|<span data-ttu-id="1b9ac-112">Tamara Johnston</span><span class="sxs-lookup"><span data-stu-id="1b9ac-112">Tamara Johnston</span></span>|  
  
 <span data-ttu-id="1b9ac-113">OrdersTable (tabela filho)</span><span class="sxs-lookup"><span data-stu-id="1b9ac-113">OrdersTable (child table)</span></span>  
  
|<span data-ttu-id="1b9ac-114">OrderID</span><span class="sxs-lookup"><span data-stu-id="1b9ac-114">OrderID</span></span>|<span data-ttu-id="1b9ac-115">OrderDate</span><span class="sxs-lookup"><span data-stu-id="1b9ac-115">OrderDate</span></span>|<span data-ttu-id="1b9ac-116">CustomerID</span><span class="sxs-lookup"><span data-stu-id="1b9ac-116">CustomerID</span></span>|  
|-------------|---------------|----------------|  
|<span data-ttu-id="1b9ac-117">903</span><span class="sxs-lookup"><span data-stu-id="1b9ac-117">903</span></span>|<span data-ttu-id="1b9ac-118">12.02.04</span><span class="sxs-lookup"><span data-stu-id="1b9ac-118">February 12, 2004</span></span>|<span data-ttu-id="1b9ac-119">712</span><span class="sxs-lookup"><span data-stu-id="1b9ac-119">712</span></span>|  
|<span data-ttu-id="1b9ac-120">904</span><span class="sxs-lookup"><span data-stu-id="1b9ac-120">904</span></span>|<span data-ttu-id="1b9ac-121">13.02.04</span><span class="sxs-lookup"><span data-stu-id="1b9ac-121">February 13, 2004</span></span>|<span data-ttu-id="1b9ac-122">713</span><span class="sxs-lookup"><span data-stu-id="1b9ac-122">713</span></span>|  
  
 <span data-ttu-id="1b9ac-123">Neste cenário, uma tabela, CustomersTable, armazena a informação real que você deseja exibir e salvar.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-123">In this scenario, one table, CustomersTable, stores the actual information you want to display and save.</span></span> <span data-ttu-id="1b9ac-124">Mas, para economizar espaço, a tabela deixa de fora dados que adicionam clareza.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-124">But to save space, the table leaves out data that adds clarity.</span></span> <span data-ttu-id="1b9ac-125">A outra tabela, OrdersTable, contém apenas informações relacionadas à aparência sobre qual número da ID do cliente é equivalente a qual data de pedido e ID do pedido.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-125">The other table, OrdersTable, contains only appearance-related information about which customer ID number is equivalent to which order date and order ID.</span></span> <span data-ttu-id="1b9ac-126">Não há nenhuma menção dos nomes dos clientes.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-126">There is no mention of the customers' names.</span></span>  
  
 <span data-ttu-id="1b9ac-127">Quatro propriedades importantes são definidas no [Controle ComboBox](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) para criar a tabela de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-127">Four important properties are set on the [ComboBox Control](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md) control to create the lookup table.</span></span>  
  
-   <span data-ttu-id="1b9ac-128">A propriedade <xref:System.Windows.Forms.ComboBox.DataSource%2A> contém o nome da tabela.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-128">The <xref:System.Windows.Forms.ComboBox.DataSource%2A> property contains the name of the table.</span></span>  
  
-   <span data-ttu-id="1b9ac-129">A propriedade <xref:System.Windows.Forms.ListControl.DisplayMember%2A> contém a coluna de dados da tabela que você deseja exibir para o texto de controle (nome do cliente).</span><span class="sxs-lookup"><span data-stu-id="1b9ac-129">The <xref:System.Windows.Forms.ListControl.DisplayMember%2A> property contains the data column of that table that you want to display for the control text (the customer's name).</span></span>  
  
-   <span data-ttu-id="1b9ac-130">A propriedade <xref:System.Windows.Forms.ListControl.ValueMember%2A> contém a coluna de dados dessa tabela com as informações armazenadas (o número de ID na tabela pai).</span><span class="sxs-lookup"><span data-stu-id="1b9ac-130">The <xref:System.Windows.Forms.ListControl.ValueMember%2A> property contains the data column of that table with the stored information (the ID number in the parent table).</span></span>  
  
-   <span data-ttu-id="1b9ac-131">A propriedade <xref:System.Windows.Forms.ListControl.SelectedValue%2A> fornece o valor de pesquisa da tabela filho, com base no <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-131">The <xref:System.Windows.Forms.ListControl.SelectedValue%2A> property provides the lookup value for the child table, based on the <xref:System.Windows.Forms.ListControl.ValueMember%2A>.</span></span>  
  
 <span data-ttu-id="1b9ac-132">Os procedimentos a seguir mostram como dispor um formulário como uma tabela de pesquisa e vincular dados aos controles nele.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-132">The procedures below show you how to lay out your form as a lookup table and bind data to the controls on it.</span></span> <span data-ttu-id="1b9ac-133">Para concluir com êxito os procedimentos, você deve ter uma fonte de dados com as tabelas pai e filho que tenham uma relação de chave estrangeira, como mencionado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-133">To successfully complete the procedures, you must have a data source with parent and child tables that have a foreign-key relationship, as mentioned previously.</span></span>  
  
### <a name="to-create-the-user-interface"></a><span data-ttu-id="1b9ac-134">Para criar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="1b9ac-134">To create the user interface</span></span>  
  
1.  <span data-ttu-id="1b9ac-135">Dos **caixa de ferramentas**, arraste um <xref:System.Windows.Forms.ComboBox> controle para o formulário.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-135">From the **ToolBox**, drag a <xref:System.Windows.Forms.ComboBox> control onto the form.</span></span>  
  
     <span data-ttu-id="1b9ac-136">Esse controle exibirá a coluna da tabela pai.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-136">This control will display the column from parent table.</span></span>  
  
2.  <span data-ttu-id="1b9ac-137">Arraste outros controles para exibir detalhes da tabela filho.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-137">Drag other controls to display details from the child table.</span></span> <span data-ttu-id="1b9ac-138">O formato dos dados na tabela deve determinar quais controles você escolhe.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-138">The format of the data in the table should determine which controls you choose.</span></span> <span data-ttu-id="1b9ac-139">Para obter mais informações, consulte [Controles dos Windows Forms por função](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span><span class="sxs-lookup"><span data-stu-id="1b9ac-139">For more information, see [Windows Forms Controls by Function](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md).</span></span>  
  
3.  <span data-ttu-id="1b9ac-140">Arraste um controle <xref:System.Windows.Forms.BindingNavigator> para o formulário; isso permitirá que você navegue os dados na tabela filho.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-140">Drag a <xref:System.Windows.Forms.BindingNavigator> control onto the form; this will allow you to navigate the data in the child table.</span></span>  
  
### <a name="to-connect-to-the-data-and-bind-it-to-controls"></a><span data-ttu-id="1b9ac-141">Para conectar-se aos dados e vinculá-lo aos controles</span><span class="sxs-lookup"><span data-stu-id="1b9ac-141">To connect to the data and bind it to controls</span></span>  
  
1.  <span data-ttu-id="1b9ac-142">Selecione o <xref:System.Windows.Forms.ComboBox> e clique no glifo da Tarefa Inteligente para exibir a caixa de diálogo Tarefa Inteligente.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-142">Select the <xref:System.Windows.Forms.ComboBox> and click the Smart Task glyph to display the Smart Task dialog box.</span></span>  
  
2.  <span data-ttu-id="1b9ac-143">Selecione **Usar itens vinculados aos dados**.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-143">Select **Use data bound items**.</span></span>  
  
3.  <span data-ttu-id="1b9ac-144">Clique na seta ao lado da caixa suspensa **Fonte de Dados**.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-144">Click the arrow next to the **Data Source** drop-down box.</span></span> <span data-ttu-id="1b9ac-145">Se uma fonte de dados foi configurada anteriormente para o projeto ou formulário, ela aparecerá; caso contrário, siga as seguintes etapas (Este exemplo usa as tabelas Clientes e Pedidos do banco de dados de amostra Northwind e refere-se a elas nos parênteses).</span><span class="sxs-lookup"><span data-stu-id="1b9ac-145">If a data source has previously been configured for the project or form, it will appear; otherwise, complete the following steps (This example uses the Customers and Orders tables of the Northwind sample database and refers to them in parentheses).</span></span>  
  
    1.  <span data-ttu-id="1b9ac-146">Clique em **Adicionar Fonte de Dados do Projeto** para conectar-se aos dados e criar uma fonte de dados.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-146">Click **Add Project Data Source** to connect to data and create a data source.</span></span>  
  
    2.  <span data-ttu-id="1b9ac-147">Na página de boas-vindas do **Assistente de Configuração de Fonte de Dados**, clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-147">On the **Data Source Configuration Wizard** welcome page, click **Next**.</span></span>  
  
    3.  <span data-ttu-id="1b9ac-148">Selecione **Banco de dados** na página **Escolher um tipo de fonte de dados**.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-148">Select **Database** on the **Choose a Data Source Type** page.</span></span>  
  
    4.  <span data-ttu-id="1b9ac-149">Escolha uma conexão de dados na lista de conexões disponíveis na página **Escolha a conexão de dados**.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-149">Select a data connection from the list of available connections on the **Choose Your Data Connection** page.</span></span> <span data-ttu-id="1b9ac-150">Se sua conexão de dados desejada não estiver disponível, selecione **Nova Conexão** para criar uma nova conexão de dados.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-150">If your desired data connection is not available, select **New Connection** to create a new data connection.</span></span>  
  
    5.  <span data-ttu-id="1b9ac-151">Clique em **Sim, salvar a conexão** para salvar a cadeia de conexão no arquivo de configuração de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-151">Click **Yes, save the connection** to save the connection string in the application configuration file.</span></span>  
  
    6.  <span data-ttu-id="1b9ac-152">Selecione os objetos de banco de dados para trazer para o seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-152">Select the database objects to bring into your application.</span></span> <span data-ttu-id="1b9ac-153">Neste caso, selecione uma tabela pai e uma tabela filho (por exemplo, clientes e pedidos) com uma relação de chave estrangeira.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-153">In this case, select a parent table and child table (for example, Customers and Orders) with a foreign key relationship.</span></span>  
  
    7.  <span data-ttu-id="1b9ac-154">Substitua o nome do conjunto de dados padrão, se quiser.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-154">Replace the default dataset name if you want.</span></span>  
  
    8.  <span data-ttu-id="1b9ac-155">Clique em **Finalizar**.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-155">Click **Finish**.</span></span>  
  
4.  <span data-ttu-id="1b9ac-156">Na caixa suspensa **Exibir Membro**, selecione o nome da coluna (por exemplo, ContactName) a ser exibida na caixa de combinação.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-156">In the **Display Member** drop-down box, select the column name (for example, ContactName) to be displayed in the combo box.</span></span>  
  
5.  <span data-ttu-id="1b9ac-157">Na caixa suspensa **Membro do Valor**, selecione a coluna (por exemplo, CustomerID) para executar a operação de pesquisa na tabela filho.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-157">In the **Value Member** drop-down box, select the column (for example, CustomerID) to perform the lookup operation in the child table.</span></span>  
  
6.  <span data-ttu-id="1b9ac-158">Na caixa suspensa **Valor Selecionado**, navegue até **Fontes de Dados do Projeto** e o conjunto de dados que você criou que contém as tabelas pai e filho.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-158">In the **Selected Value** drop-down box, navigate to **Project Data Sources** and the dataset you just created that contains the parent and child tables.</span></span> <span data-ttu-id="1b9ac-159">Selecione a mesma propriedade da tabela filho que é o Membro do Valor da tabela pai (por exemplo, Orders.CustomerID).</span><span class="sxs-lookup"><span data-stu-id="1b9ac-159">Select the same property of the child table that is the Value Member of the parent table (for example, Orders.CustomerID).</span></span> <span data-ttu-id="1b9ac-160">Os <xref:System.Windows.Forms.BindingSource>, componentes do conjunto de dados e do adaptador de tabela adequado, serão criados e adicionados ao formulário.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-160">The appropriate <xref:System.Windows.Forms.BindingSource> , data set, and table adapter components will be created and added to the form.</span></span>  
  
7.  <span data-ttu-id="1b9ac-161">Vincule o controle <xref:System.Windows.Forms.BindingNavigator> para o <xref:System.Windows.Forms.BindingSource> da tabela filho (por exemplo, `OrdersBindingSource`).</span><span class="sxs-lookup"><span data-stu-id="1b9ac-161">Bind the <xref:System.Windows.Forms.BindingNavigator> control to the <xref:System.Windows.Forms.BindingSource> of the child table (for example, `OrdersBindingSource`).</span></span>  
  
8.  <span data-ttu-id="1b9ac-162">Vincule os controles diferentes dos controles <xref:System.Windows.Forms.ComboBox> e <xref:System.Windows.Forms.BindingNavigator> aos campos de detalhes do <xref:System.Windows.Forms.BindingSource> da tabela filho (Por exemplo, `OrdersBindingSource`) que você deseja exibir.</span><span class="sxs-lookup"><span data-stu-id="1b9ac-162">Bind the controls other than the <xref:System.Windows.Forms.ComboBox> and <xref:System.Windows.Forms.BindingNavigator> control to the details fields from the child table's <xref:System.Windows.Forms.BindingSource> (for example, `OrdersBindingSource`) that you want to display.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1b9ac-163">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b9ac-163">See also</span></span>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1b9ac-164">Componente BindingSource</span><span class="sxs-lookup"><span data-stu-id="1b9ac-164">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="1b9ac-165">Controle ComboBox</span><span class="sxs-lookup"><span data-stu-id="1b9ac-165">ComboBox Control</span></span>](../../../../docs/framework/winforms/controls/combobox-control-windows-forms.md)
- [<span data-ttu-id="1b9ac-166">Associar controles a dados no Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1b9ac-166">Bind controls to data in Visual Studio</span></span>](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio)
