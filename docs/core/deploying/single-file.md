---
title: Aplicativo de arquivo único
description: Saiba o que é um aplicativo de arquivo único e por que você deve considerar o uso desse modelo de implantação de aplicativo.
author: lakshanf
ms.author: lakshanf
ms.date: 08/28/2020
ms.openlocfilehash: b7693d6c119d00a798ef03ed1019f2f04c1828cf
ms.sourcegitcommit: 4d45bda8cd9558ea8af4be591e3d5a29360c1ece
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/02/2020
ms.locfileid: "91654646"
---
# <a name="single-file-deployment-and-executable"></a><span data-ttu-id="8902f-103">Implantação de arquivo único e executável</span><span class="sxs-lookup"><span data-stu-id="8902f-103">Single file deployment and executable</span></span>

<span data-ttu-id="8902f-104">Agrupar todos os arquivos dependentes do aplicativo em um único binário fornece a um desenvolvedor de aplicativos a opção atrativa para implantar e distribuir o aplicativo como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="8902f-104">Bundling all application-dependent files into a single binary provides an application developer with the attractive option to deploy and distribute the application as a single file.</span></span> <span data-ttu-id="8902f-105">Esse modelo de implantação está disponível desde o .NET Core 3,0 e foi aprimorado no .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="8902f-105">This deployment model has been available since .NET Core 3.0 and has been enhanced in .NET 5.0.</span></span> <span data-ttu-id="8902f-106">Anteriormente no .NET Core 3,0, quando um usuário executa seu aplicativo de arquivo único, o host do .NET Core primeiro extrai todos os arquivos para um diretório temporário antes de executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8902f-106">Previously in .NET Core 3.0, when a user runs your single-file app, .NET Core host first extracts all files to a temporary directory before running the application.</span></span> <span data-ttu-id="8902f-107">O .NET 5,0 melhora essa experiência executando diretamente o código sem a necessidade de extrair os arquivos do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8902f-107">.NET 5.0 improves this experience by directly running the code without the need to extract the files from the app.</span></span>

