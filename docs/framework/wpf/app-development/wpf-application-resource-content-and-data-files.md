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
ms.openlocfilehash: 5bf1a0e1d4d8f620f83aab50aa50009a0f6a6cf4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43561438"
---
# <a name="wpf-application-resource-content-and-data-files"></a>Arquivos de recurso, conteúdo e dados do aplicativo WPF
[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)] aplicativos geralmente dependem de arquivos que contêm dados não executáveis, tais como [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], imagens, vídeo e áudio. Windows Presentation Foundation (WPF) oferece suporte especial para configurar, identificar e usar esses tipos de arquivos de dados, que são chamados de arquivos de dados do aplicativo. Esse suporte gira em torno de um conjunto específico de tipos de arquivo de dados do aplicativo, incluindo:  
  
-   **Arquivos de recurso**: os arquivos de dados que são compilados em um executável ou biblioteca [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
-   **Arquivos de conteúdo**: os arquivos de dados independentes que têm uma associação explícita com um executável [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
-   **Site de arquivos de origem**: os arquivos de dados independentes que não têm uma associação com um executável [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] assembly.  
  
 Uma distinção importante a se fazer entre esses três tipos de arquivos é que os arquivos de recurso e os arquivos de conteúdo são conhecidos em tempo de build; um assembly tem o conhecimento explícito sobre eles. Para arquivos de site de origem, no entanto, um assembly não pode ter nenhum conhecimento sobre eles, ou conhecimento implícito por meio de um pacote [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] referência; no caso do último, não há nenhuma garantia de que o local referenciado do arquivo de origem realmente existe.  
  
 Para fazer referência a arquivos de dados do aplicativo, o Windows Presentation Foundation (WPF) usa o pacote [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] esquema, que é descrito detalhadamente nas [URIs de pacote no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)).  
  
 Este tópico descreve como configurar e usar arquivos de dados do aplicativo.  
  
  
<a name="Resource_Files"></a>   
## <a name="resource-files"></a>Arquivos de recursos  
 Se um arquivo de dados do aplicativo precisar estar sempre disponível para um aplicativo, a única maneira de garantir essa disponibilidade será compilá-lo em um assembly executável principal do aplicativo ou em um de seus assemblies referenciados. Esse tipo de arquivo de dados do aplicativo é conhecido como um *arquivo de recurso*.  
  
 Você deve usar arquivos de recurso quando:  
  
-   Você não precisa atualizar o conteúdo do arquivo de recurso depois que ele é compilado em um assembly.  
  
-   Você deseja simplificar a complexidade da distribuição de aplicativos, reduzindo o número de dependências de arquivo.  
  
-   O arquivo de dados do aplicativo precisa ser localizável (consulte [visão geral de localização e globalização do WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md)).  
  
> [!NOTE]
>  Os arquivos de recurso descritos nesta seção são diferentes do que os arquivos de recurso descrito em [recursos XAML](../../../../docs/framework/wpf/advanced/xaml-resources.md) e diferentes dos recursos inseridos ou vinculados descritos [Gerenciando recursos de aplicativo (.NET) ](https://msdn.microsoft.com/library/f2582734-8ada-4baa-8a7c-e2ef943ddf7e).  
  
### <a name="configuring-resource-files"></a>Configurando arquivos de recurso  
 Na [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], um arquivo de recurso é um arquivo que está incluído em um [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] do projeto como um `Resource` item.  
  
```xml  
<Project "xmlns=http://schemas.microsoft.com/developer/msbuild/2003" ... >  
  ...  
  <ItemGroup>  
    <Resource Include="ResourceFile.xaml" />  
  </ItemGroup>  
  ...  
</Project>  
```  
  
> [!NOTE]
>  Na [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)], crie um arquivo de recurso, adicionando um arquivo a um projeto e definindo seu `Build Action` para `Resource`.  
  
 Quando o projeto é compilado, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] compila o recurso no assembly.  
  
