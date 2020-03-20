---
title: Recursos de aplicativos, conteúdo e arquivos de dados
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
ms.openlocfilehash: f17898972eeef66447060db32bae5fae377b710e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186196"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Arquivos de recurso, conteúdo e dados do aplicativo WPF
Os aplicativos microsoft windows geralmente dependem de arquivos que [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]contêm dados não executáveis, como, imagens, vídeo e áudio. O Windows Presentation Foundation (WPF) oferece suporte especial para configurar, identificar e usar esses tipos de arquivos de dados, que são chamados de arquivos de dados de aplicativos. Esse suporte gira em torno de um conjunto específico de tipos de arquivo de dados do aplicativo, incluindo:  
  
- **Arquivos de recursos**: Arquivos de dados que são compilados em um conjunto WPF executável ou de biblioteca.  
  
- **Arquivos de conteúdo**: Arquivos de dados autônomos que têm uma associação explícita com um conjunto WPF executável.  
  
- **Site of Origin Files**: Arquivos de dados autônomos que não têm associação com um conjunto WPF executável.  
  
 Uma distinção importante a se fazer entre esses três tipos de arquivos é que os arquivos de recurso e os arquivos de conteúdo são conhecidos em tempo de build; um assembly tem o conhecimento explícito sobre eles. Para arquivos de site de origem, no entanto, uma assembléia pode não ter conhecimento algum deles, ou conhecimento implícito através de uma referência uri (identificador de recursos uniforme de pacote); no caso deste último, não há garantia de que o arquivo de origem do site referenciado realmente exista.  
  
 Para referenciar arquivos de dados de aplicativos, o Windows Presentation Foundation (WPF) usa o Esquema uri (Uniform Resource Identifier) do Pack, que é descrito em detalhes em [URIs do Pack no WPF](pack-uris-in-wpf.md)).  
  
 Este tópico descreve como configurar e usar arquivos de dados do aplicativo.  

<a name="Resource_Files"></a>
## <a name="resource-files"></a>Arquivos de recursos  
 Se um arquivo de dados do aplicativo precisar estar sempre disponível para um aplicativo, a única maneira de garantir essa disponibilidade será compilá-lo em um assembly executável principal do aplicativo ou em um de seus assemblies referenciados. Esse tipo de arquivo de dados de aplicativo é conhecido como um *arquivo de recursos*.  
  
 Você deve usar arquivos de recurso quando:  
  
- Você não precisa atualizar o conteúdo do arquivo de recurso depois que ele é compilado em um assembly.  
  
- Você deseja simplificar a complexidade da distribuição de aplicativos, reduzindo o número de dependências de arquivo.  
  
