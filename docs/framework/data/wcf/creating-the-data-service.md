---
title: Criar um serviço de dados do WCF no Visual Studio
ms.date: 08/24/2018
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: e04f64338eaa87755510a84e7c84773c7fede807
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65634675"
---
# <a name="create-the-data-service"></a><span data-ttu-id="f571e-102">Criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="f571e-102">Create the data service</span></span>

<span data-ttu-id="f571e-103">Neste tópico, você cria um serviço de dados de exemplo que usa o WCF Data Services para expor um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed com base no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="f571e-103">In this topic, you create a sample data service that uses WCF Data Services to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that's based on the Northwind sample database.</span></span> <span data-ttu-id="f571e-104">A tarefa envolve as seguintes etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="f571e-104">The task involves the following basic steps:</span></span>

1. <span data-ttu-id="f571e-105">Crie um aplicativo Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f571e-105">Create an ASP.NET Web application.</span></span>

2. <span data-ttu-id="f571e-106">Defina o modelo de dados usando as ferramentas do modelo de dados de entidade.</span><span class="sxs-lookup"><span data-stu-id="f571e-106">Define the data model by using the Entity Data Model tools.</span></span>

3. <span data-ttu-id="f571e-107">Adicionar o serviço de dados para o aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f571e-107">Add the data service to the Web application.</span></span>

4. <span data-ttu-id="f571e-108">Habilitar o acesso ao serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="f571e-108">Enable access to the data service.</span></span>

## <a name="create-the-aspnet-web-app"></a><span data-ttu-id="f571e-109">Criar o aplicativo web ASP.NET</span><span class="sxs-lookup"><span data-stu-id="f571e-109">Create the ASP.NET web app</span></span>

1. <span data-ttu-id="f571e-110">No Visual Studio, sobre o **arquivo** menu, selecione **New** > **projeto**.</span><span class="sxs-lookup"><span data-stu-id="f571e-110">In Visual Studio, on the **File** menu, select **New** > **Project**.</span></span>

1. <span data-ttu-id="f571e-111">No **novo projeto** caixa de diálogo, em Visual Basic ou Visual c#, selecione a **Web** categoria e, em seguida, selecione **aplicativo Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="f571e-111">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** category, and then select **ASP.NET Web Application**.</span></span>

1. <span data-ttu-id="f571e-112">Insira `NorthwindService` como o nome do projeto e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f571e-112">Enter `NorthwindService` as the name of the project and then select **OK**.</span></span>

1. <span data-ttu-id="f571e-113">No **novo aplicativo Web ASP.NET** caixa de diálogo, selecione **vazia** e, em seguida, selecione **Okey**.</span><span class="sxs-lookup"><span data-stu-id="f571e-113">In the **New ASP.NET Web Application** dialog, select **Empty** and then select **OK**.</span></span>

1. <span data-ttu-id="f571e-114">(Opcional) Especifique um número de porta específica para seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="f571e-114">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="f571e-115">Observação: o número da porta `12345` é usado nesta série de tópicos do guia de início rápido.</span><span class="sxs-lookup"><span data-stu-id="f571e-115">Note: the port number `12345` is used in this series of quickstart topics.</span></span>

    1. <span data-ttu-id="f571e-116">Na **Gerenciador de soluções**, clique com botão direito no projeto ASP.NET que você acabou de criar e, em seguida, escolha **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="f571e-116">In **Solution Explorer**, right-click on the ASP.NET project that you just created, and then choose **Properties**.</span></span>

    2. <span data-ttu-id="f571e-117">Selecione o **Web** guia e defina o valor da **porta específica** caixa de texto para `12345`.</span><span class="sxs-lookup"><span data-stu-id="f571e-117">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>

## <a name="define-the-data-model"></a><span data-ttu-id="f571e-118">Definir o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="f571e-118">Define the data model</span></span>

1. <span data-ttu-id="f571e-119">Na **Gerenciador de soluções**, clique no nome do projeto ASP.NET e, em seguida, clique em **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="f571e-119">In **Solution Explorer**, right-click the name of the ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f571e-120">No **Adicionar Novo Item** caixa de diálogo, selecione o **dados** categoria e, em seguida, selecione **modelo de dados de entidade ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="f571e-120">In the **Add New Item** dialog box, select the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="f571e-121">Para o nome do modelo de dados, digite `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="f571e-121">For the name of the data model, enter `Northwind.edmx`.</span></span>

4. <span data-ttu-id="f571e-122">No **Assistente de modelo de dados de entidade**, selecione **EF Designer do banco de dados**e, em seguida, clique em **próxima**.</span><span class="sxs-lookup"><span data-stu-id="f571e-122">In the **Entity Data Model Wizard**, select **EF Designer from Database**, and then click **Next**.</span></span>

