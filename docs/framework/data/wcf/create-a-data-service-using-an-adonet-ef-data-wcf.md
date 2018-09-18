---
title: Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework (WCF Data Services)
ms.date: 08/24/2018
helpviewer_keywords:
- WCF Data Services, providers
- WCF Data Services, Entity Framework
ms.assetid: 6d11fec8-0108-42f5-8719-2a7866d04428
ms.openlocfilehash: 4bccd1e4655786ae24166cdc32619b420c4a54d3
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46009224"
---
# <a name="how-to-create-a-data-service-using-an-adonet-entity-framework-data-source-wcf-data-services"></a><span data-ttu-id="bd45c-102">Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="bd45c-102">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source (WCF Data Services)</span></span>

<span data-ttu-id="bd45c-103">WCF Data Services expõe dados de entidade como um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="bd45c-104">Esses dados de entidade são fornecidos pelo [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] quando a fonte de dados é um banco de dados relacional.</span><span class="sxs-lookup"><span data-stu-id="bd45c-104">This entity data is provided by the [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)][!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] when the data source is a relational database.</span></span> <span data-ttu-id="bd45c-105">Este tópico mostra como criar um [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-com base em modelo de dados em um aplicativo Web do Visual Studio com base em um banco de dados existente e usa esse modelo de dados para criar um novo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-105">This topic shows you how to create an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)]-based data model in a Visual Studio Web application that is based on an existing database and use this data model to create a new data service.</span></span>

<span data-ttu-id="bd45c-106">O [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] também fornece uma ferramenta de linha de comando que pode gerar um [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] modelo fora de um projeto do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="bd45c-106">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] also provides a command line tool that can generate an [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] model outside of a Visual Studio project.</span></span> <span data-ttu-id="bd45c-107">Para obter mais informações, consulte [como: Use EdmGen.exe para gerar arquivos de modelo e mapeamento](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="bd45c-107">For more information, see [How to: Use EdmGen.exe to Generate the Model and Mapping Files](../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).</span></span>

## <a name="to-add-an-entity-framework-model-that-is-based-on-an-existing-database-to-an-existing-web-application"></a><span data-ttu-id="bd45c-108">Para adicionar um modelo do Entity Framework que está baseado em um banco de dados existente para um aplicativo da Web existente</span><span class="sxs-lookup"><span data-stu-id="bd45c-108">To add an Entity Framework model that is based on an existing database to an existing Web application</span></span>

1. <span data-ttu-id="bd45c-109">Sobre o **projeto** menu, clique em **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-109">On the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="bd45c-110">No **modelos** painel, clique no **dados** categoria e, em seguida, selecione **modelo de dados de entidade ADO.NET**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-110">In the **Templates** pane, click the **Data** category, and then select **ADO.NET Entity Data Model**.</span></span>

3. <span data-ttu-id="bd45c-111">Insira o nome do modelo e, em seguida, clique em **adicionar**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-111">Enter the model name and then click **Add**.</span></span>

     <span data-ttu-id="bd45c-112">A primeira página do assistente do [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] é exibida.</span><span class="sxs-lookup"><span data-stu-id="bd45c-112">The first page of the [!INCLUDE[adonet_edm](../../../../includes/adonet-edm-md.md)] Wizard is displayed.</span></span>

4. <span data-ttu-id="bd45c-113">No **escolher conteúdo do modelo** caixa de diálogo, selecione **gerar a partir do banco de dados**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-113">In the **Choose Model Contents** dialog box, select **Generate from database**.</span></span> <span data-ttu-id="bd45c-114">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-114">Then click **Next**.</span></span>

5. <span data-ttu-id="bd45c-115">Clique o **nova Conexão** botão.</span><span class="sxs-lookup"><span data-stu-id="bd45c-115">Click the **New Connection** button.</span></span>

6. <span data-ttu-id="bd45c-116">No **propriedades de Conexão** caixa de diálogo, digite o nome do servidor, selecione o método de autenticação, digite o nome do banco de dados e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-116">In the **Connection Properties** dialog box, type your server name, select the authentication method, type the database name, and then click **OK**.</span></span>

     <span data-ttu-id="bd45c-117">O **escolha sua Conexão de dados** caixa de diálogo é atualizada com as configurações de conexão de banco de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-117">The **Choose Your Data Connection** dialog box is updated with your database connection settings.</span></span>

7. <span data-ttu-id="bd45c-118">Certifique-se de que o **salvar configurações de conexão de entidade em App. config como:** caixa de seleção é marcada.</span><span class="sxs-lookup"><span data-stu-id="bd45c-118">Ensure that the **Save entity connection settings in App.Config as:** checkbox is checked.</span></span> <span data-ttu-id="bd45c-119">Clique em **Avançar**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-119">Then click **Next**.</span></span>

8. <span data-ttu-id="bd45c-120">No **Choose Your Database Objects** objetos de selecionar tudo do banco de dados de caixa de diálogo, que você planeja expor no serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-120">In the **Choose Your Database Objects** dialog box, select all of database objects that you plan to expose in the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="bd45c-121">Os objetos incluídos no modelo de dados não são expostos automaticamente pelo serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-121">Objects included in the data model are not automatically exposed by the data service.</span></span> <span data-ttu-id="bd45c-122">Eles devem ser explicitamente expostos pelo próprio serviço.</span><span class="sxs-lookup"><span data-stu-id="bd45c-122">They must be explicitly exposed by the service itself.</span></span> <span data-ttu-id="bd45c-123">Para obter mais informações, consulte [Configurando o serviço de dados](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="bd45c-123">For more information, see [Configuring the Data Service](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).</span></span>

9. <span data-ttu-id="bd45c-124">Clique em **concluir** para concluir o assistente.</span><span class="sxs-lookup"><span data-stu-id="bd45c-124">Click **Finish** to complete the wizard.</span></span>

     <span data-ttu-id="bd45c-125">Isso cria um modelo de dados padrão com base no banco de dados específico.</span><span class="sxs-lookup"><span data-stu-id="bd45c-125">This creates a default data model based on the specific database.</span></span> <span data-ttu-id="bd45c-126">O [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] permite personalizar o modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-126">The [!INCLUDE[adonet_ef](../../../../includes/adonet-ef-md.md)] enables to customize the data model.</span></span> <span data-ttu-id="bd45c-127">Para obter mais informações, consulte [Tarefas](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span><span class="sxs-lookup"><span data-stu-id="bd45c-127">For more information, see [Tasks](https://msdn.microsoft.com/library/7166f1f1-4de8-4bd4-86b5-5e20a2ebaccb).</span></span>

## <a name="to-create-the-data-service-by-using-the-new-data-model"></a><span data-ttu-id="bd45c-128">Para criar o serviço de dados usando o novo modelo de dados</span><span class="sxs-lookup"><span data-stu-id="bd45c-128">To create the data service by using the new data model</span></span>

1. <span data-ttu-id="bd45c-129">No Visual Studio, abra o arquivo. edmx que representa o modelo de dados.</span><span class="sxs-lookup"><span data-stu-id="bd45c-129">In Visual Studio, open the .edmx file that represents the data model.</span></span>

2. <span data-ttu-id="bd45c-130">No **Model Browser**, o modelo com o botão direito, clique em **propriedades**e, em seguida, anote o nome do contêiner de entidade.</span><span class="sxs-lookup"><span data-stu-id="bd45c-130">In the **Model Browser**, right-click the model, click **Properties**, and then note the name of the entity container.</span></span>

3. <span data-ttu-id="bd45c-131">Na **Gerenciador de soluções**, clique no nome do seu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] de projeto e, em seguida, clique em **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-131">In **Solution Explorer**, right-click the name of your [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] project, and then click **Add** > **New Item**.</span></span>

4. <span data-ttu-id="bd45c-132">No **Adicionar Novo Item** caixa de diálogo, selecione o **WCF Data Service** modelo no **Web** categoria.</span><span class="sxs-lookup"><span data-stu-id="bd45c-132">In the **Add New Item** dialog box, select the **WCF Data Service** template in the **Web** category.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="bd45c-134">O **WCF Data Service** modelo estará disponível no Visual Studio 2015, mas não no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="bd45c-134">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

5. <span data-ttu-id="bd45c-135">Forneça um nome para o serviço e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="bd45c-135">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="bd45c-136">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="bd45c-136">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="bd45c-137">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="bd45c-137">By default, the code-editor window opens.</span></span>

6. <span data-ttu-id="bd45c-138">No código para o serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição de classe que define o serviço de dados com o tipo que herda da classe <xref:System.Data.Objects.ObjectContext> e que é o contêiner de entidade do modelo de dados, que foi observado na etapa 2.</span><span class="sxs-lookup"><span data-stu-id="bd45c-138">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that inherits from the <xref:System.Data.Objects.ObjectContext> class and that is the entity container of the data model, which was noted in step 2.</span></span>

7. <span data-ttu-id="bd45c-139">No código para o serviço de dados, permita que os clientes autorizados acessem os conjuntos de entidades que o serviço de dados expõe.</span><span class="sxs-lookup"><span data-stu-id="bd45c-139">In the code for the data service, enable authorized clients to access the entity sets that the data service exposes.</span></span> <span data-ttu-id="bd45c-140">Para obter mais informações, consulte [criando o serviço de dados](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span><span class="sxs-lookup"><span data-stu-id="bd45c-140">For more information, see [Creating the Data Service](../../../../docs/framework/data/wcf/creating-the-data-service.md).</span></span>

8. <span data-ttu-id="bd45c-141">Para testar o serviço de dados SVC usando um navegador da Web, siga as instruções no tópico [acessar o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="bd45c-141">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bd45c-142">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bd45c-142">See Also</span></span>

- <span data-ttu-id="bd45c-143">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md) (Definindo o WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="bd45c-143">[Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)</span></span>
- [<span data-ttu-id="bd45c-144">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="bd45c-144">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)
- [<span data-ttu-id="bd45c-145">Como criar um serviço de dados usando o provedor de reflexão</span><span class="sxs-lookup"><span data-stu-id="bd45c-145">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="bd45c-146">Como criar um serviço de dados usando uma fonte de dados LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="bd45c-146">How to: Create a Data Service Using a LINQ to SQL Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-linq-to-sql-wcf.md)