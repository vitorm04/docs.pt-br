---
title: 'Passo a passo: Usando somente procedimentos armazenados (C#)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ecde4bf2-fa4d-4252-b5e4-96a46b9e097d
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 1b3cc18f481a0e66d52f021b7bf6b76938fc5018
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-using-only-stored-procedures-c"></a><span data-ttu-id="6e119-102">Passo a passo: Usando somente procedimentos armazenados (C#)</span><span class="sxs-lookup"><span data-stu-id="6e119-102">Walkthrough: Using Only Stored Procedures (C#)</span></span>
<span data-ttu-id="6e119-103">Este passo a passo fornece um cenário completo do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para acessar dados executando somente procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="6e119-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by executing stored procedures only.</span></span> <span data-ttu-id="6e119-104">Essa abordagem é frequentemente usada por administradores de banco de dados para limitar como o repositório de dados é acessado.</span><span class="sxs-lookup"><span data-stu-id="6e119-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6e119-105">Você também pode usar procedimentos armazenados nos aplicativos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir o comportamento padrão, especialmente para os processos `Create`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="6e119-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="6e119-106">Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="6e119-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="6e119-107">Neste passo a passo, você usará dois métodos que foram mapeados para os procedimentos armazenados no banco de dados de exemplo Northwind: CustOrdersDetail e CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="6e119-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="6e119-108">O mapeamento ocorre quando você executa a ferramenta de linha de comando SqlMetal para gerar um arquivo C#.</span><span class="sxs-lookup"><span data-stu-id="6e119-108">The mapping occurs when you run the SqlMetal command-line tool to generate a C# file.</span></span> <span data-ttu-id="6e119-109">Para obter mais informações, consulte a seção Pré-requisitos posteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6e119-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="6e119-110">Este passo a passo não se baseia no [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e119-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="6e119-111">Os desenvolvedores que usam o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] também podem usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] para implementar a funcionalidade do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="6e119-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="6e119-112">Consulte [LINQ to SQL Tools no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="6e119-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="6e119-113">Esse passo a passo foi escrito usando as configurações de desenvolvimento do Visual C#.</span><span class="sxs-lookup"><span data-stu-id="6e119-113">This walkthrough was written by using Visual C# Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="6e119-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="6e119-114">Prerequisites</span></span>  
 <span data-ttu-id="6e119-115">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="6e119-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="6e119-116">Este passo a passo usa uma pasta dedicada ("c:\linqtest7") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="6e119-116">This walkthrough uses a dedicated folder ("c:\linqtest7") to hold files.</span></span> <span data-ttu-id="6e119-117">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6e119-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="6e119-118">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e119-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="6e119-119">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="6e119-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="6e119-120">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="6e119-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="6e119-121">Depois de baixar o banco de dados, copie o arquivo northwnd.mdf para a pasta c:\linqtest7.</span><span class="sxs-lookup"><span data-stu-id="6e119-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest7 folder.</span></span>  
  
-   <span data-ttu-id="6e119-122">Um arquivo de código C# gerado no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e119-122">A C# code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="6e119-123">Este passo a passo foi escrito usando a ferramenta SqlMetal com a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="6e119-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="6e119-124">**SqlMetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions / Pluralizar**</span><span class="sxs-lookup"><span data-stu-id="6e119-124">**sqlmetal /code:"c:\linqtest7\northwind.cs" /language:csharp "c:\linqtest7\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="6e119-125">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="6e119-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="6e119-126">Visão geral</span><span class="sxs-lookup"><span data-stu-id="6e119-126">Overview</span></span>  
 <span data-ttu-id="6e119-127">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="6e119-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="6e119-128">Configurar a solução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e119-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="6e119-129">Adicionar o assembly System.Data.Linq ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6e119-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="6e119-130">Adicionar o arquivo do código de banco de dados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6e119-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="6e119-131">Criar uma conexão com o banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6e119-131">Creating a connection with the database.</span></span>  
  
-   <span data-ttu-id="6e119-132">Configurar a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6e119-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="6e119-133">Executar e testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6e119-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="6e119-134">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e119-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="6e119-135">Nesta primeira tarefa, você cria uma solução do [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] que contém as referências necessárias para criar e executar um projeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6e119-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="6e119-136">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e119-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="6e119-137">Sobre o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **arquivo** , aponte para **novo**e, em seguida, clique em **projeto**.</span><span class="sxs-lookup"><span data-stu-id="6e119-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, point to **New**, and then click **Project**.</span></span>  
  
2.  <span data-ttu-id="6e119-138">No **tipos de projeto** painel o **novo projeto** caixa de diálogo, clique em **Visual C#**.</span><span class="sxs-lookup"><span data-stu-id="6e119-138">In the **Project types** pane in the **New Project** dialog box, click **Visual C#**.</span></span>  
  
