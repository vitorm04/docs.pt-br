---
title: Aplicativo de arquivo único
description: Saiba o que é um aplicativo de arquivo único e por que você deve considerar o uso desse modelo de implantação de aplicativo.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: 795ea98a9fd9d672b199eb2d9b24151340ef8246
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89495784"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="1965d-103">Implantação de arquivo único e executável</span><span class="sxs-lookup"><span data-stu-id="1965d-103">Single file deployment and executable</span></span>

<span data-ttu-id="1965d-104">Agrupar todos os arquivos dependentes do aplicativo em um único binário fornece a um desenvolvedor de aplicativos a opção atrativa para implantar e distribuir o aplicativo como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="1965d-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="1965d-105">Esse modelo de implantação está disponível desde o .NET Core 3,0 e foi aprimorado no .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="1965d-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="1965d-106">Anteriormente no .NET Core 3,0, quando um usuário executa seu aplicativo de arquivo único, o host do .NET Core primeiro extrai todos os arquivos para um diretório temporário antes de executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1965d-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="1965d-107">O .NET 5,0 melhora essa experiência executando diretamente o código sem a necessidade de extrair os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1965d-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="1965d-108">A implantação de arquivo único está disponível tanto para o [modelo de implantação dependente de estrutura](index.md#publish-framework-dependent) quanto para [aplicativos independentes](index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="1965d-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="1965d-109">O tamanho do único arquivo em um aplicativo independente será grande, já que incluirá o tempo de execução e as bibliotecas de estrutura.</span><span class="sxs-lookup"><span data-stu-id="1965d-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="1965d-110">A opção de implantação de arquivo único pode ser combinada com as opções de publicação [ReadyToRun](../tools/dotnet-publish.md) e [Trim (um recurso experimental no .NET 5,0)](trim-self-contained.md) .</span><span class="sxs-lookup"><span data-stu-id="1965d-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

<span data-ttu-id="1965d-111">Há algumas advertências que você precisa estar ciente para o uso de arquivo único, primeiro do qual é o uso de informações de caminho para localizar um arquivo relativo ao local do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1965d-111">There are some caveats that you need to be aware for single-file use, first of which is the use of path information to locate a file relative to the location of your application.</span></span> <span data-ttu-id="1965d-112">A <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API retornará uma cadeia de caracteres vazia, que é o comportamento padrão para assemblies carregados da memória.</span><span class="sxs-lookup"><span data-stu-id="1965d-112">The <xref:System.Reflection.Assembly.Location?displayProperty=nameWithType> API will return an empty string, which is the default behavior for assemblies loaded from memory.</span></span> <span data-ttu-id="1965d-113">O compilador fornecerá um aviso para essa API durante o tempo de compilação para alertar o desenvolvedor sobre o comportamento específico.</span><span class="sxs-lookup"><span data-stu-id="1965d-113">The compiler will give a warning for this API during build time to alert the developer to the specific behavior.</span></span> <span data-ttu-id="1965d-114">Se o caminho para o diretório do aplicativo for necessário, a <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API retornará o diretório onde o AppHost (o próprio pacote de arquivo único) reside.</span><span class="sxs-lookup"><span data-stu-id="1965d-114">If the path to the application directory is needed, the <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> API will return the directory where the AppHost (the single-file bundle itself) resides.</span></span> <span data-ttu-id="1965d-115">Os aplicativos C++ gerenciados não são adequados para implantação de arquivo único e recomendamos que você escreva aplicativos em C# para ser compatível com um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="1965d-115">Managed C++ applications aren't well suited for single-file deployment and we recommend that you write applications in C# to be single-file compatible.</span></span>

<span data-ttu-id="1965d-116">Por padrão, o arquivo único não agrupa bibliotecas nativas.</span><span class="sxs-lookup"><span data-stu-id="1965d-116">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="1965d-117">No Linux, vinculamos o tempo de execução ao pacote e somente as bibliotecas nativas do aplicativo são implantadas no mesmo diretório que o aplicativo de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="1965d-117">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="1965d-118">No Windows, previnculo apenas o código de hospedagem e as bibliotecas nativas de tempo de execução e aplicativo são implantadas no mesmo diretório que o aplicativo de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="1965d-118">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="1965d-119">Isso é para garantir uma boa experiência de depuração, que exige que os arquivos nativos sejam excluídos do único arquivo.</span><span class="sxs-lookup"><span data-stu-id="1965d-119">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="1965d-120">Há uma opção para definir um sinalizador, `IncludeNativeLibrariesForSelfExtract` , para incluir bibliotecas nativas no único pacote de arquivo, mas esses arquivos serão extraídos para um diretório temporário no computador cliente quando o aplicativo de arquivo único for executado.</span><span class="sxs-lookup"><span data-stu-id="1965d-120">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="1965d-121">Excluir arquivos de serem inseridos</span><span class="sxs-lookup"><span data-stu-id="1965d-121">Exclude files from being embedded</span></span>

<span data-ttu-id="1965d-122">Determinados arquivos podem ser explicitamente excluídos de serem inseridos no arquivo único definindo os seguintes metadados:</span><span class="sxs-lookup"><span data-stu-id="1965d-122">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="1965d-123">Por exemplo, para posicionar alguns arquivos no diretório de publicação, mas não agrupá-los no arquivo único:</span><span class="sxs-lookup"><span data-stu-id="1965d-123">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="1965d-124">Publicar um aplicativo de arquivo único-CLI</span><span class="sxs-lookup"><span data-stu-id="1965d-124">Publish a single file app - CLI</span></span>

<span data-ttu-id="1965d-125">Publicar um aplicativo de arquivo único usando o comando [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="1965d-125">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="1965d-126">Ao publicar seu aplicativo, defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1965d-126">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="1965d-127">Publicar para um tempo de execução específico: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="1965d-127">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="1965d-128">Publicar como um arquivo único: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="1965d-128">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="1965d-129">O exemplo a seguir publica um aplicativo para o Windows como um aplicativo de arquivo único independente.</span><span class="sxs-lookup"><span data-stu-id="1965d-129">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="1965d-130">O exemplo a seguir publica um aplicativo para Linux como um aplicativo de arquivo único dependente de estrutura.</span><span class="sxs-lookup"><span data-stu-id="1965d-130">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="1965d-131">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-131">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="1965d-132">Publicar um único aplicativo de arquivo-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1965d-132">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="1965d-133">O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.</span><span class="sxs-lookup"><span data-stu-id="1965d-133">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="1965d-134">No painel **Gerenciador de soluções** , clique com o botão direito do mouse no projeto que você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="1965d-134">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="1965d-135">Selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="1965d-135">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

    <span data-ttu-id="1965d-137">Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino da **pasta** .</span><span class="sxs-lookup"><span data-stu-id="1965d-137">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="1965d-138">Escolha **Editar**.</span><span class="sxs-lookup"><span data-stu-id="1965d-138">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Perfil de publicação do Visual Studio com o botão Editar.":::

01. <span data-ttu-id="1965d-140">Na caixa de diálogo **configurações de perfil** , defina as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="1965d-140">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="1965d-141">Defina o **modo de implantação** **como autônomo**.</span><span class="sxs-lookup"><span data-stu-id="1965d-141">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="1965d-142">Defina o **tempo de execução de destino** para a plataforma na qual você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="1965d-142">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="1965d-143">Selecione **produzir arquivo único**.</span><span class="sxs-lookup"><span data-stu-id="1965d-143">Select **Produce single file**.</span></span>

    <span data-ttu-id="1965d-144">Escolha **salvar** para salvar as configurações e retornar para a caixa de diálogo de **publicação** .</span><span class="sxs-lookup"><span data-stu-id="1965d-144">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Caixa de diálogo Configurações de perfil com modo de implantação, tempo de execução de destino e opções de arquivo único realçadas.":::

01. <span data-ttu-id="1965d-146">Escolha **publicar** para publicar seu aplicativo como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="1965d-146">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="1965d-147">Para obter mais informações, consulte [publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-147">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="1965d-148">Publicar um único aplicativo de arquivo-Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="1965d-148">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="1965d-149">Visual Studio para Mac não fornece opções para publicar seu aplicativo como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="1965d-149">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="1965d-150">Você precisará publicar manualmente seguindo as instruções da seção [publicar um único arquivo app-CLI](#publish-a-single-file-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="1965d-150">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="1965d-151">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-151">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1965d-152">Veja também</span><span class="sxs-lookup"><span data-stu-id="1965d-152">See also</span></span>

- <span data-ttu-id="1965d-153">[Implantação de aplicativo .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-153">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="1965d-154">[Publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-154">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="1965d-155">[Publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-155">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="1965d-156">[ `dotnet publish` comando](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="1965d-156">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
