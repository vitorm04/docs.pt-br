---
title: 'Passo a passo: Usando somente procedimentos armazenados (Visual Basic)'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- vb
ms.assetid: 5a736a30-ba66-4adb-b87c-57d19476e862
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload:
- dotnet
ms.openlocfilehash: 800cc7d6a1e4aa836ebe75afcbe29a3532ee173a
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/17/2018
---
# <a name="walkthrough-using-only-stored-procedures-visual-basic"></a><span data-ttu-id="7c2be-102">Passo a passo: Usando somente procedimentos armazenados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7c2be-102">Walkthrough: Using Only Stored Procedures (Visual Basic)</span></span>
<span data-ttu-id="7c2be-103">Essa explicação passo a passo fornece um cenário de ponta a ponta básico de [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para acessar dados usando somente procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="7c2be-103">This walkthrough provides a basic end-to-end [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] scenario for accessing data by using stored procedures only.</span></span> <span data-ttu-id="7c2be-104">Essa abordagem é frequentemente usada por administradores de banco de dados para limitar como o repositório de dados é acessado.</span><span class="sxs-lookup"><span data-stu-id="7c2be-104">This approach is often used by database administrators to limit how the datastore is accessed.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7c2be-105">Você também pode usar procedimentos armazenados nos aplicativos do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] para substituir o comportamento padrão, especialmente para os processos `Create`, `Update` e `Delete`.</span><span class="sxs-lookup"><span data-stu-id="7c2be-105">You can also use stored procedures in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] applications to override default behavior, especially for `Create`, `Update`, and `Delete` processes.</span></span> <span data-ttu-id="7c2be-106">Para obter mais informações, consulte [personalizando inserir, atualizar e excluir operações](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span><span class="sxs-lookup"><span data-stu-id="7c2be-106">For more information, see [Customizing Insert, Update, and Delete Operations](../../../../../../docs/framework/data/adonet/sql/linq/customizing-insert-update-and-delete-operations.md).</span></span>  
  
 <span data-ttu-id="7c2be-107">Neste passo a passo, você usará dois métodos que foram mapeados para os procedimentos armazenados no banco de dados de exemplo Northwind: CustOrdersDetail e CustOrderHist.</span><span class="sxs-lookup"><span data-stu-id="7c2be-107">For purposes of this walkthrough, you will use two methods that have been mapped to stored procedures in the Northwind sample database: CustOrdersDetail and CustOrderHist.</span></span> <span data-ttu-id="7c2be-108">O mapeamento ocorre quando você executa a ferramenta de linha de comando SqlMetal para gerar um arquivo de [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="7c2be-108">The mapping occurs when you run the SqlMetal command-line tool to generate a [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] file.</span></span> <span data-ttu-id="7c2be-109">Para obter mais informações, consulte a seção Pré-requisitos posteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="7c2be-109">For more information, see the Prerequisites section later in this walkthrough.</span></span>  
  
 <span data-ttu-id="7c2be-110">Este passo a passo não se baseia no [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c2be-110">This walkthrough does not rely on the [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)].</span></span> <span data-ttu-id="7c2be-111">Os desenvolvedores que usam o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] também podem usar o [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] para implementar a funcionalidade do procedimento armazenado.</span><span class="sxs-lookup"><span data-stu-id="7c2be-111">Developers using [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] can also use the [!INCLUDE[vs_ordesigner_short](../../../../../../includes/vs-ordesigner-short-md.md)] to implement stored procedure functionality.</span></span> <span data-ttu-id="7c2be-112">Consulte [LINQ to SQL Tools no Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span><span class="sxs-lookup"><span data-stu-id="7c2be-112">See [LINQ to SQL Tools in Visual Studio](/visualstudio/data-tools/linq-to-sql-tools-in-visual-studio2).</span></span>  
  
 [!INCLUDE[note_settings_general](../../../../../../includes/note-settings-general-md.md)]  
  
 <span data-ttu-id="7c2be-113">Este passo a passo foi escrito usando as Configurações de Desenvolvimento do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="7c2be-113">This walkthrough was written by using Visual Basic Development Settings.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="7c2be-114">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7c2be-114">Prerequisites</span></span>  
 <span data-ttu-id="7c2be-115">Este passo a passo requer o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7c2be-115">This walkthrough requires the following:</span></span>  
  
-   <span data-ttu-id="7c2be-116">Essa explicação passo a passo usa uma pasta c:\linqtest3 dedicada (“") para armazenar arquivos.</span><span class="sxs-lookup"><span data-stu-id="7c2be-116">This walkthrough uses a dedicated folder ("c:\linqtest3") to hold files.</span></span> <span data-ttu-id="7c2be-117">Crie essa pasta antes de iniciar o passo a passo.</span><span class="sxs-lookup"><span data-stu-id="7c2be-117">Create this folder before you begin the walkthrough.</span></span>  
  
-   <span data-ttu-id="7c2be-118">O banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c2be-118">The Northwind sample database.</span></span>  
  
     <span data-ttu-id="7c2be-119">Se você não tiver esse banco de dados no seu computador de desenvolvimento, poderá baixá-lo no site de download da Microsoft.</span><span class="sxs-lookup"><span data-stu-id="7c2be-119">If you do not have this database on your development computer, you can download it from the Microsoft download site.</span></span> <span data-ttu-id="7c2be-120">Para obter instruções, consulte [baixando bancos de dados de exemplo](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span><span class="sxs-lookup"><span data-stu-id="7c2be-120">For instructions, see [Downloading Sample Databases](../../../../../../docs/framework/data/adonet/sql/linq/downloading-sample-databases.md).</span></span> <span data-ttu-id="7c2be-121">Depois que você baixou o base de dados, copie o arquivo de northwnd.mdf para a pasta de c:\linqtest3.</span><span class="sxs-lookup"><span data-stu-id="7c2be-121">After you have downloaded the database, copy the northwnd.mdf file to the c:\linqtest3 folder.</span></span>  
  
-   <span data-ttu-id="7c2be-122">Um arquivo de código de [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] gerado de base de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c2be-122">A [!INCLUDE[vbprvb](../../../../../../includes/vbprvb-md.md)] code file generated from the Northwind database.</span></span>  
  
     <span data-ttu-id="7c2be-123">Este passo a passo foi escrito usando a ferramenta SqlMetal com a seguinte linha de comando:</span><span class="sxs-lookup"><span data-stu-id="7c2be-123">This walkthrough was written by using the SqlMetal tool with the following command line:</span></span>  
  
     <span data-ttu-id="7c2be-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span><span class="sxs-lookup"><span data-stu-id="7c2be-124">**sqlmetal /code:"c:\linqtest3\northwind.vb" /language:vb "c:\linqtest3\northwnd.mdf" /sprocs /functions /pluralize**</span></span>  
  
     <span data-ttu-id="7c2be-125">Para obter mais informações, consulte [SqlMetal.exe (ferramenta de geração de código)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="7c2be-125">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../../../docs/framework/tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="overview"></a><span data-ttu-id="7c2be-126">Visão geral</span><span class="sxs-lookup"><span data-stu-id="7c2be-126">Overview</span></span>  
 <span data-ttu-id="7c2be-127">Este passo a passo consiste em seis tarefas principais:</span><span class="sxs-lookup"><span data-stu-id="7c2be-127">This walkthrough consists of six main tasks:</span></span>  
  
-   <span data-ttu-id="7c2be-128">Configurar a solução do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] no [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c2be-128">Setting up the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] solution in [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)].</span></span>  
  
-   <span data-ttu-id="7c2be-129">Adicionar o assembly System.Data.Linq ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c2be-129">Adding the System.Data.Linq assembly to the project.</span></span>  
  
-   <span data-ttu-id="7c2be-130">Adicionar o arquivo do código de banco de dados ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c2be-130">Adding the database code file to the project.</span></span>  
  
-   <span data-ttu-id="7c2be-131">Criando uma conexão a base de dados.</span><span class="sxs-lookup"><span data-stu-id="7c2be-131">Creating a connection to the database.</span></span>  
  
-   <span data-ttu-id="7c2be-132">Configurar a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="7c2be-132">Setting up the user interface.</span></span>  
  
-   <span data-ttu-id="7c2be-133">Executar e testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c2be-133">Running and testing the application.</span></span>  
  
## <a name="creating-a-linq-to-sql-solution"></a><span data-ttu-id="7c2be-134">Criando uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7c2be-134">Creating a LINQ to SQL Solution</span></span>  
 <span data-ttu-id="7c2be-135">Nesta primeira tarefa, você cria uma solução do [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] que contém as referências necessárias para criar e executar um projeto do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7c2be-135">In this first task, you create a [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] solution that contains the necessary references to build and run a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] project.</span></span>  
  
#### <a name="to-create-a-linq-to-sql-solution"></a><span data-ttu-id="7c2be-136">Para criar uma solução LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7c2be-136">To create a LINQ to SQL solution</span></span>  
  
1.  <span data-ttu-id="7c2be-137">Sobre o [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **arquivo** menu, clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-137">On the [!INCLUDE[vs_current_short](../../../../../../includes/vs-current-short-md.md)] **File** menu, click **New Project**.</span></span>  
  
2.  <span data-ttu-id="7c2be-138">No **tipos de projeto** painel o **novo projeto** caixa de diálogo caixa, expanda **Visual Basic**e, em seguida, clique em **Windows**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-138">In the **Project types** pane in the **New Project** dialog box, expand **Visual Basic**, and then click **Windows**.</span></span>  
  
3.  <span data-ttu-id="7c2be-139">No **modelos** painel, clique em **aplicativo do Windows Forms**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-139">In the **Templates** pane, click **Windows Forms Application**.</span></span>  
  
4.  <span data-ttu-id="7c2be-140">No **nome** , digite **SprocOnlyApp**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-140">In the **Name** box, type **SprocOnlyApp**.</span></span>  
  
5.  <span data-ttu-id="7c2be-141">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-141">Click **OK**.</span></span>  
  
     <span data-ttu-id="7c2be-142">O Designer de Formulários do Windows é aberto.</span><span class="sxs-lookup"><span data-stu-id="7c2be-142">The Windows Forms Designer opens.</span></span>  
  
## <a name="adding-the-linq-to-sql-assembly-reference"></a><span data-ttu-id="7c2be-143">Adicionando a referência do assembly do LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7c2be-143">Adding the LINQ to SQL Assembly Reference</span></span>  
 <span data-ttu-id="7c2be-144">O assembly do [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] não é incluído no modelo padrão do Aplicativo do Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7c2be-144">The [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] assembly is not included in the standard Windows Forms Application template.</span></span> <span data-ttu-id="7c2be-145">Você mesmo precisará adicionar o assembly, conforme explicado nas etapas a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c2be-145">You will have to add the assembly yourself, as explained in the following steps:</span></span>  
  
#### <a name="to-add-systemdatalinqdll"></a><span data-ttu-id="7c2be-146">Para adicionar o System.Data.Linq.dll</span><span class="sxs-lookup"><span data-stu-id="7c2be-146">To add System.Data.Linq.dll</span></span>  
  
1.  <span data-ttu-id="7c2be-147">Em **Solution Explorer**, clique em **Mostrar todos os arquivos**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-147">In **Solution Explorer**, click **Show All Files**.</span></span>  
  
2.  <span data-ttu-id="7c2be-148">Em **Solution Explorer**, clique com botão direito **referências**e, em seguida, clique em **adicionar referência**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-148">In **Solution Explorer**, right-click **References**, and then click **Add Reference**.</span></span>  
  
3.  <span data-ttu-id="7c2be-149">No **adicionar referência** caixa de diálogo, clique em **.NET**, clique em assembly System.Data.Linq e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-149">In the **Add Reference** dialog box, click **.NET**, click the System.Data.Linq assembly, and then click **OK**.</span></span>  
  
     <span data-ttu-id="7c2be-150">O assembly é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c2be-150">The assembly is added to the project.</span></span>  
  
## <a name="adding-the-northwind-code-file-to-the-project"></a><span data-ttu-id="7c2be-151">Adicionando o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="7c2be-151">Adding the Northwind Code File to the Project</span></span>  
 <span data-ttu-id="7c2be-152">Esta etapa presume que você usou a ferramenta SqlMetal para gerar um arquivo de código do banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c2be-152">This step assumes that you have used the SqlMetal tool to generate a code file from the Northwind sample database.</span></span> <span data-ttu-id="7c2be-153">Para obter mais informações, consulte a seção de pré-requisitos anteriormente neste passo a passo.</span><span class="sxs-lookup"><span data-stu-id="7c2be-153">For more information, see the Prerequisites section earlier in this walkthrough.</span></span>  
  
#### <a name="to-add-the-northwind-code-file-to-the-project"></a><span data-ttu-id="7c2be-154">Para adicionar o arquivo do código Northwind ao projeto</span><span class="sxs-lookup"><span data-stu-id="7c2be-154">To add the northwind code file to the project</span></span>  
  
1.  <span data-ttu-id="7c2be-155">Sobre o **projeto** menu, clique em **Add Existing Item**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-155">On the **Project** menu, click **Add Existing Item**.</span></span>  
  
2.  <span data-ttu-id="7c2be-156">No **Add Existing Item** caixa de diálogo, mova para c:\linqtest3\northwind.vb e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-156">In the **Add Existing Item** dialog box, move to c:\linqtest3\northwind.vb, and then click **Add**.</span></span>  
  
     <span data-ttu-id="7c2be-157">O arquivo northwind.vb é adicionado ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c2be-157">The northwind.vb file is added to the project.</span></span>  
  
## <a name="creating-a-database-connection"></a><span data-ttu-id="7c2be-158">Criando uma conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="7c2be-158">Creating a Database Connection</span></span>  
 <span data-ttu-id="7c2be-159">Nesta etapa, você define a conexão com o banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="7c2be-159">In this step, you define the connection to the Northwind sample database.</span></span> <span data-ttu-id="7c2be-160">Essa explicação passo a passo usa “c:\linqtest3\northwnd.mdf” como o caminho.</span><span class="sxs-lookup"><span data-stu-id="7c2be-160">This walkthrough uses "c:\linqtest3\northwnd.mdf" as the path.</span></span>  
  
#### <a name="to-create-the-database-connection"></a><span data-ttu-id="7c2be-161">Par criar a conexão de banco de dados</span><span class="sxs-lookup"><span data-stu-id="7c2be-161">To create the database connection</span></span>  
  
1.  <span data-ttu-id="7c2be-162">Em **Solution Explorer**, clique com botão direito **Form1. vb**e, em seguida, clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-162">In **Solution Explorer**, right-click **Form1.vb**, and then click **View Code**.</span></span>  
  
     <span data-ttu-id="7c2be-163">`Class Form1` aparece no editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7c2be-163">`Class Form1` appears in the code editor.</span></span>  
  
2.  <span data-ttu-id="7c2be-164">Digite o seguinte código no bloco de código de `Form1` :</span><span class="sxs-lookup"><span data-stu-id="7c2be-164">Type the following code into the `Form1` code block:</span></span>  
  
     [!code-vb[DLinqWalk4VB#1](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#1)]  
  
## <a name="setting-up-the-user-interface"></a><span data-ttu-id="7c2be-165">Configurando a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c2be-165">Setting up the User Interface</span></span>  
 <span data-ttu-id="7c2be-166">Nesta tarefa você cria uma interface de modo que os usuários podem executar procedimentos armazenados para acessar dados na base de dados.</span><span class="sxs-lookup"><span data-stu-id="7c2be-166">In this task you create an interface so that users can execute stored procedures to access data in the database.</span></span> <span data-ttu-id="7c2be-167">No aplicativo que você está desenvolvendo com este passo-a-passo, os usuários podem acessar dados na base de dados usando somente os procedimentos armazenados inseridos no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c2be-167">In the application that you are developing with this walkthrough, users can access data in the database only by using the stored procedures embedded in the application.</span></span>  
  
#### <a name="to-set-up-the-user-interface"></a><span data-ttu-id="7c2be-168">Para configurar a interface do usuário</span><span class="sxs-lookup"><span data-stu-id="7c2be-168">To set up the user interface</span></span>  
  
1.  <span data-ttu-id="7c2be-169">Voltar para o Windows Forms Designer (**Form1.vb[Design]**).</span><span class="sxs-lookup"><span data-stu-id="7c2be-169">Return to the Windows Forms Designer (**Form1.vb[Design]**).</span></span>  
  
2.  <span data-ttu-id="7c2be-170">Sobre o **exibição** menu, clique em **caixa de ferramentas**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-170">On the **View** menu, click **Toolbox**.</span></span>  
  
     <span data-ttu-id="7c2be-171">A caixa de ferramentas é aberta.</span><span class="sxs-lookup"><span data-stu-id="7c2be-171">The toolbox opens.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="7c2be-172">Clique o **AutoOcultar** pino para manter a caixa de ferramentas aberta enquanto você executa o restante das etapas nesta seção.</span><span class="sxs-lookup"><span data-stu-id="7c2be-172">Click the **AutoHide** pushpin to keep the toolbox open while you perform the remaining steps in this section.</span></span>  
  
3.  <span data-ttu-id="7c2be-173">Arraste dois rótulos, duas caixas de texto e dois botões da caixa de ferramentas para **Form1**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-173">Drag two buttons, two text boxes, and two labels from the toolbox onto **Form1**.</span></span>  
  
     <span data-ttu-id="7c2be-174">Organize os controles conforme mostrado na ilustração de acompanhamento.</span><span class="sxs-lookup"><span data-stu-id="7c2be-174">Arrange the controls as in the accompanying illustration.</span></span> <span data-ttu-id="7c2be-175">Expanda **Form1** para que os controles se ajustar facilmente.</span><span class="sxs-lookup"><span data-stu-id="7c2be-175">Expand **Form1** so that the controls fit easily.</span></span>  
  
4.  <span data-ttu-id="7c2be-176">Clique com botão direito **Label1**e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-176">Right-click **Label1**, and then click **Properties**.</span></span>  
  
5.  <span data-ttu-id="7c2be-177">Alterar o **texto** propriedade **Label1** para **insira OrderID:**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-177">Change the **Text** property from **Label1** to **Enter OrderID:**.</span></span>  
  
6.  <span data-ttu-id="7c2be-178">Da mesma forma para **Label2**, alterar o **texto** propriedade **Label2** para **digite CustomerID:**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-178">In the same way for **Label2**, change the **Text** property from **Label2** to **Enter CustomerID:**.</span></span>  
  
7.  <span data-ttu-id="7c2be-179">Da mesma forma, alterar o **texto** propriedade **Button1** para **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-179">In the same way, change the **Text** property for **Button1** to **Order Details**.</span></span>  
  
8.  <span data-ttu-id="7c2be-180">Alterar o **texto** propriedade **Button2** para **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-180">Change the **Text** property for **Button2** to **Order History**.</span></span>  
  
     <span data-ttu-id="7c2be-181">Amplie os controles de botão de modo que todo o texto fique visível.</span><span class="sxs-lookup"><span data-stu-id="7c2be-181">Widen the button controls so that all the text is visible.</span></span>  
  
#### <a name="to-handle-button-clicks"></a><span data-ttu-id="7c2be-182">Para manipular cliques de botão</span><span class="sxs-lookup"><span data-stu-id="7c2be-182">To handle button clicks</span></span>  
  
1.  <span data-ttu-id="7c2be-183">Clique duas vezes em **Order Details** na **Form1** para criar o `Button1` manipulador de eventos e abra o editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7c2be-183">Double-click **Order Details** on **Form1** to create the `Button1` event handler and open the code editor.</span></span>  
  
2.  <span data-ttu-id="7c2be-184">Digite o código a seguir no manipulador `Button1`:</span><span class="sxs-lookup"><span data-stu-id="7c2be-184">Type the following code into the `Button1` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#2)]  
  
3.  <span data-ttu-id="7c2be-185">Agora clique duas vezes em **Button2** no Form1 para criar o `Button2` manipulador de eventos e abra o editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="7c2be-185">Now double-click **Button2** on Form1 to create the `Button2` event handler and open the code editor.</span></span>  
  
4.  <span data-ttu-id="7c2be-186">Digite o código a seguir no manipulador `Button2`:</span><span class="sxs-lookup"><span data-stu-id="7c2be-186">Type the following code into the `Button2` handler:</span></span>  
  
     [!code-vb[DLinqWalk4VB#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/DLinqWalk4VB/vb/Form1.vb#3)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="7c2be-187">Testando o aplicativo</span><span class="sxs-lookup"><span data-stu-id="7c2be-187">Testing the Application</span></span>  
 <span data-ttu-id="7c2be-188">Agora é hora de testar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7c2be-188">Now it is time to test your application.</span></span> <span data-ttu-id="7c2be-189">Observe que o contato com o repositório de dados limita-se a qualquer ação que os dois procedimentos armazenados podem executar.</span><span class="sxs-lookup"><span data-stu-id="7c2be-189">Note that your contact with the datastore is limited to whatever actions the two stored procedures can take.</span></span> <span data-ttu-id="7c2be-190">Essas ações retornarão os produtos para qualquer orderID inserida ou retornarão um histórico do produtos solicitados para qualquer CustomerID inserida.</span><span class="sxs-lookup"><span data-stu-id="7c2be-190">Those actions are to return the products included for any orderID you enter, or to return a history of products ordered for any CustomerID you enter.</span></span>  
  
#### <a name="to-test-the-application"></a><span data-ttu-id="7c2be-191">Para testar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="7c2be-191">To test the application</span></span>  
  
1.  <span data-ttu-id="7c2be-192">Pressione F5 para iniciar a depuração.</span><span class="sxs-lookup"><span data-stu-id="7c2be-192">Press F5 to start debugging.</span></span>  
  
     <span data-ttu-id="7c2be-193">Form1 aparecerá.</span><span class="sxs-lookup"><span data-stu-id="7c2be-193">Form1 appears.</span></span>  
  
2.  <span data-ttu-id="7c2be-194">No **OrderID insira** , digite **10249** e, em seguida, clique em **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-194">In the **Enter OrderID** box, type **10249** and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="7c2be-195">Uma caixa de mensagem lista os produtos incluídos no pedido 10249.</span><span class="sxs-lookup"><span data-stu-id="7c2be-195">A message box lists the products included in order 10249.</span></span>  
  
     <span data-ttu-id="7c2be-196">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7c2be-196">Click **OK** to close the message box.</span></span>  
  
3.  <span data-ttu-id="7c2be-197">No **digite CustomerID** , digite `ALFKI`e, em seguida, clique em **histórico de pedidos**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-197">In the **Enter CustomerID** box, type `ALFKI`, and then click **Order History**.</span></span>  
  
     <span data-ttu-id="7c2be-198">Uma caixa de mensagem lista o histórico de pedidos para o cliente ALFKI.</span><span class="sxs-lookup"><span data-stu-id="7c2be-198">A message box lists the order history for customer ALFKI.</span></span>  
  
     <span data-ttu-id="7c2be-199">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7c2be-199">Click **OK** to close the message box.</span></span>  
  
4.  <span data-ttu-id="7c2be-200">No **OrderID insira** , digite `123`e, em seguida, clique em **detalhes do pedido**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-200">In the **Enter OrderID** box, type `123`, and then click **Order Details**.</span></span>  
  
     <span data-ttu-id="7c2be-201">Uma caixa de mensagem não exibe “nenhum” resultado.</span><span class="sxs-lookup"><span data-stu-id="7c2be-201">A message box displays "No results."</span></span>  
  
     <span data-ttu-id="7c2be-202">Clique em **Okey** para fechar a caixa de mensagem.</span><span class="sxs-lookup"><span data-stu-id="7c2be-202">Click **OK** to close the message box.</span></span>  
  
5.  <span data-ttu-id="7c2be-203">Sobre o **depurar** menu, clique em **parar a depuração**.</span><span class="sxs-lookup"><span data-stu-id="7c2be-203">On the **Debug** menu, click **Stop debugging**.</span></span>  
  
     <span data-ttu-id="7c2be-204">A sessão de depuração é fechada.</span><span class="sxs-lookup"><span data-stu-id="7c2be-204">The debug session closes.</span></span>  
  
6.  <span data-ttu-id="7c2be-205">Se você concluiu a experimentar, você pode clicar em **fechar projeto** no **arquivo** menu e salve o projeto quando você for solicitado.</span><span class="sxs-lookup"><span data-stu-id="7c2be-205">If you have finished experimenting, you can click **Close Project** on the **File** menu, and save your project when you are prompted.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7c2be-206">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7c2be-206">Next Steps</span></span>  
 <span data-ttu-id="7c2be-207">Você pode aprimorar esse projeto fazendo algumas alterações.</span><span class="sxs-lookup"><span data-stu-id="7c2be-207">You can enhance this project by making some changes.</span></span> <span data-ttu-id="7c2be-208">Por exemplo, você pode listar os procedimentos armazenados disponíveis em uma caixa de listagem e fazer com que o usuário selecione os procedimentos que serão executados.</span><span class="sxs-lookup"><span data-stu-id="7c2be-208">For example, you could list available stored procedures in a list box and have the user select which procedures to execute.</span></span> <span data-ttu-id="7c2be-209">Você também pode transmitir a saída dos relatórios para um arquivo de texto.</span><span class="sxs-lookup"><span data-stu-id="7c2be-209">You could also stream the output of the reports to a text file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c2be-210">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7c2be-210">See Also</span></span>  
 [<span data-ttu-id="7c2be-211">Aprendendo com explicações passo a passo</span><span class="sxs-lookup"><span data-stu-id="7c2be-211">Learning by Walkthroughs</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/learning-by-walkthroughs.md)  
 [<span data-ttu-id="7c2be-212">Procedimentos armazenados</span><span class="sxs-lookup"><span data-stu-id="7c2be-212">Stored Procedures</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/stored-procedures.md)