### <a name="using-resource-files"></a>Usando arquivos de recurso  
 Para carregar um arquivo de recurso, você pode chamar o <xref:System.Windows.Application.GetResourceStream%2A> método da <xref:System.Windows.Application> classe, passando um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica o arquivo de recurso desejado. <xref:System.Windows.Application.GetResourceStream%2A> Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o arquivo de recurso como um <xref:System.IO.Stream> e descreve seu tipo de conteúdo.  
  
 Por exemplo, o código a seguir mostra como usar <xref:System.Windows.Application.GetResourceStream%2A> para carregar uma <xref:System.Windows.Controls.Page> recurso de arquivo e defina-o como o conteúdo de um <xref:System.Windows.Controls.Frame> (`pageFrame`):  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 Ao chamar <xref:System.Windows.Application.GetResourceStream%2A> fornece acesso ao <xref:System.IO.Stream>, você precisa realizar o trabalho adicional de convertê-lo para o tipo da propriedade que você usará para defini-lo com. Em vez disso, você pode deixar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] cuide da abertura e convertendo o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> (`pageFrame`) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a>Arquivos de código de aplicativo como arquivos de recurso  
 Um conjunto especial de [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] arquivos de código do aplicativo podem ser referenciados usando o pacote [!INCLUDE[TLA2#tla_uri#plural](../../../../includes/tla2sharptla-urisharpplural-md.md)], incluindo windows, páginas, documentos de fluxo e dicionários de recursos. Por exemplo, você pode definir as <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> propriedade com um pacote de [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que faz referência a janela ou página que você gostaria de carregar quando um aplicativo é iniciado.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 Você pode fazer isso quando um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo é incluído em um [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] do projeto como um `Page` item.  
  
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
>  Na [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], você adiciona um novo <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, ou <xref:System.Windows.ResourceDictionary> a um projeto, o `Build Action` para a marcação de arquivo padrão será `Page`.  
  
 Quando um projeto com `Page` itens é compilado, o [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] itens são convertidos em formato binário e compilados no assembly associado. Consequentemente, esses arquivos podem ser usados da mesma maneira que arquivos de recurso típicos.  
  
> [!NOTE]
>  Se um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo é configurado como um `Resource` item e não tem um arquivo code-behind, o raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] é compilado em um assembly em vez de uma versão binária do bruto [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
<a name="Content_Files"></a>   
## <a name="content-files"></a>Arquivos de Conteúdo  
 Um *arquivo de conteúdo* é distribuído como arquivo flexível juntamente com um assembly executável. Embora eles não sejam compilados em um assembly, os assemblies são compilados com metadados que estabelecem uma associação com cada arquivo de conteúdo.  
  
 Você deve usar arquivos de conteúdo quando o aplicativo requer um conjunto específico de arquivos de dados do aplicativo que você deseja ser capaz de atualizar sem recompilar o assembly que os consome.  
  
### <a name="configuring-content-files"></a>Configurando arquivos de conteúdo  
 Para adicionar um arquivo de conteúdo a um projeto, um arquivo de dados do aplicativo deve ser incluído como um `Content` item. Além disso, como um arquivo de conteúdo não é compilado diretamente no assembly, você precisa definir a [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` elemento de metadados para especificar que o arquivo de conteúdo é copiado para um local que é relativo ao assembly compilado. Se você deseja que o recurso a ser copiado para a pasta de saída de compilação sempre que um projeto é compilado, defina as `CopyToOutputDirectory` o elemento de metadados com o `Always` valor. Caso contrário, você pode garantir que apenas a versão mais recente do recurso é copiada para a pasta de saída de build usando o `PreserveNewest` valor.  
  
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
>  Na [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], crie um arquivo de conteúdo, adicionando um arquivo a um projeto e definindo seu `Build Action` para `Content`e defina seu `Copy to Output Directory` para `Copy always` (mesmo que `Always`) e `Copy if newer` (mesmo que `PreserveNewest`).  
  
 Quando o projeto é compilado, um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo é compilado nos metadados do assembly para cada arquivo de conteúdo.  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 O valor da <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implica o caminho para o arquivo de conteúdo relativo à sua posição no projeto. Por exemplo, se um arquivo de conteúdo foi localizado em uma subpasta do projeto, as informações de caminho adicionais seriam incorporadas ao <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor.  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 O <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor também é o valor do caminho para o arquivo de conteúdo na pasta de saída de compilação.  
  
### <a name="using-content-files"></a>Usando arquivos de conteúdo  
 Para carregar um arquivo de conteúdo, você pode chamar o <xref:System.Windows.Application.GetContentStream%2A> método da <xref:System.Windows.Application> classe, passando um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica o arquivo de conteúdo desejado. <xref:System.Windows.Application.GetContentStream%2A> Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o arquivo de conteúdo como um <xref:System.IO.Stream> e descreve seu tipo de conteúdo.  
  
 Por exemplo, o código a seguir mostra como usar <xref:System.Windows.Application.GetContentStream%2A> para carregar uma <xref:System.Windows.Controls.Page> arquivo de conteúdo e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 Ao chamar <xref:System.Windows.Application.GetContentStream%2A> fornece acesso ao <xref:System.IO.Stream>, você precisa realizar o trabalho adicional de convertê-lo para o tipo da propriedade que você usará para defini-lo com. Em vez disso, você pode deixar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] cuide da abertura e convertendo o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> (`pageFrame`) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>   
## <a name="site-of-origin-files"></a>Arquivos de site de origem  
 Arquivos de recurso têm um relacionamento explícito com os assemblies que eles são distribuídos junto com, conforme definido pelo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>. Mas, às vezes você deseja estabelecer um relacionamento implícito ou inexistente entre um assembly e um arquivo de dados do aplicativo, como quando:  
  
-   Não existe um arquivo em tempo de compilação.  
  
-   Você não sabe quais arquivos seu assembly vai requerer até o tempo de execução.  
  
-   Você deseja ser capaz de atualizar os arquivos sem recompilar o assembly ao qual eles estão associados.  
  
-   O aplicativo usa arquivos de dados grandes, como áudio e vídeo, e você só deseja que os usuários os baixem caso desejem.  
  
 É possível carregar esses tipos de arquivos usando tradicionais [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] esquemas, tais como esquemas file:/// e http://.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 No entanto, os esquemas file:/// e http:// requerem que seu aplicativo tenha confiança total. Se seu aplicativo for um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] que foi iniciado pela Internet ou intranet e solicita apenas o conjunto de permissões que são permitidas para aplicativos iniciados desses locais, arquivos flexíveis só poderão ser carregados do site de origem (do aplicativo Inicie o local). Esses arquivos são conhecidos como *site de origem* arquivos.  
  
 Os arquivos de site de origem são a única opção para aplicativos parcialmente confiáveis, apesar de não serem limitados a aplicativos parcialmente confiáveis. Os aplicativos de confiança total ainda podem precisar carregar arquivos de dados do aplicativo que eles não conhecem em tempo de build. Embora os aplicativos de confiança total possam utilizar file:///, é provável que os arquivos de dados do aplicativo sejam instalados na mesma pasta ou em uma subpasta do assembly do aplicativo. Nesse caso, usar a referência do site de origem é mais fácil do que usar file:///, porque o uso de file:/// requer que você descubra o caminho completo do arquivo.  
  
> [!NOTE]
>  Site de origem não estão em cache os arquivos com um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] em um computador cliente, enquanto são arquivos de conteúdo. Consequentemente, eles são baixados somente quando solicitado especificamente. Se um [!INCLUDE[TLA#tla_xbap](../../../../includes/tlasharptla-xbap-md.md)] aplicativo tiver arquivos de mídia grandes, configurá-los como site de arquivos de origem significa que a primeira inicialização do aplicativo é muito mais rápida e os arquivos são baixados somente sob demanda.  
  
### <a name="configuring-site-of-origin-files"></a>Configurando arquivos de site de origem  
 Se seu site de arquivos de origem é inexistentes ou desconhecidos em tempo de compilação, você precisará usar tradicionais de implantação de mecanismos para garantir que os arquivos necessários estão disponíveis em tempo de execução, incluindo o uso de qualquer um de `XCopy` programa de linha de comando ou o [!INCLUDE[TLA#tla_wininstall](../../../../includes/tlasharptla-wininstall-md.md)].  
  
 Se você souber em tempo de compilação os arquivos você que gostaria que estivessem localizados no site de origem, mas ainda desejar evitar uma dependência explícita, você pode adicionar esses arquivos em um [!INCLUDE[TLA#tla_msbuild](../../../../includes/tlasharptla-msbuild-md.md)] do projeto como `None` item. Assim como arquivos de conteúdo, você precisa definir a [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] `CopyToOutputDirectory` atributo para especificar que o local do arquivo de origem é copiado para um local que é relativo ao assembly compilado, especificando as `Always` valor ou o `PreserveNewest` valor.  
  
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
>  Na [!INCLUDE[TLA2#tla_visualstu](../../../../includes/tla2sharptla-visualstu-md.md)], crie um arquivo de site de origem, adicionando um arquivo a um projeto e definindo seu `Build Action` para `None`.  
  
 Quando o projeto é compilado, [!INCLUDE[TLA2#tla_msbuild](../../../../includes/tla2sharptla-msbuild-md.md)] copia os arquivos especificados para a pasta de saída de compilação.  
  
### <a name="using-site-of-origin-files"></a>Usando arquivos de site de origem  
 Para carregar um arquivo de site de origem, você pode chamar o <xref:System.Windows.Application.GetRemoteStream%2A> método da <xref:System.Windows.Application> classe, passando um pacote [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] que identifica o local de arquivo de origem desejado. <xref:System.Windows.Application.GetRemoteStream%2A> Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o local do arquivo de origem como um <xref:System.IO.Stream> e descreve seu tipo de conteúdo.  
  
 Por exemplo, o código a seguir mostra como usar <xref:System.Windows.Application.GetRemoteStream%2A> para carregar uma <xref:System.Windows.Controls.Page> local de origem de arquivo e defina-o como o conteúdo de um <xref:System.Windows.Controls.Frame> (`pageFrame`).  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 Ao chamar <xref:System.Windows.Application.GetRemoteStream%2A> fornece acesso ao <xref:System.IO.Stream>, você precisa realizar o trabalho adicional de convertê-lo para o tipo da propriedade que você usará para defini-lo com. Em vez disso, você pode deixar [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] cuide da abertura e convertendo o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.  
  
 O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> (`pageFrame`) usando código.  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 O exemplo a seguir é um exemplo de marcação equivalente ao anterior.  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>   
## <a name="rebuilding-after-changing-build-type"></a>Recompilando após modificar o tipo de build  
 Depois de alterar o tipo de build de um arquivo de dados do aplicativo, você precisa recompilar o aplicativo inteiro para garantir que essas alterações sejam aplicadas. Se você apenas compilar o aplicativo, as alterações não serão aplicadas.  
  
## <a name="see-also"></a>Consulte também  
 [URIs "pack://" no WPF](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)