3.  <span data-ttu-id="6e119-139">No **modelos** painel, clique em **aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="6e119-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="6e119-140">No **nome** , digite **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="6e119-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="6e119-141">No **local** , verifique se onde você deseja armazenar os arquivos de projeto.</span><span class="sxs-lookup"><span data-stu-id="6e119-141">In the **Location** box, verify where you want to store your project files.</span></span>  
  
6.  <span data-ttu-id="6e119-142">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="6e119-142">Click **OK**.</span></span>  
  
     <span data-ttu-id="6e119-143">O Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="6e119-143">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="6e119-144">Adicionando a referência do assembly do LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="6e119-144">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="6e119-145">O assembly do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é incluído no modelo padrão do Aplicativo do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6e119-145">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="6e119-146">Você mesmo precisará adicionar o assembly, conforme explicado nas etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="6e119-146">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="6e119-147">Para adicionar o System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="6e119-147">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="6e119-148">Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="6e119-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="6e119-149">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="6e119-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="6e119-150">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6e119-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="6e119-151">Adicionando o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="6e119-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="6e119-152">Esta etapa presume que você usou a ferramenta SqlMetal para gerar um arquivo de código do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e119-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="6e119-153">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="6e119-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="6e119-154">Para adicionar o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="6e119-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="6e119-155">Sobre o **projeto** menu, clique em **Add Existing Item**.</span><span class="sxs-lookup"><span data-stu-id="6e119-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="6e119-156">No **Add Existing Item** caixa de diálogo, mova para c:\linqtest7\northwind.cs e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="6e119-156">In the **Add Existing Item** dialog box, move to c:\linqtest7\northwind.cs, and then click **Add**.</span></span>  
  
     <span data-ttu-id="6e119-157">O arquivo northwind.cs é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="6e119-157">The northwind.cs file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="6e119-158">Criando uma conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="6e119-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="6e119-159">Nesta etapa, você define a conexão com o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="6e119-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="6e119-160">Este passo a passo usa "c:\linqtest7\northwnd.mdf" como caminho.</span><span class="sxs-lookup"><span data-stu-id="6e119-160">This walkthrough uses "c:\linqtest7\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="6e119-161">Par criar a conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="6e119-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="6e119-162">Em **Solution Explorer**, clique com botão direito **Form1.cs**e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="6e119-162">In **Solution Explorer**, right-click **Form1.cs**, and then click **View Code**.</span></span>  
  
2.  <span data-ttu-id="6e119-163">Digite o código a seguir na classe `Form1`:</span><span class="sxs-lookup"><span data-stu-id="6e119-163">Type the following code into the `Form1` class:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#1](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="6e119-164">Configurando a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="6e119-164">Setting up the User Interface</span></span>  
 <span data-ttu-id="6e119-165">Nesta tarefa, você configura uma interface de modo que os usuários possam executar procedimentos armazenados para acessar dados no banco de dados.</span><span class="sxs-lookup"><span data-stu-id="6e119-165">In this task you set up an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="6e119-166">Nos aplicativos que você está desenvolvendo através deste passo a passo, os usuários só podem acessar dados no banco de dados usando os procedimentos armazenados inseridos no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6e119-166">In the applications that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="6e119-167">Para configurar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="6e119-167">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="6e119-168">Voltar para o Windows Forms Designer (**Form1.cs[Design]**).</span><span class="sxs-lookup"><span data-stu-id="6e119-168">Return to the Windows Forms Designer (**Form1.cs[Design]**).</span></span>  
  
2.  <span data-ttu-id="6e119-169">Sobre o **exibição** menu, clique em **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="6e119-169">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="6e119-170">A caixa de ferramentas é aberta.</span><span class="sxs-lookup"><span data-stu-id="6e119-170">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="6e119-171">Clique o **AutoOcultar** pino para manter a caixa de ferramentas aberta enquanto você executa o restante das etapas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="6e119-171">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="6e119-172">Arraste dois rótulos, duas caixas de texto e dois botões da caixa de ferramentas para **Form1**.</span><span class="sxs-lookup"><span data-stu-id="6e119-172">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="6e119-173">Organize os controles conforme mostrado na ilustração de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="6e119-173">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="6e119-174">Expanda **Form1** para que os controles se ajustar facilmente.</span><span class="sxs-lookup"><span data-stu-id="6e119-174">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="6e119-175">Clique com botão direito **label1**e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="6e119-175">Right-click **label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="6e119-176">Alterar o **texto** propriedade **label1** para **insira OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="6e119-176">Change the **Text** property from **label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="6e119-177">Da mesma forma para **label2**, alterar o **texto** propriedade **label2** para **digite CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="6e119-177">In the same way for **label2**, change the **Text** property from **label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="6e119-178">Da mesma forma, alterar o **texto** propriedade **button1** para **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="6e119-178">In the same way, change the **Text** property for **button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="6e119-179">Alterar o **texto** propriedade **button2** para **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="6e119-179">Change the **Text** property for **button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="6e119-180">Amplie os controles de botão de modo que todo o texto fique visível.</span><span class="sxs-lookup"><span data-stu-id="6e119-180">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="6e119-181">Para manipular cliques de botão</span><span class="sxs-lookup"><span data-stu-id="6e119-181">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="6e119-182">Clique duas vezes em **Order Details** na **Form1** para abrir o manipulador de eventos button1 no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="6e119-182">Double-click **Order Details** on **Form1** to open the button1 event handler in the code editor.</span></span>  
  
