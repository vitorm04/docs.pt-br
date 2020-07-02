---
title: Recurso de aplicativo, conteúdo e arquivos de dados
description: Saiba mais sobre o suporte especial para configurar, identificar e usar arquivos de dados de aplicativo no Windows Presentation Foundation (WPF).
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
ms.openlocfilehash: 324b3eb922f0fd1d1d9ad00105a06a7fbdb8effd
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622855"
---
# <a name="wpf-application-resource-content-and-data-files"></a><span data-ttu-id="34310-103">Arquivos de recurso, conteúdo e dados do aplicativo WPF</span><span class="sxs-lookup"><span data-stu-id="34310-103">WPF Application Resource, Content, and Data Files</span></span>
<span data-ttu-id="34310-104">Os aplicativos do Microsoft Windows geralmente dependem de arquivos que contêm dados não executáveis, como [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] imagens, vídeos e áudio.</span><span class="sxs-lookup"><span data-stu-id="34310-104">Microsoft Windows applications often depend on files that contain non-executable data, such as [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], images, video, and audio.</span></span> <span data-ttu-id="34310-105">O Windows Presentation Foundation (WPF) oferece suporte especial para configurar, identificar e usar esses tipos de arquivos de dados, que são chamados de arquivos de dados de aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34310-105">Windows Presentation Foundation (WPF) offers special support for configuring, identifying, and using these types of data files, which are called application data files.</span></span> <span data-ttu-id="34310-106">Esse suporte gira em torno de um conjunto específico de tipos de arquivo de dados do aplicativo, incluindo:</span><span class="sxs-lookup"><span data-stu-id="34310-106">This support revolves around a specific set of application data file types, including:</span></span>  
  
- <span data-ttu-id="34310-107">**Arquivos de recurso**: Arquivos de dados que são compilados em um assembly executável ou de biblioteca do WPF.</span><span class="sxs-lookup"><span data-stu-id="34310-107">**Resource Files**: Data files that are compiled into either an executable or library WPF assembly.</span></span>  
  
- <span data-ttu-id="34310-108">**Arquivos de conteúdo**: Arquivos de dados autônomos que têm uma associação explícita com um assembly executável do WPF.</span><span class="sxs-lookup"><span data-stu-id="34310-108">**Content Files**: Standalone data files that have an explicit association with an executable WPF assembly.</span></span>  
  
- <span data-ttu-id="34310-109">**Arquivos de site de origem**: Arquivos de dados autônomos que não têm associação com um assembly do WPF executável.</span><span class="sxs-lookup"><span data-stu-id="34310-109">**Site of Origin Files**: Standalone data files that have no association with an executable WPF assembly.</span></span>  
  
 <span data-ttu-id="34310-110">Uma distinção importante a se fazer entre esses três tipos de arquivos é que os arquivos de recurso e os arquivos de conteúdo são conhecidos em tempo de build; um assembly tem o conhecimento explícito sobre eles.</span><span class="sxs-lookup"><span data-stu-id="34310-110">One important distinction to make between these three types of files is that resource files and content files are known at build time; an assembly has explicit knowledge of them.</span></span> <span data-ttu-id="34310-111">Para arquivos de site de origem, no entanto, um assembly pode não ter nenhum conhecimento sobre eles ou conhecimento implícito por meio de uma referência de URI (identificador de recurso uniforme) de pacote; o caso do último, não há nenhuma garantia de que o site de origem do arquivo referenciado realmente existe.</span><span class="sxs-lookup"><span data-stu-id="34310-111">For site of origin files, however, an assembly may have no knowledge of them at all, or implicit knowledge through a pack uniform resource identifier (URI) reference; the case of the latter, there is no guarantee that the referenced site of origin file actually exists.</span></span>  
  
 <span data-ttu-id="34310-112">Para fazer referência a arquivos de dados de aplicativo, Windows Presentation Foundation (WPF) usa o esquema do URI (Uniform Resource Identifier) do Pack, que é descrito em detalhes em [URIs de pacote no WPF](pack-uris-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="34310-112">To reference application data files, Windows Presentation Foundation (WPF) uses the Pack uniform resource identifier (URI) Scheme, which is described in detail in [Pack URIs in WPF](pack-uris-in-wpf.md)).</span></span>  
  
 <span data-ttu-id="34310-113">Este tópico descreve como configurar e usar arquivos de dados do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34310-113">This topic describes how to configure and use application data files.</span></span>  

