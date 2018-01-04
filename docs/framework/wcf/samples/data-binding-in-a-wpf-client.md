---
title: "Associação de dados em um cliente do Windows Presentation Foundation"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 55e60aaba0ebba57668f91d692ce774bd0ef0115
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="79e43-102">Associação de dados em um cliente do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="79e43-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="79e43-103">Este exemplo demonstra o uso de associação de dados em um cliente do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="79e43-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="79e43-104">O exemplo usa um [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] serviço gerados aleatoriamente uma matriz de álbuns para retornar ao cliente.</span><span class="sxs-lookup"><span data-stu-id="79e43-104">The sample uses a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="79e43-105">Cada álbum tem um nome, um preço e uma lista de faixas de álbum.</span><span class="sxs-lookup"><span data-stu-id="79e43-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="79e43-106">As faixas de álbum tem um nome e a duração.</span><span class="sxs-lookup"><span data-stu-id="79e43-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="79e43-107">As informações que são retornadas pelo serviço é automaticamente vinculadas a interface do usuário (UI) fornecido pelo [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] cliente.</span><span class="sxs-lookup"><span data-stu-id="79e43-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the [!INCLUDE[avalon1](../../../../includes/avalon1-md.md)] client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79e43-108">As instruções de procedimento e a compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="79e43-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="79e43-109">Associação de dados permite que uma fonte de dados a ser associado automaticamente a uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="79e43-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="79e43-110">Isso simplifica o modelo de programação porque ele não requer que você atualize cada elemento de interface do usuário por meio de programação com os dados de um objeto de dados ou uma matriz de objetos de dados.</span><span class="sxs-lookup"><span data-stu-id="79e43-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="79e43-111">Você pode vincular um objeto a um único elemento de interface do usuário ou uma matriz a um controle que usa várias entradas, como um `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="79e43-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="79e43-112">O código a seguir mostra como associar dados para o `DataContext` de um elemento de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="79e43-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="79e43-113">No exemplo anterior, o `DataContext` para o `grid` elemento layout denominado `myPanel` é definido como os dados retornados pelo `GetAlbumList` método.</span><span class="sxs-lookup"><span data-stu-id="79e43-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="79e43-114">O `DataContext` permite aos elementos herdar informações de seus elementos pais sobre a fonte de dados que é usado para associação, bem como outras características da associação, como o caminho.</span><span class="sxs-lookup"><span data-stu-id="79e43-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="79e43-115">A linha de código deve ser executada sempre que os dados no servidor for atualizados.</span><span class="sxs-lookup"><span data-stu-id="79e43-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="79e43-116">Por exemplo, ele é executado quando a janela é inicializada e quando é adicionado um novo álbum.</span><span class="sxs-lookup"><span data-stu-id="79e43-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="79e43-117">No código a seguir XAML de exemplo, o `ListBox` especifica `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="79e43-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="79e43-118">Especifica que os dados associados a elemento de interface do usuário de nível superior também são associados a este controle (ou seja, a matriz de álbuns).</span><span class="sxs-lookup"><span data-stu-id="79e43-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="79e43-119">Além disso, `ItemTemplate="{StaticResource AlbumStyle}"` Especifica o modelo de dados a ser usado para cada item de `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="79e43-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="79e43-120">Você também pode definir modelos de dados para especificar como os dados devem ser formatados.</span><span class="sxs-lookup"><span data-stu-id="79e43-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="79e43-121">Esses modelos podem ser reutilizados para outros elementos de interface do usuário no aplicativo de dados, a vantagem é que o modelo de dados é definido e mantido em um único local.</span><span class="sxs-lookup"><span data-stu-id="79e43-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="79e43-122">O `AlbumStyle` modelo de dados estabelece uma grade com dois `TextBlock`s lado a lado.</span><span class="sxs-lookup"><span data-stu-id="79e43-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="79e43-123">Uma Especifica o nome do álbum e o outro, o número de faixas no álbum.</span><span class="sxs-lookup"><span data-stu-id="79e43-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="79e43-124">O código XAML a seguir cria um segundo `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="79e43-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="79e43-125">O código especifica um caminho para o `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="79e43-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="79e43-126">Isso indica que os dados associados a este controle não são uma propriedade dos dados de nível superior chamados, mas os dados de nível superior `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="79e43-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="79e43-127">Esta propriedade representa a matriz de faixas contidos no álbum.</span><span class="sxs-lookup"><span data-stu-id="79e43-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="79e43-128">Além disso, outro `DataTemplate` chamado `TrackStyle` for especificado.</span><span class="sxs-lookup"><span data-stu-id="79e43-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="79e43-129">O layout do `TrackStyle` modelo é semelhante do `AlbumStyle` modelo, mas o `TextBlock`s estão associados a diferentes propriedades.</span><span class="sxs-lookup"><span data-stu-id="79e43-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="79e43-130">Isso ocorre porque os dois modelos são usados com objetos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="79e43-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="79e43-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="79e43-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="79e43-132">Certifique-se de que você executou o [único procedimento de instalação para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79e43-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="79e43-133">Para compilar o c# ou Visual Basic .NET edição da solução, siga as instruções em [compilar os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79e43-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="79e43-134">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="79e43-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="79e43-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="79e43-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="79e43-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="79e43-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="79e43-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e exemplos do Windows Workflow Foundation (WF) para o .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="79e43-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="79e43-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="79e43-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a><span data-ttu-id="79e43-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="79e43-139">See Also</span></span>
