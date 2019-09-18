---
title: 'Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework (WCF Data Services)'
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 8c597738d656b32e7b4c75246027b726f425c6ef
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053014"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="a2e13-102">Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="a2e13-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="a2e13-103">O WCF Data Services expõe os dados da entidade como um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="a2e13-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="a2e13-104">Esses dados de entidade são fornecidos pelo ADO. NETEntity Framework quando a fonte de dados é um banco de dado relacional.</span><span class="sxs-lookup"><span data-stu-id="a2e13-104">This entity data is provided by the ADO.NETEntity Framework when the data source is a relational database.</span></span> <span data-ttu-id="a2e13-105">Este tópico mostra como criar um modelo de dados baseado em Entity Framework em um aplicativo Web do Visual Studio com base em um banco de dados existente e usar esse modelo para criar um novo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="a2e13-105">This topic shows you how to create an Entity Framework-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="a2e13-106">O Entity Framework também fornece uma ferramenta de linha de comando que pode gerar um modelo de Entity Framework fora de um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a2e13-106">The Entity Framework also provides a command line tool that can generate an Entity Framework model outside of a Visual Studio project.</span></span> <span data-ttu-id="a2e13-107">Para obter mais informações, confira [Como: Use EdmGen. exe para gerar o modelo e os arquivos](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md)de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a2e13-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="a2e13-108">Para adicionar um modelo do Entity Framework que está baseado em um banco de dados existente para um aplicativo da Web existente</span><span class="sxs-lookup"><span data-stu-id="a2e13-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="a2e13-109">No menu **projeto** , clique em **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="a2e13-110">No painel **modelos** , clique na categoria **dados** e selecione **ADO.NET modelo de dados de entidade**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="a2e13-111">Insira o nome do modelo e clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="a2e13-112">A primeira página do assistente de Modelo de Dados de Entidade é exibida.</span><span class="sxs-lookup"><span data-stu-id="a2e13-112">The first page of the Entity Data Model Wizard is displayed.</span></span>

4. <span data-ttu-id="a2e13-113">Na caixa de diálogo **escolher conteúdo do modelo** , selecione **gerar do banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="a2e13-114">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-114">Then click **Next**.</span></span>

5. <span data-ttu-id="a2e13-115">Clique no botão **nova conexão** .</span><span class="sxs-lookup"><span data-stu-id="a2e13-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="a2e13-116">Na caixa de diálogo **Propriedades da conexão** , digite o nome do servidor, selecione o método de autenticação, digite o nome do banco de dados e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="a2e13-117">A caixa de diálogo **escolher sua conexão de dados** é atualizada com as configurações de conexão do banco de dado.</span><span class="sxs-lookup"><span data-stu-id="a2e13-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="a2e13-118">Verifique se a caixa de seleção **salvar configurações de conexão de entidade em app. config as:** está marcada.</span><span class="sxs-lookup"><span data-stu-id="a2e13-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="a2e13-119">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-119">Then click **Next**.</span></span>

8. <span data-ttu-id="a2e13-120">Na caixa de diálogo **escolher seu objeto de banco** de dados, selecione todos os objetos de banco de dados que você planeja expor no Data Service.</span><span class="sxs-lookup"><span data-stu-id="a2e13-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="a2e13-121">Os objetos incluídos no modelo de dados não são expostos automaticamente pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="a2e13-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="a2e13-122">Eles devem ser explicitamente expostos pelo próprio serviço.</span><span class="sxs-lookup"><span data-stu-id="a2e13-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="a2e13-123">Para obter mais informações, consulte [Configurando o serviço de dados](configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a2e13-123">For more information, see [Configuring the Data Service](configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="a2e13-124">Clique em **concluir** para concluir o assistente.</span><span class="sxs-lookup"><span data-stu-id="a2e13-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="a2e13-125">Isso cria um modelo de dados padrão com base no banco de dados específico.</span><span class="sxs-lookup"><span data-stu-id="a2e13-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="a2e13-126">O Entity Framework permite personalizar o modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="a2e13-126">The Entity Framework enables to customize the data model.</span></span> <span data-ttu-id="a2e13-127">Para obter mais informações, consulte [tarefas de ferramentas de modelo de dados de entidade](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a2e13-127">For more information, see [Entity Data Model Tools Tasks](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb738480(v=vs.100)).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="a2e13-128">Para criar o serviço de dados usando o novo modelo de dados</span><span class="sxs-lookup"><span data-stu-id="a2e13-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="a2e13-129">No Visual Studio, abra o arquivo. edmx que representa o modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="a2e13-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="a2e13-130">No **navegador de modelos**, clique com o botão direito do mouse no modelo, clique em **Propriedades**e observe o nome do contêiner de entidade.</span><span class="sxs-lookup"><span data-stu-id="a2e13-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="a2e13-131">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do seu projeto ASP.net e clique em **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-131">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="a2e13-132">Na caixa de diálogo **Adicionar novo item** , selecione o modelo do **WCF Data Service** na categoria **Web** .</span><span class="sxs-lookup"><span data-stu-id="a2e13-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="a2e13-134">O modelo do **WCF Data Service** está disponível no visual Studio 2015, mas não no visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="a2e13-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="a2e13-135">Forneça um nome para o serviço e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="a2e13-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="a2e13-136">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="a2e13-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="a2e13-137">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="a2e13-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="a2e13-138">No código para o serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição de classe que define o serviço de dados com o tipo que herda da classe <xref:System.Data.Objects.ObjectContext> e que é o contêiner de entidade do modelo de dados, que foi observado na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="a2e13-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="a2e13-139">No código para o serviço de dados, permita que os clientes autorizados acessem os conjuntos de entidades que o serviço de dados expõe.</span><span class="sxs-lookup"><span data-stu-id="a2e13-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="a2e13-140">Para obter mais informações, consulte [criando o serviço de dados](creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="a2e13-140">For more information, see [Creating the Data Service](creating-the-data-service.md).</span></span>

8. <span data-ttu-id="a2e13-141">Para testar o serviço de dados Northwind. svc usando um navegador da Web, siga as instruções no tópico [acessando o serviço em um navegador da Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="a2e13-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a2e13-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a2e13-142">See also</span></span>

- <span data-ttu-id="a2e13-143">[Defining WCF Data Services](defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="a2e13-143">[Defining WCF Data Services](defining-wcf-data-services.md)</span></span>
- [<span data-ttu-id="a2e13-144">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="a2e13-144">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="a2e13-145">Como: Criar um serviço de dados usando o provedor de reflexão</span><span class="sxs-lookup"><span data-stu-id="a2e13-145">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="a2e13-146">Como: Criar um serviço de dados usando uma fonte de dados LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="a2e13-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](create-a-data-service-using-linq-to-sql-wcf.md)
