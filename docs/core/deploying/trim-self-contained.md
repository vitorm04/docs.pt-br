---
title: Cortar aplicativos independentes
description: Saiba como cortar aplicativos independentes para reduzir seu tamanho. O .NET Core agrupa o tempo de execução com um aplicativo que é publicado de forma independente e, em geral, inclui mais do tempo de execução e, em seguida, é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 47bccf25b6f6a1b65742bb5e3f5f299932659c3c
ms.sourcegitcommit: 60dc0a11ebdd77f969f41891d5cca06335cda6a7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/27/2020
ms.locfileid: "88957547"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="1ab7d-104">Cortar implantações e executáveis autossuficientes</span><span class="sxs-lookup"><span data-stu-id="1ab7d-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="1ab7d-105">O [modelo de implantação dependente de estrutura](index.md#publish-framework-dependent) foi o modelo de implantação mais bem-sucedido desde o início do .net.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="1ab7d-106">Nesse cenário, o desenvolvedor de aplicativos agrupa apenas o aplicativo e os assemblies de terceiros, com a expectativa de que as bibliotecas de tempo de execução .NET e estrutura estarão disponíveis no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="1ab7d-107">Esse modelo de implantação continua sendo o dominante no .NET Core, mas há alguns cenários em que o modelo dependente de estrutura não é o ideal.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="1ab7d-108">A alternativa é publicar um [aplicativo](index.md#publish-self-contained)independente, em que o tempo de execução e a estrutura do .NET Core são agrupados com o aplicativo e com assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="1ab7d-109">O modelo de implantação de preparo – autocontido é uma versão especializada do modelo de implantação independente que é otimizado para reduzir o tamanho da implantação.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="1ab7d-110">Minimizar o tamanho da implantação é um requisito crítico para alguns cenários do lado do cliente, como aplicativos mais Incrivelmenteos.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="1ab7d-111">Dependendo da complexidade do aplicativo, apenas um subconjunto dos assemblies da estrutura são referenciados e um subconjunto do código dentro de cada assembly é necessário para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-111">Depending on the complexity of the application, only a subset of the framework assemblies are referenced, and a subset of the code within each assembly is required to run the application.</span></span> <span data-ttu-id="1ab7d-112">As partes não utilizadas das bibliotecas são desnecessárias e podem ser cortadas do aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-112">The unused parts of the libraries are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="1ab7d-113">No entanto, há um risco de que a análise de tempo de compilação do aplicativo possa causar falhas em tempo de execução, devido ao fato de não poder analisar de maneira confiável vários padrões de código problemáticos (amplamente centrados no uso de reflexão).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="1ab7d-114">Como a confiabilidade não pode ser garantida, esse modelo de implantação é oferecido como um recurso de visualização.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span>