2.  <span data-ttu-id="6e119-183">Digite o código a seguir no manipulador `button1`:</span><span class="sxs-lookup"><span data-stu-id="6e119-183">Type the following code into the `button1` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#2)]  
  
3.  <span data-ttu-id="6e119-184">Agora clique duas vezes em **button2** na **Form1** para abrir o `button2` manipulador</span><span class="sxs-lookup"><span data-stu-id="6e119-184">Now double-click **button2** on **Form1** to open the `button2` handler</span></span>  
  
4.  <span data-ttu-id="6e119-185">Digite o código a seguir no manipulador `button2`:</span><span class="sxs-lookup"><span data-stu-id="6e119-185">Type the following code into the `button2` handler:</span></span>  
  
     [!code-csharp[DLinqWalk4CS#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/DLinqWalk4CS/cs/Form1.cs#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="6e119-186">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="6e119-186">Testing the Application</span></span>  
 <span data-ttu-id="6e119-187">Agora é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6e119-187">Now it is time to test your application.</span></span> <span data-ttu-id="6e119-188">Observe que o contato com o repositório de dados limita-se a qualquer ação que os dois procedimentos armazenados podem executar.</span><span class="sxs-lookup"><span data-stu-id="6e119-188">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="6e119-189">Essas ações retornarão os produtos para qualquer orderID inserida ou retornarão um histórico do produtos solicitados para qualquer CustomerID inserida.</span><span class="sxs-lookup"><span data-stu-id="6e119-189">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="6e119-190">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="6e119-190">To test the application</span></span>  
  
1.  <span data-ttu-id="6e119-191">Pressione F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="6e119-191">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="6e119-192">Form1 aparecerá.</span><span class="sxs-lookup"><span data-stu-id="6e119-192">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="6e119-193">No **OrderID insira** , digite `10249`e, em seguida, clique em **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="6e119-193">In the **Enter OrderID** box, type `10249`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="6e119-194">Uma caixa de mensagem lista os produtos incluídos no pedido 10249.</span><span class="sxs-lookup"><span data-stu-id="6e119-194">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="6e119-195">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6e119-195">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="6e119-196">No **digite CustomerID** , digite `ALFKI`e, em seguida, clique em **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="6e119-196">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="6e119-197">Uma caixa de mensagem aparecerá, listando o histórico do pedido do cliente ALFKI.</span><span class="sxs-lookup"><span data-stu-id="6e119-197">A message box appears that lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="6e119-198">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6e119-198">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="6e119-199">No **OrderID insira** , digite `123`e, em seguida, clique em **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="6e119-199">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="6e119-200">Uma caixa de mensagem exibirá "Nenhum resultado".</span><span class="sxs-lookup"><span data-stu-id="6e119-200">A message box appears that displays "No results."</span></span>  
  
     <span data-ttu-id="6e119-201">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="6e119-201">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="6e119-202">Sobre o **depurar** menu, clique em **parar a depuração**.</span><span class="sxs-lookup"><span data-stu-id="6e119-202">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="6e119-203">A sessão de depuração é fechada.</span><span class="sxs-lookup"><span data-stu-id="6e119-203">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="6e119-204">Se você concluiu a experimentar, você pode clicar em **fechar projeto** no **arquivo** menu e salve o projeto quando você for solicitado.</span><span class="sxs-lookup"><span data-stu-id="6e119-204">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="6e119-205">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="6e119-205">Next Steps</span></span>  
 <span data-ttu-id="6e119-206">Você pode aprimorar esse projeto fazendo algumas alterações.</span><span class="sxs-lookup"><span data-stu-id="6e119-206">You can enhance this project by making some changes.</span></span> <span data-ttu-id="6e119-207">Por exemplo, você pode listar os procedimentos armazenados disponíveis em uma caixa de listagem e fazer com que o usuário selecione os procedimentos que serão executados.</span><span class="sxs-lookup"><span data-stu-id="6e119-207">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="6e119-208">Você também pode transmitir a saída dos relatórios para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="6e119-208">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e119-209">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e119-209">See Also</span></span>  
 [<span data-ttu-id="6e119-210">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="6e119-210">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="6e119-211">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="6e119-211">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
