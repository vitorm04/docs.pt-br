---
title: Arquivos de recurso, conteúdo e dados do aplicativo WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF application [WPF], files
- loose resources [WPF]
- content files [WPF]
- Site of Origin files [WPF]
- resource files [WPF]
- remote files [WPF]
- embedded resources [WPF]
- files [WPF]
- referencing application files [WPF]
- application development [WPF], files
- application management [WPF]
ms.assetid: 7ad2943b-3961-41d3-8fc6-1582d43f5d99
ms.openlocfilehash: 57eae5067a72777db2c19331029b6df679a9fdce
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956186"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Arquivos de recurso, conteúdo e dados do aplicativo WPF
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]os aplicativos geralmente dependem de arquivos que contêm dados não executáveis, como [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]imagens, vídeos e áudio. O Windows Presentation Foundation (WPF) oferece suporte especial para configurar, identificar e usar esses tipos de arquivos de dados, que são chamados de arquivos de dados de aplicativo. Esse suporte gira em torno de um conjunto específico de tipos de arquivo de dados do aplicativo, incluindo:  
  
- **Arquivos de recurso**: Arquivos de dados que são compilados em um assembly executável [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] ou de biblioteca.  
  
- **Arquivos de conteúdo**: Arquivos de dados autônomos que têm uma associação explícita com [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] um assembly executável.  
  
- **Arquivos de site de origem**: Arquivos de dados autônomos que não têm associação com [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] um assembly executável.  
  
 Uma distinção importante a se fazer entre esses três tipos de arquivos é que os arquivos de recurso e os arquivos de conteúdo são conhecidos em tempo de build; um assembly tem o conhecimento explícito sobre eles. Para arquivos de site de origem, no entanto, um assembly pode não ter nenhum conhecimento sobre eles ou conhecimento implícito por meio [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] de uma referência de pacote; o caso do último, não há garantia de que o site de origem referenciado realmente existe.  
  
 Para fazer referência a arquivos de dados de aplicativo, Windows Presentation Foundation (WPF [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] ) usa o esquema de pacote, que é descrito em detalhes em [URIs de pacote no WPF](pack-uris-in-wpf.md)).  
  
 Este tópico descreve como configurar e usar arquivos de dados do aplicativo.  

<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Arquivos de recursos  
 Se um arquivo de dados do aplicativo precisar estar sempre disponível para um aplicativo, a única maneira de garantir essa disponibilidade será compilá-lo em um assembly executável principal do aplicativo ou em um de seus assemblies referenciados. Esse tipo de arquivo de dados de aplicativo é conhecido como um *arquivo de recurso*.  
  
 Você deve usar arquivos de recurso quando:  
  
- Você não precisa atualizar o conteúdo do arquivo de recurso depois que ele é compilado em um assembly.  
  
- Você deseja simplificar a complexidade da distribuição de aplicativos, reduzindo o número de dependências de arquivo.  
  
