---
title: 'Como: Desenvolver um WCF Data Service em execução no IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: c9b0128de6459c65e42fc2935222aecc643ec1d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362508"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="c3752-102">Como: Desenvolver um WCF Data Service em execução no IIS</span><span class="sxs-lookup"><span data-stu-id="c3752-102">How to: Develop a WCF Data Service Running on IIS</span></span>
<span data-ttu-id="c3752-103">Este tópico mostra como usar [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para criar um serviço de dados se baseia em dados de exemplo Northwind que é hospedado por um aplicativo Web ASP.NET que está em execução nos serviços de informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="c3752-103">This topic shows how to use [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="c3752-104">Para obter um exemplo de como criar o mesmo serviço de dados Northwind como um aplicativo Web ASP.NET que é executado no servidor de desenvolvimento ASP.NET, consulte o [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c3752-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c3752-105">Para criar o serviço de dados Northwind, o banco de dados de exemplo Northwind deve estar instalado no computador local.</span><span class="sxs-lookup"><span data-stu-id="c3752-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="c3752-106">Para baixar esse banco de dados de exemplo, consulte a página de download [bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="c3752-106">To download this sample database, see the download page, [Sample Databases for SQL Server](http://go.microsoft.com/fwlink/?linkid=24758).</span></span>  
  
 <span data-ttu-id="c3752-107">Este tópico mostra como criar um serviço de dados usando o provedor de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="c3752-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="c3752-108">Outros provedores de serviços de dados estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="c3752-108">Other data services providers are available.</span></span> <span data-ttu-id="c3752-109">Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c3752-109">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="c3752-110">Após criar o serviço, você deve fornecer explicitamente acesso aos recursos de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="c3752-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="c3752-111">Para obter mais informações, consulte [como: habilitar acesso ao serviço de dados](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="c3752-111">For more information, see [How to: Enable Access to the Data Service](../../../../docs/framework/data/wcf/how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="c3752-112">Para criar o aplicativo Web ASP.NET executado no IIS</span><span class="sxs-lookup"><span data-stu-id="c3752-112">To create the ASP.NET Web application that runs on IIS</span></span>  
  
1.  <span data-ttu-id="c3752-113">No Visual Studio, no **arquivo** menu, selecione **novo**e, em seguida, selecione **projeto**.</span><span class="sxs-lookup"><span data-stu-id="c3752-113">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="c3752-114">No **novo projeto** caixa de diálogo, selecione Visual Basic ou Visual c# como linguagem de programação.</span><span class="sxs-lookup"><span data-stu-id="c3752-114">In the **New Project** dialog box, select either Visual Basic or Visual C# as the programming language.</span></span>  
  
3.  <span data-ttu-id="c3752-115">No **modelos** painel, selecione **aplicativo Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="c3752-115">In the **Templates** pane, select **ASP.NET Web Application**.</span></span> <span data-ttu-id="c3752-116">Observação: se você usar o Visual Studio Web Developer, crie um novo site em vez de um novo aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="c3752-116">Note: If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
4.  <span data-ttu-id="c3752-117">Tipo `NorthwindService` como o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="c3752-117">Type `NorthwindService` as the name of the project.</span></span>  
  
5.  <span data-ttu-id="c3752-118">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="c3752-118">Click **OK**.</span></span>  
  
6.  <span data-ttu-id="c3752-119">Sobre o **projeto** menu, selecione **NorthwindService propriedades**.</span><span class="sxs-lookup"><span data-stu-id="c3752-119">On the **Project** menu, select **NorthwindService Properties**.</span></span>  
  
7.  <span data-ttu-id="c3752-120">Selecione o **Web** guia e, em seguida, selecione **usar servidor Web do IIS Local**.</span><span class="sxs-lookup"><span data-stu-id="c3752-120">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>  
  
8.  <span data-ttu-id="c3752-121">Clique em **criar diretório Virtual** e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="c3752-121">Click **Create Virtual Directory** and then click **OK**.</span></span>  
  
9. <span data-ttu-id="c3752-122">No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):</span><span class="sxs-lookup"><span data-stu-id="c3752-122">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="c3752-123">sistemas de 32 bits:</span><span class="sxs-lookup"><span data-stu-id="c3752-123">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
    -   <span data-ttu-id="c3752-124">Sistemas de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="c3752-124">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i  
        ```  
  
     <span data-ttu-id="c3752-125">Isso garantirá que o Windows Communication Foundation (WCF) será registrado no computador.</span><span class="sxs-lookup"><span data-stu-id="c3752-125">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>  
  
10. <span data-ttu-id="c3752-126">No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):</span><span class="sxs-lookup"><span data-stu-id="c3752-126">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>  
  
    -   <span data-ttu-id="c3752-127">sistemas de 32 bits:</span><span class="sxs-lookup"><span data-stu-id="c3752-127">32-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
    -   <span data-ttu-id="c3752-128">Sistemas de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="c3752-128">64-bit systems:</span></span>  
  
        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable  
        ```  
  
     <span data-ttu-id="c3752-129">Isso garantirá que o IIS será executado corretamente após a instalação do WCF no computador.</span><span class="sxs-lookup"><span data-stu-id="c3752-129">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="c3752-130">Talvez seja necessário também reiniciar o IIS.</span><span class="sxs-lookup"><span data-stu-id="c3752-130">You might have to also restart IIS.</span></span>  
  
11. <span data-ttu-id="c3752-131">Quando o aplicativo ASP.NET for executado no IIS7, você também deverá executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="c3752-131">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>  
  
    1.  <span data-ttu-id="c3752-132">Abra o Gerenciador do IIS e navegue até o aplicativo PhotoService em **Default Web Site**.</span><span class="sxs-lookup"><span data-stu-id="c3752-132">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>  
  
    2.  <span data-ttu-id="c3752-133">Em **exibição de recursos**, clique duas vezes em **autenticação**.</span><span class="sxs-lookup"><span data-stu-id="c3752-133">In **Features View**, double-click **Authentication**.</span></span>  
  
    3.  <span data-ttu-id="c3752-134">Sobre o **autenticação** página, selecione **autenticação anônima**.</span><span class="sxs-lookup"><span data-stu-id="c3752-134">On the **Authentication** page, select **Anonymous Authentication**.</span></span>  
  
    4.  <span data-ttu-id="c3752-135">No **ações** painel, clique em **editar** para definir a segurança principal em que usuários anônimos conectará ao site.</span><span class="sxs-lookup"><span data-stu-id="c3752-135">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>  
  
    5.  <span data-ttu-id="c3752-136">No **Editar credenciais de autenticação anônima** caixa de diálogo, selecione **identidade do pool de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="c3752-136">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="c3752-137">Ao usar a conta de Serviço de Rede, você concede a usuários anônimos acesso completo à rede interna associado a essa conta.</span><span class="sxs-lookup"><span data-stu-id="c3752-137">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>  
  
12. <span data-ttu-id="c3752-138">Usando o SQL Server Management Studio, o utilitário sqlcmd.exe ou o Editor Transact-SQL no Visual Studio, execute o seguinte comando Transact-SQL na instância do SQL Server que tem o banco de dados Northwind anexado:</span><span class="sxs-lookup"><span data-stu-id="c3752-138">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>  
  
    ```sql  
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;  
    GO   
    ```  
  
     <span data-ttu-id="c3752-139">Isso cria um logon na instância do SQL Server para a conta do Windows usada para executar o IIS.</span><span class="sxs-lookup"><span data-stu-id="c3752-139">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="c3752-140">Assim, o IIS pode se conectar à instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c3752-140">This enables IIS to connect to the SQL Server instance.</span></span>  
  
13. <span data-ttu-id="c3752-141">Com o banco de dados Northwind anexado, execute os seguintes comandos Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="c3752-141">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>  
  
    ```sql  
    USE Northwind  
    GO  
    CREATE USER [NT AUTHORITY\NETWORK SERVICE]   
    FOR LOGIN [NT AUTHORITY\NETWORK SERVICE] WITH DEFAULT_SCHEMA=[dbo];  
    GO  
    ALTER LOGIN [NT AUTHORITY\NETWORK SERVICE]   
    WITH DEFAULT_DATABASE=[Northwind];   
    GO  
    EXEC sp_addrolemember 'db_datareader', 'NT AUTHORITY\NETWORK SERVICE'  
    GO  
    EXEC sp_addrolemember 'db_datawriter', 'NT AUTHORITY\NETWORK SERVICE'  
    GO   
    ```  
  
     <span data-ttu-id="c3752-142">Isso concede direitos ao novo logon, que permite ao IIS ler e gravar dados no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="c3752-142">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="c3752-143">Para definir o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="c3752-143">To define the data model</span></span>  
  
1.  <span data-ttu-id="c3752-144">Em **Solution Explorer**, clique no nome do projeto ASP.NET e, em seguida, clique em **Adicionar Novo Item.**</span><span class="sxs-lookup"><span data-stu-id="c3752-144">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="c3752-145">No **Adicionar Novo Item** caixa de diálogo, selecione **modelo de dados de entidade ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="c3752-145">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="c3752-146">Para o nome do modelo de dados, digite `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="c3752-146">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="c3752-147">No Assistente de modelo de dados de entidade, selecione **gerar do banco de dados**e, em seguida, clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="c3752-147">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="c3752-148">Conecte o modelo de dados para o banco de dados seguindo um destes procedimentos e, em seguida, clique em **próximo**:</span><span class="sxs-lookup"><span data-stu-id="c3752-148">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="c3752-149">Se você não tiver uma conexão de banco de dados já configurado, clique em **nova Conexão** e criar uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="c3752-149">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="c3752-150">Para obter mais informações, consulte [como: criar conexões com bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="c3752-150">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="c3752-151">Esta instância do SQL Server deve ter o banco de dados de exemplo e anexado.</span><span class="sxs-lookup"><span data-stu-id="c3752-151">This SQL Server instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="c3752-152">\- ou -</span><span class="sxs-lookup"><span data-stu-id="c3752-152">\- or -</span></span>  
  
    -   <span data-ttu-id="c3752-153">Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.</span><span class="sxs-lookup"><span data-stu-id="c3752-153">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="c3752-154">Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="c3752-154">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="c3752-155">Clique em **concluir** para fechar o assistente.</span><span class="sxs-lookup"><span data-stu-id="c3752-155">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c3752-156">Esse modelo de dados gerado expõe as propriedades de chave estrangeira em tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="c3752-156">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="c3752-157">Os modelos de dados criados por meio do Visual Studio 2008 não incluem essas propriedades de chave estrangeira.</span><span class="sxs-lookup"><span data-stu-id="c3752-157">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="c3752-158">Por isso, você deverá atualizar as classes de serviço de dados do cliente de todos os aplicativos cliente que foram criados para acessar o serviço de dados Northwind criado por meio do Visual Studio 2008 antes de tentar acessar essa versão do serviço de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="c3752-158">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="c3752-159">Para criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="c3752-159">To create the data service</span></span>  
  
1.  <span data-ttu-id="c3752-160">Em **Solution Explorer**, clique no nome do seu projeto do ASP.NET e, em seguida, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="c3752-160">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="c3752-161">No **Adicionar Novo Item** caixa de diálogo, selecione **serviço de dados ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="c3752-161">In the **Add New Item** dialog box, select **ADO.NET Data Service**.</span></span>  
  
3.  <span data-ttu-id="c3752-162">Para o nome do serviço, digite `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="c3752-162">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="c3752-163">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="c3752-163">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="c3752-164">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="c3752-164">By default, the code-editor window opens.</span></span> <span data-ttu-id="c3752-165">Em **Solution Explorer**, o serviço terá o nome do Northwind, com a extensão. svc.cs ou. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="c3752-165">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="c3752-166">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="c3752-166">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="c3752-167">A definição da classe deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="c3752-167">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
## <a name="see-also"></a><span data-ttu-id="c3752-168">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c3752-168">See Also</span></span>  
 [<span data-ttu-id="c3752-169">Expondo seus dados como um serviço</span><span class="sxs-lookup"><span data-stu-id="c3752-169">Exposing Your Data as a Service</span></span>](../../../../docs/framework/data/wcf/exposing-your-data-as-a-service-wcf-data-services.md)
