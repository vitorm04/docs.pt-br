---
title: 'Passo a passo: usar somente procedimentos armazenados (C#)'
ms.date: 03/30/2017
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
ms.openlocfilehash: f980402c976db9ee327a7b726e36a0a4d9d6d73f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70792092"
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="5b36e-102">Passo a passo: usar somente procedimentos armazenados (C#)</span><span class="sxs-lookup"><span data-stu-id="5b36e-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>

<span data-ttu-id="5b36e-103">Este passo a passo fornece um cenário completo do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para acessar dados executando somente procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="5b36e-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="5b36e-104">Essa abordagem é frequentemente usada por administradores de banco de dados para limitar como o repositório de dados é acessado.</span><span class="sxs-lookup"><span data-stu-id="5b36e-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>

> [!NOTE]
> <span data-ttu-id="5b36e-105">Você também pode usar procedimentos armazenados nos aplicativos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir o comportamento padrão, especialmente para os processos `Create`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="5b36e-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="5b36e-106">Para obter mais informações, consulte [Personalizando as operações de inserção, atualização e exclusão](customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="5b36e-106">For more information, see [Customizing Insert, Update, and Delete Operations](customizing-insert-update-and-delete-operations.md).</span></span>

<span data-ttu-id="5b36e-107">Para fins deste passo a passos, você usará dois métodos que foram mapeados para procedimentos armazenados no banco de dados de exemplo Northwind: CustOrdersDetail e CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="5b36e-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="5b36e-108">O mapeamento ocorre quando você executa a ferramenta de linha de comando SqlMetal para gerar um arquivo C#.</span><span class="sxs-lookup"><span data-stu-id="5b36e-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="5b36e-109">Para obter mais informações, consulte a seção Pré-requisitos posteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="5b36e-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>

<span data-ttu-id="5b36e-110">Este tutorial não depende do Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="5b36e-110">This walkthrough does not rely on the Object Relational Designer.</span></span> <span data-ttu-id="5b36e-111">Os desenvolvedores que usam o Visual Studio também podem usar o o/R Designer para implementar a funcionalidade de procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="5b36e-111">Developers using Visual Studio can also use the O/R Designer to implement stored procedure functionality.</span></span> <span data-ttu-id="5b36e-112">Consulte [LINQ to SQL Tools no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="5b36e-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>

[!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]

<span data-ttu-id="5b36e-113">Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="5b36e-113">This walkthrough was written by using Visual C# Development Settings.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5b36e-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="5b36e-114">Prerequisites</span></span>

<span data-ttu-id="5b36e-115">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="5b36e-115">This walkthrough requires the following:</span></span>

- <span data-ttu-id="5b36e-116">Este passo a passo usa uma pasta dedicada ("c:\linqtest7") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="5b36e-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="5b36e-117">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="5b36e-117">Create this folder before you begin the walkthrough.</span></span>

- <span data-ttu-id="5b36e-118">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="5b36e-118">The Northwind sample database.</span></span>

     <span data-ttu-id="5b36e-119">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5b36e-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="5b36e-120">Para obter instruções, consulte [baixar bancos de dados de exemplo](downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="5b36e-120">For instructions, see [Downloading Sample Databases](downloading-sample-databases.md).</span></span> <span data-ttu-id="5b36e-121">Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="5b36e-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>

- <span data-ttu-id="5b36e-122">Um arquivo de código C# gerado no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="5b36e-122">A C# code file generated from the Northwind database.</span></span>

     <span data-ttu-id="5b36e-123">Este passo a passo foi escrito usando a ferramenta SqlMetal com a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="5b36e-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>

     <span data-ttu-id="5b36e-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="5b36e-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>

     <span data-ttu-id="5b36e-125">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="5b36e-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>

## <a name="overview"></a><span data-ttu-id="5b36e-126">Visão geral</span><span class="sxs-lookup"><span data-stu-id="5b36e-126">Overview</span></span>

<span data-ttu-id="5b36e-127">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="5b36e-127">This walkthrough consists of six main tasks:</span></span>

- <span data-ttu-id="5b36e-128">Configurando [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] a solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="5b36e-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>

- <span data-ttu-id="5b36e-129">Adicionar o assembly System.Data.Linq ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-129">Adding the System.Data.Linq assembly to the project.</span></span>

- <span data-ttu-id="5b36e-130">Adicionar o arquivo do código de banco de dados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-130">Adding the database code file to the project.</span></span>

- <span data-ttu-id="5b36e-131">Criar uma conexão com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5b36e-131">Creating a connection with the database.</span></span>

- <span data-ttu-id="5b36e-132">Configurar a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="5b36e-132">Setting up the user interface.</span></span>

- <span data-ttu-id="5b36e-133">Executar e testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b36e-133">Running and testing the application.</span></span>

## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="5b36e-134">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5b36e-134">Creating a LINQ to SQL Solution</span></span>

<span data-ttu-id="5b36e-135">Nesta primeira tarefa, você cria uma solução do Visual Studio que contém as referências necessárias para compilar e executar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>

### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="5b36e-136">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5b36e-136">To create a LINQ to SQL solution</span></span>

1. <span data-ttu-id="5b36e-137">No menu **arquivo** do Visual Studio, aponte para **novo**e clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-137">On the Visual Studio **File** menu, point to **New**, and then click **Project**.</span></span>

2. <span data-ttu-id="5b36e-138">No painel **tipos de projeto** na caixa de diálogo **novo projeto** , clique **em C#Visual** .</span><span class="sxs-lookup"><span data-stu-id="5b36e-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>

3. <span data-ttu-id="5b36e-139">No painel **modelos** , clique em **Windows Forms aplicativo**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>

4. <span data-ttu-id="5b36e-140">Na caixa **nome** , digite **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-140">In the **Name** box, type **SprocOnlyApp**.</span></span>

5. <span data-ttu-id="5b36e-141">Na caixa **local** , verifique onde você deseja armazenar os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-141">In the **Location** box, verify where you want to store your project files.</span></span>

6. <span data-ttu-id="5b36e-142">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-142">Click **OK**.</span></span>

     <span data-ttu-id="5b36e-143">O Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-143">The Windows Forms Designer opens.</span></span>

## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="5b36e-144">Adicionando a referência do assembly do LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="5b36e-144">Adding the LINQ to SQL Assembly Reference</span></span>

<span data-ttu-id="5b36e-145">O assembly do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é incluído no modelo padrão do Aplicativo do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="5b36e-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="5b36e-146">Você mesmo precisará adicionar o assembly, conforme explicado nas etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="5b36e-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>

### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="5b36e-147">Para adicionar o System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="5b36e-147">To add System.Data.Linq.dll</span></span>

1. <span data-ttu-id="5b36e-148">Em **Gerenciador de soluções**, clique com o botão direito do mouse em **referências**e clique em **Adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>

2. <span data-ttu-id="5b36e-149">Na caixa de diálogo **Adicionar referência** , clique em **.net**, clique no assembly System. Data. LINQ e, em seguida, clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>

     <span data-ttu-id="5b36e-150">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-150">The assembly is added to the project.</span></span>

## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="5b36e-151">Adicionando o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="5b36e-151">Adding the Northwind Code File to the Project</span></span>

<span data-ttu-id="5b36e-152">Esta etapa presume que você usou a ferramenta SqlMetal para gerar um arquivo de código do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="5b36e-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="5b36e-153">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="5b36e-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>

### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="5b36e-154">Para adicionar o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="5b36e-154">To add the northwind code file to the project</span></span>

1. <span data-ttu-id="5b36e-155">No menu **projeto** , clique em **Adicionar item existente**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-155">On the **Project** menu, click **Add Existing Item**.</span></span>

2. <span data-ttu-id="5b36e-156">Na caixa de diálogo **Adicionar item existente** , vá para c:\linqtest7\northwind.cs e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>

     <span data-ttu-id="5b36e-157">O arquivo northwind.cs é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-157">The northwind.cs file is added to the project.</span></span>

## <a name="creating-a-database-connection"></a><span data-ttu-id="5b36e-158">Criando uma conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="5b36e-158">Creating a Database Connection</span></span>

<span data-ttu-id="5b36e-159">Nesta etapa, você define a conexão com o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="5b36e-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="5b36e-160">Este passo a passo usa "c:\linqtest7\northwnd.mdf" como caminho.</span><span class="sxs-lookup"><span data-stu-id="5b36e-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>

### <a name="to-create-the-database-connection"></a><span data-ttu-id="5b36e-161">Par criar a conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="5b36e-161">To create the database connection</span></span>

1. <span data-ttu-id="5b36e-162">Em **Gerenciador de soluções**, clique com o botão direito do mouse em **Form1.cs**e clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>

2. <span data-ttu-id="5b36e-163">Digite o código a seguir na classe `Form1`:</span><span class="sxs-lookup"><span data-stu-id="5b36e-163">Type the following code into the `Form1` class:</span></span>

     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]

## <a name="setting-up-the-user-interface"></a><span data-ttu-id="5b36e-164">Configurando a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5b36e-164">Setting up the User Interface</span></span>

<span data-ttu-id="5b36e-165">Nesta tarefa, você configura uma interface de modo que os usuários possam executar procedimentos armazenados para acessar dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="5b36e-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="5b36e-166">Nos aplicativos que você está desenvolvendo através deste passo a passo, os usuários só podem acessar dados no banco de dados usando os procedimentos armazenados inseridos no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b36e-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>

### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="5b36e-167">Para configurar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="5b36e-167">To set up the user interface</span></span>

1. <span data-ttu-id="5b36e-168">Retorne para o Designer de Formulários do Windows (**Form1. cs [Design]** ).</span><span class="sxs-lookup"><span data-stu-id="5b36e-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>

2. <span data-ttu-id="5b36e-169">No menu **Exibir**, clique em **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-169">On the **View** menu, click **Toolbox**.</span></span>

     <span data-ttu-id="5b36e-170">A caixa de ferramentas é aberta.</span><span class="sxs-lookup"><span data-stu-id="5b36e-170">The toolbox opens.</span></span>

    > [!NOTE]
    > <span data-ttu-id="5b36e-171">Clique na anotação de **AutoOcultar** para manter a caixa de ferramentas aberta enquanto você executa as etapas restantes nesta seção.</span><span class="sxs-lookup"><span data-stu-id="5b36e-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>

3. <span data-ttu-id="5b36e-172">Arraste dois botões, duas caixas de texto e dois rótulos da caixa de ferramentas para o **Form1**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>

     <span data-ttu-id="5b36e-173">Organize os controles conforme mostrado na ilustração de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="5b36e-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="5b36e-174">Expanda **Form1** para que os controles caibam facilmente.</span><span class="sxs-lookup"><span data-stu-id="5b36e-174">Expand **Form1** so that the controls fit easily.</span></span>

4. <span data-ttu-id="5b36e-175">Clique com o botão direito do mouse em **Label1**e clique em **Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-175">Right-click **label1**, and then click **Properties**.</span></span>

5. <span data-ttu-id="5b36e-176">Altere a propriedade **Text** de **Label1** para **Enter OrderID:** .</span><span class="sxs-lookup"><span data-stu-id="5b36e-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>

6. <span data-ttu-id="5b36e-177">Da mesma forma para o **Label2**, altere a propriedade **Text** de **Label2** para **Enter CustomerID:** .</span><span class="sxs-lookup"><span data-stu-id="5b36e-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>

7. <span data-ttu-id="5b36e-178">Da mesma forma, altere a propriedade **Text** de **Button1** para **Order Details**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>

8. <span data-ttu-id="5b36e-179">Altere a propriedade **Text** de **Button2** para **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-179">Change the **Text** property for **button2** to **Order History**.</span></span>

     <span data-ttu-id="5b36e-180">Amplie os controles de botão de modo que todo o texto fique visível.</span><span class="sxs-lookup"><span data-stu-id="5b36e-180">Widen the button controls so that all the text is visible.</span></span>

### <a name="to-handle-button-clicks"></a><span data-ttu-id="5b36e-181">Para manipular cliques de botão</span><span class="sxs-lookup"><span data-stu-id="5b36e-181">To handle button clicks</span></span>

1. <span data-ttu-id="5b36e-182">Clique duas vezes em **Order Details** no **Form1** para abrir o manipulador de eventos Button1 no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="5b36e-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>

2. <span data-ttu-id="5b36e-183">Digite o código a seguir no manipulador `button1`:</span><span class="sxs-lookup"><span data-stu-id="5b36e-183">Type the following code into the `button1` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]

3. <span data-ttu-id="5b36e-184">Agora, clique duas vezes em **Button2** no **Form1** para `button2` abrir o manipulador</span><span class="sxs-lookup"><span data-stu-id="5b36e-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>

4. <span data-ttu-id="5b36e-185">Digite o código a seguir no manipulador `button2`:</span><span class="sxs-lookup"><span data-stu-id="5b36e-185">Type the following code into the `button2` handler:</span></span>

     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]

