---
title: Escrevendo um aplicativo da Windows Store que consome um OData Service
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
ms.assetid: 9917a0e9-ec93-49e5-a366-fd39b892eb8b
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3a2eb79e8bf8a5c683c9d48a0a69e4d7f5d270eb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="writing-a-windows-store-app-that-consumes-an-odata-service"></a>Escrevendo um aplicativo da Windows Store que consome um OData Service
Windows 8 apresenta um novo tipo de aplicativo: o aplicativo da Windows Store. Aplicativos da Windows Store tem uma aparência nova, executados em uma variedade de dispositivos e ficam disponíveis na Windows Store. Este tópico descreve como escrever um aplicativo da Windows Store que consome um serviço OData, especificamente o serviço de catálogo de NetFlix OData. Para obter mais informações sobre aplicativos da Windows Store, leia [Introdução aos aplicativos da Windows Store](http://msdn.microsoft.com/library/windows/apps/br211386.aspx).  
  
## <a name="prerequisites"></a>Pré-requisitos  
  
1.  [Microsoft Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266654)  
  
2.  [Microsoft Visual Studio 2012](http://go.microsoft.com/fwlink/p/?LinkId=266655)  
  
3.  [WCF Data Services](http://msdn.microsoft.com/data/bb931106)  
  
#### <a name="creating-the-default-windows-store-grid-application"></a>Criando o aplicativo da Windows Store grade padrão  
  
1.  Crie um novo aplicativo de grade de armazenamento Windows usando o c# e XAML. Nome do aplicativo OData.WindowsStore.NetflixDemo:  
  
     ![Caixa de diálogo Novo projeto](../../../../docs/framework/data/wcf/media/win8clientcreatenewproject.png "Win8ClientCreateNewProject")  
  
2.  Abra o Package. appxmanifest e insira um nome amigável na caixa de texto de nome de exibição. Especifica que o nome do aplicativo usado com o Windows 8 a funcionalidade de pesquisa.  
  
     ![Arquivo de manifesto do aplicativo](../../../../docs/framework/data/wcf/media/appxmanifest.png "appxmanifest")  
  
3.  Insira um nome amigável no \<AppName > elemento no arquivo App. XAML. Isso define o nome do aplicativo que é exibido quando o aplicativo é iniciado:  
  
     ![Arquivo App. XAML](../../../../docs/framework/data/wcf/media/appxaml.png "appxaml")  
  
4.  Criar e iniciar o aplicativo. Primeiro, você verá tela inicial do aplicativo. Captura de tela abaixo exibe a tela inicial do padrão. A imagem usada é armazenada na pasta de ativos do projeto.  
  
     ![A tela inicial do aplicativo padrão](../../../../docs/framework/data/wcf/media/defualtappsplash.png "defualtAppSplash")  
  
     Em seguida, o aplicativo será exibido.  
  
     ![O aplicativo padrão](../../../../docs/framework/data/wcf/media/defaultapplication.png "DefaultApplication")  
  
     O aplicativo padrão define um conjunto de classes em Sampledatasource: SampleDataGroup e SampleDataItem, que são derivados de SampleDataCommon, que é derivada de BindableBase. SampleDataGroup e SampleDataItem estão associados ao padrão GridView. Sampledatasource está localizado na pasta DataModel dentro do projeto NetflixDemo. O aplicativo exibe uma coleção agrupada. Cada grupo contém qualquer número de itens, representado por SampleDataGroup e SampleDataItem, respectivamente. Na captura de tela anterior, você pode ver um grupo chamado grupo título 1 e todos os itens no grupo exibido juntos.  
  
     A página principal do aplicativo é Groupeditemspage. Ele contém um GridView que exibe os dados de exemplo criados pela classe Sampledatasource. O GroupedItemsPage é carregado pelo App.xaml.cs em uma chamada para rootFrame.Navigate:  
  
    ```csharp  
    if (!rootFrame.Navigate(typeof(GroupedItemsPage), "AllGroups"))  
    {  
        throw new Exception("Failed to create initial page");  
    }  
    ```  
  
     Isso faz com que o GroupedItemsPage a ser instanciado e seu método LoadState é chamado. LoadState faz com que a instância de SampleDataSource estática deve ser criada, que cria uma coleção de objetos SampleDataGroup. Cada objeto SampleDataGroup contém uma coleção de objetos SampleDataItem. LoadState armazena a coleção de objetos SampleDataGroup no DefaultViewModel:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     O DefaultViewModel é associado a GridView. Isso é referenciado no arquivo Groupeditemspage ao configurar a associação de dados.  
  
    ```xaml
    <CollectionViewSource  
                x:Name="groupedItemsViewSource"  
                Source="{Binding Groups}"  
                IsSourceGrouped="true"  
                ItemsPath="TopItems"  
                d:Source="{Binding AllGroups, Source={d:DesignInstance Type=data:SampleDataSource, IsDesignTimeCreatable=True}}"/>  
    ```  
  
     O CollectionViewSource é usado como um proxy para manipular coleções agrupadas. Quando a associação ocorre, ele itera através da coleção de objetos SampleDataGroup para preencher o GridView.  O atributo ItemsPath informa a CollectionViewSource que propriedade em cada objeto SampleDataGroup para localizar o SampleDataItems que ele contém. Nesse caso, cada objeto SampleDataGroup contém uma coleção de TopItems de SampleDataItem objetos.  
  
     Para o aplicativo Netflix, filmes são agrupados por gênero. Portanto, o aplicativo exibe um número de gêneros e uma lista de filmes dentro desse gênero.  
  
#### <a name="add-a-service-reference-to-the-netflix-odata-service"></a>Adicionar uma referência de serviço para o serviço Netflix OData  
  
1.  Antes de fazermos qualquer chamada para o serviço Netflix OData, precisamos adicionar uma referência de serviço. Clique com botão direito no projeto no Gerenciador de soluções e selecione Adicionar referência de serviço...  
  
     ![Adicionar caixa de diálogo de referência de serviço](../../../../docs/framework/data/wcf/media/addservicereferenceodata.png "AddServiceReferenceOData")  
  
2.  Insira a URL para o serviço Netflix OData na barra de endereços e clique em Ir. Defina o Namespace da referência de serviço para Netflix e clique em Okey.  
  
     ![Adicionar erro de referência de serviço](../../../../docs/framework/data/wcf/media/addservicereferenceerror.png "AddServiceReferenceError")  
  
    > [!NOTE]
    >  Se você ainda não tiver instalado [WCF Data Services ferramentas para aplicativos da Windows Store](http://go.microsoft.com/fwlink/p/?LinkId=266652), você receberá uma mensagem, como mostrado acima. Você precisará baixar e instalar as ferramentas referenciadas no link para continuar.  
  
 Adicionar que uma referência de serviço gera fortemente tipado classes WCF Data Services usará para analisar o OData retornado pelo serviço Netflix OData. As classes definidas no Sampledatasource poderão estar associadas a GridView, portanto, precisamos transfira os dados das classes de cliente OData geradas para as classes associáveis definidas Sampledatasource.  Para fazer isso, precisamos fazer algumas alterações ao modelo de dados definido no Sampledatasource.  
  
#### <a name="update-the-data-model-for-the-application"></a>Atualizar o modelo de dados para o aplicativo  
  
1.  Substitua o código existente no Sampledatasource com o código de [este essência](https://gist.github.com/3419288). O código atualizado adiciona um método LoadMovies (para a classe SampleDataSource) que executa uma consulta em relação ao serviço Netflix OData e preenche uma lista de gêneros (allGroups) e dentro de cada uma lista de filmes gênero. A classe SampleDataGroup é usada para representar um gênero e a classe SampleDataItem é usada para representar um filme.  
  
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
  
     O [padrão assíncrono baseado em tarefa](http://go.microsoft.com/fwlink/p/?LinkId=266651) (TAP) é usado para obter assincronamente 300 (têm) recente (OrderByDescending) classificados PG (onde) filmes fazer do Netflix. O restante do código constrói SimpleDataItems e SimpleDataGroups das entidades que foram retornadas no feed OData.  
  
     A classe SampleDataSource também implementa um método de pesquisa simples. Nesse caso, ele faz uma pesquisa de memória simples de filmes carregados.  
  
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
  
     Também no Sampledatasource é definida uma classe chamada ExtensionMethods. Cada um desses métodos de extensão usa o padrão de toque para permitir a SampleDataSource executar uma consulta OData sem bloquear a interface do usuário. Por exemplo, o código a seguir usa o método Task.Factory.FromAsync para implementar um toque.  
  
    ```csharp  
    public static async Task<IEnumerable<T>> ExecuteAsync<T>(this DataServiceQuery<T> query)  
    {  
        return await Task.Factory.FromAsync<IEnumerable<T>>(query.BeginExecute(null, null), query.EndExecute);  
    }  
    ```  
  
     Como o aplicativo padrão, a página principal do aplicativo é GroupedItemsPage. Neste momento, no entanto, ele exibe os filmes recuperados do Netflix agrupado por gênero.  Quando o GroupedItemsPage é instanciada, seu método LoadState é chamado. LoadState faz com que a instância SampleDataSource estática deve ser criada, fazendo uma chamada para o serviço Netflix OData, conforme discutido anteriormente. LoadState armazena a coleção de gêneros (SampleDataGroup objetos) no DefaultViewModel:  
  
    ```csharp  
    protected override void LoadState(Object navigationParameter, Dictionary<String, Object> pageState)  
    {  
  
        var sampleDataGroups = SampleDataSource.GetGroups((String)navigationParameter);  
        this.DefaultViewModel["Groups"] = sampleDataGroups;  
    }  
    ```  
  
     Conforme descrito anteriormente, o DefaultViewModel é usado para associar os dados a GridView.  
  
#### <a name="add-a-search-contract-to-allow-the-application-to-participate-in-windows-search"></a>Adicionar um contrato de pesquisa para permitir que o aplicativo participar da pesquisa do Windows  
  
1.  Adicione um contrato de pesquisa para o aplicativo. Isso permite que o aplicativo para integração com a experiência de pesquisa do Windows 8. Nome do contrato de pesquisa SearchResultsPage.xaml  
  
     ![Adicionar um contrato de pesquisa](../../../../docs/framework/data/wcf/media/addsearchcontract.png "AddSearchContract")  
  
2.  Modificar linha 58 de SearchResultsPage.xaml.cs removendo queryText aspas incorporadas.  
  
    ```csharp  
    // Communicate results through the view model  
    this.DefaultViewModel["QueryText"] = queryText;  
    this.DefaultViewModel["Filters"] = filterList;  
    this.DefaultViewModel["ShowFilters"] = filterList.Count > 1;  
    ```  
  
3.  Insira as duas linhas de código a seguir na linha 81 em SearchResultsPage.xaml.cs para recuperar os resultados da pesquisa.  
  
    ```csharp  
    // TODO: Respond to the change in active filter by setting this.DefaultViewModel["Results"]  
                    //       to a collection of items with bindable Image, Title, Subtitle, and Description properties  
                    var searchValue = (string)this.DefaultViewModel["QueryText"];  
                    this.DefaultViewModel["Results"] = new List<SampleDataItem>(SampleDataSource.Search(searchValue));  
    ```  
  
 Quando um usuário invoca o Windows search, tipos em um termo de pesquisa e, em seguida, toque no ícone do aplicativo de demonstração do Netflix na barra de pesquisa, o método LoadState o SearchResultsPage é executado. O parâmetro de navegação enviado ao LoadState contém o texto da consulta. O método Filter_SelectionChanged é chamado que em seguida, chama o método de pesquisa na classe SampleDataSource. Os resultados são retornados e exibidos na página SearchResultsPage.xaml.  
  
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
  
 Para obter mais informações sobre a integração de pesquisa em um aplicativo, consulte [pesquisa: integrar a experiência de pesquisa do Windows 8](http://go.microsoft.com/fwlink/p/?LinkId=266650).  
  
## <a name="run-the-application"></a>Executar o aplicativo  
 Inicie o aplicativo pressionando F5. Observe que levará alguns segundos para carregar as imagens após a inicialização do aplicativo. Além disso, sua primeira tentativa de pesquisa pode não retornar nenhum resultado. Em um aplicativo do mundo real, você deseja lidar com esses dois problemas.  
  
 O aplicativo chama o serviço Netflix OData, recebe os dados nas classes de cliente OData geradas e, em seguida, transfere dados para classes de dados (SampleDataSource, SampleDataGroup e SampleDataItem). Ele usa essas classes associáveis para associar os dados a GridView. Se você estiver familiarizado com associação de dados XAML funcionamento consulte [como agrupar itens em uma lista ou grade (aplicativos da Windows Store usando c# /VB/c + + e XAML)](http://msdn.microsoft.com/library/windows/apps/xaml/hh780627).
