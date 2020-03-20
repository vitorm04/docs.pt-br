---
title: Associação de dados em um cliente do Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 7bc389056872841905336dcf658a07223906bf82
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183817"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="888af-102">Associação de dados em um cliente do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="888af-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="888af-103">Esta amostra demonstra o uso da vinculação de dados em um cliente WPF (Windows Presentation Foundation).</span><span class="sxs-lookup"><span data-stu-id="888af-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="888af-104">A amostra usa um serviço do Windows Communication Foundation (WCF) que gera aleatoriamente uma série de álbuns para retornar ao cliente.</span><span class="sxs-lookup"><span data-stu-id="888af-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="888af-105">Cada álbum tem um nome, um preço e uma lista de faixas de álbuns.</span><span class="sxs-lookup"><span data-stu-id="888af-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="888af-106">As faixas do álbum têm nome e duração.</span><span class="sxs-lookup"><span data-stu-id="888af-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="888af-107">As informações que são devolvidas pelo serviço estão automaticamente vinculadas à interface do usuário (UI) fornecida pelo cliente Da Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="888af-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="888af-108">O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="888af-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="888af-109">A vinculação de dados permite que uma fonte de dados seja automaticamente vinculada a uma ui.</span><span class="sxs-lookup"><span data-stu-id="888af-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="888af-110">Isso simplifica o modelo de programação porque não exige que você atualize programáticamente cada elemento de UI com os dados de um objeto de dados ou de um conjunto de objetos de dados.</span><span class="sxs-lookup"><span data-stu-id="888af-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="888af-111">Você pode vincular um objeto a um único elemento de ia ou a `ListBox`uma matriz a um controle que requer várias entradas, como a .</span><span class="sxs-lookup"><span data-stu-id="888af-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="888af-112">O código a seguir mostra `DataContext` como vincular dados ao de um elemento de IA.</span><span class="sxs-lookup"><span data-stu-id="888af-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 <span data-ttu-id="888af-113">Na amostra anterior, `DataContext` o `grid` elemento `myPanel` para layout nomeado é definido `GetAlbumList` para os dados retornados pelo método.</span><span class="sxs-lookup"><span data-stu-id="888af-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="888af-114">O `DataContext` permite que os elementos herdem informações de seus elementos-mãe sobre a fonte de dados que é usada para vinculação, bem como outras características da ligação, como o caminho.</span><span class="sxs-lookup"><span data-stu-id="888af-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="888af-115">A linha de código deve ser executada sempre que os dados do servidor forem atualizados.</span><span class="sxs-lookup"><span data-stu-id="888af-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="888af-116">Por exemplo, ele é executado quando a janela é inicializada e quando um novo álbum é adicionado.</span><span class="sxs-lookup"><span data-stu-id="888af-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="888af-117">Na seguinte amostra código XAML, as `ListBox` especificações `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="888af-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="888af-118">Isso especifica que os dados vinculados ao elemento de iu de nível superior também estão vinculados a esse controle (ou seja, a matriz de Álbuns).</span><span class="sxs-lookup"><span data-stu-id="888af-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="888af-119">Além disso, `ItemTemplate="{StaticResource AlbumStyle}"` especifica o modelo de dados a `ListBox`ser usado para cada item no .</span><span class="sxs-lookup"><span data-stu-id="888af-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="888af-120">Você também pode definir modelos de dados para especificar como os dados devem ser formatados.</span><span class="sxs-lookup"><span data-stu-id="888af-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="888af-121">Esses modelos de dados podem ser reutilizados para outros elementos de interface do ida e osso no aplicativo, a vantagem é que o modelo de dados é definido e mantido em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="888af-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="888af-122">O `AlbumStyle` modelo de dados estabelece `TextBlock`uma grade com dois s lado a lado.</span><span class="sxs-lookup"><span data-stu-id="888af-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="888af-123">Um especifica o nome do Álbum e o outro o número de faixas no álbum.</span><span class="sxs-lookup"><span data-stu-id="888af-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
```xaml  
<DataTemplate x:Key="AlbumStyle">  
    <Grid>  
        <Grid.ColumnDefinitions>  
            <ColumnDefinition Width="260" />  
            <ColumnDefinition Width="60" />  
        </Grid.ColumnDefinitions>  
        <TextBlock Grid.Column="0" TextContent="{Binding Path=Title}" />  
        <TextBlock Grid.Column="1" TextContent="{Binding Path=Tracks#.Count}" HorizontalAlignment="Right" />  
    </Grid>  
</DataTemplate>  
```  
  
 <span data-ttu-id="888af-124">O código XAML a `ListBox`seguir cria um segundo .</span><span class="sxs-lookup"><span data-stu-id="888af-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="888af-125">O código especifica um `ItemsSource`caminho para o .</span><span class="sxs-lookup"><span data-stu-id="888af-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="888af-126">Isso indica que os dados vinculados a este controle não são os dados `Tracks`de nível superior, mas uma propriedade dos dados de nível superior nomeados .</span><span class="sxs-lookup"><span data-stu-id="888af-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="888af-127">Esta propriedade representa a matriz de faixas contidas no álbum.</span><span class="sxs-lookup"><span data-stu-id="888af-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="888af-128">Além disso, `DataTemplate` um `TrackStyle` nome diferente é especificado.</span><span class="sxs-lookup"><span data-stu-id="888af-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="888af-129">O layout `TrackStyle` do modelo é semelhante `AlbumStyle` ao do `TextBlock`modelo, mas o s está vinculado a diferentes propriedades.</span><span class="sxs-lookup"><span data-stu-id="888af-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="888af-130">Isso porque os dois modelos são usados com diferentes objetos de dados.</span><span class="sxs-lookup"><span data-stu-id="888af-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="888af-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="888af-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="888af-132">Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="888af-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="888af-133">Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="888af-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="888af-134">Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="888af-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="888af-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="888af-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="888af-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="888af-136">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="888af-137">Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation).</span><span class="sxs-lookup"><span data-stu-id="888af-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="888af-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="888af-138">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