## <a name="testing-the-application"></a><span data-ttu-id="5b36e-186">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5b36e-186">Testing the Application</span></span>

<span data-ttu-id="5b36e-187">Agora é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="5b36e-187">Now it is time to test your application.</span></span> <span data-ttu-id="5b36e-188">Observe que o contato com o repositório de dados limita-se a qualquer ação que os dois procedimentos armazenados podem executar.</span><span class="sxs-lookup"><span data-stu-id="5b36e-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="5b36e-189">Essas ações retornarão os produtos para qualquer orderID inserida ou retornarão um histórico do produtos solicitados para qualquer CustomerID inserida.</span><span class="sxs-lookup"><span data-stu-id="5b36e-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>

### <a name="to-test-the-application"></a><span data-ttu-id="5b36e-190">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="5b36e-190">To test the application</span></span>

1. <span data-ttu-id="5b36e-191">Pressione F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="5b36e-191">Press F5 to start debugging.</span></span>

     <span data-ttu-id="5b36e-192">Form1 aparecerá.</span><span class="sxs-lookup"><span data-stu-id="5b36e-192">Form1 appears.</span></span>

2. <span data-ttu-id="5b36e-193">Na caixa **Inserir NúmeroDoPedido** , digite `10249`e clique em detalhes do **pedido**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>

     <span data-ttu-id="5b36e-194">Uma caixa de mensagem lista os produtos incluídos no pedido 10249.</span><span class="sxs-lookup"><span data-stu-id="5b36e-194">A message box lists the products included in order 10249.</span></span>

     <span data-ttu-id="5b36e-195">Clique em **OK** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5b36e-195">Click **OK** to close the message box.</span></span>

