---
title: 'Passo a passo: usar somente procedimentos armazenados (Visual Basic)'
ms.date: 03/30/2017
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
ms.openlocfilehash: 686d1797666c36f47d1ab0244754bbf2daf97eaf
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188564"
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="fc370-102">Passo a passo: usar somente procedimentos armazenados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fc370-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="fc370-103">Essa explicação passo a passo fornece um cenário de ponta a ponta básico de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para acessar dados usando somente procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="fc370-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="fc370-104">Essa abordagem é frequentemente usada por administradores de banco de dados para limitar como o repositório de dados é acessado.</span><span class="sxs-lookup"><span data-stu-id="fc370-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fc370-105">Você também pode usar procedimentos armazenados nos aplicativos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir o comportamento padrão, especialmente para os processos `Create`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="fc370-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="fc370-106">Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="fc370-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="fc370-107">Para fins deste passo a passo, você usará dois métodos que foram mapeados para procedimentos armazenados no banco de dados de exemplo Northwind: CustOrdersDetail e CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="fc370-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="fc370-108">O mapeamento ocorre quando você executar a ferramenta de linha de comando SqlMetal para gerar um arquivo de Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fc370-108">The mapping occurs when you run the SqlMetal command-line tool to generate a Visual Basic file.</span></span> <span data-ttu-id="fc370-109">Para obter mais informações, consulte a seção Pré-requisitos posteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="fc370-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="fc370-110">Este passo a passo não se baseia no [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="fc370-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="fc370-111">Os desenvolvedores usando o Visual Studio também podem usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] para implementar a funcionalidade do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="fc370-111">Developers using Visual Studio can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="fc370-112">Ver [ferramentas LINQ to SQL no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="fc370-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="fc370-113">Este passo a passo foi escrito usando as Configurações de Desenvolvimento do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="fc370-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="fc370-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="fc370-114">Prerequisites</span></span>  
 <span data-ttu-id="fc370-115">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="fc370-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="fc370-116">Essa explicação passo a passo usa uma pasta c:\linqtest3 dedicada (“") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="fc370-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="fc370-117">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="fc370-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="fc370-118">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="fc370-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="fc370-119">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="fc370-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="fc370-120">Para obter instruções, consulte [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="fc370-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="fc370-121">Depois que você baixou o base de dados, copie o arquivo de northwnd.mdf para a pasta de c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="fc370-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="fc370-122">Um arquivo de código do Visual Basic gerado do banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="fc370-122">A Visual Basic code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="fc370-123">Este passo a passo foi escrito usando a ferramenta SqlMetal com a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="fc370-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     **<span data-ttu-id="fc370-124">sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize</span><span class="sxs-lookup"><span data-stu-id="fc370-124">sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize</span></span>**  
  
     <span data-ttu-id="fc370-125">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="fc370-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="fc370-126">Visão geral</span><span class="sxs-lookup"><span data-stu-id="fc370-126">Overview</span></span>  
 <span data-ttu-id="fc370-127">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="fc370-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="fc370-128">Configurando o [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solução no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fc370-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in Visual Studio.</span></span>  
  
-   <span data-ttu-id="fc370-129">Adicionar o assembly System.Data.Linq ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fc370-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="fc370-130">Adicionar o arquivo do código de banco de dados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fc370-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="fc370-131">Criando uma conexão a base de dados.</span><span class="sxs-lookup"><span data-stu-id="fc370-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="fc370-132">Configurar a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="fc370-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="fc370-133">Executar e testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc370-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="fc370-134">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fc370-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="fc370-135">A primeira tarefa, você cria uma solução do Visual Studio que contém as referências necessárias para compilar e executar um [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] projeto.</span><span class="sxs-lookup"><span data-stu-id="fc370-135">In this first task, you create a Visual Studio solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="fc370-136">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fc370-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="fc370-137">No Visual Studio **arquivo** menu, clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="fc370-137">On the Visual Studio **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="fc370-138">No **tipos de projeto** painel na **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**e, em seguida, clique em **Windows**.</span><span class="sxs-lookup"><span data-stu-id="fc370-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="fc370-139">No **modelos** painel, clique em **aplicativo de formulários do Windows**.</span><span class="sxs-lookup"><span data-stu-id="fc370-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="fc370-140">No **nome** , digite **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="fc370-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="fc370-141">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="fc370-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="fc370-142">O Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="fc370-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="fc370-143">Adicionando a referência do assembly do LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="fc370-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="fc370-144">O assembly do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é incluído no modelo padrão do Aplicativo do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fc370-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="fc370-145">Você mesmo precisará adicionar o assembly, conforme explicado nas etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="fc370-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="fc370-146">Para adicionar o System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="fc370-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="fc370-147">Na **Gerenciador de soluções**, clique em **Mostrar todos os arquivos**.</span><span class="sxs-lookup"><span data-stu-id="fc370-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="fc370-148">Na **Gerenciador de soluções**, clique com botão direito **referências**e, em seguida, clique em **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="fc370-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="fc370-149">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique no assembly System e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="fc370-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="fc370-150">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fc370-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="fc370-151">Adicionando o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="fc370-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="fc370-152">Esta etapa presume que você usou a ferramenta SqlMetal para gerar um arquivo de código do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="fc370-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="fc370-153">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="fc370-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="fc370-154">Para adicionar o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="fc370-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="fc370-155">Sobre o **Project** menu, clique em **Add Existing Item**.</span><span class="sxs-lookup"><span data-stu-id="fc370-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="fc370-156">No **Adicionar Item existente** caixa de diálogo, mova para c:\linqtest3\northwind.vb e, em seguida, clique em **Add**.</span><span class="sxs-lookup"><span data-stu-id="fc370-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="fc370-157">O arquivo northwind.vb é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="fc370-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="fc370-158">Criando uma conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="fc370-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="fc370-159">Nesta etapa, você define a conexão com o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="fc370-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="fc370-160">Essa explicação passo a passo usa “c:\linqtest3\northwnd.mdf” como o caminho.</span><span class="sxs-lookup"><span data-stu-id="fc370-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="fc370-161">Par criar a conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="fc370-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="fc370-162">Na **Gerenciador de soluções**, clique com botão direito **Form1.vb**e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="fc370-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     `Class Form1` <span data-ttu-id="fc370-163">é exibido no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="fc370-163">appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="fc370-164">Digite o seguinte código no bloco de código de `Form1` :</span><span class="sxs-lookup"><span data-stu-id="fc370-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="fc370-165">Configurando a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="fc370-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="fc370-166">Nesta tarefa você cria uma interface de modo que os usuários podem executar procedimentos armazenados para acessar dados na base de dados.</span><span class="sxs-lookup"><span data-stu-id="fc370-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="fc370-167">No aplicativo que você está desenvolvendo com este passo-a-passo, os usuários podem acessar dados na base de dados usando somente os procedimentos armazenados inseridos no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc370-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="fc370-168">Para configurar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="fc370-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="fc370-169">Retorne para o Windows Forms Designer (**Form1.vb design []**).</span><span class="sxs-lookup"><span data-stu-id="fc370-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="fc370-170">No menu **Exibir**, clique em **Caixa de Ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="fc370-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="fc370-171">A caixa de ferramentas é aberta.</span><span class="sxs-lookup"><span data-stu-id="fc370-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fc370-172">Clique o **ocultar automaticamente** pino para manter a caixa de ferramentas aberta enquanto você executa o restante das etapas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="fc370-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="fc370-173">Arraste dois botões, duas caixas de texto e dois rótulos da toolbox **Form1**.</span><span class="sxs-lookup"><span data-stu-id="fc370-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="fc370-174">Organize os controles conforme mostrado na ilustração de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="fc370-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="fc370-175">Expandir **Form1** para que os controles se encaixem facilmente.</span><span class="sxs-lookup"><span data-stu-id="fc370-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="fc370-176">Clique com botão direito **Label1**e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="fc370-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="fc370-177">Alterar o **texto** propriedade de **Label1** para **Enter OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="fc370-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="fc370-178">Da mesma forma para **Label2**, altere o **texto** propriedade de **Label2** para **Enter CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="fc370-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="fc370-179">Da mesma forma, altere o **texto** propriedade **Button1** para **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="fc370-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="fc370-180">Alterar o **texto** propriedade **Button2** para **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="fc370-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="fc370-181">Amplie os controles de botão de modo que todo o texto fique visível.</span><span class="sxs-lookup"><span data-stu-id="fc370-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="fc370-182">Para manipular cliques de botão</span><span class="sxs-lookup"><span data-stu-id="fc370-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="fc370-183">Clique duas vezes em **detalhes do pedido** nos **Form1** para criar o `Button1` manipulador de eventos e abrir o editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="fc370-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="fc370-184">Digite o código a seguir no manipulador `Button1`:</span><span class="sxs-lookup"><span data-stu-id="fc370-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="fc370-185">Agora clique duas vezes **Button2** em Form1 para criar o `Button2` manipulador de eventos e abrir o editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="fc370-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="fc370-186">Digite o código a seguir no manipulador `Button2`:</span><span class="sxs-lookup"><span data-stu-id="fc370-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="fc370-187">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="fc370-187">Testing the Application</span></span>  
 <span data-ttu-id="fc370-188">Agora é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="fc370-188">Now it is time to test your application.</span></span> <span data-ttu-id="fc370-189">Observe que o contato com o repositório de dados limita-se a qualquer ação que os dois procedimentos armazenados podem executar.</span><span class="sxs-lookup"><span data-stu-id="fc370-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="fc370-190">Essas ações retornarão os produtos para qualquer orderID inserida ou retornarão um histórico do produtos solicitados para qualquer CustomerID inserida.</span><span class="sxs-lookup"><span data-stu-id="fc370-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="fc370-191">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="fc370-191">To test the application</span></span>  
  
1.  <span data-ttu-id="fc370-192">Pressione F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="fc370-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="fc370-193">Form1 aparecerá.</span><span class="sxs-lookup"><span data-stu-id="fc370-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="fc370-194">No **Enter OrderID** , digite **10249** e, em seguida, clique em **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="fc370-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="fc370-195">Uma caixa de mensagem lista os produtos incluídos no pedido 10249.</span><span class="sxs-lookup"><span data-stu-id="fc370-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="fc370-196">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fc370-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="fc370-197">No **Enter CustomerID** , digite `ALFKI`e, em seguida, clique em **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="fc370-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="fc370-198">Uma caixa de mensagem lista o histórico de pedidos para o cliente ALFKI.</span><span class="sxs-lookup"><span data-stu-id="fc370-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="fc370-199">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fc370-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="fc370-200">No **Enter OrderID** , digite `123`e, em seguida, clique em **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="fc370-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="fc370-201">Uma caixa de mensagem não exibe “nenhum” resultado.</span><span class="sxs-lookup"><span data-stu-id="fc370-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="fc370-202">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="fc370-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="fc370-203">Sobre o **Debug** menu, clique em **parar a depuração**.</span><span class="sxs-lookup"><span data-stu-id="fc370-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="fc370-204">A sessão de depuração é fechada.</span><span class="sxs-lookup"><span data-stu-id="fc370-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="fc370-205">Se você tiver terminado o teste, você pode clicar em **fechar projeto** sobre o **arquivo** menu e salvar o projeto quando solicitado.</span><span class="sxs-lookup"><span data-stu-id="fc370-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fc370-206">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="fc370-206">Next Steps</span></span>  
 <span data-ttu-id="fc370-207">Você pode aprimorar esse projeto fazendo algumas alterações.</span><span class="sxs-lookup"><span data-stu-id="fc370-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="fc370-208">Por exemplo, você pode listar os procedimentos armazenados disponíveis em uma caixa de listagem e fazer com que o usuário selecione os procedimentos que serão executados.</span><span class="sxs-lookup"><span data-stu-id="fc370-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="fc370-209">Você também pode transmitir a saída dos relatórios para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="fc370-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc370-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc370-210">See also</span></span>

- [<span data-ttu-id="fc370-211">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="fc370-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)
- [<span data-ttu-id="fc370-212">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="fc370-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
