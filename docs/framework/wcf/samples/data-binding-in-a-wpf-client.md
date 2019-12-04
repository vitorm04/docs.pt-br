---
title: Associação de dados em um cliente do Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 44a208cf081ef00396dfc874349dff57363c0df3
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715394"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="31662-102">Associação de dados em um cliente do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="31662-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="31662-103">Este exemplo demonstra o uso de associação de dados em um cliente Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="31662-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="31662-104">O exemplo usa um serviço de Windows Communication Foundation (WCF) que gera aleatoriamente uma matriz de álbuns para retornar ao cliente.</span><span class="sxs-lookup"><span data-stu-id="31662-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="31662-105">Cada álbum tem um nome, um preço e uma lista de faixas de álbuns.</span><span class="sxs-lookup"><span data-stu-id="31662-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="31662-106">As faixas do álbum têm um nome e uma duração.</span><span class="sxs-lookup"><span data-stu-id="31662-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="31662-107">As informações retornadas pelo serviço são associadas automaticamente à interface do usuário (IU) fornecida pelo cliente do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="31662-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="31662-108">O procedimento de instalação e as instruções de Build para este exemplo estão localizados no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="31662-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="31662-109">A vinculação de dados permite que uma fonte de dados seja associada automaticamente a uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="31662-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="31662-110">Isso simplifica o modelo de programação porque não requer que você atualize programaticamente cada elemento de interface do usuário com os dados de um objeto de dados ou de uma matriz de objetos de dados.</span><span class="sxs-lookup"><span data-stu-id="31662-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="31662-111">Você pode associar um objeto a um único elemento de interface do usuário ou a uma matriz a um controle que usa várias entradas, como um `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="31662-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="31662-112">O código a seguir mostra como associar dados ao `DataContext` de um elemento de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="31662-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="31662-113">No exemplo anterior, o `DataContext` para o elemento de layout de `grid` chamado `myPanel` é definido como os dados retornados pelo método `GetAlbumList`.</span><span class="sxs-lookup"><span data-stu-id="31662-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="31662-114">O `DataContext` permite que os elementos herdem informações de seus elementos pai sobre a fonte de dados usada para associação, bem como outras características da associação, como o caminho.</span><span class="sxs-lookup"><span data-stu-id="31662-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="31662-115">A linha de código deve ser executada toda vez que os dados no servidor são atualizados.</span><span class="sxs-lookup"><span data-stu-id="31662-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="31662-116">Por exemplo, ele é executado quando a janela é inicializada e quando um novo álbum é adicionado.</span><span class="sxs-lookup"><span data-stu-id="31662-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="31662-117">No código XAML de exemplo a seguir, o `ListBox` especifica `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="31662-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="31662-118">Isso especifica que os dados vinculados ao elemento de interface de usuário de nível superior também estão associados a esse controle (ou seja, a matriz de álbuns).</span><span class="sxs-lookup"><span data-stu-id="31662-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="31662-119">Além disso, `ItemTemplate="{StaticResource AlbumStyle}"` especifica o modelo de dados a ser usado para cada item na `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="31662-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="31662-120">Você também pode definir modelos de dados para especificar como os dados devem ser formatados.</span><span class="sxs-lookup"><span data-stu-id="31662-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="31662-121">Esses modelos de dados podem ser reutilizados para outros elementos da interface do usuário no aplicativo, a vantagem é que o modelo de dados é definido e mantido em um único local.</span><span class="sxs-lookup"><span data-stu-id="31662-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="31662-122">O modelo de dados `AlbumStyle` cria uma grade com duas `TextBlock`s lado a lado.</span><span class="sxs-lookup"><span data-stu-id="31662-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="31662-123">Um especifica o nome do álbum e o outro número de faixas no álbum.</span><span class="sxs-lookup"><span data-stu-id="31662-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="31662-124">O código XAML a seguir cria um segundo `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="31662-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="31662-125">O código especifica um caminho para o `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="31662-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="31662-126">Isso indica que os dados associados a esse controle não são os dados de nível superior, mas uma propriedade dos dados de nível superior chamados `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="31662-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="31662-127">Essa propriedade representa a matriz de faixas contidas no álbum.</span><span class="sxs-lookup"><span data-stu-id="31662-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="31662-128">Além disso, um `DataTemplate` diferente chamado `TrackStyle` é especificado.</span><span class="sxs-lookup"><span data-stu-id="31662-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="31662-129">O layout do modelo de `TrackStyle` é semelhante ao do modelo de `AlbumStyle`, mas os `TextBlock`s estão associados a propriedades diferentes.</span><span class="sxs-lookup"><span data-stu-id="31662-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="31662-130">Isso ocorre porque os dois modelos são usados com objetos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="31662-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="31662-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="31662-131">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="31662-132">Verifique se você executou o [procedimento de configuração única para os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31662-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="31662-133">Para compilar a C# edição do ou Visual Basic .NET da solução, siga as instruções em [criando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31662-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="31662-134">Para executar o exemplo em uma configuração de computador único ou cruzado, siga as instruções em [executando os exemplos de Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="31662-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="31662-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="31662-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="31662-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="31662-136">Check for the following (default) directory before continuing.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> <span data-ttu-id="31662-137">Se esse diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos de Windows Workflow Foundation (WF) para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] amostras.</span><span class="sxs-lookup"><span data-stu-id="31662-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="31662-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="31662-138">This sample is located in the following directory.</span></span>  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