3. <span data-ttu-id="5b36e-196">Na caixa **Inserir CustomerID** , digite `ALFKI`e, em seguida, clique em **histórico do pedido**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>

     <span data-ttu-id="5b36e-197">Uma caixa de mensagem aparecerá, listando o histórico do pedido do cliente ALFKI.</span><span class="sxs-lookup"><span data-stu-id="5b36e-197">A message box appears that lists the order history for customer ALFKI.</span></span>

     <span data-ttu-id="5b36e-198">Clique em **OK** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5b36e-198">Click **OK** to close the message box.</span></span>

4. <span data-ttu-id="5b36e-199">Na caixa **Inserir NúmeroDoPedido** , digite `123`e clique em detalhes do **pedido**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>

     <span data-ttu-id="5b36e-200">Uma caixa de mensagem exibirá "Nenhum resultado".</span><span class="sxs-lookup"><span data-stu-id="5b36e-200">A message box appears that displays "No results."</span></span>

     <span data-ttu-id="5b36e-201">Clique em **OK** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="5b36e-201">Click **OK** to close the message box.</span></span>

5. <span data-ttu-id="5b36e-202">No menu **depurar** , clique em **parar depuração**.</span><span class="sxs-lookup"><span data-stu-id="5b36e-202">On the **Debug** menu, click **Stop debugging**.</span></span>

     <span data-ttu-id="5b36e-203">A sessão de depuração é fechada.</span><span class="sxs-lookup"><span data-stu-id="5b36e-203">The debug session closes.</span></span>

6. <span data-ttu-id="5b36e-204">Se você concluiu o experimento, pode clicar em **fechar projeto** no menu **arquivo** e salvar seu projeto quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="5b36e-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>

## <a name="next-steps"></a><span data-ttu-id="5b36e-205">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5b36e-205">Next Steps</span></span>

<span data-ttu-id="5b36e-206">Você pode aprimorar esse projeto fazendo algumas alterações.</span><span class="sxs-lookup"><span data-stu-id="5b36e-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="5b36e-207">Por exemplo, você pode listar os procedimentos armazenados disponíveis em uma caixa de listagem e fazer com que o usuário selecione os procedimentos que serão executados.</span><span class="sxs-lookup"><span data-stu-id="5b36e-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="5b36e-208">Você também pode transmitir a saída dos relatórios para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="5b36e-208">You could also stream the output of the reports to a text file.</span></span>

## <a name="see-also"></a><span data-ttu-id="5b36e-209">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b36e-209">See also</span></span>

- [<span data-ttu-id="5b36e-210">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="5b36e-210">Learning by Walkthroughs</span></span>](learning-by-walkthroughs.md)
- [<span data-ttu-id="5b36e-211">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="5b36e-211">Stored Procedures</span></span>](stored-procedures.md)