<span data-ttu-id="8902f-108">A implantação de arquivo único está disponível tanto para o [modelo de implantação dependente de estrutura](index.md#publish-framework-dependent) quanto para [aplicativos independentes](index.md#publish-self-contained).</span><span class="sxs-lookup"><span data-stu-id="8902f-108">Single File deployment is available for both the [framework-dependent deployment model](index.md#publish-framework-dependent) and [self-contained applications](index.md#publish-self-contained).</span></span> <span data-ttu-id="8902f-109">O tamanho do único arquivo em um aplicativo independente será grande, já que incluirá o tempo de execução e as bibliotecas de estrutura.</span><span class="sxs-lookup"><span data-stu-id="8902f-109">The size of the single file in a self-contained application will be large since it will include the runtime and the framework libraries.</span></span> <span data-ttu-id="8902f-110">A opção de implantação de arquivo único pode ser combinada com as opções de publicação [ReadyToRun](../tools/dotnet-publish.md) e [Trim (um recurso experimental no .NET 5,0)](trim-self-contained.md) .</span><span class="sxs-lookup"><span data-stu-id="8902f-110">The single file deployment option can be combined with [ReadyToRun](../tools/dotnet-publish.md) and [Trim (an experimental feature in .NET 5.0)](trim-self-contained.md) publish options.</span></span>

## <a name="api-incompatibility"></a><span data-ttu-id="8902f-111">Incompatibilidade de API</span><span class="sxs-lookup"><span data-stu-id="8902f-111">API incompatibility</span></span>

<span data-ttu-id="8902f-112">Algumas APIs não são compatíveis com a implantação de arquivo único e os aplicativos podem exigir modificações se usarem essas APIs.</span><span class="sxs-lookup"><span data-stu-id="8902f-112">Some APIs are not compatible with single-file deployment and applications may require modification if they use these APIs.</span></span> <span data-ttu-id="8902f-113">Se você usar uma estrutura ou pacote de terceiros, é possível que eles também possam usar uma dessas APIs e precisar de modificação.</span><span class="sxs-lookup"><span data-stu-id="8902f-113">If you use a third-party framework or package, it's possible that they may also use one of these APIs and need modification.</span></span> <span data-ttu-id="8902f-114">A causa mais comum de problemas é a dependência de caminhos de arquivo para arquivos ou DLLs fornecidos com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="8902f-114">The most common cause of problems is dependence on file paths for files or DLLs shipped with the application.</span></span>

<span data-ttu-id="8902f-115">A tabela a seguir tem os detalhes relevantes da API da biblioteca de tempo de execução para uso de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="8902f-115">The table below has the relevant runtime library API details for single-file use.</span></span>

| <span data-ttu-id="8902f-116">API</span><span class="sxs-lookup"><span data-stu-id="8902f-116">API</span></span>                            | <span data-ttu-id="8902f-117">Observação</span><span class="sxs-lookup"><span data-stu-id="8902f-117">Note</span></span>                                                                   |
|--------------------------------|------------------------------------------------------------------------|
| `Assembly.Location`            | <span data-ttu-id="8902f-118">Retorna uma cadeia de caracteres vazia.</span><span class="sxs-lookup"><span data-stu-id="8902f-118">Returns an empty string.</span></span>                                               |
| `Module.FullyQualifiedName`    | <span data-ttu-id="8902f-119">Retorna uma cadeia de caracteres com o valor de `<Unknown>` ou gera uma exceção.</span><span class="sxs-lookup"><span data-stu-id="8902f-119">Returns a string with the value of `<Unknown>` or throws an exception.</span></span> |
| `Module.Name`                  | <span data-ttu-id="8902f-120">Retorna uma cadeia de caracteres com o valor de `<Unknown>` .</span><span class="sxs-lookup"><span data-stu-id="8902f-120">Returns a string with the value of `<Unknown>`.</span></span>                        |
| `Assembly.GetFile`             | <span data-ttu-id="8902f-121">Gera <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="8902f-121">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.GetFiles`            | <span data-ttu-id="8902f-122">Gera <xref:System.IO.IOException>.</span><span class="sxs-lookup"><span data-stu-id="8902f-122">Throws <xref:System.IO.IOException>.</span></span>                                   |
| `Assembly.CodeBase`            | <span data-ttu-id="8902f-123">Gera <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="8902f-123">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `Assembly.EscapedCodeBase`     | <span data-ttu-id="8902f-124">Gera <xref:System.PlatformNotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="8902f-124">Throws <xref:System.PlatformNotSupportedException>.</span></span>                    |
| `AssemblyName.CodeBase`        | <span data-ttu-id="8902f-125">Retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="8902f-125">Returns `null`.</span></span>                                                        |
| `AssemblyName.EscapedCodeBase` | <span data-ttu-id="8902f-126">Retorna `null`.</span><span class="sxs-lookup"><span data-stu-id="8902f-126">Returns `null`.</span></span>                                                        |

<span data-ttu-id="8902f-127">Temos algumas recomendações para corrigir cenários comuns:</span><span class="sxs-lookup"><span data-stu-id="8902f-127">We have some recommendations for fixing common scenarios:</span></span>

* <span data-ttu-id="8902f-128">Para acessar arquivos ao lado do executável, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8902f-128">To access files next to the executable, use <xref:System.AppContext.BaseDirectory?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="8902f-129">Para localizar o nome de arquivo do executável, use o primeiro elemento de <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="8902f-129">To find the file name of the executable, use the first element of <xref:System.Environment.GetCommandLineArgs?displayProperty=nameWithType>.</span></span>

* <span data-ttu-id="8902f-130">Para evitar inteiramente o envio de arquivos soltos, considere o uso de [recursos incorporados](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-130">To avoid shipping loose files entirely, consider using [embedded resources](../../framework/resources/creating-resource-files-for-desktop-apps.md).</span></span>

## <a name="other-considerations"></a><span data-ttu-id="8902f-131">Outras considerações</span><span class="sxs-lookup"><span data-stu-id="8902f-131">Other considerations</span></span>

<span data-ttu-id="8902f-132">Por padrão, o arquivo único não agrupa bibliotecas nativas.</span><span class="sxs-lookup"><span data-stu-id="8902f-132">Single-file doesn't bundle native libraries by default.</span></span> <span data-ttu-id="8902f-133">No Linux, vinculamos o tempo de execução ao pacote e somente as bibliotecas nativas do aplicativo são implantadas no mesmo diretório que o aplicativo de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="8902f-133">On Linux, we prelink the runtime into the bundle and only application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="8902f-134">No Windows, previnculo apenas o código de hospedagem e as bibliotecas nativas de tempo de execução e aplicativo são implantadas no mesmo diretório que o aplicativo de arquivo único.</span><span class="sxs-lookup"><span data-stu-id="8902f-134">On Windows, we prelink only the hosting code and both the runtime and application native libraries are deployed to the same directory as the single-file app.</span></span> <span data-ttu-id="8902f-135">Isso é para garantir uma boa experiência de depuração, que exige que os arquivos nativos sejam excluídos do único arquivo.</span><span class="sxs-lookup"><span data-stu-id="8902f-135">This is to ensure a good debugging experience, which requires native files to be excluded from the single file.</span></span> <span data-ttu-id="8902f-136">Há uma opção para definir um sinalizador, `IncludeNativeLibrariesForSelfExtract` , para incluir bibliotecas nativas no único pacote de arquivo, mas esses arquivos serão extraídos para um diretório temporário no computador cliente quando o aplicativo de arquivo único for executado.</span><span class="sxs-lookup"><span data-stu-id="8902f-136">There is an option to set a flag, `IncludeNativeLibrariesForSelfExtract`, to include native libraries in the single file bundle, but these files will be extracted to a temporary directory in the client machine when the single file application is run.</span></span>

<span data-ttu-id="8902f-137">O aplicativo de arquivo único terá todos os arquivos PDB relacionados juntamente com ele e não será agrupado por padrão.</span><span class="sxs-lookup"><span data-stu-id="8902f-137">Single-file application will have all related PDB files alongside it and will not be bundled by default.</span></span> <span data-ttu-id="8902f-138">Se você quiser incluir PDBs dentro do assembly para projetos que você criar, defina o `DebugType` como `embedded` conforme descrito [abaixo](#include-pdb-files-inside-the-bundle) em detalhes.</span><span class="sxs-lookup"><span data-stu-id="8902f-138">If you want to include PDBs inside the assembly for projects you build, set the `DebugType` to `embedded` as described [below](#include-pdb-files-inside-the-bundle) in detail.</span></span>

<span data-ttu-id="8902f-139">Os componentes C++ gerenciados não são adequados para implantação de arquivo único e recomendamos que você escreva aplicativos em C# ou em outra linguagem C++ não gerenciada para que seja compatível com arquivo único.</span><span class="sxs-lookup"><span data-stu-id="8902f-139">Managed C++ components aren't well suited for single-file deployment and we recommend that you write applications in C# or another non-managed C++ language to be single-file compatible.</span></span>

## <a name="exclude-files-from-being-embedded"></a><span data-ttu-id="8902f-140">Excluir arquivos de serem inseridos</span><span class="sxs-lookup"><span data-stu-id="8902f-140">Exclude files from being embedded</span></span>

<span data-ttu-id="8902f-141">Determinados arquivos podem ser explicitamente excluídos de serem inseridos no arquivo único definindo os seguintes metadados:</span><span class="sxs-lookup"><span data-stu-id="8902f-141">Certain files can be explicitly excluded from being embedded in the single-file by setting following metadata:</span></span>

```xml
<ExcludeFromSingleFile>true</ExcludeFromSingleFile>
```

<span data-ttu-id="8902f-142">Por exemplo, para posicionar alguns arquivos no diretório de publicação, mas não agrupá-los no arquivo único:</span><span class="sxs-lookup"><span data-stu-id="8902f-142">For example, to place some files in the publish directory but not bundle them in the single-file:</span></span>

```xml
<ItemGroup>
  <Content Update="Plugin.dll">
    <CopyToPublishDirectory>PreserveNewest</CopyToPublishDirectory>
    <ExcludeFromSingleFile>true</ExcludeFromSingleFile>
  </Content>
</ItemGroup>
```

## <a name="include-pdb-files-inside-the-bundle"></a><span data-ttu-id="8902f-143">Incluir arquivos PDB dentro do pacote</span><span class="sxs-lookup"><span data-stu-id="8902f-143">Include PDB files inside the bundle</span></span>

<span data-ttu-id="8902f-144">O arquivo PDB de um assembly pode ser inserido no próprio assembly (o `.dll` ) usando a configuração abaixo.</span><span class="sxs-lookup"><span data-stu-id="8902f-144">The PDB file for an assembly can be embedded into the assembly itself (the `.dll`) using the setting below.</span></span> <span data-ttu-id="8902f-145">Como os símbolos fazem parte do assembly, eles também serão parte do aplicativo de arquivo único:</span><span class="sxs-lookup"><span data-stu-id="8902f-145">Since the symbols are part of the assembly, they will be part of the single-file application as well:</span></span>

```xml
<DebugType>embedded</DebugType>
```

<span data-ttu-id="8902f-146">Por exemplo, adicione a seguinte propriedade ao arquivo de projeto de um assembly para inserir o arquivo PDB nesse assembly:</span><span class="sxs-lookup"><span data-stu-id="8902f-146">For example, add the following property to the project file of an assembly to embed the PDB file to that assembly:</span></span>

```xml
<PropertyGroup>
  <DebugType>embedded</DebugType>
</PropertyGroup>
```

## <a name="publish-a-single-file-app---cli"></a><span data-ttu-id="8902f-147">Publicar um aplicativo de arquivo único-CLI</span><span class="sxs-lookup"><span data-stu-id="8902f-147">Publish a single file app - CLI</span></span>

<span data-ttu-id="8902f-148">Publicar um aplicativo de arquivo único usando o comando [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="8902f-148">Publish a single file application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="8902f-149">Ao publicar seu aplicativo, defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="8902f-149">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="8902f-150">Publicar para um tempo de execução específico: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="8902f-150">Publish for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="8902f-151">Publicar como um arquivo único: `-p:PublishSingleFile=true`</span><span class="sxs-lookup"><span data-stu-id="8902f-151">Publish as a single-file: `-p:PublishSingleFile=true`</span></span>

<span data-ttu-id="8902f-152">O exemplo a seguir publica um aplicativo para o Windows como um aplicativo de arquivo único independente.</span><span class="sxs-lookup"><span data-stu-id="8902f-152">The following example publishes an app for Windows as a self-contained single file application.</span></span>

```dotnetcli
dotnet publish -r win-x64 -p:PublishSingleFile=true --self-contained true
```

<span data-ttu-id="8902f-153">O exemplo a seguir publica um aplicativo para Linux como um aplicativo de arquivo único dependente de estrutura.</span><span class="sxs-lookup"><span data-stu-id="8902f-153">The following example publishes an app for Linux as a framework dependent single file application.</span></span>

```dotnetcli
dotnet publish -r linux-x64 -p:PublishSingleFile=true --self-contained false
```

<span data-ttu-id="8902f-154">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-154">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio"></a><span data-ttu-id="8902f-155">Publicar um único aplicativo de arquivo-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8902f-155">Publish a single file app - Visual Studio</span></span>

<span data-ttu-id="8902f-156">O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.</span><span class="sxs-lookup"><span data-stu-id="8902f-156">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="8902f-157">No painel **Gerenciador de soluções** , clique com o botão direito do mouse no projeto que você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="8902f-157">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="8902f-158">Selecione **Publicar**.</span><span class="sxs-lookup"><span data-stu-id="8902f-158">Select **Publish**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-solution-explorer.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

    <span data-ttu-id="8902f-160">Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino da **pasta** .</span><span class="sxs-lookup"><span data-stu-id="8902f-160">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="8902f-161">Escolha **Editar**.</span><span class="sxs-lookup"><span data-stu-id="8902f-161">Choose **Edit**.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-edit-settings.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

01. <span data-ttu-id="8902f-163">Na caixa de diálogo **configurações de perfil** , defina as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="8902f-163">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="8902f-164">Defina o **modo de implantação** **como autônomo**.</span><span class="sxs-lookup"><span data-stu-id="8902f-164">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="8902f-165">Defina o **tempo de execução de destino** para a plataforma na qual você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="8902f-165">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="8902f-166">Selecione **produzir arquivo único**.</span><span class="sxs-lookup"><span data-stu-id="8902f-166">Select **Produce single file**.</span></span>

    <span data-ttu-id="8902f-167">Escolha **salvar** para salvar as configurações e retornar para a caixa de diálogo de **publicação** .</span><span class="sxs-lookup"><span data-stu-id="8902f-167">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/single-file/visual-studio-publish-single-file-properties.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

01. <span data-ttu-id="8902f-169">Escolha **publicar** para publicar seu aplicativo como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="8902f-169">Choose **Publish** to publish your app as a single file.</span></span>

<span data-ttu-id="8902f-170">Para obter mais informações, consulte [publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-170">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="publish-a-single-file-app---visual-studio-for-mac"></a><span data-ttu-id="8902f-171">Publicar um único aplicativo de arquivo-Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="8902f-171">Publish a single file app - Visual Studio for Mac</span></span>

<span data-ttu-id="8902f-172">Visual Studio para Mac não fornece opções para publicar seu aplicativo como um único arquivo.</span><span class="sxs-lookup"><span data-stu-id="8902f-172">Visual Studio for Mac doesn't provide options to publish your app as a single file.</span></span> <span data-ttu-id="8902f-173">Você precisará publicar manualmente seguindo as instruções da seção [publicar um único arquivo app-CLI](#publish-a-single-file-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="8902f-173">You'll need to publish manually by following the instructions from the [Publish a single file app - CLI](#publish-a-single-file-app---cli) section.</span></span> <span data-ttu-id="8902f-174">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-174">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="8902f-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8902f-175">See also</span></span>

- <span data-ttu-id="8902f-176">[Implantação de aplicativo .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-176">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="8902f-177">[Publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-177">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="8902f-178">[Publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-178">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="8902f-179">[ `dotnet publish` comando](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="8902f-179">[`dotnet publish` command](../tools/dotnet-publish.md).</span></span>