<a name="Resource_Files"></a>
## <a name="resource-files"></a><span data-ttu-id="34310-114">Arquivos de recursos</span><span class="sxs-lookup"><span data-stu-id="34310-114">Resource Files</span></span>  
 <span data-ttu-id="34310-115">Se um arquivo de dados do aplicativo precisar estar sempre disponível para um aplicativo, a única maneira de garantir essa disponibilidade será compilá-lo em um assembly executável principal do aplicativo ou em um de seus assemblies referenciados.</span><span class="sxs-lookup"><span data-stu-id="34310-115">If an application data file must always be available to an application, the only way to guarantee availability is to compile it into an application's main executable assembly or one of its referenced assemblies.</span></span> <span data-ttu-id="34310-116">Esse tipo de arquivo de dados de aplicativo é conhecido como um *arquivo de recurso*.</span><span class="sxs-lookup"><span data-stu-id="34310-116">This type of application data file is known as a *resource file*.</span></span>  
  
 <span data-ttu-id="34310-117">Você deve usar arquivos de recurso quando:</span><span class="sxs-lookup"><span data-stu-id="34310-117">You should use resource files when:</span></span>  
  
- <span data-ttu-id="34310-118">Você não precisa atualizar o conteúdo do arquivo de recurso depois que ele é compilado em um assembly.</span><span class="sxs-lookup"><span data-stu-id="34310-118">You don't need to update the resource file's content after it is compiled into an assembly.</span></span>  
  
- <span data-ttu-id="34310-119">Você deseja simplificar a complexidade da distribuição de aplicativos, reduzindo o número de dependências de arquivo.</span><span class="sxs-lookup"><span data-stu-id="34310-119">You want to simplify application distribution complexity by reducing the number of file dependencies.</span></span>  
  
