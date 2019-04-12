---
title: Criando o aplicativo cliente do .NET Framework (Início rápido do WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 41ade767-eeab-437d-9121-9797e8fb8045
ms.openlocfilehash: dfc08d4623f124a41412907f5a118e8d9ee7833d
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517766"
---
# <a name="creating-the-net-framework-client-application-wcf-data-services-quickstart"></a><span data-ttu-id="8569f-102">Criando o aplicativo cliente do .NET Framework (Início rápido do WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="8569f-102">Creating the .NET Framework Client Application (WCF Data Services Quickstart)</span></span>

<span data-ttu-id="8569f-103">Esta é a tarefa final do início rápido WCF Data Services.</span><span class="sxs-lookup"><span data-stu-id="8569f-103">This is the final task of the WCF Data Services quickstart.</span></span> <span data-ttu-id="8569f-104">Nesta tarefa, você irá adicionar um aplicativo de console à solução, adicione uma referência para o [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] alimentar a esse novo aplicativo de cliente e acessar o feed OData do aplicativo cliente usando as classes de serviço de dados do cliente gerado e bibliotecas de cliente .</span><span class="sxs-lookup"><span data-stu-id="8569f-104">In this task, you will add a console application to the solution, add a reference to the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] feed into this new client application, and access the OData feed from the client application by using the generated client data service classes and client libraries.</span></span>