- O arquivo de dados do aplicativo precisa ser localizado (consulte [Visão Geral de Globalização e Localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
> Os arquivos de recursos descritos nesta seção são diferentes dos arquivos de recursos descritos no [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) e diferentes dos recursos incorporados ou vinculados descritos no [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).  
  
### <a name="configuring-resource-files"></a>Configurando arquivos de recurso  
 No WPF, um arquivo de recursos é um arquivo incluído em um `Resource` projeto de mecanismo de compilação microsoft (MSBuild) como um item.  
  
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
> No Visual Studio, você cria um arquivo de recursos `Build Action` adicionando um arquivo a um projeto e definindo-o para `Resource`.  
  
 Quando o projeto é construído, o MSBuild compila o recurso na montagem.  
  
### <a name="using-resource-files"></a>Usando arquivos de recurso  
 Para carregar um arquivo de <xref:System.Windows.Application.GetResourceStream%2A> recursos, <xref:System.Windows.Application> você pode chamar o método da classe, passando um URI de pacote que identifica o arquivo de recurso desejado. <xref:System.Windows.Application.GetResourceStream%2A>retorna <xref:System.Windows.Resources.StreamResourceInfo> um objeto, que expõe o <xref:System.IO.Stream> arquivo de recursos como um e descreve seu tipo de conteúdo.  
  
 Como exemplo, o código a <xref:System.Windows.Application.GetResourceStream%2A> seguir mostra <xref:System.Windows.Controls.Page> como usar para carregar um <xref:System.Windows.Controls.Frame> `pageFrame`arquivo de recurso e defini-lo como o conteúdo de a ( ):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Ao <xref:System.Windows.Application.GetResourceStream%2A> ligar, você <xref:System.IO.Stream>precisa realizar o trabalho adicional de convertê-lo para o tipo de propriedade com a que você estará definindo-o. Em vez disso, você pode deixar o <xref:System.IO.Stream> WPF cuidar da abertura e conversão do carregamento de um arquivo de recursos diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir <xref:System.Windows.Controls.Page> mostra como <xref:System.Windows.Controls.Frame> `pageFrame`carregar um diretamente em um ( ) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Arquivos de código de aplicativo como arquivos de recurso  
 Um conjunto especial de arquivos de código de aplicativo WPF pode ser referenciado usando URIs de pacote, incluindo janelas, páginas, documentos de fluxo e dicionários de recursos. Por exemplo, você <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> pode definir a propriedade com um URI de pacote que faz referência à janela ou página que você gostaria de carregar quando um aplicativo for iniciado.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Você pode fazer isso quando um arquivo XAML é `Page` incluído em um projeto MSBuild como item.  
  
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
> No Visual Studio, você <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>adiciona <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>um <xref:System.Windows.ResourceDictionary> novo , , `Build Action` , ou a um `Page`projeto, o arquivo de marcação será padrão para .  
  
 Quando um `Page` projeto com itens é [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compilado, os itens são convertidos em formato binário e compilados no conjunto associado. Consequentemente, esses arquivos podem ser usados da mesma maneira que arquivos de recurso típicos.  
  
> [!NOTE]
> Se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo for `Resource` configurado como um item e não tiver [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de código atrás, o raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]será compilado em um conjunto em vez de uma versão binária do raw .  
  
<a name="Content_Files"></a>
## <a name="content-files"></a>Arquivos de Conteúdo  
 Um *arquivo de conteúdo* é distribuído como um arquivo solto ao lado de um conjunto executável. Embora eles não sejam compilados em um assembly, os assemblies são compilados com metadados que estabelecem uma associação com cada arquivo de conteúdo.  
  
 Você deve usar arquivos de conteúdo quando o aplicativo requer um conjunto específico de arquivos de dados do aplicativo que você deseja ser capaz de atualizar sem recompilar o assembly que os consome.  
  
### <a name="configuring-content-files"></a>Configurando arquivos de conteúdo  
 Para adicionar um arquivo de conteúdo a um projeto, `Content` um arquivo de dados de aplicativo deve ser incluído como um item. Além disso, como um arquivo de conteúdo não é compilado diretamente no `CopyToOutputDirectory` conjunto, você precisa definir o elemento metadados do MSBuild para especificar que o arquivo de conteúdo é copiado para um local que é relativo ao conjunto construído. Se você quiser que o recurso seja copiado para a pasta de `CopyToOutputDirectory` saída de `Always` compilação toda vez que um projeto for construído, você definirá o elemento metadados com o valor. Caso contrário, você pode garantir que apenas a versão mais recente do recurso `PreserveNewest` seja copiada para a pasta de saída de compilação usando o valor.  
  
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
> No Visual Studio, você cria um arquivo de conteúdo `Build Action` adicionando um arquivo a um projeto e definindo-o `Content`para , e definir -lo `Copy to Output Directory` `Copy always` (mesmo que `Always`) e `Copy if newer` (mesmo que `PreserveNewest`).  
  
 Quando o projeto é <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> construído, um atributo é compilado nos metadados do conjunto para cada arquivo de conteúdo.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 O valor <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> do implica o caminho para o arquivo de conteúdo em relação à sua posição no projeto. Por exemplo, se um arquivo de conteúdo estivesse localizado em uma subpasta <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> de projeto, as informações adicionais de caminho seriam incorporadas ao valor.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 O <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor também é o valor do caminho para o arquivo de conteúdo na pasta de saída de compilação.  
  
### <a name="using-content-files"></a>Usando arquivos de conteúdo  
 Para carregar um arquivo de <xref:System.Windows.Application.GetContentStream%2A> conteúdo, <xref:System.Windows.Application> você pode chamar o método da classe, passando um URI de pacote que identifica o arquivo de conteúdo desejado. <xref:System.Windows.Application.GetContentStream%2A>retorna <xref:System.Windows.Resources.StreamResourceInfo> um objeto, que expõe o <xref:System.IO.Stream> arquivo de conteúdo como um e descreve seu tipo de conteúdo.  
  
 Como exemplo, o código a <xref:System.Windows.Application.GetContentStream%2A> seguir mostra <xref:System.Windows.Controls.Page> como usar para carregar um <xref:System.Windows.Controls.Frame> `pageFrame`arquivo de conteúdo e defini-lo como o conteúdo de a ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Ao <xref:System.Windows.Application.GetContentStream%2A> ligar, você <xref:System.IO.Stream>precisa realizar o trabalho adicional de convertê-lo para o tipo de propriedade com a que você estará definindo-o. Em vez disso, você pode deixar o <xref:System.IO.Stream> WPF cuidar da abertura e conversão do carregamento de um arquivo de recursos diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir <xref:System.Windows.Controls.Page> mostra como <xref:System.Windows.Controls.Frame> `pageFrame`carregar um diretamente em um ( ) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a>Arquivos de site de origem  
 Os arquivos de recursos têm uma relação explícita com as assembléias que são distribuídas ao lado, conforme definido pelo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Mas, às vezes você deseja estabelecer um relacionamento implícito ou inexistente entre um assembly e um arquivo de dados do aplicativo, como quando:  
  
- Um arquivo não existe no momento da compilação.  
  
- Você não sabe quais arquivos seu assembly vai requerer até o tempo de execução.  
  
- Você deseja ser capaz de atualizar os arquivos sem recompilar o assembly ao qual eles estão associados.  
  
- O aplicativo usa arquivos de dados grandes, como áudio e vídeo, e você só deseja que os usuários os baixem caso desejem.  
  
 É possível carregar esses tipos de arquivos usando esquemas URI tradicionais, como os esquemas de file:/// e http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 No entanto, os esquemas file:/// e http:// requerem que seu aplicativo tenha confiança total. Se o seu aplicativo é um aplicativo de navegador XAML (XBAP) que foi lançado a partir da Internet ou intranet, e solicita apenas o conjunto de permissões que são permitidas para aplicativos lançados a partir desses locais, arquivos soltos só podem ser carregados a partir do site de origem do aplicativo (local de lançamento). Esses arquivos são conhecidos como *arquivos de origem.*  
  
 Os arquivos de site de origem são a única opção para aplicativos parcialmente confiáveis, apesar de não serem limitados a aplicativos parcialmente confiáveis. Os aplicativos de confiança total ainda podem precisar carregar arquivos de dados do aplicativo que eles não conhecem em tempo de build. Embora os aplicativos de confiança total possam utilizar file:///, é provável que os arquivos de dados do aplicativo sejam instalados na mesma pasta ou em uma subpasta do assembly do aplicativo. Nesse caso, usar a referência do site de origem é mais fácil do que usar file:///, porque o uso de file:/// requer que você descubra o caminho completo do arquivo.  
  
> [!NOTE]
> Os arquivos de origem do site não são armazenados em cache com um aplicativo de navegador XAML (XBAP) em uma máquina cliente, enquanto os arquivos de conteúdo são. Consequentemente, eles são baixados somente quando solicitado especificamente. Se um aplicativo xaml de navegador (XBAP) tiver arquivos de mídia grandes, configurá-los como arquivos de origem significa que o lançamento inicial do aplicativo é muito mais rápido, e os arquivos só são baixados demanda.  
  
### <a name="configuring-site-of-origin-files"></a>Configurando arquivos de site de origem  
 Se os arquivos de origem do seu site não existirem ou forem desconhecidos no momento da compilação, você `XCopy` precisará usar mecanismos tradicionais de implantação para garantir que os arquivos necessários estejam disponíveis em tempo de execução, incluindo o uso do programa de linha de comando ou do Microsoft Windows Installer.  
  
 Se você souber na hora da compilação os arquivos que você gostaria de estar localizado no local de origem, mas ainda quiser `None` evitar uma dependência explícita, você pode adicionar esses arquivos a um projeto MSBuild como item. Como acontece com os arquivos de conteúdo, você precisa definir o atributo MSBuild `CopyToOutputDirectory` para especificar que o arquivo `Always` de origem `PreserveNewest` do site é copiado para um local que é relativo ao conjunto construído, especificando o valor ou o valor.  
  
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
> No Visual Studio, você cria um arquivo de origem adicionando `Build Action` `None`um arquivo a um projeto e definindo-o para .  
  
 Quando o projeto é construído, o MSBuild copia os arquivos especificados para a pasta de saída de compilação.  
  
### <a name="using-site-of-origin-files"></a>Usando arquivos de site de origem  
 Para carregar um arquivo de origem, <xref:System.Windows.Application.GetRemoteStream%2A> você <xref:System.Windows.Application> pode chamar o método da classe, passando um URI de pacote que identifica o arquivo de origem desejado. <xref:System.Windows.Application.GetRemoteStream%2A>retorna <xref:System.Windows.Resources.StreamResourceInfo> um objeto, que expõe o arquivo <xref:System.IO.Stream> do site de origem como um e descreve seu tipo de conteúdo.  
  
 Como exemplo, o código a <xref:System.Windows.Application.GetRemoteStream%2A> seguir mostra <xref:System.Windows.Controls.Page> como usar para carregar um arquivo <xref:System.Windows.Controls.Frame> `pageFrame`de origem do site e defini-lo como o conteúdo de a ( ).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Ao <xref:System.Windows.Application.GetRemoteStream%2A> ligar, você <xref:System.IO.Stream>precisa realizar o trabalho adicional de convertê-lo para o tipo de propriedade com a que você estará definindo-o. Em vez disso, você pode deixar o <xref:System.IO.Stream> WPF cuidar da abertura e conversão do carregamento de um arquivo de recursos diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir <xref:System.Windows.Controls.Page> mostra como <xref:System.Windows.Controls.Frame> `pageFrame`carregar um diretamente em um ( ) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a>Recompilando após modificar o tipo de build  
 Depois de alterar o tipo de build de um arquivo de dados do aplicativo, você precisa recompilar o aplicativo inteiro para garantir que essas alterações sejam aplicadas. Se você apenas compilar o aplicativo, as alterações não serão aplicadas.  
  
## <a name="see-also"></a>Confira também

- [URIs "pack://" no WPF](pack-uris-in-wpf.md)
