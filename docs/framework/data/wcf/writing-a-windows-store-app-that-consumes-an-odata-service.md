---
title: Escrevendo um aplicativo da Windows Store que consome um OData Service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0c1e2b9092abd54fd62848f58e2385bee5058553
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a><span data-ttu-id="803ba-102">Escrevendo um aplicativo da Windows Store que consome um OData Service</span><span class="sxs-lookup"><span data-stu-id="803ba-102">Writing a Windows Store App that consumes an OData Service</span></span>
<span data-ttu-id="803ba-103">Windows 8 apresenta um novo tipo de aplicativo: o aplicativo da Windows Store.</span><span class="sxs-lookup"><span data-stu-id="803ba-103">Windows 8 introduces a new type of application: the Windows Store app.</span></span> <span data-ttu-id="803ba-104">Aplicativos da Windows Store tem uma aparência nova, executados em uma variedade de dispositivos e ficam disponíveis na Windows Store.</span><span class="sxs-lookup"><span data-stu-id="803ba-104">Windows Store apps have a brand new look and feel, run on a variety of devices, and are made available on the Windows Store.</span></span> <span data-ttu-id="803ba-105">Este tópico descreve como escrever um aplicativo da Windows Store que consome um serviço OData, especificamente o serviço de catálogo de NetFlix OData.</span><span class="sxs-lookup"><span data-stu-id="803ba-105">This topic describes how to write a Windows Store app that consumes an OData service, specifically the NetFlix Catalog OData service.</span></span> <span data-ttu-id="803ba-106">Para obter mais informações sobre aplicativos da Windows Store, leia [Introdução aos aplicativos da Windows Store](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span><span class="sxs-lookup"><span data-stu-id="803ba-106">For more information about Windows Store Apps, please read [Getting Started with Windows Store apps](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="803ba-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="803ba-107">Prerequisites</span></span>  
  
1.  [<span data-ttu-id="803ba-108">Microsoft Windows 8</span><span class="sxs-lookup"><span data-stu-id="803ba-108">Microsoft Windows 8</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [<span data-ttu-id="803ba-109">Microsoft Visual Studio 2012</span><span class="sxs-lookup"><span data-stu-id="803ba-109">Microsoft Visual Studio 2012</span></span>](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [<span data-ttu-id="803ba-110">WCF Data Services</span><span class="sxs-lookup"><span data-stu-id="803ba-110">WCF Data Services</span></span>](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a><span data-ttu-id="803ba-111">Criando o aplicativo da Windows Store grade padrão</span><span class="sxs-lookup"><span data-stu-id="803ba-111">Creating the default Windows Store Grid Application</span></span>  
  
1.  <span data-ttu-id="803ba-112">Crie um novo aplicativo de grade de armazenamento Windows usando o c# e XAML.</span><span class="sxs-lookup"><span data-stu-id="803ba-112">Create a new Windows Store Grid Application using C# and XAML.</span></span> <span data-ttu-id="803ba-113">Nome do aplicativo OData.WindowsStore.NetflixDemo:</span><span class="sxs-lookup"><span data-stu-id="803ba-113">Name the application OData.WindowsStore.NetflixDemo:</span></span>  
  
     <span data-ttu-id="803ba-114">![Caixa de diálogo Novo projeto](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span><span class="sxs-lookup"><span data-stu-id="803ba-114">![New Project Dialog](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")</span></span>  
  
2.  <span data-ttu-id="803ba-115">Abra o Package. appxmanifest e insira um nome amigável na caixa de texto de nome de exibição.</span><span class="sxs-lookup"><span data-stu-id="803ba-115">Open the Package.appxmanifest and enter a friendly name in the Display name text box.</span></span> <span data-ttu-id="803ba-116">Especifica que o nome do aplicativo usado com o Windows 8 a funcionalidade de pesquisa.</span><span class="sxs-lookup"><span data-stu-id="803ba-116">This specifies the application name used with the Windows 8 search functionality.</span></span>  
  
     <span data-ttu-id="803ba-117">![Arquivo de manifesto do aplicativo](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span><span class="sxs-lookup"><span data-stu-id="803ba-117">![Application manifest file](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")</span></span>  
  
3.  <span data-ttu-id="803ba-118">Insira um nome amigável no \<AppName > elemento no arquivo App. XAML.</span><span class="sxs-lookup"><span data-stu-id="803ba-118">Enter a friendly name in the \<AppName> element in the App.xaml file.</span></span> <span data-ttu-id="803ba-119">Isso define o nome do aplicativo que é exibido quando o aplicativo é iniciado:</span><span class="sxs-lookup"><span data-stu-id="803ba-119">This sets the application name that is displayed when the application is launched:</span></span>  
  
     <span data-ttu-id="803ba-120">![Arquivo App. XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span><span class="sxs-lookup"><span data-stu-id="803ba-120">![App.xaml file](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")</span></span>  
  
4.  <span data-ttu-id="803ba-121">Criar e iniciar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803ba-121">Build and launch the application.</span></span> <span data-ttu-id="803ba-122">Primeiro, você verá tela inicial do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803ba-122">You first see the application’s splash screen.</span></span> <span data-ttu-id="803ba-123">Captura de tela abaixo exibe a tela inicial do padrão.</span><span class="sxs-lookup"><span data-stu-id="803ba-123">The screenshot below displays the default splash screen.</span></span> <span data-ttu-id="803ba-124">A imagem usada é armazenada na pasta de ativos do projeto.</span><span class="sxs-lookup"><span data-stu-id="803ba-124">The image used is stored in the project’s Assets folder.</span></span>  
  
     <span data-ttu-id="803ba-125">![A tela inicial do aplicativo padrão](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span><span class="sxs-lookup"><span data-stu-id="803ba-125">![The default app splash screen](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")</span></span>  
  
     <span data-ttu-id="803ba-126">Em seguida, o aplicativo será exibido.</span><span class="sxs-lookup"><span data-stu-id="803ba-126">Then the application will be displayed.</span></span>  
  
     <span data-ttu-id="803ba-127">![O aplicativo padrão](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span><span class="sxs-lookup"><span data-stu-id="803ba-127">![The default application](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")</span></span>  
  
     <span data-ttu-id="803ba-128">O aplicativo padrão define um conjunto de classes em Sampledatasource: SampleDataGroup e SampleDataItem, que são derivados de SampleDataCommon, que é derivada de BindableBase.</span><span class="sxs-lookup"><span data-stu-id="803ba-128">The default application defines a set of classes in SampleDataSource.cs: SampleDataGroup and SampleDataItem, both of which are derived from SampleDataCommon, which itself is derived from BindableBase.</span></span> <span data-ttu-id="803ba-129">SampleDataGroup e SampleDataItem estão associados ao padrão GridView.</span><span class="sxs-lookup"><span data-stu-id="803ba-129">SampleDataGroup and SampleDataItem are bound to the default GridView.</span></span> <span data-ttu-id="803ba-130">Sampledatasource está localizado na pasta DataModel dentro do projeto NetflixDemo.</span><span class="sxs-lookup"><span data-stu-id="803ba-130">SampleDataSource.cs is located in the DataModel folder within the NetflixDemo project.</span></span> <span data-ttu-id="803ba-131">O aplicativo exibe uma coleção agrupada.</span><span class="sxs-lookup"><span data-stu-id="803ba-131">The application displays a grouped collection.</span></span> <span data-ttu-id="803ba-132">Cada grupo contém qualquer número de itens, representado por SampleDataGroup e SampleDataItem, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="803ba-132">Each group contains any number of items, represented by SampleDataGroup and SampleDataItem, respectively.</span></span> <span data-ttu-id="803ba-133">Na captura de tela anterior, você pode ver um grupo chamado grupo título 1 e todos os itens no grupo exibido juntos.</span><span class="sxs-lookup"><span data-stu-id="803ba-133">In the previous screen shot you can see a group called Group Title 1 and all of the items in the group displayed together.</span></span>  
  
     <span data-ttu-id="803ba-134">A página principal do aplicativo é Groupeditemspage.</span><span class="sxs-lookup"><span data-stu-id="803ba-134">The main page of the application is GroupedItemsPage.xaml.</span></span> <span data-ttu-id="803ba-135">Ele contém um GridView que exibe os dados de exemplo criados pela classe Sampledatasource.</span><span class="sxs-lookup"><span data-stu-id="803ba-135">It contains a GridView that displays the sample data created by the SampleDataSource.cs class.</span></span> <span data-ttu-id="803ba-136">O GroupedItemsPage é carregado pelo App.xaml.cs em uma chamada para rootFrame.Navigate:</span><span class="sxs-lookup"><span data-stu-id="803ba-136">The GroupedItemsPage is loaded by the App.xaml.cs in a call to rootFrame.Navigate:</span></span>  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     <span data-ttu-id="803ba-137">Isso faz com que o GroupedItemsPage a ser instanciado e seu método LoadState é chamado.</span><span class="sxs-lookup"><span data-stu-id="803ba-137">This causes the GroupedItemsPage to be instantiated and it’s LoadState method is called.</span></span> <span data-ttu-id="803ba-138">LoadState faz com que a instância de SampleDataSource estática deve ser criada, que cria uma coleção de objetos SampleDataGroup.</span><span class="sxs-lookup"><span data-stu-id="803ba-138">LoadState causes the static SampleDataSource instance to be created, which creates a collection of SampleDataGroup objects.</span></span> <span data-ttu-id="803ba-139">Cada objeto SampleDataGroup contém uma coleção de objetos SampleDataItem.</span><span class="sxs-lookup"><span data-stu-id="803ba-139">Each SampleDataGroup object contains a collection of SampleDataItem objects.</span></span> <span data-ttu-id="803ba-140">LoadState armazena a coleção de objetos SampleDataGroup no DefaultViewModel:</span><span class="sxs-lookup"><span data-stu-id="803ba-140">LoadState stores the collection of SampleDataGroup objects in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="803ba-141">O DefaultViewModel é associado a GridView.</span><span class="sxs-lookup"><span data-stu-id="803ba-141">The DefaultViewModel is then bound to the GridView.</span></span> <span data-ttu-id="803ba-142">Isso é referenciado no arquivo Groupeditemspage ao configurar a associação de dados.</span><span class="sxs-lookup"><span data-stu-id="803ba-142">This is referenced in the GroupedItemsPage.xaml file when configuring the data binding.</span></span>  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     <span data-ttu-id="803ba-143">O CollectionViewSource é usado como um proxy para manipular coleções agrupadas.</span><span class="sxs-lookup"><span data-stu-id="803ba-143">The CollectionViewSource is used as a proxy for handling grouped collections.</span></span> <span data-ttu-id="803ba-144">Quando a associação ocorre, ele itera através da coleção de objetos SampleDataGroup para preencher o GridView.</span><span class="sxs-lookup"><span data-stu-id="803ba-144">When binding occurs, it iterates through the collection of SampleDataGroup objects to populate the GridView.</span></span>  <span data-ttu-id="803ba-145">O atributo ItemsPath informa a CollectionViewSource que propriedade em cada objeto SampleDataGroup para localizar o SampleDataItems que ele contém.</span><span class="sxs-lookup"><span data-stu-id="803ba-145">The ItemsPath attribute tells the CollectionViewSource what property on each SampleDataGroup object to use to find the SampleDataItems it contains.</span></span> <span data-ttu-id="803ba-146">Nesse caso, cada objeto SampleDataGroup contém uma coleção de TopItems de SampleDataItem objetos.</span><span class="sxs-lookup"><span data-stu-id="803ba-146">In this case each SampleDataGroup object contains a TopItems collection of SampleDataItem objects.</span></span>  
  
     <span data-ttu-id="803ba-147">Para o aplicativo Netflix, filmes são agrupados por gênero.</span><span class="sxs-lookup"><span data-stu-id="803ba-147">For the Netflix application, movies are grouped by genre.</span></span> <span data-ttu-id="803ba-148">Portanto, o aplicativo exibe um número de gêneros e uma lista de filmes dentro desse gênero.</span><span class="sxs-lookup"><span data-stu-id="803ba-148">So the application displays a number of genres and a list of movies within that genre.</span></span>  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a><span data-ttu-id="803ba-149">Adicionar uma referência de serviço para o serviço Netflix OData</span><span class="sxs-lookup"><span data-stu-id="803ba-149">Add a Service Reference to the Netflix OData Service</span></span>  
  
1.  <span data-ttu-id="803ba-150">Antes de fazermos qualquer chamada para o serviço Netflix OData, precisamos adicionar uma referência de serviço.</span><span class="sxs-lookup"><span data-stu-id="803ba-150">Before we can make any calls to the Netflix OData service we need to add a service reference.</span></span> <span data-ttu-id="803ba-151">Clique com botão direito no projeto no Gerenciador de soluções e selecione Adicionar referência de serviço...</span><span class="sxs-lookup"><span data-stu-id="803ba-151">Right-click the project in the Solution Explorer and select Add Service Reference…</span></span>  
  
     <span data-ttu-id="803ba-152">![Adicionar caixa de diálogo de referência de serviço](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span><span class="sxs-lookup"><span data-stu-id="803ba-152">![Add Service Reference Dialog](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")</span></span>  
  
2.  <span data-ttu-id="803ba-153">Insira a URL para o serviço Netflix OData na barra de endereços e clique em Ir.</span><span class="sxs-lookup"><span data-stu-id="803ba-153">Enter the URL for the Netflix OData service in the Address bar and click Go.</span></span> <span data-ttu-id="803ba-154">Defina o Namespace da referência de serviço para Netflix e clique em Okey.</span><span class="sxs-lookup"><span data-stu-id="803ba-154">Set the Namespace of the service reference to Netflix and click OK.</span></span>  
  
     <span data-ttu-id="803ba-155">![Adicionar erro de referência de serviço](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span><span class="sxs-lookup"><span data-stu-id="803ba-155">![Add Service Reference Error](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="803ba-156">Se você ainda não tiver instalado [WCF Data Services ferramentas para aplicativos da Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=266652), você receberá uma mensagem, como mostrado acima.</span><span class="sxs-lookup"><span data-stu-id="803ba-156">If you have not yet installed [WCF Data Services Tools for Windows Store Apps](http://go.microsoft.com/fwlink/p/?LinkId=266652), you will be prompted with a message such as the one above.</span></span> <span data-ttu-id="803ba-157">Você precisará baixar e instalar as ferramentas referenciadas no link para continuar.</span><span class="sxs-lookup"><span data-stu-id="803ba-157">You will need to download and install the tools referenced in the link to continue.</span></span>  
  
 <span data-ttu-id="803ba-158">Adicionar que uma referência de serviço gera fortemente tipado classes WCF Data Services usará para analisar o OData retornado pelo serviço Netflix OData.</span><span class="sxs-lookup"><span data-stu-id="803ba-158">Adding a service reference generates strongly typed classes that WCF Data Services will use to parse the OData returned by the Netflix OData service.</span></span> <span data-ttu-id="803ba-159">As classes definidas no Sampledatasource poderão estar associadas a GridView, portanto, precisamos transfira os dados das classes de cliente OData geradas para as classes associáveis definidas Sampledatasource.</span><span class="sxs-lookup"><span data-stu-id="803ba-159">The classes defined in SampleDataSource.cs can be bound to the GridView so we need to transfer the data from the generated OData client classes into the bindable classes defined in SampleDataSource.cs.</span></span>  <span data-ttu-id="803ba-160">Para fazer isso, precisamos fazer algumas alterações ao modelo de dados definido no Sampledatasource.</span><span class="sxs-lookup"><span data-stu-id="803ba-160">In order to do this, we need to make some changes to the data model defined in SampleDataSource.cs.</span></span>  
  
#### <a name="update-the-data-model-for-the-application"></a><span data-ttu-id="803ba-161">Atualizar o modelo de dados para o aplicativo</span><span class="sxs-lookup"><span data-stu-id="803ba-161">Update the data model for the application</span></span>  
  
1.  <span data-ttu-id="803ba-162">Substitua o código existente no Sampledatasource com o código de [este essência](https://gist.github.com/3419288).</span><span class="sxs-lookup"><span data-stu-id="803ba-162">Replace the existing code in SampleDataSource.cs with the code from [this gist](https://gist.github.com/3419288).</span></span> <span data-ttu-id="803ba-163">O código atualizado adiciona um método LoadMovies (para a classe SampleDataSource) que executa uma consulta em relação ao serviço Netflix OData e preenche uma lista de gêneros (allGroups) e dentro de cada uma lista de filmes gênero.</span><span class="sxs-lookup"><span data-stu-id="803ba-163">The updated code adds a LoadMovies method (to the SampleDataSource class)  that performs a query against the Netflix OData service and populates a list of genres (allGroups) and within each genre a list of movies.</span></span> <span data-ttu-id="803ba-164">A classe SampleDataGroup é usada para representar um gênero e a classe SampleDataItem é usada para representar um filme.</span><span class="sxs-lookup"><span data-stu-id="803ba-164">The SampleDataGroup class is used to represent a genre and the SampleDataItem class is used to represent a movie.</span></span>  
  
    ```csharp  
    public static async void LoadMovies()  
    {  
        IEnumerable<Title> titles = await ((DataServiceQuery<Title>)Context.Titles  
            .Expand("Genres,AudioFormats,AudioFormats/Language,Awards,Cast")  
            .Where(t => t.Rating == "PG")  
            .OrderByDescending(t => t.ReleaseYear)  
            .Take(300)).ExecuteAsync();  
  
        foreach (Title title in titles)  
        {  
            foreach (Genre netflixGenre in title.Genres)  
            {  
                SampleDataGroup genre = GetGroup(netflixGenre.Name);  
                if (genre == null)  
                {  
                    genre = new SampleDataGroup(netflixGenre.Name, netflixGenre.Name, String.Empty, title.BoxArt.LargeUrl, String.Empty);  
                    Instance.AllGroups.Add(genre);  
                }  
                var content = new StringBuilder();  
                // Write additional things to content here if you want them to display in the item detail.  
                genre.Items.Add(new SampleDataItem(title.Id, title.Name, String.Format("{0}rnrn{1} ({2})", title.Synopsis, title.Rating, title.ReleaseYear), title.BoxArt.HighDefinitionUrl ?? title.BoxArt.LargeUrl, "Description", content.ToString()));  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="803ba-165">O [padrão assíncrono baseado em tarefa](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) é usado para obter assincronamente 300 (têm) recente (OrderByDescending) classificados PG (onde) filmes fazer do Netflix.</span><span class="sxs-lookup"><span data-stu-id="803ba-165">The [Task-based Asynchronous Pattern](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) is used to asynchronously get 300 (Take) recent (OrderByDescending) PG-rated (Where) movies back from Netflix.</span></span> <span data-ttu-id="803ba-166">O restante do código constrói SimpleDataItems e SimpleDataGroups das entidades que foram retornadas no feed OData.</span><span class="sxs-lookup"><span data-stu-id="803ba-166">The rest of the code constructs SimpleDataItems and SimpleDataGroups from the entities that were returned in the OData feed.</span></span>  
  
     <span data-ttu-id="803ba-167">A classe SampleDataSource também implementa um método de pesquisa simples.</span><span class="sxs-lookup"><span data-stu-id="803ba-167">The SampleDataSource class also implements a simple search method.</span></span> <span data-ttu-id="803ba-168">Nesse caso, ele faz uma pesquisa de memória simples de filmes carregados.</span><span class="sxs-lookup"><span data-stu-id="803ba-168">In this case, it does a simple in-memory search of the loaded movies.</span></span>  
  
    ```csharp  
    public static IEnumerable<SampleDataItem> Search(string searchString)  
    {  
            var regex = new Regex(searchString, RegexOptions.CultureInvariant | RegexOptions.IgnoreCase | RegexOptions.IgnorePatternWhitespace);  
            return Instance.AllGroups  
                .SelectMany(g => g.Items)  
                .Where(m => regex.IsMatch(m.Title) || regex.IsMatch(m.Subtitle))  
                    .Distinct(new SampleDataItemComparer());  
    }  
    ```  
  
     <span data-ttu-id="803ba-169">Também no Sampledatasource é definida uma classe chamada ExtensionMethods.</span><span class="sxs-lookup"><span data-stu-id="803ba-169">Also in SampleDataSource.cs a class called ExtensionMethods is defined.</span></span> <span data-ttu-id="803ba-170">Cada um desses métodos de extensão usa o padrão de toque para permitir a SampleDataSource executar uma consulta OData sem bloquear a interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="803ba-170">Each of these extension methods uses the TAP pattern to allow the SampleDataSource to execute an OData query without blocking the UI.</span></span> <span data-ttu-id="803ba-171">Por exemplo, o código a seguir usa o método Task.Factory.FromAsync para implementar um toque.</span><span class="sxs-lookup"><span data-stu-id="803ba-171">For example, the following code uses the Task.Factory.FromAsync method to implement TAP.</span></span>  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     <span data-ttu-id="803ba-172">Como o aplicativo padrão, a página principal do aplicativo é GroupedItemsPage.</span><span class="sxs-lookup"><span data-stu-id="803ba-172">As in the default application, the main page of the application is GroupedItemsPage.</span></span> <span data-ttu-id="803ba-173">Neste momento, no entanto, ele exibe os filmes recuperados do Netflix agrupado por gênero.</span><span class="sxs-lookup"><span data-stu-id="803ba-173">This time, however, it displays the movies retrieved from Netflix grouped by genre.</span></span>  <span data-ttu-id="803ba-174">Quando o GroupedItemsPage é instanciada, seu método LoadState é chamado.</span><span class="sxs-lookup"><span data-stu-id="803ba-174">When the GroupedItemsPage is instantiated, its LoadState method is called.</span></span> <span data-ttu-id="803ba-175">LoadState faz com que a instância SampleDataSource estática deve ser criada, fazendo uma chamada para o serviço Netflix OData, conforme discutido anteriormente.</span><span class="sxs-lookup"><span data-stu-id="803ba-175">LoadState causes the static SampleDataSource instance to be created, making a call to the Netflix OData service as discussed previously.</span></span> <span data-ttu-id="803ba-176">LoadState armazena a coleção de gêneros (SampleDataGroup objetos) no DefaultViewModel:</span><span class="sxs-lookup"><span data-stu-id="803ba-176">LoadState stores the collection of genres (SampleDataGroup objects) in the DefaultViewModel:</span></span>  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     <span data-ttu-id="803ba-177">Conforme descrito anteriormente, o DefaultViewModel é usado para associar os dados a GridView.</span><span class="sxs-lookup"><span data-stu-id="803ba-177">As described previously, the DefaultViewModel is then used to bind the data to the GridView.</span></span>  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a><span data-ttu-id="803ba-178">Adicionar um contrato de pesquisa para permitir que o aplicativo participar da pesquisa do Windows</span><span class="sxs-lookup"><span data-stu-id="803ba-178">Add a search contract to allow the application to participate in Windows search</span></span>  
  
1.  <span data-ttu-id="803ba-179">Adicione um contrato de pesquisa para o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803ba-179">Add a search contract to the application.</span></span> <span data-ttu-id="803ba-180">Isso permite que o aplicativo para integração com a experiência de pesquisa do Windows 8.</span><span class="sxs-lookup"><span data-stu-id="803ba-180">This allows the application to integrate with the Windows 8 search experience.</span></span> <span data-ttu-id="803ba-181">Nome do contrato de pesquisa SearchResultsPage.xaml</span><span class="sxs-lookup"><span data-stu-id="803ba-181">Name the search contract SearchResultsPage.xaml</span></span>  
  
     <span data-ttu-id="803ba-182">![Adicionar um contrato de pesquisa](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span><span class="sxs-lookup"><span data-stu-id="803ba-182">![Add a search contract](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")</span></span>  
  
2.  <span data-ttu-id="803ba-183">Modificar linha 58 de SearchResultsPage.xaml.cs removendo queryText aspas incorporadas.</span><span class="sxs-lookup"><span data-stu-id="803ba-183">Modify line 58 of SearchResultsPage.xaml.cs by removing the embedded quotes around queryText.</span></span>  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  <span data-ttu-id="803ba-184">Insira as duas linhas de código a seguir na linha 81 em SearchResultsPage.xaml.cs para recuperar os resultados da pesquisa.</span><span class="sxs-lookup"><span data-stu-id="803ba-184">Insert the following two lines of code at line 81 in SearchResultsPage.xaml.cs to retrieve the search results.</span></span>  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 <span data-ttu-id="803ba-185">Quando um usuário invoca o Windows search, tipos em um termo de pesquisa e, em seguida, toque no ícone do aplicativo de demonstração do Netflix na barra de pesquisa, o método LoadState o SearchResultsPage é executado.</span><span class="sxs-lookup"><span data-stu-id="803ba-185">When a user invokes Windows search, types in a search term and then touches the Netflix Demo app icon in the search bar, the LoadState method of the SearchResultsPage is executed.</span></span> <span data-ttu-id="803ba-186">O parâmetro de navegação enviado ao LoadState contém o texto da consulta.</span><span class="sxs-lookup"><span data-stu-id="803ba-186">The navigation parameter sent to LoadState contains the query text.</span></span> <span data-ttu-id="803ba-187">O método Filter_SelectionChanged é chamado que em seguida, chama o método de pesquisa na classe SampleDataSource.</span><span class="sxs-lookup"><span data-stu-id="803ba-187">Next the Filter_SelectionChanged method is called which then calls the Search method on the SampleDataSource class.</span></span> <span data-ttu-id="803ba-188">Os resultados são retornados e exibidos na página SearchResultsPage.xaml.</span><span class="sxs-lookup"><span data-stu-id="803ba-188">The results are returned and displayed in the SearchResultsPage.xaml page.</span></span>  
  
```csharp  
/// <summary>  
        /// Invoked when a filter is selected using the ComboBox in snapped view state.  
        /// </summary>  
        /// <param name="sender">The ComboBox instance.</param>  
        /// <param name="e">Event data describing how the selected filter was changed.</param>  
        void Filter_SelectionChanged(object sender, SelectionChangedEventArgs e)  
        {  
            // Determine what filter was selected  
            var selectedFilter = e.AddedItems.FirstOrDefault() as Filter;  
            if (selectedFilter != null)  
            {  
                // Mirror the results into the corresponding Filter object to allow the  
                // RadioButton representation used when not snapped to reflect the change  
                selectedFilter.Active = true;  
  
                // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                var searchValue = (string)this.DefaultViewModel["QueryText"];  
                this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
  
                // Ensure results are found  
                object results;  
                ICollection resultsCollection;  
                if (this.DefaultViewModel.TryGetValue("Results", out results) &&  
                    (resultsCollection = results as ICollection) != null &&  
                    resultsCollection.Count != 0)  
                {  
                    VisualStateManager.GoToState(this, "ResultsFound", true);  
                    return;  
                }  
            }  
  
            // Display informational text when there are no search results.  
            VisualStateManager.GoToState(this, "NoResultsFound", true);  
        }  
```  
  
 <span data-ttu-id="803ba-189">Para obter mais informações sobre a integração de pesquisa em um aplicativo, consulte [pesquisa: integrar a experiência de pesquisa do Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span><span class="sxs-lookup"><span data-stu-id="803ba-189">For more information on integrating search into an application see, [Search: integrating into the Windows 8 search experience](http://go.microsoft.com/fwlink/p/?LinkId=266650).</span></span>  
  
## <a name="run-the-application"></a><span data-ttu-id="803ba-190">Executar o aplicativo</span><span class="sxs-lookup"><span data-stu-id="803ba-190">Run the application</span></span>  
 <span data-ttu-id="803ba-191">Inicie o aplicativo pressionando F5.</span><span class="sxs-lookup"><span data-stu-id="803ba-191">Launch the application by pressing F5.</span></span> <span data-ttu-id="803ba-192">Observe que levará alguns segundos para carregar as imagens após a inicialização do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="803ba-192">Note that it will take a few seconds to load the images upon application launch.</span></span> <span data-ttu-id="803ba-193">Além disso, sua primeira tentativa de pesquisa pode não retornar nenhum resultado.</span><span class="sxs-lookup"><span data-stu-id="803ba-193">Also, your first search attempt may not return any results.</span></span> <span data-ttu-id="803ba-194">Em um aplicativo do mundo real, você deseja lidar com esses dois problemas.</span><span class="sxs-lookup"><span data-stu-id="803ba-194">In a real-world application, you would want to deal with both of these issues.</span></span>  
  
 <span data-ttu-id="803ba-195">O aplicativo chama o serviço Netflix OData, recebe os dados nas classes de cliente OData geradas e, em seguida, transfere dados para classes de dados (SampleDataSource, SampleDataGroup e SampleDataItem).</span><span class="sxs-lookup"><span data-stu-id="803ba-195">The application calls the Netflix OData service, receives the data in the generated OData client classes and then transfers that data to bindable data classes (SampleDataSource, SampleDataGroup, and SampleDataItem).</span></span> <span data-ttu-id="803ba-196">Ele usa essas classes associáveis para associar os dados a GridView.</span><span class="sxs-lookup"><span data-stu-id="803ba-196">It uses these bindable classes to bind the data to the GridView.</span></span> <span data-ttu-id="803ba-197">Se você estiver familiarizado com associação de dados XAML funcionamento consulte [como agrupar itens em uma lista ou grade (aplicativos da Windows Store usando c# /VB/c + + e XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span><span class="sxs-lookup"><span data-stu-id="803ba-197">If you are unfamiliar with how XAML databinding works see [How to group items in a list or grid (Windows Store apps using C#/VB/C++ and XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).</span></span>