- <span data-ttu-id="34310-120">O arquivo de dados do aplicativo precisa ser localizável (consulte [visão geral de globalização e localização do WPF](../advanced/wpf-globalization-and-localization-overview.md)).</span><span class="sxs-lookup"><span data-stu-id="34310-120">Your application data file needs to be localizable (see [WPF Globalization and Localization Overview](../advanced/wpf-globalization-and-localization-overview.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34310-121">Os arquivos de recursos descritos nesta seção são diferentes dos arquivos de recursos descritos em [recursos XAML](../../../desktop-wpf/fundamentals/xaml-resources-define.md) e diferentes dos recursos incorporados ou vinculados descritos em [gerenciar recursos do aplicativo (.net)](/visualstudio/ide/managing-application-resources-dotnet).</span><span class="sxs-lookup"><span data-stu-id="34310-121">The resource files described in this section are different than the resource files described in [XAML Resources](../../../desktop-wpf/fundamentals/xaml-resources-define.md) and different than the embedded or linked resources described in [Manage Application Resources (.NET)](/visualstudio/ide/managing-application-resources-dotnet).</span></span>  
  
### <a name="configuring-resource-files"></a><span data-ttu-id="34310-122">Configurando arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="34310-122">Configuring Resource Files</span></span>  
 <span data-ttu-id="34310-123">No WPF, um arquivo de recurso é um arquivo que é incluído em um projeto do Microsoft Build Engine (MSBuild) como um `Resource` Item.</span><span class="sxs-lookup"><span data-stu-id="34310-123">In WPF, a resource file is a file that is included in an Microsoft build engine (MSBuild) project as a `Resource` item.</span></span>  
  
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
> <span data-ttu-id="34310-124">No Visual Studio, você cria um arquivo de recurso adicionando um arquivo a um projeto e definindo seu `Build Action` como `Resource` .</span><span class="sxs-lookup"><span data-stu-id="34310-124">In Visual Studio, you create a resource file by adding a file to a project and setting its `Build Action` to `Resource`.</span></span>  
  
 <span data-ttu-id="34310-125">Quando o projeto é compilado, o MSBuild compila o recurso no assembly.</span><span class="sxs-lookup"><span data-stu-id="34310-125">When the project is built, MSBuild compiles the resource into the assembly.</span></span>  
  
### <a name="using-resource-files"></a><span data-ttu-id="34310-126">Usando arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="34310-126">Using Resource Files</span></span>  
 <span data-ttu-id="34310-127">Para carregar um arquivo de recurso, você pode chamar o <xref:System.Windows.Application.GetResourceStream%2A> método da <xref:System.Windows.Application> classe, passando um URI de pacote que identifica o arquivo de recurso desejado.</span><span class="sxs-lookup"><span data-stu-id="34310-127">To load a resource file, you can call the <xref:System.Windows.Application.GetResourceStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired resource file.</span></span> <span data-ttu-id="34310-128"><xref:System.Windows.Application.GetResourceStream%2A>Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o arquivo de recurso como um <xref:System.IO.Stream> e descreve seu tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="34310-128"><xref:System.Windows.Application.GetResourceStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the resource file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="34310-129">Por exemplo, o código a seguir mostra como usar o <xref:System.Windows.Application.GetResourceStream%2A> para carregar um <xref:System.Windows.Controls.Page> arquivo de recurso e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> ( `pageFrame` ):</span><span class="sxs-lookup"><span data-stu-id="34310-129">As an example, the following code shows how to use <xref:System.Windows.Application.GetResourceStream%2A> to load a <xref:System.Windows.Controls.Page> resource file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`):</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadapageresourcefilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageResourceFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadapageresourcefilemanuallycode)]  
  
 <span data-ttu-id="34310-130">Embora <xref:System.Windows.Application.GetResourceStream%2A> a chamada forneça acesso ao <xref:System.IO.Stream> , você precisa executar o trabalho adicional de convertê-lo para o tipo da propriedade com a qual você irá configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="34310-130">While calling <xref:System.Windows.Application.GetResourceStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="34310-131">Em vez disso, você pode deixar o WPF cuidar de abrir e converter o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.</span><span class="sxs-lookup"><span data-stu-id="34310-131">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="34310-132">O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> ( `pageFrame` ) usando código.</span><span class="sxs-lookup"><span data-stu-id="34310-132">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.cs#loadpageresourcefilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml.vb#loadpageresourcefilefromcode)]  
  
 <span data-ttu-id="34310-133">O exemplo a seguir é um exemplo de marcação equivalente ao anterior.</span><span class="sxs-lookup"><span data-stu-id="34310-133">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageResourceFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetResourceStreamSnippetWindow.xaml#loadpageresourcefilefromxaml)]  
  
### <a name="application-code-files-as-resource-files"></a><span data-ttu-id="34310-134">Arquivos de código de aplicativo como arquivos de recurso</span><span class="sxs-lookup"><span data-stu-id="34310-134">Application Code Files as Resource Files</span></span>  
 <span data-ttu-id="34310-135">Um conjunto especial de arquivos de código do aplicativo WPF pode ser referenciado usando URIs de pacote, incluindo janelas, páginas, documentos de fluxo e dicionários de recursos.</span><span class="sxs-lookup"><span data-stu-id="34310-135">A special set of WPF application code files can be referenced using pack URIs, including windows, pages, flow documents, and resource dictionaries.</span></span> <span data-ttu-id="34310-136">Por exemplo, você pode definir a <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> propriedade com um pacote URI que faz referência à janela ou à página que você deseja carregar quando um aplicativo é iniciado.</span><span class="sxs-lookup"><span data-stu-id="34310-136">For example, you can set the <xref:System.Windows.Application.StartupUri%2A?displayProperty=nameWithType> property with a pack URI that references the window or page that you would like to load when an application starts.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#SetApplicationStartupURI](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/App.xaml#setapplicationstartupuri)]  
  
 <span data-ttu-id="34310-137">Você pode fazer isso quando um arquivo XAML é incluído em um projeto do MSBuild como um `Page` Item.</span><span class="sxs-lookup"><span data-stu-id="34310-137">You can do this when a XAML file is included in an MSBuild project as a `Page` item.</span></span>  
  
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
> <span data-ttu-id="34310-138">No Visual Studio, você adiciona um novo <xref:System.Windows.Window> , <xref:System.Windows.Navigation.NavigationWindow> , <xref:System.Windows.Controls.Page> , <xref:System.Windows.Documents.FlowDocument> ou <xref:System.Windows.ResourceDictionary> a um projeto, o `Build Action` para o arquivo de marcação usará como padrão `Page` .</span><span class="sxs-lookup"><span data-stu-id="34310-138">In Visual Studio, you add a new <xref:System.Windows.Window>, <xref:System.Windows.Navigation.NavigationWindow>, <xref:System.Windows.Controls.Page>, <xref:System.Windows.Documents.FlowDocument>, or <xref:System.Windows.ResourceDictionary> to a project, the `Build Action` for the markup file will default to `Page`.</span></span>  
  
 <span data-ttu-id="34310-139">Quando um projeto com `Page` itens é compilado, os [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] itens são convertidos em formato binário e compilados no assembly associado.</span><span class="sxs-lookup"><span data-stu-id="34310-139">When a project with `Page` items is compiled, the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] items are converted to binary format and compiled into the associated assembly.</span></span> <span data-ttu-id="34310-140">Consequentemente, esses arquivos podem ser usados da mesma maneira que arquivos de recurso típicos.</span><span class="sxs-lookup"><span data-stu-id="34310-140">Consequently, these files can be used in the same way as typical resource files.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34310-141">Se um [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] arquivo estiver configurado como um `Resource` Item e não tiver um arquivo code-behind, o RAW [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] será compilado em um assembly em vez de uma versão binária do RAW [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="34310-141">If a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file is configured as a `Resource` item, and does not have a code-behind file, the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] is compiled into an assembly rather than a binary version of the raw [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
<a name="Content_Files"></a>
## <a name="content-files"></a><span data-ttu-id="34310-142">Arquivos de Conteúdo</span><span class="sxs-lookup"><span data-stu-id="34310-142">Content Files</span></span>  
 <span data-ttu-id="34310-143">Um *arquivo de conteúdo* é distribuído como um arquivo flexível junto com um assembly executável.</span><span class="sxs-lookup"><span data-stu-id="34310-143">A *content file* is distributed as a loose file alongside an executable assembly.</span></span> <span data-ttu-id="34310-144">Embora eles não sejam compilados em um assembly, os assemblies são compilados com metadados que estabelecem uma associação com cada arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="34310-144">Although they are not compiled into an assembly, assemblies are compiled with metadata that establishes an association with each content file.</span></span>  
  
 <span data-ttu-id="34310-145">Você deve usar arquivos de conteúdo quando o aplicativo requer um conjunto específico de arquivos de dados do aplicativo que você deseja ser capaz de atualizar sem recompilar o assembly que os consome.</span><span class="sxs-lookup"><span data-stu-id="34310-145">You should use content files when your application requires a specific set of application data files that you want to be able to update without recompiling the assembly that consumes them.</span></span>  
  
### <a name="configuring-content-files"></a><span data-ttu-id="34310-146">Configurando arquivos de conteúdo</span><span class="sxs-lookup"><span data-stu-id="34310-146">Configuring Content Files</span></span>  
 <span data-ttu-id="34310-147">Para adicionar um arquivo de conteúdo a um projeto, um arquivo de dados do aplicativo deve ser incluído como um `Content` Item.</span><span class="sxs-lookup"><span data-stu-id="34310-147">To add a content file to a project, an application data file must be included as a `Content` item.</span></span> <span data-ttu-id="34310-148">Além disso, como um arquivo de conteúdo não é compilado diretamente no assembly, você precisa definir o elemento de metadados do MSBuild `CopyToOutputDirectory` para especificar que o arquivo de conteúdo seja copiado para um local relativo ao assembly compilado.</span><span class="sxs-lookup"><span data-stu-id="34310-148">Furthermore, because a content file is not compiled directly into the assembly, you need to set the MSBuild `CopyToOutputDirectory` metadata element to specify that the content file is copied to a location that is relative to the built assembly.</span></span> <span data-ttu-id="34310-149">Se você quiser que o recurso seja copiado para a pasta de saída de compilação toda vez que um projeto for compilado, defina o `CopyToOutputDirectory` elemento de metadados com o `Always` valor.</span><span class="sxs-lookup"><span data-stu-id="34310-149">If you want the resource to be copied to the build output folder every time a project is built, you set the `CopyToOutputDirectory` metadata element with the `Always` value.</span></span> <span data-ttu-id="34310-150">Caso contrário, você pode garantir que apenas a versão mais recente do recurso seja copiada para a pasta de saída de compilação usando o `PreserveNewest` valor.</span><span class="sxs-lookup"><span data-stu-id="34310-150">Otherwise, you can ensure that only the newest version of the resource is copied to the build output folder by using the `PreserveNewest` value.</span></span>  
  
 <span data-ttu-id="34310-151">A seguir é mostrado um arquivo que está configurado como um arquivo de conteúdo que é copiado para a pasta de saída de build somente quando uma nova versão do recurso é adicionada ao projeto.</span><span class="sxs-lookup"><span data-stu-id="34310-151">The following shows a file that is configured as a content file which is copied to the build output folder only when a new version of the resource is added to the project.</span></span>  
  
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
> <span data-ttu-id="34310-152">No Visual Studio, você cria um arquivo de conteúdo adicionando um arquivo a um projeto e definindo seu como e `Build Action` `Content` define seu `Copy to Output Directory` como `Copy always` (igual a `Always` ) e `Copy if newer` (o mesmo que `PreserveNewest` ).</span><span class="sxs-lookup"><span data-stu-id="34310-152">In Visual Studio, you create a content file by adding a file to a project and setting its `Build Action` to `Content`, and set its `Copy to Output Directory` to `Copy always` (same as `Always`) and `Copy if newer` (same as `PreserveNewest`).</span></span>  
  
 <span data-ttu-id="34310-153">Quando o projeto é compilado, um <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> atributo é compilado nos metadados do assembly para cada arquivo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="34310-153">When the project is built, an <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> attribute is compiled into the metadata of the assembly for each content file.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("ContentFile.xaml")]`  
  
 <span data-ttu-id="34310-154">O valor de <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implica o caminho para o arquivo de conteúdo relativo à sua posição no projeto.</span><span class="sxs-lookup"><span data-stu-id="34310-154">The value of the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> implies the path to the content file relative to its position in the project.</span></span> <span data-ttu-id="34310-155">Por exemplo, se um arquivo de conteúdo estava localizado em uma subpasta do projeto, as informações de caminho adicionais seriam incorporadas ao <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor.</span><span class="sxs-lookup"><span data-stu-id="34310-155">For example, if a content file was located in a project subfolder, the additional path information would be incorporated into the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value.</span></span>  
  
 `[assembly: AssemblyAssociatedContentFile("Resources/ContentFile.xaml")]`  
  
 <span data-ttu-id="34310-156">O <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> valor também é o valor do caminho para o arquivo de conteúdo na pasta de saída de compilação.</span><span class="sxs-lookup"><span data-stu-id="34310-156">The <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> value is also the value of the path to the content file in the build output folder.</span></span>  
  
### <a name="using-content-files"></a><span data-ttu-id="34310-157">Usando arquivos de conteúdo</span><span class="sxs-lookup"><span data-stu-id="34310-157">Using Content Files</span></span>  
 <span data-ttu-id="34310-158">Para carregar um arquivo de conteúdo, você pode chamar o <xref:System.Windows.Application.GetContentStream%2A> método da <xref:System.Windows.Application> classe, passando um URI de pacote que identifica o arquivo de conteúdo desejado.</span><span class="sxs-lookup"><span data-stu-id="34310-158">To load a content file, you can call the <xref:System.Windows.Application.GetContentStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired content file.</span></span> <span data-ttu-id="34310-159"><xref:System.Windows.Application.GetContentStream%2A>Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o arquivo de conteúdo como um <xref:System.IO.Stream> e descreve seu tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="34310-159"><xref:System.Windows.Application.GetContentStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the content file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="34310-160">Por exemplo, o código a seguir mostra como usar o <xref:System.Windows.Application.GetContentStream%2A> para carregar um <xref:System.Windows.Controls.Page> arquivo de conteúdo e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="34310-160">As an example, the following code shows how to use <xref:System.Windows.Application.GetContentStream%2A> to load a <xref:System.Windows.Controls.Page> content file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadapagecontentfilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageContentFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadapagecontentfilemanuallycode)]  
  
 <span data-ttu-id="34310-161">Embora <xref:System.Windows.Application.GetContentStream%2A> a chamada forneça acesso ao <xref:System.IO.Stream> , você precisa executar o trabalho adicional de convertê-lo para o tipo da propriedade com a qual você irá configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="34310-161">While calling <xref:System.Windows.Application.GetContentStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="34310-162">Em vez disso, você pode deixar o WPF cuidar de abrir e converter o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.</span><span class="sxs-lookup"><span data-stu-id="34310-162">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="34310-163">O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> ( `pageFrame` ) usando código.</span><span class="sxs-lookup"><span data-stu-id="34310-163">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.cs#loadpagecontentfilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageContentFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml.vb#loadpagecontentfilefromcode)]  
  
 <span data-ttu-id="34310-164">O exemplo a seguir é um exemplo de marcação equivalente ao anterior.</span><span class="sxs-lookup"><span data-stu-id="34310-164">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageContentFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/ApplicationGetContentStreamSnippetWindow.xaml#loadpagecontentfilefromxaml)]  
  
