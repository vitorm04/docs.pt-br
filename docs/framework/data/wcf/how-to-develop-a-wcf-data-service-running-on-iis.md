---
title: 'Como: desenvolver um serviço de dados do WCF em execução no IIS'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, developing
- WCF Data Services, deploying
- WCF Data Services, hosting
ms.assetid: f6f768c5-4989-49e3-a36f-896ab4ded86e
ms.openlocfilehash: 89be7aa8339a4edf6d6ab9c0c243e4320d2fdfa8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052970"
---
# <a name="how-to-develop-a-wcf-data-service-running-on-iis"></a><span data-ttu-id="d818f-102">Como: Desenvolver um serviço de dados WCF em execução no IIS</span><span class="sxs-lookup"><span data-stu-id="d818f-102">How to: Develop a WCF data service running on IIS</span></span>

<span data-ttu-id="d818f-103">Este tópico mostra como usar WCF Data Services para criar um serviço de dados que é baseado no exemplo Northwind que é hospedado por um aplicativo Web ASP.NET em execução no Serviços de Informações da Internet (IIS).</span><span class="sxs-lookup"><span data-stu-id="d818f-103">This topic shows how to use WCF Data Services to create a data service that is based on the Northwind sample database that is hosted by an ASP.NET Web application that is running on Internet Information Services (IIS).</span></span> <span data-ttu-id="d818f-104">Para obter um exemplo de como criar o mesmo serviço de dados Northwind como um aplicativo Web ASP.NET que é executado no ASP.NET Development Server, consulte o guia de [início rápido WCF Data Services](quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d818f-104">For an example of how to create the same Northwind data service as an ASP.NET Web application that runs on the ASP.NET Development Server, see the [WCF Data Services quickstart](quickstart-wcf-data-services.md).</span></span>

> [!NOTE]
> <span data-ttu-id="d818f-105">Para criar o serviço de dados Northwind, o banco de dados de exemplo Northwind deve estar instalado no computador local.</span><span class="sxs-lookup"><span data-stu-id="d818f-105">To create the Northwind data service, you must have installed the Northwind sample database on the local computer.</span></span> <span data-ttu-id="d818f-106">Para baixar esse banco de dados de exemplo, consulte a página de download, [bancos de dados de exemplo para SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span><span class="sxs-lookup"><span data-stu-id="d818f-106">To download this sample database, see the download page, [Sample Databases for SQL Server](https://go.microsoft.com/fwlink/?linkid=24758).</span></span>

<span data-ttu-id="d818f-107">Este tópico mostra como criar um serviço de dados usando o provedor de Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="d818f-107">This topic shows how to create a data service by using the Entity Framework provider.</span></span> <span data-ttu-id="d818f-108">Outros provedores de serviços de dados estão disponíveis.</span><span class="sxs-lookup"><span data-stu-id="d818f-108">Other data services providers are available.</span></span> <span data-ttu-id="d818f-109">Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d818f-109">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span>

<span data-ttu-id="d818f-110">Após criar o serviço, você deve fornecer explicitamente acesso aos recursos de serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="d818f-110">After you create the service, you must explicitly provide access to data service resources.</span></span> <span data-ttu-id="d818f-111">Para obter mais informações, confira [Como: Habilite o acesso ao serviço](how-to-enable-access-to-the-data-service-wcf-data-services.md)de dados.</span><span class="sxs-lookup"><span data-stu-id="d818f-111">For more information, see [How to: Enable Access to the Data Service](how-to-enable-access-to-the-data-service-wcf-data-services.md).</span></span>

## <a name="create-the-aspnet-web-application-that-runs-on-iis"></a><span data-ttu-id="d818f-112">Criar o aplicativo Web ASP.NET que é executado no IIS</span><span class="sxs-lookup"><span data-stu-id="d818f-112">Create the ASP.NET web application that runs on IIS</span></span>

1. <span data-ttu-id="d818f-113">No Visual Studio, no menu **arquivo** , selecione **novo** > **projeto**.</span><span class="sxs-lookup"><span data-stu-id="d818f-113">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

2. <span data-ttu-id="d818f-114">Na caixa de diálogo **novo projeto** , selecione a categoria **da Web** > **instalada** [ **C# Visual** ou **Visual Basic**] >.</span><span class="sxs-lookup"><span data-stu-id="d818f-114">In the **New Project** dialog box, select the **Installed** > [**Visual C#** or **Visual Basic**] > **Web** category.</span></span>

3. <span data-ttu-id="d818f-115">Selecione o modelo de **aplicativo Web ASP.net** .</span><span class="sxs-lookup"><span data-stu-id="d818f-115">Select the **ASP.NET Web Application** template.</span></span>

4. <span data-ttu-id="d818f-116">Insira `NorthwindService` como o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="d818f-116">Enter `NorthwindService` as the name of the project.</span></span>

5. <span data-ttu-id="d818f-117">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d818f-117">Click **OK**.</span></span>

6. <span data-ttu-id="d818f-118">No menu **projeto** , selecione **NorthwindService Propriedades**.</span><span class="sxs-lookup"><span data-stu-id="d818f-118">On the **Project** menu, select **NorthwindService Properties**.</span></span>

7. <span data-ttu-id="d818f-119">Selecione a guia **Web** e, em seguida, selecione **usar servidor Web IIS local**.</span><span class="sxs-lookup"><span data-stu-id="d818f-119">Select the **Web** tab, and then select **Use Local IIS Web Server**.</span></span>

8. <span data-ttu-id="d818f-120">Clique em **criar diretório virtual** e em **OK**.</span><span class="sxs-lookup"><span data-stu-id="d818f-120">Click **Create Virtual Directory** and then click **OK**.</span></span>

9. <span data-ttu-id="d818f-121">No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):</span><span class="sxs-lookup"><span data-stu-id="d818f-121">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="d818f-122">sistemas de 32 bits:</span><span class="sxs-lookup"><span data-stu-id="d818f-122">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

    - <span data-ttu-id="d818f-123">Sistemas de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="d818f-123">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v3.0\Windows Communication Foundation\ServiceModelReg.exe" -i
        ```

     <span data-ttu-id="d818f-124">Isso garantirá que o Windows Communication Foundation (WCF) será registrado no computador.</span><span class="sxs-lookup"><span data-stu-id="d818f-124">This makes sure that Windows Communication Foundation (WCF) is registered on the computer.</span></span>

10. <span data-ttu-id="d818f-125">No prompt de comando com privilégios de administrador, execute um dos seguintes comandos (dependendo do sistema operacional):</span><span class="sxs-lookup"><span data-stu-id="d818f-125">From the command prompt with administrator privileges, execute one of the following commands (depending on the operating system):</span></span>

    - <span data-ttu-id="d818f-126">sistemas de 32 bits:</span><span class="sxs-lookup"><span data-stu-id="d818f-126">32-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

    - <span data-ttu-id="d818f-127">Sistemas de 64 bits:</span><span class="sxs-lookup"><span data-stu-id="d818f-127">64-bit systems:</span></span>

        ```console
        "%windir%\Microsoft.NET\Framework64\v4.0.30319\aspnet_regiis.exe" -i -enable
        ```

     <span data-ttu-id="d818f-128">Isso garantirá que o IIS será executado corretamente após a instalação do WCF no computador.</span><span class="sxs-lookup"><span data-stu-id="d818f-128">This makes sure that IIS runs correctly after WCF has been installed on the computer.</span></span> <span data-ttu-id="d818f-129">Talvez seja necessário também reiniciar o IIS.</span><span class="sxs-lookup"><span data-stu-id="d818f-129">You might have to also restart IIS.</span></span>

11. <span data-ttu-id="d818f-130">Quando o aplicativo ASP.NET for executado no IIS7, você também deverá executar as seguintes etapas:</span><span class="sxs-lookup"><span data-stu-id="d818f-130">When the ASP.NET application runs on IIS7, you must also perform the following steps:</span></span>

    1. <span data-ttu-id="d818f-131">Abra o Gerenciador do IIS e navegue até o aplicativo de serviço em **site da Web padrão**.</span><span class="sxs-lookup"><span data-stu-id="d818f-131">Open IIS Manager and navigate to the PhotoService application under **Default Web Site**.</span></span>

    2. <span data-ttu-id="d818f-132">Na **exibição recursos**, clique duas vezes em **autenticação**.</span><span class="sxs-lookup"><span data-stu-id="d818f-132">In **Features View**, double-click **Authentication**.</span></span>

    3. <span data-ttu-id="d818f-133">Na página **autenticação** , selecione **autenticação anônima**.</span><span class="sxs-lookup"><span data-stu-id="d818f-133">On the **Authentication** page, select **Anonymous Authentication**.</span></span>

    4. <span data-ttu-id="d818f-134">No painel **ações** , clique em **Editar** para definir a entidade de segurança sob a qual os usuários anônimos se conectarão ao site.</span><span class="sxs-lookup"><span data-stu-id="d818f-134">In the **Actions** pane, click **Edit** to set the security principal under which anonymous users will connect to the site.</span></span>

    5. <span data-ttu-id="d818f-135">Na caixa de diálogo **Editar credenciais de autenticação anônima** , selecione **identidade do pool de aplicativos**.</span><span class="sxs-lookup"><span data-stu-id="d818f-135">In the **Edit Anonymous Authentication Credentials** dialog box, select **Application pool identity**.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="d818f-136">Ao usar a conta de Serviço de Rede, você concede a usuários anônimos acesso completo à rede interna associado a essa conta.</span><span class="sxs-lookup"><span data-stu-id="d818f-136">When you use the Network Service account, you grant anonymous users all the internal network access associated with that account.</span></span>

12. <span data-ttu-id="d818f-137">Usando o SQL Server Management Studio, o utilitário sqlcmd.exe ou o Editor Transact-SQL no Visual Studio, execute o seguinte comando Transact-SQL na instância do SQL Server que tem o banco de dados Northwind anexado:</span><span class="sxs-lookup"><span data-stu-id="d818f-137">By using SQL Server Management Studio, the sqlcmd.exe utility, or the Transact-SQL Editor in Visual Studio, execute the following Transact-SQL command against the instance of SQL Server that has the Northwind database attached:</span></span>

    ```sql
    CREATE LOGIN [NT AUTHORITY\NETWORK SERVICE] FROM WINDOWS;
    GO
    ```

    <span data-ttu-id="d818f-138">Isso cria um logon na instância do SQL Server para a conta do Windows usada para executar o IIS.</span><span class="sxs-lookup"><span data-stu-id="d818f-138">This creates a login in the SQL Server instance for the Windows account used to run IIS.</span></span> <span data-ttu-id="d818f-139">Assim, o IIS pode se conectar à instância do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d818f-139">This enables IIS to connect to the SQL Server instance.</span></span>

13. <span data-ttu-id="d818f-140">Com o banco de dados Northwind anexado, execute os seguintes comandos Transact-SQL:</span><span class="sxs-lookup"><span data-stu-id="d818f-140">With the Northwind database attached, execute the following Transact-SQL commands:</span></span>

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

    <span data-ttu-id="d818f-141">Isso concede direitos ao novo logon, que permite ao IIS ler e gravar dados no banco de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="d818f-141">This grants rights to the new login, which enables IIS to read data from and write data to the Northwind database.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="d818f-142">Definir o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="d818f-142">Define the data model</span></span>

1. <span data-ttu-id="d818f-143">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do projeto ASP.net e clique em **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="d818f-143">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d818f-144">Na caixa de diálogo **Adicionar novo item** , selecione **ADO.NET modelo de dados de entidade**.</span><span class="sxs-lookup"><span data-stu-id="d818f-144">In the **Add New Item** dialog box, select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="d818f-145">Para o nome do modelo de dados, digite `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="d818f-145">For the name of the data model, type `Northwind.edmx`.</span></span>

4. <span data-ttu-id="d818f-146">No assistente de Modelo de Dados de Entidade, selecione **gerar do banco de dados**e clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="d818f-146">In the Entity Data Model Wizard, select **Generate from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="d818f-147">Conecte o modelo de dados ao banco de dado executando uma das etapas a seguir e clique em **Avançar**:</span><span class="sxs-lookup"><span data-stu-id="d818f-147">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="d818f-148">Se você não tiver uma conexão de banco de dados já configurada, clique em **nova conexão** e crie uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="d818f-148">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="d818f-149">Para obter mais informações, confira [Como: Crie conexões com bancos de dados](https://go.microsoft.com/fwlink/?LinkId=123631)SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d818f-149">For more information, see [How to: Create Connections to SQL Server Databases](https://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="d818f-150">Esta instância de SQL Server deve ter o banco de dados de exemplo Northwind anexado.</span><span class="sxs-lookup"><span data-stu-id="d818f-150">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="d818f-151">\- ou -</span><span class="sxs-lookup"><span data-stu-id="d818f-151">\- or -</span></span>

    - <span data-ttu-id="d818f-152">Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.</span><span class="sxs-lookup"><span data-stu-id="d818f-152">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="d818f-153">Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="d818f-153">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="d818f-154">Clique em **Concluir** para fechar o assistente.</span><span class="sxs-lookup"><span data-stu-id="d818f-154">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-data-service"></a><span data-ttu-id="d818f-155">Criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="d818f-155">Create the data service</span></span>

1. <span data-ttu-id="d818f-156">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do seu projeto ASP.net e clique em **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="d818f-156">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d818f-157">Na caixa de diálogo **Adicionar novo item** , selecione **WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="d818f-157">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="d818f-159">O modelo do **WCF Data Service** está disponível no visual Studio 2015, mas não no visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d818f-159">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="d818f-160">Para o nome do serviço, digite `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="d818f-160">For the name of the service, enter `Northwind`.</span></span>

     <span data-ttu-id="d818f-161">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="d818f-161">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="d818f-162">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="d818f-162">By default, the code-editor window opens.</span></span> <span data-ttu-id="d818f-163">No **Gerenciador de soluções**, o serviço tem o nome, Northwind e a extensão. svc.cs ou. svc. vb.</span><span class="sxs-lookup"><span data-stu-id="d818f-163">In **Solution Explorer**, the service has the name, Northwind, and the extension .svc.cs or .svc.vb.</span></span>

4. <span data-ttu-id="d818f-164">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="d818f-164">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="d818f-165">A definição da classe deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="d818f-165">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="see-also"></a><span data-ttu-id="d818f-166">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d818f-166">See also</span></span>

- [<span data-ttu-id="d818f-167">Expondo seus dados como um serviço</span><span class="sxs-lookup"><span data-stu-id="d818f-167">Exposing Your Data as a Service</span></span>](exposing-your-data-as-a-service-wcf-data-services.md)
