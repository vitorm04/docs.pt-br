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
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Associação de dados em um cliente do Windows Presentation Foundation
Esta amostra demonstra o uso da vinculação de dados em um cliente WPF (Windows Presentation Foundation). A amostra usa um serviço do Windows Communication Foundation (WCF) que gera aleatoriamente uma série de álbuns para retornar ao cliente. Cada álbum tem um nome, um preço e uma lista de faixas de álbuns. As faixas do álbum têm nome e duração. As informações que são devolvidas pelo serviço estão automaticamente vinculadas à interface do usuário (UI) fornecida pelo cliente Da Windows Presentation Foundation (WPF).  
  
> [!NOTE]
> O procedimento de configuração e as instruções de construção desta amostra estão localizados no final deste tópico.  
  
 A vinculação de dados permite que uma fonte de dados seja automaticamente vinculada a uma ui. Isso simplifica o modelo de programação porque não exige que você atualize programáticamente cada elemento de UI com os dados de um objeto de dados ou de um conjunto de objetos de dados. Você pode vincular um objeto a um único elemento de ia ou a `ListBox`uma matriz a um controle que requer várias entradas, como a . O código a seguir mostra `DataContext` como vincular dados ao de um elemento de IA.  
  
```csharp  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;
}  
```  
  
 Na amostra anterior, `DataContext` o `grid` elemento `myPanel` para layout nomeado é definido `GetAlbumList` para os dados retornados pelo método. O `DataContext` permite que os elementos herdem informações de seus elementos-mãe sobre a fonte de dados que é usada para vinculação, bem como outras características da ligação, como o caminho. A linha de código deve ser executada sempre que os dados do servidor forem atualizados. Por exemplo, ele é executado quando a janela é inicializada e quando um novo álbum é adicionado.  
  
 Na seguinte amostra código XAML, as `ListBox` especificações `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Isso especifica que os dados vinculados ao elemento de iu de nível superior também estão vinculados a esse controle (ou seja, a matriz de Álbuns). Além disso, `ItemTemplate="{StaticResource AlbumStyle}"` especifica o modelo de dados a `ListBox`ser usado para cada item no . Você também pode definir modelos de dados para especificar como os dados devem ser formatados. Esses modelos de dados podem ser reutilizados para outros elementos de interface do ida e osso no aplicativo, a vantagem é que o modelo de dados é definido e mantido em um só lugar.  
  
 O `AlbumStyle` modelo de dados estabelece `TextBlock`uma grade com dois s lado a lado. Um especifica o nome do Álbum e o outro o número de faixas no álbum.  
  
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
  
 O código XAML a `ListBox`seguir cria um segundo .  
  
```xaml  
<ListBox Grid.Row="2"
            Grid.ColumnSpan="2"
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 O código especifica um `ItemsSource`caminho para o . Isso indica que os dados vinculados a este controle não são os dados `Tracks`de nível superior, mas uma propriedade dos dados de nível superior nomeados . Esta propriedade representa a matriz de faixas contidas no álbum. Além disso, `DataTemplate` um `TrackStyle` nome diferente é especificado. O layout `TrackStyle` do modelo é semelhante `AlbumStyle` ao do `TextBlock`modelo, mas o s está vinculado a diferentes propriedades. Isso porque os dois modelos são usados com diferentes objetos de dados.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha realizado o [procedimento de configuração única para as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para construir a edição C# ou Visual Basic .NET da solução, siga as instruções em [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar a amostra em uma configuração de máquina única ou cruzada, siga as instruções em [Executar as amostras da Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Se esse diretório não existir, vá para [a Windows Communication Foundation (WCF) e para o Windows Workflow Foundation (WF) Amostras para .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) para baixar todas as Amostras e amostras da [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Windows Communication Foundation (Windows Communication Foundation). Este exemplo está localizado no seguinte diretório.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