<a name="Site_of_Origin_Files"></a>
## <a name="site-of-origin-files"></a><span data-ttu-id="34310-165">Arquivos de site de origem</span><span class="sxs-lookup"><span data-stu-id="34310-165">Site of Origin Files</span></span>  
 <span data-ttu-id="34310-166">Os arquivos de recurso têm uma relação explícita com os assemblies que eles são distribuídos juntamente com o, conforme definido pelo <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute> .</span><span class="sxs-lookup"><span data-stu-id="34310-166">Resource files have an explicit relationship with the assemblies that they are distributed alongside, as defined by the <xref:System.Windows.Resources.AssemblyAssociatedContentFileAttribute>.</span></span> <span data-ttu-id="34310-167">Mas, às vezes você deseja estabelecer um relacionamento implícito ou inexistente entre um assembly e um arquivo de dados do aplicativo, como quando:</span><span class="sxs-lookup"><span data-stu-id="34310-167">But, there are times when you may want to establish either an implicit or non-existent relationship between an assembly and an application data file, including when:</span></span>  
  
- <span data-ttu-id="34310-168">Um arquivo não existe no momento da compilação.</span><span class="sxs-lookup"><span data-stu-id="34310-168">A file doesn't exist at compile time.</span></span>  
  
- <span data-ttu-id="34310-169">Você não sabe quais arquivos seu assembly vai requerer até o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="34310-169">You don't know what files your assembly will require until run time.</span></span>  
  