> [!NOTE]
> <span data-ttu-id="8569f-105">Um aplicativo cliente baseado no .NET framework não é necessário para acessar um feed de dados.</span><span class="sxs-lookup"><span data-stu-id="8569f-105">A .NET Framework-based client application is not required to access a data feed.</span></span> <span data-ttu-id="8569f-106">O serviço de dados pode ser acessado por qualquer componente do aplicativo que consome um feed OData.</span><span class="sxs-lookup"><span data-stu-id="8569f-106">The data service can be accessed by any application component that consumes an OData feed.</span></span> <span data-ttu-id="8569f-107">Para obter mais informações, consulte [usando um serviço de dados em um aplicativo cliente](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="8569f-107">For more information, see [Using a Data Service in a Client Application](../../../../docs/framework/data/wcf/using-a-data-service-in-a-client-application-wcf-data-services.md).</span></span>

## <a name="to-create-the-client-application-by-using-visual-studio"></a><span data-ttu-id="8569f-108">Para criar o aplicativo cliente usando Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8569f-108">To create the client application by using Visual Studio</span></span>

1. <span data-ttu-id="8569f-109">Na **Gerenciador de soluções**, a solução com o botão direito, clique em **Add**e, em seguida, clique em **novo projeto**.</span><span class="sxs-lookup"><span data-stu-id="8569f-109">In **Solution Explorer**, right-click the solution, click **Add**, and then click **New Project**.</span></span>

2. <span data-ttu-id="8569f-110">No painel esquerdo, selecione **Installed** > [**Visual C#**  ou **Visual Basic**] > **Desktop Windows**e, em seguida, selecione o  **Aplicativo WPF** modelo.</span><span class="sxs-lookup"><span data-stu-id="8569f-110">In the left pane, select **Installed** > [**Visual C#** or **Visual Basic**] > **Windows Desktop**, and then select the **WPF App** template.</span></span>

3. <span data-ttu-id="8569f-111">Insira `NorthwindClient` para o nome do projeto e clique **Okey**.</span><span class="sxs-lookup"><span data-stu-id="8569f-111">Enter `NorthwindClient` for the project name, and then click **OK**.</span></span>

4. <span data-ttu-id="8569f-112">Abra o arquivo MainWindow.xaml e substitua o XAML pelo seguinte código:</span><span class="sxs-lookup"><span data-stu-id="8569f-112">Open the file MainWindow.xaml and replace the XAML code with the following code:</span></span>

     [!code-xaml[Astoria Quickstart Client#Window1Xaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml#window1xaml)]

## <a name="to-add-a-data-service-reference-to-the-project"></a><span data-ttu-id="8569f-113">Para adicionar uma referência de serviço de dados ao projeto</span><span class="sxs-lookup"><span data-stu-id="8569f-113">To add a data service reference to the project</span></span>

1. <span data-ttu-id="8569f-114">Na **Gerenciador de soluções**, clique com botão direito no projeto NorthwindClient, clique em **Add** > **referência de serviço**e, em seguida, clique em **Discover** .</span><span class="sxs-lookup"><span data-stu-id="8569f-114">In **Solution Explorer**, right-click the NorthwindClient project, click **Add** > **Service Reference**, and then click **Discover**.</span></span>

     <span data-ttu-id="8569f-115">Isso exibe o serviço de dados Northwind que você criou na primeira tarefa.</span><span class="sxs-lookup"><span data-stu-id="8569f-115">This displays the Northwind data service that you created in the first task.</span></span>

2. <span data-ttu-id="8569f-116">No **Namespace** caixa de texto, digite `Northwind`e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="8569f-116">In the **Namespace** text box, type `Northwind`, and then click **OK**.</span></span>

     <span data-ttu-id="8569f-117">Isso adiciona um novo arquivo de código ao projeto, que contém classes de dados que são usadas para acessar e interagir com os recursos do serviço de dados como objetos.</span><span class="sxs-lookup"><span data-stu-id="8569f-117">This adds a new code file to the project, which contains the data classes that are used to access and interact with data service resources as objects.</span></span> <span data-ttu-id="8569f-118">As classes de dados são criadas no namespace `NorthwindClient.Northwind`.</span><span class="sxs-lookup"><span data-stu-id="8569f-118">The data classes are created in the namespace `NorthwindClient.Northwind`.</span></span>

## <a name="to-access-data-service-data-in-the-wpf-application"></a><span data-ttu-id="8569f-119">Para acessar dados do serviço de dados no aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="8569f-119">To access data service data in the WPF application</span></span>

1. <span data-ttu-id="8569f-120">Na **Gerenciador de soluções** sob **NorthwindClient**, clique com botão direito no projeto e clique em **Add Reference**.</span><span class="sxs-lookup"><span data-stu-id="8569f-120">In **Solution Explorer** under **NorthwindClient**, right-click the project and click **Add Reference**.</span></span>

2. <span data-ttu-id="8569f-121">No **adicionar referência** caixa de diálogo, clique o **.NET** guia, selecione o assembly da dll e, em seguida, clique em **Okey**.</span><span class="sxs-lookup"><span data-stu-id="8569f-121">In the **Add Reference** dialog box, click the **.NET** tab, select the System.Data.Services.Client.dll assembly, and then click **OK**.</span></span>

3. <span data-ttu-id="8569f-122">Na **Gerenciador de soluções** sob **NorthwindClient**, abra a página de código para o arquivo MainWindow. XAML e adicione o seguinte `using` instrução (`Imports` no Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="8569f-122">In **Solution Explorer** under **NorthwindClient**, open the code page for the MainWindow.xaml file, and add the following `using` statement (`Imports` in Visual Basic).</span></span>

     [!code-csharp[Astoria Quickstart Client#Using](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#using)]
     [!code-vb[Astoria Quickstart Client#Using](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#using)]

3. <span data-ttu-id="8569f-123">Insira o código a seguir que consulta esse serviço de dados e associa o resultado a uma classe <xref:System.Data.Services.Client.DataServiceCollection%601> na classe `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="8569f-123">Insert the following code that queries that data service and binds the result to a <xref:System.Data.Services.Client.DataServiceCollection%601> into the `MainWindow` class:</span></span>

    > [!NOTE]
    > <span data-ttu-id="8569f-124">Você deve substituir o nome de host `localhost:12345` pelo servidor e a porta que está hospedando sua instância do serviço de dados Northwind.</span><span class="sxs-lookup"><span data-stu-id="8569f-124">You must replace the host name `localhost:12345` with the server and port that is hosting your instance of the Northwind data service.</span></span>

     [!code-csharp[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#querycode)]
     [!code-vb[Astoria Quickstart Client#QueryCode](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#querycode)]

4. <span data-ttu-id="8569f-125">Insira o seguinte código que salvar as alterações na classe `MainWindow`:</span><span class="sxs-lookup"><span data-stu-id="8569f-125">Insert the following code that saves changes into the `MainWindow` class:</span></span>

     [!code-csharp[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_quickstart_client/cs/window1.xaml.cs#savechanges)]
     [!code-vb[Astoria Quickstart Client#SaveChanges](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_quickstart_client/vb/window1.xaml.vb#savechanges)]

## <a name="to-build-and-run-the-northwindclient-application"></a><span data-ttu-id="8569f-126">Para compilar e executar o aplicativo NorthwindClient</span><span class="sxs-lookup"><span data-stu-id="8569f-126">To build and run the NorthwindClient application</span></span>

1. <span data-ttu-id="8569f-127">Na **Gerenciador de soluções**, clique com botão direito no projeto NorthwindClient e selecione **definir como projeto de inicialização**.</span><span class="sxs-lookup"><span data-stu-id="8569f-127">In **Solution Explorer**, right-click the NorthwindClient project and select **Set as startup project**.</span></span>

2. <span data-ttu-id="8569f-128">Pressione **F5** para iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8569f-128">Press **F5** to start the application.</span></span>

     <span data-ttu-id="8569f-129">Isso compila a solução e inicia o aplicativo cliente.</span><span class="sxs-lookup"><span data-stu-id="8569f-129">This builds the solution and starts the client application.</span></span> <span data-ttu-id="8569f-130">Os dados são solicitados do serviço e exibidos no console.</span><span class="sxs-lookup"><span data-stu-id="8569f-130">Data is requested from the service and displayed in the console.</span></span>

3. <span data-ttu-id="8569f-131">Editar um valor na **quantidade** coluna da grade de dados e clique **salvar**.</span><span class="sxs-lookup"><span data-stu-id="8569f-131">Edit a value in the **Quantity** column of the data grid, and then click **Save**.</span></span>

     <span data-ttu-id="8569f-132">As alterações são salvas no serviço de dados.</span><span class="sxs-lookup"><span data-stu-id="8569f-132">Changes are saved to the data service.</span></span>

    > [!NOTE]
    > <span data-ttu-id="8569f-133">Esta versão do aplicativo NorthwindClient não dá suporte a adição e exclusão de entidades.</span><span class="sxs-lookup"><span data-stu-id="8569f-133">This version of the NorthwindClient application does not support adding and deleting of entities.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8569f-134">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="8569f-134">Next Steps</span></span>

<span data-ttu-id="8569f-135">Você criou com êxito o aplicativo cliente que acessa o feed Northwind OData de exemplo.</span><span class="sxs-lookup"><span data-stu-id="8569f-135">You have successfully created the client application that accesses the sample Northwind OData feed.</span></span> <span data-ttu-id="8569f-136">Você concluiu o guia de início rápido do WCF Data Services também!</span><span class="sxs-lookup"><span data-stu-id="8569f-136">You've also completed the WCF Data Services quickstart!</span></span>

<span data-ttu-id="8569f-137">Para obter mais informações sobre como acessar um OData feed de um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] aplicativo, consulte [biblioteca de cliente do WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span><span class="sxs-lookup"><span data-stu-id="8569f-137">For more information about accessing an OData feed from a [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] application, see [WCF Data Services Client Library](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8569f-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8569f-138">See also</span></span>

- [<span data-ttu-id="8569f-139">Introdução</span><span class="sxs-lookup"><span data-stu-id="8569f-139">Getting Started</span></span>](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [<span data-ttu-id="8569f-140">Recursos</span><span class="sxs-lookup"><span data-stu-id="8569f-140">Resources</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-resources.md)
