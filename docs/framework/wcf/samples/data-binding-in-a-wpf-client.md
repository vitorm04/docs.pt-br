---
title: Associação de dados em um cliente do Windows Presentation Foundation
ms.date: 03/30/2017
ms.assetid: bb8c8293-5973-4aef-9b07-afeff5d3293c
ms.openlocfilehash: 1bc6dd2ef981115068cbd4cd491a14fea70d7e3a
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59305436"
---
# <a name="data-binding-in-a-windows-presentation-foundation-client"></a>Associação de dados em um cliente do Windows Presentation Foundation
Este exemplo demonstra o uso da ligação de dados em um cliente do Windows Presentation Foundation (WPF). O exemplo usa um serviço do Windows Communication Foundation (WCF) que gera aleatoriamente uma matriz de álbuns para retornar ao cliente. Cada álbum tem um nome, um preço e uma lista de faixas do álbum. As faixas do álbum tem um nome e uma duração. As informações que são retornadas pelo serviço são associadas automaticamente a interface do usuário (IU) fornecida pelo cliente do Windows Presentation Foundation (WPF).  
  
> [!NOTE]
>  As instruções de procedimento e compilação de configuração para este exemplo estão localizadas no final deste tópico.  
  
 Associação de dados permite que uma fonte de dados ser automaticamente associado a uma interface do usuário. Isso simplifica o modelo de programação porque ele não requer que você atualize cada elemento de interface do usuário por meio de programação com os dados de um objeto de dados ou uma matriz de objetos de dados. Você pode associar um objeto a um único elemento de interface do usuário ou uma matriz a um controle que recebe várias entradas, como um `ListBox`. O código a seguir mostra como associar dados para o `DataContext` de um elemento de interface do usuário.  
  
```  
// Event handler executed when call is complete  
void client_GetAlbumListCompleted(object sender, GetAlbumListCompletedEventArgs e)  
{  
    // This is on the UI thread, myPanel can be accessed directly  
    myPanel.DataContext = e.Result;   
}  
```  
  
 No exemplo anterior, o `DataContext` para o `grid` elemento de layout denominado `myPanel` é definido como os dados retornados pelo `GetAlbumList` método. O `DataContext` permite aos elementos herdar informações de seus elementos pais sobre a fonte de dados que é usado para associação, bem como outras características da associação como o caminho. A linha de código deve ser executada toda vez que os dados no servidor são atualizados. Por exemplo, ele é executado quando a janela é inicializada e quando um novo álbum é adicionado.  
  
 No código a seguir XAML de exemplo, o `ListBox` especifica `ItemsSource="{Binding }"`.  
  
```xml  
<ListBox   
          ItemTemplate="{StaticResource AlbumStyle}"  
          ItemsSource="{Binding }"   
          IsSynchronizedWithCurrentItem="true" />  
```  
  
 Isso especifica que os dados associados ao elemento de interface do usuário de nível superior também estão associados a esse controle (ou seja, a matriz de álbuns). Além disso, `ItemTemplate="{StaticResource AlbumStyle}"` Especifica o modelo de dados a ser usado para cada item no `ListBox`. Você também pode definir modelos de dados para especificar como os dados devem ser formatados. Esses modelos podem ser reutilizados para outros elementos de interface do usuário no aplicativo de dados, a vantagem é que o modelo de dados é definido e mantido em um só lugar.  
  
 O `AlbumStyle` modelo de dados dispõe de uma grade com dois `TextBlock`s lado a lado. Uma Especifica o nome do álbum e o outro, o número de faixas do álbum.  
  
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
  
 O código XAML a seguir cria um segundo `ListBox`.  
  
```xaml  
<ListBox Grid.Row="2"   
            Grid.ColumnSpan="2"   
            ItemTemplate="{StaticResource TrackStyle}"  
            ItemsSource="{Binding Path=Tracks}" />  
```  
  
 O código especifica um caminho para o `ItemsSource`. Isso indica que os dados associados a esse controle não são uma propriedade dos dados de nível superior chamados, mas os dados de nível superior `Tracks`. Esta propriedade representa a matriz de faixas contidos no álbum. Além disso, uma opção diferente `DataTemplate` chamado `TrackStyle` for especificado. O layout do `TrackStyle` modelo é semelhante do `AlbumStyle` modelo, mas o `TextBlock`s são associados a diferentes propriedades. Isso ocorre porque os dois modelos são usados com objetos de dados diferentes.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Para configurar, compilar, e executar o exemplo  
  
1. Certifique-se de que você tenha executado o [procedimento de configuração de uso único para os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Para compilar a edição em C# ou Visual Basic .NET da solução, siga as instruções em [compilando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Para executar o exemplo em uma configuração ou entre computadores, siga as instruções em [executando os exemplos do Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Os exemplos podem já estar instalados no seu computador. Verifique o seguinte diretório (padrão) antes de continuar.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Se este diretório não existir, vá para [Windows Communication Foundation (WCF) e o Windows Workflow Foundation (WF) exemplos do .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) para baixar todos os Windows Communication Foundation (WCF) e [!INCLUDE[wf1](../../../../includes/wf1-md.md)] exemplos. Este exemplo está localizado no seguinte diretório.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WPFDataBinding`  