- <span data-ttu-id="34310-170">Você deseja ser capaz de atualizar os arquivos sem recompilar o assembly ao qual eles estão associados.</span><span class="sxs-lookup"><span data-stu-id="34310-170">You want to be able to update files without recompiling the assembly that they are associated with.</span></span>  
  
- <span data-ttu-id="34310-171">O aplicativo usa arquivos de dados grandes, como áudio e vídeo, e você só deseja que os usuários os baixem caso desejem.</span><span class="sxs-lookup"><span data-stu-id="34310-171">Your application uses large data files, such as audio and video, and you only want users to download them if they choose to.</span></span>  
  
 <span data-ttu-id="34310-172">É possível carregar esses tipos de arquivos usando esquemas de URI tradicionais, como os `file:///` `http://` esquemas e.</span><span class="sxs-lookup"><span data-stu-id="34310-172">It is possible to load these types of files by using traditional URI schemes, such as the `file:///` and `http://` schemes.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#AbsolutePackUriFileHttpReferenceXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/AbsolutePackUriPage.xaml#absolutepackurifilehttpreferencexaml)]  
  
 <span data-ttu-id="34310-173">No entanto, os `file:///` `http://` esquemas e exigem que seu aplicativo tenha confiança total.</span><span class="sxs-lookup"><span data-stu-id="34310-173">However, the `file:///` and `http://` schemes require your application to have full trust.</span></span> <span data-ttu-id="34310-174">Se seu aplicativo for um aplicativo de navegador XAML (XBAP) que foi iniciado pela Internet ou intranet e solicitar somente o conjunto de permissões permitido para aplicativos iniciados nesses locais, os arquivos flexíveis só poderão ser carregados a partir do site de origem do aplicativo (local de inicialização).</span><span class="sxs-lookup"><span data-stu-id="34310-174">If your application is a XAML browser application (XBAP) that was launched from the Internet or intranet, and it requests only the set of permissions that are allowed for applications launched from those locations, loose files can only be loaded from the application's site of origin (launch location).</span></span> <span data-ttu-id="34310-175">Esses arquivos são conhecidos como arquivos *de site de origem* .</span><span class="sxs-lookup"><span data-stu-id="34310-175">Such files are known as *site of origin* files.</span></span>  
  
 <span data-ttu-id="34310-176">Os arquivos de site de origem são a única opção para aplicativos parcialmente confiáveis, apesar de não serem limitados a aplicativos parcialmente confiáveis.</span><span class="sxs-lookup"><span data-stu-id="34310-176">Site of origin files are the only option for partial trust applications, although are not limited to partial trust applications.</span></span> <span data-ttu-id="34310-177">Os aplicativos de confiança total ainda podem precisar carregar arquivos de dados do aplicativo que eles não conhecem em tempo de build. Embora os aplicativos de confiança total possam utilizar file:///, é provável que os arquivos de dados do aplicativo sejam instalados na mesma pasta ou em uma subpasta do assembly do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="34310-177">Full trust applications may still need to load application data files that they do not know about at build time; while full trust applications could use file:///, it is likely that the application data files will be installed in the same folder as, or a subfolder of, the application assembly.</span></span> <span data-ttu-id="34310-178">Nesse caso, usar a referência do site de origem é mais fácil do que usar file:///, porque o uso de file:/// requer que você descubra o caminho completo do arquivo.</span><span class="sxs-lookup"><span data-stu-id="34310-178">In this case, using site of origin referencing is easier than using file:///, because using file:/// requires you to work out the full path the file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34310-179">Os arquivos de site de origem não são armazenados em cache com um aplicativo de navegador XAML (XBAP) em um computador cliente, enquanto os arquivos de conteúdo são.</span><span class="sxs-lookup"><span data-stu-id="34310-179">Site of origin files are not cached with an XAML browser application (XBAP) on a client machine, while content files are.</span></span> <span data-ttu-id="34310-180">Consequentemente, eles são baixados somente quando solicitado especificamente.</span><span class="sxs-lookup"><span data-stu-id="34310-180">Consequently, they are only downloaded when specifically requested.</span></span> <span data-ttu-id="34310-181">Se um aplicativo XBAP (aplicativo de navegador XAML) tiver arquivos de mídia grandes, configurá-los como arquivos de site de origem significa que a inicialização inicial do aplicativo é muito mais rápida e os arquivos só serão baixados sob demanda.</span><span class="sxs-lookup"><span data-stu-id="34310-181">If an XAML browser application (XBAP) application has large media files, configuring them as site of origin files means the initial application launch is much faster, and the files are only downloaded on demand.</span></span>  
  
