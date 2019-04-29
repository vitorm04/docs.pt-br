---
title: 'Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: b33eb8f470fc8ce3851c7843de992b39e86ce018
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765799"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="d426f-102">Como: Criar um serviço de dados usando um LINQ para a fonte de dados SQL (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="d426f-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="d426f-103">WCF Data Services expõe dados de entidade como um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="d426f-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="d426f-104">O provedor de reflexão permite que você defina um modelo de dados com base em qualquer classe que expõe membros que retornam um <xref:System.Linq.IQueryable%601> implementação.</span><span class="sxs-lookup"><span data-stu-id="d426f-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="d426f-105">Para poder fazer atualizações nos dados na fonte de dados, essas classes também devem implementar o <xref:System.Data.Services.IUpdatable> interface.</span><span class="sxs-lookup"><span data-stu-id="d426f-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="d426f-106">Para obter mais informações, consulte [provedores de serviços de dados](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="d426f-106">For more information, see [Data Services Providers](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="d426f-107">Este tópico mostra como criar LINQ to SQL classes que acessam o banco de dados de exemplo Northwind usando o provedor de reflexão, bem como para criar o serviço de dados com base nessas classes de dados.</span><span class="sxs-lookup"><span data-stu-id="d426f-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="d426f-108">Para adicionar LINQ to SQL classes a um projeto</span><span class="sxs-lookup"><span data-stu-id="d426f-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="d426f-109">De dentro de um aplicativo Visual Basic ou c#, sobre o **projeto** menu, clique em **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="d426f-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d426f-110">Clique o **Classes LINQ to SQL** modelo.</span><span class="sxs-lookup"><span data-stu-id="d426f-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="d426f-111">Altere o nome para **dbml**.</span><span class="sxs-lookup"><span data-stu-id="d426f-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="d426f-112">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="d426f-112">Click **Add**.</span></span>

     <span data-ttu-id="d426f-113">O arquivo dbml é adicionado ao projeto e abre o Object Relational Designer (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="d426f-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="d426f-114">Na **Server**/**Database Explorer**, em Northwind, expanda **tabelas** e arraste o `Customers` tabela em Object Relational Designer (O/R Designer).</span><span class="sxs-lookup"><span data-stu-id="d426f-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="d426f-115">Um `Customer` classe de entidade é criada e aparece na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="d426f-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="d426f-116">Repita a etapa 6 para o `Orders`, `Order_Details`, e `Products` tabelas.</span><span class="sxs-lookup"><span data-stu-id="d426f-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="d426f-117">O novo arquivo. dbml que representa o LINQ para classes SQL e clique com o botão direito **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="d426f-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="d426f-118">Isso cria uma página code-behind novo chamada Northwind.cs que contém uma definição de classe parcial para a classe que herda de <xref:System.Data.Linq.DataContext> classe, que nesse caso é `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d426f-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="d426f-119">Substitua o conteúdo do arquivo de código Northwind.cs com o código a seguir.</span><span class="sxs-lookup"><span data-stu-id="d426f-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="d426f-120">Esse código implementa o provedor de reflexão, estendendo o <xref:System.Data.Linq.DataContext> e classes de dados geradas pelo LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="d426f-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="d426f-121">Para criar um serviço de dados usando um LINQ ao modelo de dados baseado em SQL</span><span class="sxs-lookup"><span data-stu-id="d426f-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="d426f-122">Na **Gerenciador de soluções**, clique com botão direito no nome do seu projeto ASP.NET e, em seguida, clique em **Add** > **Novo Item**.</span><span class="sxs-lookup"><span data-stu-id="d426f-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="d426f-123">No **Adicionar Novo Item** caixa de diálogo, selecione o **WCF Data Service** modelo a partir o **Web** categoria.</span><span class="sxs-lookup"><span data-stu-id="d426f-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="d426f-125">O **WCF Data Service** modelo estará disponível no Visual Studio 2015, mas não no Visual Studio 2017.</span><span class="sxs-lookup"><span data-stu-id="d426f-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017.</span></span>

3. <span data-ttu-id="d426f-126">Forneça um nome para o serviço e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="d426f-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="d426f-127">O Visual Studio cria a marcação XML e os arquivos de código do novo serviço.</span><span class="sxs-lookup"><span data-stu-id="d426f-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="d426f-128">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="d426f-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="d426f-129">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="d426f-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="d426f-130">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="d426f-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="d426f-131">Isso permite que os clientes autorizados acessem recursos para os três conjuntos de entidade especificada.</span><span class="sxs-lookup"><span data-stu-id="d426f-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="d426f-132">Para testar o serviço de dados SVC usando um navegador da Web, siga as instruções no tópico [acessar o serviço de um navegador da Web](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="d426f-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](../../../../docs/framework/data/wcf/accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d426f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d426f-133">See also</span></span>

- [<span data-ttu-id="d426f-134">Como: Criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="d426f-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="d426f-135">Como: Criar um serviço de dados usando o provedor de reflexão</span><span class="sxs-lookup"><span data-stu-id="d426f-135">How to: Create a Data Service Using the Reflection Provider</span></span>](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="d426f-136">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="d426f-136">Data Services Providers</span></span>](../../../../docs/framework/data/wcf/data-services-providers-wcf-data-services.md)