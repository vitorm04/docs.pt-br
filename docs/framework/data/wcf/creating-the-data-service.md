---
title: Criando o serviço de dados
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 34d1d971-5e18-4c22-9bf6-d3612e27ea59
ms.openlocfilehash: bb6e2f7c1160fa51cd897cc953ad0ed721559294
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33362829"
---
# <a name="creating-the-data-service"></a><span data-ttu-id="4f740-102">Criando o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="4f740-102">Creating the Data Service</span></span>
<span data-ttu-id="4f740-103">Nesta tarefa, você criará um serviço de dados de exemplo que usa [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] para expor um [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed com base no banco de dados de exemplo Northwind.</span><span class="sxs-lookup"><span data-stu-id="4f740-103">In this task, you will create a sample data service that uses [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] to expose an [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed that is based on the Northwind sample database.</span></span> <span data-ttu-id="4f740-104">A tarefa envolve as seguintes etapas básicas:</span><span class="sxs-lookup"><span data-stu-id="4f740-104">The task involves the following basic steps:</span></span>  
  
1.  <span data-ttu-id="4f740-105">Criar um aplicativo Web [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f740-105">Create an [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span>  
  
2.  <span data-ttu-id="4f740-106">Definir o modelo de dados usando as ferramentas do [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4f740-106">Define the data model by using the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] tools.</span></span>  
  
3.  <span data-ttu-id="4f740-107">Adicionar o serviço de dados para o aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="4f740-107">Add the data service to the Web application.</span></span>  
  
4.  <span data-ttu-id="4f740-108">Habilitar o acesso ao serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="4f740-108">Enable access to the data service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4f740-109">O [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Web que você criar quando você concluir essa tarefa é executada [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server fornecidos pelo Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4f740-109">The [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application that you create when you complete this task runs on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server provided by Visual Studio.</span></span> <span data-ttu-id="4f740-110">O Servidor de Desenvolvimento do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] somente dá suporte a acesso do computador local.</span><span class="sxs-lookup"><span data-stu-id="4f740-110">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Development Server only supports access from the local computer.</span></span> <span data-ttu-id="4f740-111">Para facilitar o teste e a solução de problemas do serviço de dados durante o desenvolvimento, execute o aplicativo que hospeda o serviço de dados usando o IIS (Serviços de Informações da Internet).</span><span class="sxs-lookup"><span data-stu-id="4f740-111">To also make it easier to test and troubleshoot the data service during development, consider running the application that hosts the data service by using Internet Information Services (IIS).</span></span> <span data-ttu-id="4f740-112">Para obter mais informações, consulte [como: desenvolver um WCF Data Service em execução no IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span><span class="sxs-lookup"><span data-stu-id="4f740-112">For more information, see [How to: Develop a WCF Data Service Running on IIS](../../../../docs/framework/data/wcf/how-to-develop-a-wcf-data-service-running-on-iis.md).</span></span>  
  
### <a name="to-create-the-aspnet-web-application"></a><span data-ttu-id="4f740-113">Para criar o aplicativo Web do ASP.NET</span><span class="sxs-lookup"><span data-stu-id="4f740-113">To create the ASP.NET Web application</span></span>  
  
1.  <span data-ttu-id="4f740-114">No Visual Studio, no **arquivo** menu, selecione **novo**e, em seguida, selecione **projeto**.</span><span class="sxs-lookup"><span data-stu-id="4f740-114">In Visual Studio, on the **File** menu, select **New**, and then select **Project**.</span></span>  
  
2.  <span data-ttu-id="4f740-115">No **novo projeto** caixa de diálogo, em Visual Basic ou Visual c#, selecione a **Web** modelo e selecione **aplicativo Web ASP.NET**.</span><span class="sxs-lookup"><span data-stu-id="4f740-115">In the **New Project** dialog box, under either Visual Basic or Visual C# select the **Web** template, and then select **ASP.NET Web Application**.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f740-116">Se você usar o Visual Studio Web Developer, você deve criar um novo site em vez de um novo aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="4f740-116">If you use Visual Studio Web Developer, you must create a new Web site instead of a new Web application.</span></span>  
  
3.  <span data-ttu-id="4f740-117">Tipo `NorthwindService` como o nome do projeto.</span><span class="sxs-lookup"><span data-stu-id="4f740-117">Type `NorthwindService` as the name of the project.</span></span>  
  
4.  <span data-ttu-id="4f740-118">Clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="4f740-118">Click **OK**.</span></span>  
  
5.  <span data-ttu-id="4f740-119">(Opcional) Especifique um número de porta específica para seu aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="4f740-119">(Optional) Specify a specific port number for your Web application.</span></span> <span data-ttu-id="4f740-120">Observação: o número da porta `12345` é usado no restante do início rápido.</span><span class="sxs-lookup"><span data-stu-id="4f740-120">Note: the port number `12345` is used in the rest of the quickstart.</span></span>  
  
    1.  <span data-ttu-id="4f740-121">Em **Solution Explorer**, clique no nome do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] projeto a que você acabou de criado e, em seguida, clique em **propriedades**.</span><span class="sxs-lookup"><span data-stu-id="4f740-121">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project that you just created, and then click **Properties**.</span></span>  
  
    2.  <span data-ttu-id="4f740-122">Selecione o **Web** guia e defina o valor da **porta específica** caixa de texto `12345`.</span><span class="sxs-lookup"><span data-stu-id="4f740-122">Select the **Web** tab, and set the value of the **Specific port** text box to `12345`.</span></span>  
  
### <a name="to-define-the-data-model"></a><span data-ttu-id="4f740-123">Para definir o modelo de dados</span><span class="sxs-lookup"><span data-stu-id="4f740-123">To define the data model</span></span>  
  
1.  <span data-ttu-id="4f740-124">Em **Solution Explorer**, clique no nome do [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] do projeto e, em seguida, clique em **Adicionar Novo Item.**</span><span class="sxs-lookup"><span data-stu-id="4f740-124">In **Solution Explorer**, right-click the name of the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item.**</span></span>  
  
2.  <span data-ttu-id="4f740-125">No **Adicionar Novo Item** caixa de diálogo, clique o **dados** modelo e selecione **modelo de dados de entidade ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="4f740-125">In the **Add New Item** dialog box, click the **Data** template and then select **ADO.NET Entity Data Model**.</span></span>  
  
3.  <span data-ttu-id="4f740-126">Para o nome do modelo de dados, digite `Northwind.edmx`.</span><span class="sxs-lookup"><span data-stu-id="4f740-126">For the name of the data model, type `Northwind.edmx`.</span></span>  
  
4.  <span data-ttu-id="4f740-127">No [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] assistente, selecione **gerar do banco de dados**e, em seguida, clique em **próximo**.</span><span class="sxs-lookup"><span data-stu-id="4f740-127">In the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard, select **Generate from Database**, and then click **Next**.</span></span>  
  
5.  <span data-ttu-id="4f740-128">Conecte o modelo de dados para o banco de dados seguindo um destes procedimentos e, em seguida, clique em **próximo**:</span><span class="sxs-lookup"><span data-stu-id="4f740-128">Connect the data model to the database by doing one of the following steps, and then click **Next**:</span></span>  
  
    -   <span data-ttu-id="4f740-129">Se você não tiver uma conexão de banco de dados já configurado, clique em **nova Conexão** e criar uma nova conexão.</span><span class="sxs-lookup"><span data-stu-id="4f740-129">If you do not have a database connection already configured, click **New Connection** and create a new connection.</span></span> <span data-ttu-id="4f740-130">Para obter mais informações, consulte [como: criar conexões com bancos de dados do SQL Server](http://go.microsoft.com/fwlink/?LinkId=123631).</span><span class="sxs-lookup"><span data-stu-id="4f740-130">For more information, see [How to: Create Connections to SQL Server Databases](http://go.microsoft.com/fwlink/?LinkId=123631).</span></span> <span data-ttu-id="4f740-131">Esta instância do SQL Server deve ter o banco de dados de exemplo e anexado.</span><span class="sxs-lookup"><span data-stu-id="4f740-131">This SQL Server instance must have the Northwind sample database attached.</span></span>  
  
         <span data-ttu-id="4f740-132">\- ou -</span><span class="sxs-lookup"><span data-stu-id="4f740-132">\- or -</span></span>  
  
    -   <span data-ttu-id="4f740-133">Se você tiver uma conexão de banco de dados já configurada para se conectar ao banco de dados Northwind, selecione a conexão da lista de conexões.</span><span class="sxs-lookup"><span data-stu-id="4f740-133">If you have a database connection already configured to connect to the Northwind database, select that connection from the list of connections.</span></span>  
  
6.  <span data-ttu-id="4f740-134">Na página final do assistente, selecione as caixas de seleção para todas as tabelas no banco de dados e desmarque as caixas de seleção para exibições e procedimentos armazenados.</span><span class="sxs-lookup"><span data-stu-id="4f740-134">On the final page of the wizard, select the check boxes for all tables in the database, and clear the check boxes for views and stored procedures.</span></span>  
  
7.  <span data-ttu-id="4f740-135">Clique em **concluir** para fechar o assistente.</span><span class="sxs-lookup"><span data-stu-id="4f740-135">Click **Finish** to close the wizard.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f740-136">Esse modelo de dados gerado expõe as propriedades de chave estrangeira em tipos de entidade.</span><span class="sxs-lookup"><span data-stu-id="4f740-136">This generated data model exposes foreign key properties on entity types.</span></span> <span data-ttu-id="4f740-137">Os modelos de dados criados por meio do Visual Studio 2008 não incluem essas propriedades de chave estrangeira.</span><span class="sxs-lookup"><span data-stu-id="4f740-137">Data models created using Visual Studio 2008 do not include these foreign key properties.</span></span> <span data-ttu-id="4f740-138">Por isso, você deverá atualizar as classes de serviço de dados do cliente de todos os aplicativos cliente que foram criados para acessar o serviço de dados Northwind criado por meio do Visual Studio 2008 antes de tentar acessar essa versão do serviço de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="4f740-138">Because of this, you must update the client data service classes of any client applications that were created to access the Northwind data service that was created using Visual Studio 2008 before attempting to access this version of the Northwind data service.</span></span>  
  
### <a name="to-create-the-data-service"></a><span data-ttu-id="4f740-139">Para criar o serviço de dados</span><span class="sxs-lookup"><span data-stu-id="4f740-139">To create the data service</span></span>  
  
1.  <span data-ttu-id="4f740-140">Em **Solution Explorer**, clique no nome do seu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] do projeto e, em seguida, clique em **Adicionar Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="4f740-140">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add New Item**.</span></span>  
  
2.  <span data-ttu-id="4f740-141">No **Adicionar Novo Item** caixa de diálogo, selecione **WCF Data Service**.</span><span class="sxs-lookup"><span data-stu-id="4f740-141">In the **Add New Item** dialog box, select **WCF Data Service**.</span></span>  
  
3.  <span data-ttu-id="4f740-142">Para o nome do serviço, digite `Northwind`.</span><span class="sxs-lookup"><span data-stu-id="4f740-142">For the name of the service, type `Northwind`.</span></span>  
  
     <span data-ttu-id="4f740-143">O Visual StudioVisual Studio cria os arquivos de marcação e o código XML para o novo serviço.</span><span class="sxs-lookup"><span data-stu-id="4f740-143">Visual StudioVisual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="4f740-144">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="4f740-144">By default, the code-editor window opens.</span></span> <span data-ttu-id="4f740-145">Em **Solution Explorer**, o serviço terá o nome do Northwind, com a extensão. svc.cs ou. svc.vb.</span><span class="sxs-lookup"><span data-stu-id="4f740-145">In **Solution Explorer**, the service will have the name, Northwind, with the extension .svc.cs or .svc.vb.</span></span>  
  
4.  <span data-ttu-id="4f740-146">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindEntities`.</span><span class="sxs-lookup"><span data-stu-id="4f740-146">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindEntities`.</span></span> <span data-ttu-id="4f740-147">A definição da classe deve ter a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="4f740-147">The class definition should look this the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#servicedefinition)]
     [!code-vb[Astoria Quickstart Service#ServiceDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#servicedefinition)]  
  
### <a name="to-enable-access-to-data-service-resources"></a><span data-ttu-id="4f740-148">Para restringir o acesso a recursos do serviço de dados</span><span class="sxs-lookup"><span data-stu-id="4f740-148">To enable access to data service resources</span></span>  
  
1.  <span data-ttu-id="4f740-149">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="4f740-149">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>  
  
     [!code-csharp[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria quickstart service/cs/northwind.svc.cs#allreadconfig)]
     [!code-vb[Astoria Quickstart Service#AllReadConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria quickstart service/vb/northwind.svc.vb#allreadconfig)]  
  
     <span data-ttu-id="4f740-150">Isso permite que clientes autorizados tenham acesso de leitura e gravação aos recursos para os conjuntos de entidades especificados.</span><span class="sxs-lookup"><span data-stu-id="4f740-150">This enables authorized clients to have read and write access to resources for the specified entity sets.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4f740-151">Qualquer cliente que possa acessar o aplicativo [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] também poderá acessar os recursos expostos pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="4f740-151">Any client that can access the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] application can also access the resources exposed by the data service.</span></span> <span data-ttu-id="4f740-152">Em um serviço de dados de produção, para impedir o acesso não autorizado a recursos, você também deverá proteger o próprio aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4f740-152">In a production data service, to prevent unauthorized access to resources you should also secure the application itself.</span></span> <span data-ttu-id="4f740-153">Para obter mais informações, consulte [protegendo o WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="4f740-153">For more information, see [Securing WCF Data Services](../../../../docs/framework/data/wcf/securing-wcf-data-services.md).</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="4f740-154">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4f740-154">Next Steps</span></span>  
 <span data-ttu-id="4f740-155">Você criou com êxito um novo serviço de dados que expõe um [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed baseado no banco de dados de exemplo Northwind e você tiver habilitado o acesso ao feed para clientes que têm permissões no [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplicativo Web.</span><span class="sxs-lookup"><span data-stu-id="4f740-155">You have successfully created a new data service that exposes an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed that is based on the Northwind sample database, and you have enabled access to the feed for clients that have permissions on the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Web application.</span></span> <span data-ttu-id="4f740-156">Em seguida, você iniciará o serviço de dados do Visual Studio e terão acesso a [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed enviando solicitações HTTP GET por meio de um navegador da Web:</span><span class="sxs-lookup"><span data-stu-id="4f740-156">Next, you will start the data service from Visual Studio and you will access the [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] feed by submitting HTTP GET requests through a Web browser:</span></span>  
  
 [<span data-ttu-id="4f740-157">Acessando o serviço de um navegador da Web</span><span class="sxs-lookup"><span data-stu-id="4f740-157">Accessing the Service from a Web Browser</span></span>](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md)  
  
## <a name="see-also"></a><span data-ttu-id="4f740-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f740-158">See Also</span></span>  
 <span data-ttu-id="4f740-159">[ADO.NET Entity Data Model Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527) (Ferramentas de modelo de dados de entidade do ADO.NET)</span><span class="sxs-lookup"><span data-stu-id="4f740-159">[ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/library/91076853-0881-421b-837a-f582f36be527)</span></span>