### <a name="configuring-site-of-origin-files"></a><span data-ttu-id="34310-182">Configurando arquivos de site de origem</span><span class="sxs-lookup"><span data-stu-id="34310-182">Configuring Site of Origin Files</span></span>  
 <span data-ttu-id="34310-183">Se os arquivos do site de origem forem inexistentes ou desconhecidos no momento da compilação, você precisará usar mecanismos de implantação tradicionais para garantir que os arquivos necessários estejam disponíveis em tempo de execução, incluindo o uso do `XCopy` programa de linha de comando ou do Microsoft Windows Installer.</span><span class="sxs-lookup"><span data-stu-id="34310-183">If your site of origin files are non-existent or unknown at compile time, you need to use traditional deployment mechanisms for ensuring the required files are available at run time, including using either the `XCopy` command-line program or the Microsoft Windows Installer.</span></span>  
  
 <span data-ttu-id="34310-184">Se você souber em tempo de compilação os arquivos que deseja que estejam localizados no site de origem, mas ainda quiser evitar uma dependência explícita, poderá adicionar esses arquivos a um projeto do MSBuild como `None` Item.</span><span class="sxs-lookup"><span data-stu-id="34310-184">If you do know at compile time the files that you would like to be located at the site of origin, but still want to avoid an explicit dependency, you can add those files to an MSBuild project as `None` item.</span></span> <span data-ttu-id="34310-185">Assim como os arquivos de conteúdo, você precisa definir o `CopyToOutputDirectory` atributo MSBuild para especificar que o arquivo de site de origem seja copiado para um local relativo ao assembly compilado, especificando o `Always` valor ou o `PreserveNewest` valor.</span><span class="sxs-lookup"><span data-stu-id="34310-185">As with content files, you need to set the MSBuild `CopyToOutputDirectory` attribute to specify that the site of origin file is copied to a location that is relative to the built assembly, by specifying either the `Always` value or the `PreserveNewest` value.</span></span>  
  
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
> <span data-ttu-id="34310-186">No Visual Studio, você cria um arquivo de site de origem adicionando um arquivo a um projeto e definindo seu `Build Action` como `None` .</span><span class="sxs-lookup"><span data-stu-id="34310-186">In Visual Studio, you create a site of origin file by adding a file to a project and setting its `Build Action` to `None`.</span></span>  
  
 <span data-ttu-id="34310-187">Quando o projeto é compilado, o MSBuild copia os arquivos especificados para a pasta de saída de compilação.</span><span class="sxs-lookup"><span data-stu-id="34310-187">When the project is built, MSBuild copies the specified files to the build output folder.</span></span>  
  
