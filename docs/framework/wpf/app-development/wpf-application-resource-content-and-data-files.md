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
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="213da-102">Arquivos de recurso, conteúdo e dados do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="213da-102">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="213da-103">Os aplicativos microsoft windows geralmente dependem de arquivos que [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]contêm dados não executáveis, como, imagens, vídeo e áudio.</span><span class="sxs-lookup"><span data-stu-id="213da-103">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="213da-104">O Windows Presentation Foundation (WPF) oferece suporte especial para configurar, identificar e usar esses tipos de arquivos de dados, que são chamados de arquivos de dados de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="213da-104">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="213da-105">Esse suporte gira em torno de um conjunto específico de tipos de arquivo de dados do aplicativo, incluindo:</span><span class="sxs-lookup"><span data-stu-id="213da-105">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="213da-106">**Arquivos de recursos**: Arquivos de dados que são compilados em um conjunto WPF executável ou de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="213da-106">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="213da-107">**Arquivos de conteúdo**: Arquivos de dados autônomos que têm uma associação explícita com um conjunto WPF executável.</span><span class="sxs-lookup"><span data-stu-id="213da-107">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="213da-108">**Site of Origin Files**: Arquivos de dados autônomos que não têm associação com um conjunto WPF executável.</span><span class="sxs-lookup"><span data-stu-id="213da-108">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="213da-109">Uma distinção importante a se fazer entre esses três tipos de arquivos é que os arquivos de recurso e os arquivos de conteúdo são conhecidos em tempo de build; um assembly tem o conhecimento explícito sobre eles.</span><span class="sxs-lookup"><span data-stu-id="213da-109">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="213da-110">Para arquivos de site de origem, no entanto, uma assembléia pode não ter conhecimento algum deles, ou conhecimento implícito através de uma referência uri (identificador de recursos uniforme de pacote); no caso deste último, não há garantia de que o arquivo de origem do site referenciado realmente exista.</span><span class="sxs-lookup"><span data-stu-id="213da-110">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="213da-111">Para referenciar arquivos de dados de aplicativos, o Windows Presentation Foundation (WPF) usa o Esquema uri (Uniform Resource Identifier) do Pack, que é descrito em detalhes em [URIs do Pack no WPF](pack-uris-in-wpf.md)).</span><span class="sxs-lookup"><span data-stu-id="213da-111">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="213da-112">Este tópico descreve como configurar e usar arquivos de dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="213da-112">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="213da-113">Arquivos de recursos</span><span class="sxs-lookup"><span data-stu-id="213da-113">Resource Files</span></span>  
 <span data-ttu-id="213da-114">Se um arquivo de dados do aplicativo precisar estar sempre disponível para um aplicativo, a única maneira de garantir essa disponibilidade será compilá-lo em um assembly executável principal do aplicativo ou em um de seus assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="213da-114">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="213da-115">Esse tipo de arquivo de dados de aplicativo é conhecido como um *arquivo de recursos*.</span><span class="sxs-lookup"><span data-stu-id="213da-115">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="213da-116">Você deve usar arquivos de recurso quando:</span><span class="sxs-lookup"><span data-stu-id="213da-116">You should use resource files when:</span></span>  
  