<span data-ttu-id="1ab7d-115">O mecanismo de análise de tempo de compilação fornece avisos para o desenvolvedor de padrões de código que são problemmatic para detectar qual outro código é necessário.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-115">The build time analysis engine provides warnings to the developer of code patterns that are problemmatic to detect which other code is required.</span></span> <span data-ttu-id="1ab7d-116">O código pode ser anotado com atributos para informar ao corte o que mais incluir.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-116">Code can be annotated with attributes to tell the trimmer what else to include.</span></span> <span data-ttu-id="1ab7d-117">Muitos padrões de reflexão podem ser substituídos com geração de código em tempo de compilação usando [geradores de origem](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-117">Many reflection patterns can be replaced with build-time code generation using [Source Generators](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span></span>

<span data-ttu-id="1ab7d-118">O modo de corte para os aplicativos é configurado com a `TrimMode` configuração.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-118">The trim mode for the applications is configured with the `TrimMode` setting.</span></span> <span data-ttu-id="1ab7d-119">O valor padrão é `copyused` e agrupa os assemblies referenciados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-119">The default value is `copyused` and bundles referenced assemblies with the application.</span></span> <span data-ttu-id="1ab7d-120">O `link` valor é usado com aplicativos Webassembly mais podestas e corta código não utilizado em assemblies.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-120">The `link` value is used with Blazor WebAssembly applications and trims unused code within assemblies.</span></span> <span data-ttu-id="1ab7d-121">Avisos de análise de corte fornecem informações sobre padrões de código em que uma análise de dependência completa não era possível.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-121">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="1ab7d-122">Esses avisos são suprimidos por padrão e podem ser ativados definindo o sinalizador `SuppressTrimAnalysisWarnings` como `false` .</span><span class="sxs-lookup"><span data-stu-id="1ab7d-122">These warnings are suppressed by default and can be turned on by setting the flag `SuppressTrimAnalysisWarnings` to `false`.</span></span> <span data-ttu-id="1ab7d-123">Para obter mais informações sobre as opções de corte disponíveis, consulte a [página ILLinker](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-123">For more information about the trim options available, see the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="1ab7d-124">O corte é um recurso experimental no .NET Core 3,1, 5,0 e está disponível _somente_ para aplicativos que são publicados internamente.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-124">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="1ab7d-125">Impedir que os assemblies sejam cortados</span><span class="sxs-lookup"><span data-stu-id="1ab7d-125">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="1ab7d-126">Há cenários em que a funcionalidade de corte falhará ao detectar referências.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-126">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="1ab7d-127">Por exemplo, quando a reflexão é usada em um assembly de tempo de execução, seja pelo aplicativo ou por uma biblioteca que é referenciada pelo seu aplicativo, o assembly não é referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-127">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="1ab7d-128">O corte não reconhece essas referências indiretas e excluiria a biblioteca da pasta publicada.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-128">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="1ab7d-129">Quando o código está indiretamente referenciando um assembly por meio de reflexão, você pode impedir que o assembly seja cortado com a `<TrimmerRootAssembly>` configuração.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-129">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="1ab7d-130">O exemplo a seguir mostra como impedir que um assembly chamado `System.Security` assembly seja cortado:</span><span class="sxs-lookup"><span data-stu-id="1ab7d-130">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="1ab7d-131">Cortar sua app-CLI</span><span class="sxs-lookup"><span data-stu-id="1ab7d-131">Trim your app - CLI</span></span>

<span data-ttu-id="1ab7d-132">Corte seu aplicativo usando o comando [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="1ab7d-132">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="1ab7d-133">Ao publicar seu aplicativo, defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="1ab7d-133">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="1ab7d-134">Publicar como um aplicativo independente para um tempo de execução específico: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="1ab7d-134">Publish as a self-contained app for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="1ab7d-135">Habilitar corte: `/p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="1ab7d-135">Enable trimming: `/p:PublishTrimmed=true`</span></span>

<span data-ttu-id="1ab7d-136">O exemplo a seguir publica um aplicativo para o Windows como independente e corta a saída.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-136">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

<span data-ttu-id="1ab7d-137">O exemplo a seguir publica um aplicativo no modo de corte agressivo em que o código não utilizado nos assemblies será cortado e os avisos de corte serão habilitados.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-137">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and trimmer warnings enabled.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

<span data-ttu-id="1ab7d-138">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-138">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="1ab7d-139">Cortar seu aplicativo-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1ab7d-139">Trim your app - Visual Studio</span></span>

<span data-ttu-id="1ab7d-140">O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-140">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="1ab7d-141">No painel **Gerenciador de soluções** , clique com o botão direito do mouse no projeto que você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-141">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="1ab7d-142">Selecione **publicar...**.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-142">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

    <span data-ttu-id="1ab7d-144">Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino da **pasta** .</span><span class="sxs-lookup"><span data-stu-id="1ab7d-144">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="1ab7d-145">Escolha **Editar**.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-145">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Perfil de publicação do Visual Studio com o botão Editar.":::

01. <span data-ttu-id="1ab7d-147">Na caixa de diálogo **configurações de perfil** , defina as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="1ab7d-147">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="1ab7d-148">Defina o **modo de implantação** **como autônomo**.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-148">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="1ab7d-149">Defina o **tempo de execução de destino** para a plataforma na qual você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-149">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="1ab7d-150">Selecione **aparar assemblies não utilizados (em visualização)**.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-150">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="1ab7d-151">Escolha **salvar** para salvar as configurações e retornar para a caixa de diálogo de **publicação** .</span><span class="sxs-lookup"><span data-stu-id="1ab7d-151">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Caixa de diálogo Configurações de perfil com modo de implantação, tempo de execução de destino e opções de corte de assemblies não utilizados realçadas.":::

01. <span data-ttu-id="1ab7d-153">Escolha **publicar** para publicar seu aplicativo cortado.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-153">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="1ab7d-154">Para obter mais informações, consulte [publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-154">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="1ab7d-155">Corte do seu aplicativo-Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="1ab7d-155">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="1ab7d-156">Visual Studio para Mac não fornece opções para cortar seu aplicativo durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="1ab7d-156">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="1ab7d-157">Você precisará publicar manualmente seguindo as instruções da seção [cortar sua app-CLI](#trim-your-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="1ab7d-157">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="1ab7d-158">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-158">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1ab7d-159">Confira também</span><span class="sxs-lookup"><span data-stu-id="1ab7d-159">See also</span></span>

- <span data-ttu-id="1ab7d-160">[Implantação de aplicativo .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-160">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="1ab7d-161">[Publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-161">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="1ab7d-162">[Publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-162">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="1ab7d-163">[dotnet Publish comando](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="1ab7d-163">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