### <a name="using-site-of-origin-files"></a><span data-ttu-id="34310-188">Usando arquivos de site de origem</span><span class="sxs-lookup"><span data-stu-id="34310-188">Using Site of Origin Files</span></span>  
 <span data-ttu-id="34310-189">Para carregar um arquivo de site de origem, você pode chamar o <xref:System.Windows.Application.GetRemoteStream%2A> método da <xref:System.Windows.Application> classe, passando um URI de pacote que identifica o arquivo de site de origem desejado.</span><span class="sxs-lookup"><span data-stu-id="34310-189">To load a site of origin file, you can call the <xref:System.Windows.Application.GetRemoteStream%2A> method of the <xref:System.Windows.Application> class, passing a pack URI that identifies the desired site of origin file.</span></span> <span data-ttu-id="34310-190"><xref:System.Windows.Application.GetRemoteStream%2A>Retorna um <xref:System.Windows.Resources.StreamResourceInfo> objeto, que expõe o site do arquivo de origem como um <xref:System.IO.Stream> e descreve seu tipo de conteúdo.</span><span class="sxs-lookup"><span data-stu-id="34310-190"><xref:System.Windows.Application.GetRemoteStream%2A> returns a <xref:System.Windows.Resources.StreamResourceInfo> object, which exposes the site of origin file as a <xref:System.IO.Stream> and describes its content type.</span></span>  
  
 <span data-ttu-id="34310-191">Por exemplo, o código a seguir mostra como usar o <xref:System.Windows.Application.GetRemoteStream%2A> para carregar um <xref:System.Windows.Controls.Page> arquivo de site de origem e defini-lo como o conteúdo de um <xref:System.Windows.Controls.Frame> ( `pageFrame` ).</span><span class="sxs-lookup"><span data-stu-id="34310-191">As an example, the following code shows how to use <xref:System.Windows.Application.GetRemoteStream%2A> to load a <xref:System.Windows.Controls.Page> site of origin file and set it as the content of a <xref:System.Windows.Controls.Frame> (`pageFrame`).</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadapagesoofilemanuallycode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadAPageSOOFileManuallyCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadapagesoofilemanuallycode)]  
  
 <span data-ttu-id="34310-192">Embora <xref:System.Windows.Application.GetRemoteStream%2A> a chamada forneça acesso ao <xref:System.IO.Stream> , você precisa executar o trabalho adicional de convertê-lo para o tipo da propriedade com a qual você irá configurá-lo.</span><span class="sxs-lookup"><span data-stu-id="34310-192">While calling <xref:System.Windows.Application.GetRemoteStream%2A> gives you access to the <xref:System.IO.Stream>, you need to perform the additional work of converting it to the type of the property that you'll be setting it with.</span></span> <span data-ttu-id="34310-193">Em vez disso, você pode deixar o WPF cuidar de abrir e converter o <xref:System.IO.Stream> carregando um arquivo de recurso diretamente na propriedade de um tipo usando código.</span><span class="sxs-lookup"><span data-stu-id="34310-193">Instead, you can let WPF take care of opening and converting the <xref:System.IO.Stream> by loading a resource file directly into the property of a type using code.</span></span>  
  
 <span data-ttu-id="34310-194">O exemplo a seguir mostra como carregar um <xref:System.Windows.Controls.Page> diretamente em um <xref:System.Windows.Controls.Frame> ( `pageFrame` ) usando código.</span><span class="sxs-lookup"><span data-stu-id="34310-194">The following example shows how to load a <xref:System.Windows.Controls.Page> directly into a <xref:System.Windows.Controls.Frame> (`pageFrame`) using code.</span></span>  
  
 [!code-csharp[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml.cs#loadpagesoofilefromcode)]
 [!code-vb[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromCODE](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/VisualBasic/ResourcesSample/SOOPage.xaml.vb#loadpagesoofilefromcode)]  
  
 <span data-ttu-id="34310-195">O exemplo a seguir é um exemplo de marcação equivalente ao anterior.</span><span class="sxs-lookup"><span data-stu-id="34310-195">The following example is the markup equivalent of the preceding example.</span></span>  
  
 [!code-xaml[WPFAssemblyResourcesSnippets#LoadPageSOOFileFromXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/WPFAssemblyResourcesSnippets/CSharp/ResourcesSample/SOOPage.xaml#loadpagesoofilefromxaml)]  
  
<a name="Rebuilding_after_Changing_Build_Type"></a>
## <a name="rebuilding-after-changing-build-type"></a><span data-ttu-id="34310-196">Recompilando após modificar o tipo de build</span><span class="sxs-lookup"><span data-stu-id="34310-196">Rebuilding After Changing Build Type</span></span>  
 <span data-ttu-id="34310-197">Depois de alterar o tipo de build de um arquivo de dados do aplicativo, você precisa recompilar o aplicativo inteiro para garantir que essas alterações sejam aplicadas.</span><span class="sxs-lookup"><span data-stu-id="34310-197">After you change the build type of an application data file, you need to rebuild the entire application to ensure those changes are applied.</span></span> <span data-ttu-id="34310-198">Se você apenas compilar o aplicativo, as alterações não serão aplicadas.</span><span class="sxs-lookup"><span data-stu-id="34310-198">If you only build the application, the changes are not applied.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34310-199">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34310-199">See also</span></span>

- [<span data-ttu-id="34310-200">URIs "pack://" no WPF</span><span class="sxs-lookup"><span data-stu-id="34310-200">Pack URIs in WPF</span></span>](pack-uris-in-wpf.md)