- O arquivo de dados do aplicativo precisa ser localizável (consulte [visão geral de globalização e localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Os arquivos de recursos descritos nesta seção são diferentes dos arquivos de recursos descritos em [recursos XAML](../advanced/xaml-resources.md) e diferentes dos recursos incorporados ou vinculados descritos em [gerenciar recursos do aplicativo (.net)](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>Configurando arquivos de recurso  
 No [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], um arquivo de recurso é um arquivo que é incluído em um projeto do Microsoft Build Engine (MSBuild) `Resource` como um item.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> No [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], você cria um arquivo de recurso adicionando um arquivo a um projeto e definindo seu `Build Action` como `Resource`.  
  
 Quando o projeto é compilado, o MSBuild compila o recurso no assembly.  
  
### <a name="using-resource-files"></a>Usando arquivos de recurso  
 Para carregar um arquivo <xref:System.Windows.Application.GetResourceStream%2A> <xref:System.Windows.Application> de recurso, você pode chamar o método da classe, passando um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica o arquivo de recurso desejado. <xref:System.Windows.Application.GetResourceStream%2A>Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o arquivo de recurso como <xref:System.IO.Stream> um e descreve seu tipo de conteúdo.  
  
 Por exemplo, o código a seguir mostra como <xref:System.Windows.Application.GetResourceStream%2A> usar o para carregar um <xref:System.Windows.Controls.Page> arquivo de recurso e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Embora a <xref:System.Windows.Application.GetResourceStream%2A> chamada forneça acesso <xref:System.IO.Stream>ao, você precisa executar o trabalho adicional de convertê-lo para o tipo da propriedade com a qual você irá configurá-lo. Em vez disso, você [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pode cuidar de abrir e converter o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> (`pageFrame`) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Arquivos de código de aplicativo como arquivos de recurso  
 Um conjunto especial de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] arquivos de código do aplicativo pode ser referenciado usando o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], incluindo janelas, páginas, documentos de fluxo e dicionários de recursos. Por exemplo, você pode definir a <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> Propriedade com um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que faz referência à janela ou à página que você deseja carregar quando um aplicativo é iniciado.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Você pode fazer isso quando um arquivo XAML é incluído em um projeto do MSBuild como `Page` um item.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Page Include="MainWindow.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> No [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], você adiciona um novo <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>, ou `Build Action` `Page`a um projeto, o para o arquivo de marcação usará como padrão. <xref:System.Windows.ResourceDictionary>  
  
 Quando um projeto com `Page` itens é compilado, os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] itens são convertidos em formato binário e compilados no assembly associado. Consequentemente, esses arquivos podem ser usados da mesma maneira que arquivos de recurso típicos.  
  
> [!NOTE]
> Se um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo estiver configurado como um `Resource` item e não tiver um arquivo code-behind, o RAW [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] será compilado em um assembly em vez de uma versão binária do RAW [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Arquivos de Conteúdo  
 Um *arquivo de conteúdo* é distribuído como um arquivo flexível junto com um assembly executável. Embora eles não sejam compilados em um assembly, os assemblies são compilados com metadados que estabelecem uma associação com cada arquivo de conteúdo.  
  
 Você deve usar arquivos de conteúdo quando o aplicativo requer um conjunto específico de arquivos de dados do aplicativo que você deseja ser capaz de atualizar sem recompilar o assembly que os consome.  
  
### <a name="configuring-content-files"></a>Configurando arquivos de conteúdo  
 Para adicionar um arquivo de conteúdo a um projeto, um arquivo de dados do aplicativo deve ser `Content` incluído como um item. Além disso, como um arquivo de conteúdo não é compilado diretamente no assembly, você precisa definir o elemento `CopyToOutputDirectory` de metadados do MSBuild para especificar que o arquivo de conteúdo seja copiado para um local relativo ao assembly compilado. Se você quiser que o recurso seja copiado para a pasta de saída de compilação toda vez que um projeto for compilado `CopyToOutputDirectory` , defina o elemento `Always` de metadados com o valor. Caso contrário, você pode garantir que apenas a versão mais recente do recurso seja copiada para a pasta de saída de `PreserveNewest` compilação usando o valor.  
  
 A seguir é mostrado um arquivo que está configurado como um arquivo de conteúdo que é copiado para a pasta de saída de build somente quando uma nova versão do recurso é adicionada ao projeto.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Content Include="ContentFile.xaml">  
      <CopyToOutputDirectory>PreserveNewest</CopyToOutputDirectory>  
    </Content>  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
> No [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], você cria um arquivo de conteúdo adicionando um arquivo a um projeto e definindo `Content`seu `Build Action` como e define seu `Copy to Output Directory` como `Copy always` (igual `Always`a) e `Copy if newer` (o mesmo que `PreserveNewest`).  
  
 Quando o projeto é compilado, um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo é compilado nos metadados do assembly para cada arquivo de conteúdo.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 O valor de <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implica o caminho para o arquivo de conteúdo relativo à sua posição no projeto. Por exemplo, se um arquivo de conteúdo estava localizado em uma subpasta do projeto, as informações de caminho adicionais seriam <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> incorporadas ao valor.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 O <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor também é o valor do caminho para o arquivo de conteúdo na pasta de saída de compilação.  
  
### <a name="using-content-files"></a>Usando arquivos de conteúdo  
 Para carregar um arquivo <xref:System.Windows.Application.GetContentStream%2A> <xref:System.Windows.Application> de conteúdo, você pode chamar o método da classe, passando um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica o arquivo de conteúdo desejado. <xref:System.Windows.Application.GetContentStream%2A>Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o arquivo de conteúdo como <xref:System.IO.Stream> um e descreve seu tipo de conteúdo.  
  
 Por exemplo, o código a seguir mostra como <xref:System.Windows.Application.GetContentStream%2A> usar o para carregar um <xref:System.Windows.Controls.Page> arquivo de conteúdo e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Embora a <xref:System.Windows.Application.GetContentStream%2A> chamada forneça acesso <xref:System.IO.Stream>ao, você precisa executar o trabalho adicional de convertê-lo para o tipo da propriedade com a qual você irá configurá-lo. Em vez disso, você [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pode cuidar de abrir e converter o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> (`pageFrame`) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Arquivos de site de origem  
 Os arquivos de recurso têm uma relação explícita com os assemblies que eles são distribuídos juntamente com o <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>, conforme definido pelo. Mas, às vezes você deseja estabelecer um relacionamento implícito ou inexistente entre um assembly e um arquivo de dados do aplicativo, como quando:  
  
- Um arquivo não existe no momento da compilação.  
  
- Você não sabe quais arquivos seu assembly vai requerer até o tempo de execução.  
  
- Você deseja ser capaz de atualizar os arquivos sem recompilar o assembly ao qual eles estão associados.  
  
- O aplicativo usa arquivos de dados grandes, como áudio e vídeo, e você só deseja que os usuários os baixem caso desejem.  
  
 É possível carregar esses tipos de arquivos usando esquemas tradicionais [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] , como os esquemas file:///e http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 No entanto, os esquemas file:/// e http:// requerem que seu aplicativo tenha confiança total. Se seu aplicativo é um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] que foi iniciado pela Internet ou intranet e solicita apenas o conjunto de permissões permitido para aplicativos iniciados a partir desses locais, os arquivos flexíveis só podem ser carregados a partir do site de origem do aplicativo ( local de inicialização). Esses arquivos são conhecidos como arquivos *de site de origem* .  
  
 Os arquivos de site de origem são a única opção para aplicativos parcialmente confiáveis, apesar de não serem limitados a aplicativos parcialmente confiáveis. Os aplicativos de confiança total ainda podem precisar carregar arquivos de dados do aplicativo que eles não conhecem em tempo de build. Embora os aplicativos de confiança total possam utilizar file:///, é provável que os arquivos de dados do aplicativo sejam instalados na mesma pasta ou em uma subpasta do assembly do aplicativo. Nesse caso, usar a referência do site de origem é mais fácil do que usar file:///, porque o uso de file:/// requer que você descubra o caminho completo do arquivo.  
  
> [!NOTE]
> Os arquivos de site de origem não são armazenados em [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] cache com um em um computador cliente, enquanto os arquivos de conteúdo são. Consequentemente, eles são baixados somente quando solicitado especificamente. Se um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplicativo tiver arquivos de mídia grandes, configurá-los como arquivos de site de origem significa que a inicialização inicial do aplicativo é muito mais rápida e os arquivos só são baixados sob demanda.  
  
### <a name="configuring-site-of-origin-files"></a>Configurando arquivos de site de origem  
 Se os arquivos do site de origem forem inexistentes ou desconhecidos no momento da compilação, você precisará usar mecanismos de implantação tradicionais para garantir que os arquivos necessários estejam disponíveis em tempo `XCopy` de execução, incluindo o uso do programa de linha de comando ou do [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Se você souber em tempo de compilação os arquivos que deseja que estejam localizados no site de origem, mas ainda quiser evitar uma dependência explícita, poderá adicionar esses arquivos a um projeto do MSBuild como `None` item. Assim como os arquivos de conteúdo, você precisa definir o `CopyToOutputDirectory` atributo MSBuild para especificar que o arquivo de site de origem seja copiado para um local relativo ao assembly compilado, especificando o `Always` valor ou o `PreserveNewest` valor.  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <None Include="PageSiteOfOriginFile.xaml">  
    <CopyToOutputDirectory>Always</CopyToOutputDirectory>  
  </None>  
  ...  
</Project>  
```  
  
> [!NOTE]
> No [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], você cria um arquivo de site de origem adicionando um arquivo a um projeto e definindo seu `Build Action` como `None`.  
  
 Quando o projeto é compilado, o MSBuild copia os arquivos especificados para a pasta de saída de compilação.  
  
### <a name="using-site-of-origin-files"></a>Usando arquivos de site de origem  
 Para carregar um arquivo de site de origem, você pode chamar <xref:System.Windows.Application.GetRemoteStream%2A> o método <xref:System.Windows.Application> da classe, passando um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica o local de arquivo de origem desejado. <xref:System.Windows.Application.GetRemoteStream%2A>Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o site do arquivo de origem como <xref:System.IO.Stream> um e descreve seu tipo de conteúdo.  
  
 Por exemplo, o código a seguir mostra como <xref:System.Windows.Application.GetRemoteStream%2A> usar o para carregar um <xref:System.Windows.Controls.Page> arquivo de site de origem e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Embora a <xref:System.Windows.Application.GetRemoteStream%2A> chamada forneça acesso <xref:System.IO.Stream>ao, você precisa executar o trabalho adicional de convertê-lo para o tipo da propriedade com a qual você irá configurá-lo. Em vez disso, você [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] pode cuidar de abrir e converter o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> (`pageFrame`) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Recompilando após modificar o tipo de build  
 Depois de alterar o tipo de build de um arquivo de dados do aplicativo, você precisa recompilar o aplicativo inteiro para garantir que essas alterações sejam aplicadas. Se você apenas compilar o aplicativo, as alterações não serão aplicadas.  
  
## <a name="see-also"></a>Consulte também

- [URIs "pack://" no WPF](pack-uris-in-wpf.md)
