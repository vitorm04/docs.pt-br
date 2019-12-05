---
title: 'Como: criar um serviço de dados usando uma fonte de dados LINQ to SQL (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ to SQL
- WCF Data Services, providers
ms.assetid: 3b01c2fd-8c6e-4bf5-b38f-9e61bdc3c328
ms.openlocfilehash: cde5b9903a1fd164ce106a6a408ac4bb79976642
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802284"
---
# <a name="how-to-create-a-data-service-using-a-linq-to-sql-data-source-wcf-data-services"></a><span data-ttu-id="2f19f-102">Como: criar um serviço de dados usando uma fonte de dados LINQ to SQL (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="2f19f-102">How to: Create a Data Service Using a LINQ to SQL Data Source (WCF Data Services)</span></span>

<span data-ttu-id="2f19f-103">O WCF Data Services expõe os dados da entidade como um serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="2f19f-103">WCF Data Services exposes entity data as a data service.</span></span> <span data-ttu-id="2f19f-104">O provedor de reflexão permite que você defina um modelo de dados baseado em qualquer classe que expõe Membros que retornam uma implementação de <xref:System.Linq.IQueryable%601>.</span><span class="sxs-lookup"><span data-stu-id="2f19f-104">The reflection provider enables you to define a data model that is based on any class that exposes members that return an <xref:System.Linq.IQueryable%601> implementation.</span></span> <span data-ttu-id="2f19f-105">Para poder fazer atualizações nos dados na fonte de dados, essas classes também devem implementar a interface <xref:System.Data.Services.IUpdatable>.</span><span class="sxs-lookup"><span data-stu-id="2f19f-105">To be able to make updates to data in the data source, these classes must also implement the <xref:System.Data.Services.IUpdatable> interface.</span></span> <span data-ttu-id="2f19f-106">Para obter mais informações, consulte [provedores de serviços de dados](data-services-providers-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="2f19f-106">For more information, see [Data Services Providers](data-services-providers-wcf-data-services.md).</span></span> <span data-ttu-id="2f19f-107">Este tópico mostra como criar LINQ to SQL classes que acessam o banco de dados de exemplo Northwind usando o provedor de reflexão, além de como criar o serviço de dado baseado nessas classes de dados.</span><span class="sxs-lookup"><span data-stu-id="2f19f-107">This topic shows you how to create LINQ to SQL classes that access the Northwind sample database by using the reflection provider, as well as how to create the data service that is based on these data classes.</span></span>

## <a name="to-add-linq-to-sql-classes-to-a-project"></a><span data-ttu-id="2f19f-108">Para adicionar LINQ to SQL classes a um projeto</span><span class="sxs-lookup"><span data-stu-id="2f19f-108">To add LINQ to SQL classes to a project</span></span>

1. <span data-ttu-id="2f19f-109">De dentro de um Visual Basic C# ou aplicativo, no menu **projeto** , clique em **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="2f19f-109">From within a Visual Basic or C# application, on the **Project** menu, click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="2f19f-110">Clique no modelo **classes de LINQ to SQL** .</span><span class="sxs-lookup"><span data-stu-id="2f19f-110">Click the **LINQ to SQL Classes** template.</span></span>

3. <span data-ttu-id="2f19f-111">Altere o nome para **Northwind. dbml**.</span><span class="sxs-lookup"><span data-stu-id="2f19f-111">Change the name to **Northwind.dbml**.</span></span>

4. <span data-ttu-id="2f19f-112">Clique em **Adicionar**.</span><span class="sxs-lookup"><span data-stu-id="2f19f-112">Click **Add**.</span></span>

     <span data-ttu-id="2f19f-113">O arquivo Northwind. dbml é adicionado ao projeto e o Object Relational Designer (O/R Designer) é aberto.</span><span class="sxs-lookup"><span data-stu-id="2f19f-113">The Northwind.dbml file is added to the project and the Object Relational Designer (O/R Designer) opens.</span></span>

5. <span data-ttu-id="2f19f-114">Em **servidor**/**Gerenciador de banco de dados**, em Northwind, expanda **tabelas** e arraste a tabela `Customers` para a Object Relational Designer (o/R Designer).</span><span class="sxs-lookup"><span data-stu-id="2f19f-114">In **Server**/**Database Explorer**, under Northwind, expand **Tables** and drag the `Customers` table onto the Object Relational Designer (O/R Designer).</span></span>

     <span data-ttu-id="2f19f-115">Uma classe de entidade `Customer` é criada e exibida na superfície de design.</span><span class="sxs-lookup"><span data-stu-id="2f19f-115">A `Customer` entity class is created and appears on the design surface.</span></span>

6. <span data-ttu-id="2f19f-116">Repita a etapa 6 para as tabelas `Orders`, `Order_Details`e `Products`.</span><span class="sxs-lookup"><span data-stu-id="2f19f-116">Repeat step 6 for the `Orders`, `Order_Details`, and `Products` tables.</span></span>

7. <span data-ttu-id="2f19f-117">Clique com o botão direito do mouse no novo arquivo. dbml que representa as classes de LINQ to SQL e clique em **Exibir código**.</span><span class="sxs-lookup"><span data-stu-id="2f19f-117">Right-click the new .dbml file that represents the LINQ to SQL classes and click **View Code**.</span></span>

     <span data-ttu-id="2f19f-118">Isso cria uma nova página code-behind chamada Northwind.cs que contém uma definição de classe parcial para a classe que herda da classe <xref:System.Data.Linq.DataContext>, que nesse caso é `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="2f19f-118">This creates a new code-behind page named Northwind.cs that contains a partial class definition for the class that inherits from the <xref:System.Data.Linq.DataContext> class, which in this case is `NorthwindDataContext`.</span></span>

8. <span data-ttu-id="2f19f-119">Substitua o conteúdo do arquivo de código Northwind.cs pelo código a seguir.</span><span class="sxs-lookup"><span data-stu-id="2f19f-119">Replace the contents of the Northwind.cs code file with the following code.</span></span> <span data-ttu-id="2f19f-120">Esse código implementa o provedor de reflexão estendendo o <xref:System.Data.Linq.DataContext> e as classes de dados geradas pelo LINQ to SQL:</span><span class="sxs-lookup"><span data-stu-id="2f19f-120">This code implements the reflection provider by extending the <xref:System.Data.Linq.DataContext> and data classes generated by LINQ to SQL:</span></span>

     [!code-csharp[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.cs#linq2sqlprovider)]
     [!code-vb[Astoria Linq Provider#Linq2SqlProvider](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.vb#linq2sqlprovider)]

### <a name="to-create-a-data-service-by-using-a-linq-to-sql-based-data-model"></a><span data-ttu-id="2f19f-121">Para criar um serviço de dados usando um modelo de dados baseado em LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="2f19f-121">To create a data service by using a LINQ to SQL-based data model</span></span>

1. <span data-ttu-id="2f19f-122">Em **Gerenciador de soluções**, clique com o botão direito do mouse no nome do seu projeto ASP.net e clique em **Adicionar** > **novo item**.</span><span class="sxs-lookup"><span data-stu-id="2f19f-122">In **Solution Explorer**, right-click the name of your ASP.NET project, and then click **Add** > **New Item**.</span></span>

2. <span data-ttu-id="2f19f-123">Na caixa de diálogo **Adicionar novo item** , selecione o modelo do **WCF Data Service** na categoria **Web** .</span><span class="sxs-lookup"><span data-stu-id="2f19f-123">In the **Add New Item** dialog box, select the **WCF Data Service** template from the **Web** category.</span></span>

   ![Modelo de item do WCF Data Service no Visual Studio 2015](./media/wcf-data-service-item-template.png)

   > [!NOTE]
   > <span data-ttu-id="2f19f-125">O modelo do **WCF Data Service** está disponível no visual Studio 2015, mas não no visual Studio 2017 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="2f19f-125">The **WCF Data Service** template is available in Visual Studio 2015, but not in Visual Studio 2017 or later.</span></span>

3. <span data-ttu-id="2f19f-126">Forneça um nome para o serviço e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="2f19f-126">Supply a name for the service, and then click **OK**.</span></span>

     <span data-ttu-id="2f19f-127">O Visual Studio cria a marcação XML e arquivos de código para o novo serviço.</span><span class="sxs-lookup"><span data-stu-id="2f19f-127">Visual Studio creates the XML markup and code files for the new service.</span></span> <span data-ttu-id="2f19f-128">Por padrão, a janela do editor de códigos é aberta.</span><span class="sxs-lookup"><span data-stu-id="2f19f-128">By default, the code-editor window opens.</span></span>

4. <span data-ttu-id="2f19f-129">No código do serviço de dados, substitua o comentário `/* TODO: put your data source class name here */` na definição da classe que define o serviço de dados pelo tipo que é o contêiner de entidade do modelo de dados, que, neste caso, é `NorthwindDataContext`.</span><span class="sxs-lookup"><span data-stu-id="2f19f-129">In the code for the data service, replace the comment `/* TODO: put your data source class name here */` in the definition of the class that defines the data service with the type that is the entity container of the data model, which in this case is `NorthwindDataContext`.</span></span>

5. <span data-ttu-id="2f19f-130">No código para o serviço de dados, substitua o código de espaço reservado na função `InitializeService` pelo seguinte:</span><span class="sxs-lookup"><span data-stu-id="2f19f-130">In the code for the data service, replace the placeholder code in the `InitializeService` function with the following:</span></span>

     [!code-csharp[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_linq_provider/cs/northwind.svc.cs#enableaccess)]
     [!code-vb[Astoria Linq Provider#EnableAccess](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_linq_provider/vb/northwind.svc.vb#enableaccess)]

     <span data-ttu-id="2f19f-131">Isso permite que clientes autorizados acessem recursos para os três conjuntos de entidades especificados.</span><span class="sxs-lookup"><span data-stu-id="2f19f-131">This enables authorized clients to access resources for the three specified entity sets.</span></span>

6. <span data-ttu-id="2f19f-132">Para testar o serviço de dados Northwind. svc usando um navegador da Web, siga as instruções no tópico [acessando o serviço em um navegador da Web](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span><span class="sxs-lookup"><span data-stu-id="2f19f-132">To test the Northwind.svc data service by using a Web browser, follow the instructions in the topic [Accessing the Service from a Web Browser](accessing-the-service-from-a-web-browser-wcf-data-services-quickstart.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2f19f-133">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2f19f-133">See also</span></span>

- [<span data-ttu-id="2f19f-134">Como criar um serviço de dados usando uma fonte de dados do ADO.NET Entity Framework</span><span class="sxs-lookup"><span data-stu-id="2f19f-134">How to: Create a Data Service Using an ADO.NET Entity Framework Data Source</span></span>](create-a-data-service-using-an-adonet-ef-data-wcf.md)
- [<span data-ttu-id="2f19f-135">Como criar um serviço de dados usando o provedor de reflexão</span><span class="sxs-lookup"><span data-stu-id="2f19f-135">How to: Create a Data Service Using the Reflection Provider</span></span>](create-a-data-service-using-rp-wcf-data-services.md)
- [<span data-ttu-id="2f19f-136">Provedores de Serviços de Dados</span><span class="sxs-lookup"><span data-stu-id="2f19f-136">Data Services Providers</span></span>](data-services-providers-wcf-data-services.md)