5. <span data-ttu-id="f571e-123">Conectar-se o modelo de dados no banco de dados de uma das seguintes etapas e, em seguida, clique em **próxima**:</span><span class="sxs-lookup"><span data-stu-id="f571e-123">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>

    - <span data-ttu-id="f571e-124">Se você não tiver uma conexão de banco de dados já configurada, clique em **nova Conexão** e criar uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="f571e-124">If you don't have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="f571e-125">Para obter mais informações, confira [Como: Criar conexões com bancos de dados do SQL Server](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="f571e-125">For more information, see [How to: Create Connections to SQL Server Databases](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/s4yys16a(v=vs.90)).</span></span> <span data-ttu-id="f571e-126">Esta instância do SQL Server deve ter o banco de dados de exemplo Northwind anexado.</span><span class="sxs-lookup"><span data-stu-id="f571e-126">This SQL Server instance must have the Northwind sample database attached.</span></span>

         <span data-ttu-id="f571e-127">\- ou -</span><span class="sxs-lookup"><span data-stu-id="f571e-127">\- or -</span></span>

    - <span data-ttu-id="f571e-128">Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.</span><span class="sxs-lookup"><span data-stu-id="f571e-128">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>

6. <span data-ttu-id="f571e-129">Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="f571e-129">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>

7. <span data-ttu-id="f571e-130">Clique em **concluir** para fechar o assistente.</span><span class="sxs-lookup"><span data-stu-id="f571e-130">Click **Finish** to close the wizard.</span></span>

## <a name="create-the-wcf-data-service"></a><span data-ttu-id="f571e-131">Criar o serviço de dados do WCF</span><span class="sxs-lookup"><span data-stu-id="f571e-131">Create the WCF data service</span></span>

1. <span data-ttu-id="f571e-132">Na **Gerenciador de soluções**, clique com botão direito no projeto do ASP.NET e, em seguida, escolha **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="f571e-132">In **Solution Explorer**, right-click on the ASP.NET project, and then choose **Add** > **New Item**.</span></span>

2. <span data-ttu-id="f571e-133">No **Adicionar Novo Item** caixa de diálogo, selecione o **WCF Data Service** modelo de item dos **Web** categoria.</span><span class="sxs-lookup"><span data-stu-id="f571e-133">In the **Add New Item** dialog box, select the **WCF Data Service** item template from the **Web** category.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="f571e-135">O **WCF Data Service** modelo estará disponível no Visual Studio 2015, mas não no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="f571e-135">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="f571e-136">Para o nome do serviço, digite `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="f571e-136">For the name of the service, type `Northwind`.</span></span>

     <span data-ttu-id="f571e-137">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="f571e-137">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="f571e-138">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="f571e-138">By default, the code-editor window opens.</span></span> <span data-ttu-id="f571e-139">Na **Gerenciador de soluções**, o serviço tem o nome Northwind com a extensão *. svc.cs* ou *. svc*.</span><span class="sxs-lookup"><span data-stu-id="f571e-139">In **Solution Explorer**, the service has the name Northwind with the extension *.svc.cs* or *.svc.vb*.</span></span>

4. <span data-ttu-id="f571e-140">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="f571e-140">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="f571e-141">A definição da classe deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="f571e-141">The class definition should look this the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#servicedefinition)]

## <a name="enable-access-to-data-service-resources"></a><span data-ttu-id="f571e-142">Habilitar o acesso aos recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="f571e-142">Enable access to data service resources</span></span>

1. <span data-ttu-id="f571e-143">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="f571e-143">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_service/vb/northwind.svc.vb#allreadconfig)]

     <span data-ttu-id="f571e-144">Isso permite que clientes autorizados tenham acesso de leitura e gravação aos recursos para os conjuntos de entidades especificados.</span><span class="sxs-lookup"><span data-stu-id="f571e-144">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f571e-145">Qualquer cliente que pode acessar o aplicativo ASP.NET também pode acessar os recursos expostos pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="f571e-145">Any client that can access the ASP.NET application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="f571e-146">Em um serviço de dados de produção, para impedir o acesso não autorizado a recursos, você também deverá proteger o próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="f571e-146">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="f571e-147">Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="f571e-147">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="f571e-148">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="f571e-148">Next steps</span></span>

<span data-ttu-id="f571e-149">Você criou com êxito um novo serviço de dados que expõe um feed de OData com base no banco de dados de exemplo Northwind, e você tiver habilitado o acesso a feed para clientes que têm permissões no aplicativo Web do ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="f571e-149">You have successfully created a new data service that exposes an OData feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the ASP.NET Web application.</span></span> <span data-ttu-id="f571e-150">Em seguida, inicie o serviço de dados do Visual Studio e acessar o feed enviando solicitações HTTP GET por meio de um navegador da Web OData:</span><span class="sxs-lookup"><span data-stu-id="f571e-150">Next, you'll start the data service from Visual Studio and access the OData feed by submitting HTTP GET requests through a Web browser:</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f571e-151">Acessar o serviço de um navegador da web</span><span class="sxs-lookup"><span data-stu-id="f571e-151">Access the service from a web browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)

## <a name="see-also"></a><span data-ttu-id="f571e-152">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f571e-152">See also</span></span>

- <span data-ttu-id="f571e-153">[Ferramentas de modelo de dados de entidade ADO.NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f571e-153">[ADO.NET Entity Data Model Tools](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb399249(v=vs.100))</span></span>
