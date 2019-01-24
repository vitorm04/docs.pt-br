---
title: Associação de dados em um cliente do Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 467a81c3f574137bc95390f70d6913a532da6ffe
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54626895"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a><span data-ttu-id="d2da6-102">Associação de dados em um cliente do Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="d2da6-102">Data Binding in a Windows Presentation Foundation Client</span></span>
<span data-ttu-id="d2da6-103">Este exemplo demonstra o uso da ligação de dados em um cliente do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d2da6-103">This sample demonstrates the use of data binding in a Windows Presentation Foundation (WPF) client.</span></span> <span data-ttu-id="d2da6-104">O exemplo usa um serviço do Windows Communication Foundation (WCF) que gera aleatoriamente uma matriz de álbuns para retornar ao cliente.</span><span class="sxs-lookup"><span data-stu-id="d2da6-104">The sample uses a Windows Communication Foundation (WCF) service that randomly generates an array of albums to return to the client.</span></span> <span data-ttu-id="d2da6-105">Cada álbum tem um nome, um preço e uma lista de faixas do álbum.</span><span class="sxs-lookup"><span data-stu-id="d2da6-105">Each album has a name, a price, and a list of album tracks.</span></span> <span data-ttu-id="d2da6-106">As faixas do álbum tem um nome e uma duração.</span><span class="sxs-lookup"><span data-stu-id="d2da6-106">The album tracks have a name and duration.</span></span> <span data-ttu-id="d2da6-107">As informações que são retornadas pelo serviço são associadas automaticamente a interface do usuário (IU) fornecida pelo cliente do Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="d2da6-107">The information that is returned by the service is automatically bound to the user interface (UI) provided by the Windows Presentation Foundation (WPF) client.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2da6-108">As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.</span><span class="sxs-lookup"><span data-stu-id="d2da6-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="d2da6-109">Associação de dados permite que uma fonte de dados ser automaticamente associado a uma interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d2da6-109">Data binding allows a data source to be automatically bound to a UI.</span></span> <span data-ttu-id="d2da6-110">Isso simplifica o modelo de programação porque ele não requer que você atualize cada elemento de interface do usuário por meio de programação com os dados de um objeto de dados ou uma matriz de objetos de dados.</span><span class="sxs-lookup"><span data-stu-id="d2da6-110">This simplifies the programming model because it does not require that you programmatically update each UI element with the data from a data object or an array of data objects.</span></span> <span data-ttu-id="d2da6-111">Você pode associar um objeto a um único elemento de interface do usuário ou uma matriz a um controle que recebe várias entradas, como um `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2da6-111">You can bind an object to a single UI element or an array to a control that takes multiple inputs, such as a `ListBox`.</span></span> <span data-ttu-id="d2da6-112">O código a seguir mostra como associar dados para o `DataContext` de um elemento de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="d2da6-112">The following code shows how to bind data to the `DataContext` of a UI element.</span></span>  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 <span data-ttu-id="d2da6-113">No exemplo anterior, o `DataContext` para o `grid` elemento de layout denominado `myPanel` é definido como os dados retornados pelo `GetAlbumList` método.</span><span class="sxs-lookup"><span data-stu-id="d2da6-113">In the previous sample, the `DataContext` for the `grid` layout element named `myPanel` is set to the data returned by the `GetAlbumList` method.</span></span> <span data-ttu-id="d2da6-114">O `DataContext` permite aos elementos herdar informações de seus elementos pais sobre a fonte de dados que é usado para associação, bem como outras características da associação como o caminho.</span><span class="sxs-lookup"><span data-stu-id="d2da6-114">The `DataContext` allows elements to inherit information from their parent elements about the data source that is used for binding, as well as other characteristics of the binding such as the path.</span></span> <span data-ttu-id="d2da6-115">A linha de código deve ser executada toda vez que os dados no servidor são atualizados.</span><span class="sxs-lookup"><span data-stu-id="d2da6-115">The line of code must be executed every time the data on the server is updated.</span></span> <span data-ttu-id="d2da6-116">Por exemplo, ele é executado quando a janela é inicializada e quando um novo álbum é adicionado.</span><span class="sxs-lookup"><span data-stu-id="d2da6-116">For example, it is executed when the window is initialized and when a new album is added.</span></span>  
  
 <span data-ttu-id="d2da6-117">No código a seguir XAML de exemplo, o `ListBox` especifica `ItemsSource="{Binding }"`.</span><span class="sxs-lookup"><span data-stu-id="d2da6-117">In the following sample XAML code, the `ListBox` specifies `ItemsSource="{Binding }"`.</span></span>  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 <span data-ttu-id="d2da6-118">Isso especifica que os dados associados ao elemento de interface do usuário de nível superior também estão associados a esse controle (ou seja, a matriz de álbuns).</span><span class="sxs-lookup"><span data-stu-id="d2da6-118">This specifies that the data bound to the top-level UI element is also bound to this control (that is, the array of Albums).</span></span> <span data-ttu-id="d2da6-119">Além disso, `ItemTemplate="{StaticResource AlbumStyle}"` Especifica o modelo de dados a ser usado para cada item no `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2da6-119">In addition, `ItemTemplate="{StaticResource AlbumStyle}"` specifies the data template to be used for each item in the `ListBox`.</span></span> <span data-ttu-id="d2da6-120">Você também pode definir modelos de dados para especificar como os dados devem ser formatados.</span><span class="sxs-lookup"><span data-stu-id="d2da6-120">You can also define data templates to specify how the data should be formatted.</span></span> <span data-ttu-id="d2da6-121">Esses modelos podem ser reutilizados para outros elementos de interface do usuário no aplicativo de dados, a vantagem é que o modelo de dados é definido e mantido em um só lugar.</span><span class="sxs-lookup"><span data-stu-id="d2da6-121">These data templates can be reused for other UI elements in the application, the advantage is that the data template is defined and maintained in one place.</span></span>  
  
 <span data-ttu-id="d2da6-122">O `AlbumStyle` modelo de dados dispõe de uma grade com dois `TextBlock`s lado a lado.</span><span class="sxs-lookup"><span data-stu-id="d2da6-122">The `AlbumStyle` data template lays out a grid with two `TextBlock`s side by side.</span></span> <span data-ttu-id="d2da6-123">Uma Especifica o nome do álbum e o outro, o número de faixas do álbum.</span><span class="sxs-lookup"><span data-stu-id="d2da6-123">One specifies the name of the Album and the other the number of Tracks in the album.</span></span>  
  
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
  
 <span data-ttu-id="d2da6-124">O código XAML a seguir cria um segundo `ListBox`.</span><span class="sxs-lookup"><span data-stu-id="d2da6-124">The following XAML code creates a second `ListBox`.</span></span>  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 <span data-ttu-id="d2da6-125">O código especifica um caminho para o `ItemsSource`.</span><span class="sxs-lookup"><span data-stu-id="d2da6-125">The code specifies a path for the `ItemsSource`.</span></span> <span data-ttu-id="d2da6-126">Isso indica que os dados associados a esse controle não são uma propriedade dos dados de nível superior chamados, mas os dados de nível superior `Tracks`.</span><span class="sxs-lookup"><span data-stu-id="d2da6-126">This indicates that the data bound to this control is not the top-level data but a property of the top-level data named `Tracks`.</span></span> <span data-ttu-id="d2da6-127">Esta propriedade representa a matriz de faixas contidos no álbum.</span><span class="sxs-lookup"><span data-stu-id="d2da6-127">This property represents the array of tracks contained within the album.</span></span> <span data-ttu-id="d2da6-128">Além disso, uma opção diferente `DataTemplate` chamado `TrackStyle` for especificado.</span><span class="sxs-lookup"><span data-stu-id="d2da6-128">In addition, a different `DataTemplate` named `TrackStyle` is specified.</span></span> <span data-ttu-id="d2da6-129">O layout do `TrackStyle` modelo é semelhante do `AlbumStyle` modelo, mas o `TextBlock`s são associados a diferentes propriedades.</span><span class="sxs-lookup"><span data-stu-id="d2da6-129">The layout of the `TrackStyle` template is similar to that of the `AlbumStyle` template, but the `TextBlock`s are bound to different properties.</span></span> <span data-ttu-id="d2da6-130">Isso ocorre porque os dois modelos são usados com objetos de dados diferentes.</span><span class="sxs-lookup"><span data-stu-id="d2da6-130">This is because the two templates are used with different data objects.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="d2da6-131">Para configurar, compilar, e executar o exemplo</span><span class="sxs-lookup"><span data-stu-id="d2da6-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="d2da6-132">Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2da6-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="d2da6-133">Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2da6-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="d2da6-134">Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="d2da6-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2da6-135">Os exemplos podem já estar instalados no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d2da6-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d2da6-136">Verifique o seguinte diretório (padrão) antes de continuar.</span><span class="sxs-lookup"><span data-stu-id="d2da6-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="d2da6-137">Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos.</span><span class="sxs-lookup"><span data-stu-id="d2da6-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d2da6-138">Este exemplo está localizado no seguinte diretório.</span><span class="sxs-lookup"><span data-stu-id="d2da6-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
  
## <a name="see-also"></a><span data-ttu-id="d2da6-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d2da6-139">See also</span></span>