- <span data-ttu-id="213da-117">Você não precisa atualizar o conteúdo do arquivo de recurso depois que ele é compilado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="213da-117">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="213da-118">Você deseja simplificar a complexidade da distribuição de aplicativos, reduzindo o número de dependências de arquivo.</span><span class="sxs-lookup"><span data-stu-id="213da-118">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="213da-119">O arquivo de dados do aplicativo precisa ser localizado (consulte [Visão Geral de Globalização e Localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="213da-119">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213da-120">Os arquivos de recursos descritos nesta seção são diferentes dos arquivos de recursos descritos no [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) e diferentes dos recursos incorporados ou vinculados descritos no [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="213da-120">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="213da-121">Configurando arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="213da-121">Configuring Resource Files</span></span>  
 <span data-ttu-id="213da-122">No WPF, um arquivo de recursos é um arquivo incluído em um `Resource` projeto de mecanismo de compilação microsoft (MSBuild) como um item.</span><span class="sxs-lookup"><span data-stu-id="213da-122">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="213da-123">No Visual Studio, você cria um arquivo de recursos `Build Action` adicionando um arquivo a um projeto e definindo-o para `Resource`.</span><span class="sxs-lookup"><span data-stu-id="213da-123">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="213da-124">Quando o projeto é construído, o MSBuild compila o recurso na montagem.</span><span class="sxs-lookup"><span data-stu-id="213da-124">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="213da-125">Usando arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="213da-125">Using Resource Files</span></span>  
 <span data-ttu-id="213da-126">Para carregar um arquivo de <xref:System.Windows.Application.GetResourceStream%2A> recursos, <xref:System.Windows.Application> você pode chamar o método da classe, passando um URI de pacote que identifica o arquivo de recurso desejado.</span><span class="sxs-lookup"><span data-stu-id="213da-126">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="213da-127"><xref:System.Windows.Application.GetResourceStream%2A>retorna <xref:System.Windows.Resources.StreamResourceInfo> um objeto, que expõe o <xref:System.IO.Stream> arquivo de recursos como um e descreve seu tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="213da-127"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="213da-128">Como exemplo, o código a <xref:System.Windows.Application.GetResourceStream%2A> seguir mostra <xref:System.Windows.Controls.Page> como usar para carregar um <xref:System.Windows.Controls.Frame> `pageFrame`arquivo de recurso e defini-lo como o conteúdo de a ( ):</span><span class="sxs-lookup"><span data-stu-id="213da-128">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="213da-129">Ao <xref:System.Windows.Application.GetResourceStream%2A> ligar, você <xref:System.IO.Stream>precisa realizar o trabalho adicional de convertê-lo para o tipo de propriedade com a que você estará definindo-o.</span><span class="sxs-lookup"><span data-stu-id="213da-129">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="213da-130">Em vez disso, você pode deixar o <xref:System.IO.Stream> WPF cuidar da abertura e conversão do carregamento de um arquivo de recursos diretamente na propriedade de um tipo usando código.</span><span class="sxs-lookup"><span data-stu-id="213da-130">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="213da-131">O exemplo a seguir <xref:System.Windows.Controls.Page> mostra como <xref:System.Windows.Controls.Frame> `pageFrame`carregar um diretamente em um ( ) usando código.</span><span class="sxs-lookup"><span data-stu-id="213da-131">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="213da-132">O exemplo a seguir é um exemplo de marcação equivalente ao anterior.</span><span class="sxs-lookup"><span data-stu-id="213da-132">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="213da-133">Arquivos de código de aplicativo como arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="213da-133">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="213da-134">Um conjunto especial de arquivos de código de aplicativo WPF pode ser referenciado usando URIs de pacote, incluindo janelas, páginas, documentos de fluxo e dicionários de recursos.</span><span class="sxs-lookup"><span data-stu-id="213da-134">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="213da-135">Por exemplo, você <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> pode definir a propriedade com um URI de pacote que faz referência à janela ou página que você gostaria de carregar quando um aplicativo for iniciado.</span><span class="sxs-lookup"><span data-stu-id="213da-135">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="213da-136">Você pode fazer isso quando um arquivo XAML é `Page` incluído em um projeto MSBuild como item.</span><span class="sxs-lookup"><span data-stu-id="213da-136">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="213da-137">No Visual Studio, você <xref:System.Windows.Window> <xref:System.Windows.Navigation.NavigationWindow>adiciona <xref:System.Windows.Controls.Page> <xref:System.Windows.Documents.FlowDocument>um <xref:System.Windows.ResourceDictionary> novo , , `Build Action` , ou a um `Page`projeto, o arquivo de marcação será padrão para .</span><span class="sxs-lookup"><span data-stu-id="213da-137">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="213da-138">Quando um `Page` projeto com itens é [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] compilado, os itens são convertidos em formato binário e compilados no conjunto associado.</span><span class="sxs-lookup"><span data-stu-id="213da-138">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="213da-139">Consequentemente, esses arquivos podem ser usados da mesma maneira que arquivos de recurso típicos.</span><span class="sxs-lookup"><span data-stu-id="213da-139">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213da-140">Se [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo for `Resource` configurado como um item e não tiver [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] um arquivo de código atrás, o raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]será compilado em um conjunto em vez de uma versão binária do raw .</span><span class="sxs-lookup"><span data-stu-id="213da-140">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="213da-141">Arquivos de Conteúdo</span><span class="sxs-lookup"><span data-stu-id="213da-141">Content Files</span></span>  
 <span data-ttu-id="213da-142">Um *arquivo de conteúdo* é distribuído como um arquivo solto ao lado de um conjunto executável.</span><span class="sxs-lookup"><span data-stu-id="213da-142">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="213da-143">Embora eles não sejam compilados em um assembly, os assemblies são compilados com metadados que estabelecem uma associação com cada arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="213da-143">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="213da-144">Você deve usar arquivos de conteúdo quando o aplicativo requer um conjunto específico de arquivos de dados do aplicativo que você deseja ser capaz de atualizar sem recompilar o assembly que os consome.</span><span class="sxs-lookup"><span data-stu-id="213da-144">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="213da-145">Configurando arquivos de conteúdo</span><span class="sxs-lookup"><span data-stu-id="213da-145">Configuring Content Files</span></span>  
 <span data-ttu-id="213da-146">Para adicionar um arquivo de conteúdo a um projeto, `Content` um arquivo de dados de aplicativo deve ser incluído como um item.</span><span class="sxs-lookup"><span data-stu-id="213da-146">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="213da-147">Além disso, como um arquivo de conteúdo não é compilado diretamente no `CopyToOutputDirectory` conjunto, você precisa definir o elemento metadados do MSBuild para especificar que o arquivo de conteúdo é copiado para um local que é relativo ao conjunto construído.</span><span class="sxs-lookup"><span data-stu-id="213da-147">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="213da-148">Se você quiser que o recurso seja copiado para a pasta de `CopyToOutputDirectory` saída de `Always` compilação toda vez que um projeto for construído, você definirá o elemento metadados com o valor.</span><span class="sxs-lookup"><span data-stu-id="213da-148">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="213da-149">Caso contrário, você pode garantir que apenas a versão mais recente do recurso `PreserveNewest` seja copiada para a pasta de saída de compilação usando o valor.</span><span class="sxs-lookup"><span data-stu-id="213da-149">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="213da-150">A seguir é mostrado um arquivo que está configurado como um arquivo de conteúdo que é copiado para a pasta de saída de build somente quando uma nova versão do recurso é adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="213da-150">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="213da-151">No Visual Studio, você cria um arquivo de conteúdo `Build Action` adicionando um arquivo a um projeto e definindo-o `Content`para , e definir -lo `Copy to Output Directory` `Copy always` (mesmo que `Always`) e `Copy if newer` (mesmo que `PreserveNewest`).</span><span class="sxs-lookup"><span data-stu-id="213da-151">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="213da-152">Quando o projeto é <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> construído, um atributo é compilado nos metadados do conjunto para cada arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="213da-152">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="213da-153">O valor <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> do implica o caminho para o arquivo de conteúdo em relação à sua posição no projeto.</span><span class="sxs-lookup"><span data-stu-id="213da-153">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="213da-154">Por exemplo, se um arquivo de conteúdo estivesse localizado em uma subpasta <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> de projeto, as informações adicionais de caminho seriam incorporadas ao valor.</span><span class="sxs-lookup"><span data-stu-id="213da-154">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="213da-155">O <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor também é o valor do caminho para o arquivo de conteúdo na pasta de saída de compilação.</span><span class="sxs-lookup"><span data-stu-id="213da-155">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="213da-156">Usando arquivos de conteúdo</span><span class="sxs-lookup"><span data-stu-id="213da-156">Using Content Files</span></span>  
 <span data-ttu-id="213da-157">Para carregar um arquivo de <xref:System.Windows.Application.GetContentStream%2A> conteúdo, <xref:System.Windows.Application> você pode chamar o método da classe, passando um URI de pacote que identifica o arquivo de conteúdo desejado.</span><span class="sxs-lookup"><span data-stu-id="213da-157">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="213da-158"><xref:System.Windows.Application.GetContentStream%2A>retorna <xref:System.Windows.Resources.StreamResourceInfo> um objeto, que expõe o <xref:System.IO.Stream> arquivo de conteúdo como um e descreve seu tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="213da-158"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="213da-159">Como exemplo, o código a <xref:System.Windows.Application.GetContentStream%2A> seguir mostra <xref:System.Windows.Controls.Page> como usar para carregar um <xref:System.Windows.Controls.Frame> `pageFrame`arquivo de conteúdo e defini-lo como o conteúdo de a ( ).</span><span class="sxs-lookup"><span data-stu-id="213da-159">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="213da-160">Ao <xref:System.Windows.Application.GetContentStream%2A> ligar, você <xref:System.IO.Stream>precisa realizar o trabalho adicional de convertê-lo para o tipo de propriedade com a que você estará definindo-o.</span><span class="sxs-lookup"><span data-stu-id="213da-160">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="213da-161">Em vez disso, você pode deixar o <xref:System.IO.Stream> WPF cuidar da abertura e conversão do carregamento de um arquivo de recursos diretamente na propriedade de um tipo usando código.</span><span class="sxs-lookup"><span data-stu-id="213da-161">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="213da-162">O exemplo a seguir <xref:System.Windows.Controls.Page> mostra como <xref:System.Windows.Controls.Frame> `pageFrame`carregar um diretamente em um ( ) usando código.</span><span class="sxs-lookup"><span data-stu-id="213da-162">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="213da-163">O exemplo a seguir é um exemplo de marcação equivalente ao anterior.</span><span class="sxs-lookup"><span data-stu-id="213da-163">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="213da-164">Arquivos de site de origem</span><span class="sxs-lookup"><span data-stu-id="213da-164">Site of Origin Files</span></span>  
 <span data-ttu-id="213da-165">Os arquivos de recursos têm uma relação explícita com as assembléias que são distribuídas ao lado, conforme definido pelo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span><span class="sxs-lookup"><span data-stu-id="213da-165">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="213da-166">Mas, às vezes você deseja estabelecer um relacionamento implícito ou inexistente entre um assembly e um arquivo de dados do aplicativo, como quando:</span><span class="sxs-lookup"><span data-stu-id="213da-166">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="213da-167">Um arquivo não existe no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="213da-167">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="213da-168">Você não sabe quais arquivos seu assembly vai requerer até o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="213da-168">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="213da-169">Você deseja ser capaz de atualizar os arquivos sem recompilar o assembly ao qual eles estão associados.</span><span class="sxs-lookup"><span data-stu-id="213da-169">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="213da-170">O aplicativo usa arquivos de dados grandes, como áudio e vídeo, e você só deseja que os usuários os baixem caso desejem.</span><span class="sxs-lookup"><span data-stu-id="213da-170">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="213da-171">É possível carregar esses tipos de arquivos usando esquemas URI tradicionais, como os esquemas de file:/// e http://.</span><span class="sxs-lookup"><span data-stu-id="213da-171">It is possible to load these types of files by using traditional URI schemes, such as the file:/// and http:// schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="213da-172">No entanto, os esquemas file:/// e http:// requerem que seu aplicativo tenha confiança total.</span><span class="sxs-lookup"><span data-stu-id="213da-172">However, the file:/// and http:// schemes require your application to have full trust.</span></span> <span data-ttu-id="213da-173">Se o seu aplicativo é um aplicativo de navegador XAML (XBAP) que foi lançado a partir da Internet ou intranet, e solicita apenas o conjunto de permissões que são permitidas para aplicativos lançados a partir desses locais, arquivos soltos só podem ser carregados a partir do site de origem do aplicativo (local de lançamento).</span><span class="sxs-lookup"><span data-stu-id="213da-173">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="213da-174">Esses arquivos são conhecidos como *arquivos de origem.*</span><span class="sxs-lookup"><span data-stu-id="213da-174">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="213da-175">Os arquivos de site de origem são a única opção para aplicativos parcialmente confiáveis, apesar de não serem limitados a aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="213da-175">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="213da-176">Os aplicativos de confiança total ainda podem precisar carregar arquivos de dados do aplicativo que eles não conhecem em tempo de build. Embora os aplicativos de confiança total possam utilizar file:///, é provável que os arquivos de dados do aplicativo sejam instalados na mesma pasta ou em uma subpasta do assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="213da-176">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="213da-177">Nesse caso, usar a referência do site de origem é mais fácil do que usar file:///, porque o uso de file:/// requer que você descubra o caminho completo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="213da-177">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="213da-178">Os arquivos de origem do site não são armazenados em cache com um aplicativo de navegador XAML (XBAP) em uma máquina cliente, enquanto os arquivos de conteúdo são.</span><span class="sxs-lookup"><span data-stu-id="213da-178">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="213da-179">Consequentemente, eles são baixados somente quando solicitado especificamente.</span><span class="sxs-lookup"><span data-stu-id="213da-179">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="213da-180">Se um aplicativo xaml de navegador (XBAP) tiver arquivos de mídia grandes, configurá-los como arquivos de origem significa que o lançamento inicial do aplicativo é muito mais rápido, e os arquivos só são baixados demanda.</span><span class="sxs-lookup"><span data-stu-id="213da-180">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="213da-181">Configurando arquivos de site de origem</span><span class="sxs-lookup"><span data-stu-id="213da-181">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="213da-182">Se os arquivos de origem do seu site não existirem ou forem desconhecidos no momento da compilação, você `XCopy` precisará usar mecanismos tradicionais de implantação para garantir que os arquivos necessários estejam disponíveis em tempo de execução, incluindo o uso do programa de linha de comando ou do Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="213da-182">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="213da-183">Se você souber na hora da compilação os arquivos que você gostaria de estar localizado no local de origem, mas ainda quiser `None` evitar uma dependência explícita, você pode adicionar esses arquivos a um projeto MSBuild como item.</span><span class="sxs-lookup"><span data-stu-id="213da-183">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="213da-184">Como acontece com os arquivos de conteúdo, você precisa definir o atributo MSBuild `CopyToOutputDirectory` para especificar que o arquivo `Always` de origem `PreserveNewest` do site é copiado para um local que é relativo ao conjunto construído, especificando o valor ou o valor.</span><span class="sxs-lookup"><span data-stu-id="213da-184">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="213da-185">No Visual Studio, você cria um arquivo de origem adicionando `Build Action` `None`um arquivo a um projeto e definindo-o para .</span><span class="sxs-lookup"><span data-stu-id="213da-185">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="213da-186">Quando o projeto é construído, o MSBuild copia os arquivos especificados para a pasta de saída de compilação.</span><span class="sxs-lookup"><span data-stu-id="213da-186">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="213da-187">Usando arquivos de site de origem</span><span class="sxs-lookup"><span data-stu-id="213da-187">Using Site of Origin Files</span></span>  
 <span data-ttu-id="213da-188">Para carregar um arquivo de origem, <xref:System.Windows.Application.GetRemoteStream%2A> você <xref:System.Windows.Application> pode chamar o método da classe, passando um URI de pacote que identifica o arquivo de origem desejado.</span><span class="sxs-lookup"><span data-stu-id="213da-188">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="213da-189"><xref:System.Windows.Application.GetRemoteStream%2A>retorna <xref:System.Windows.Resources.StreamResourceInfo> um objeto, que expõe o arquivo <xref:System.IO.Stream> do site de origem como um e descreve seu tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="213da-189"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="213da-190">Como exemplo, o código a <xref:System.Windows.Application.GetRemoteStream%2A> seguir mostra <xref:System.Windows.Controls.Page> como usar para carregar um arquivo <xref:System.Windows.Controls.Frame> `pageFrame`de origem do site e defini-lo como o conteúdo de a ( ).</span><span class="sxs-lookup"><span data-stu-id="213da-190">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="213da-191">Ao <xref:System.Windows.Application.GetRemoteStream%2A> ligar, você <xref:System.IO.Stream>precisa realizar o trabalho adicional de convertê-lo para o tipo de propriedade com a que você estará definindo-o.</span><span class="sxs-lookup"><span data-stu-id="213da-191">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="213da-192">Em vez disso, você pode deixar o <xref:System.IO.Stream> WPF cuidar da abertura e conversão do carregamento de um arquivo de recursos diretamente na propriedade de um tipo usando código.</span><span class="sxs-lookup"><span data-stu-id="213da-192">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="213da-193">O exemplo a seguir <xref:System.Windows.Controls.Page> mostra como <xref:System.Windows.Controls.Frame> `pageFrame`carregar um diretamente em um ( ) usando código.</span><span class="sxs-lookup"><span data-stu-id="213da-193">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="213da-194">O exemplo a seguir é um exemplo de marcação equivalente ao anterior.</span><span class="sxs-lookup"><span data-stu-id="213da-194">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="213da-195">Recompilando após modificar o tipo de build</span><span class="sxs-lookup"><span data-stu-id="213da-195">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="213da-196">Depois de alterar o tipo de build de um arquivo de dados do aplicativo, você precisa recompilar o aplicativo inteiro para garantir que essas alterações sejam aplicadas.</span><span class="sxs-lookup"><span data-stu-id="213da-196">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="213da-197">Se você apenas compilar o aplicativo, as alterações não serão aplicadas.</span><span class="sxs-lookup"><span data-stu-id="213da-197">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="213da-198">Confira também</span><span class="sxs-lookup"><span data-stu-id="213da-198">See also</span></span>

- [<span data-ttu-id="213da-199">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="213da-199">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
