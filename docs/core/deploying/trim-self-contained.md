---
title: Cortar aplicativos independentes
description: Saiba como cortar aplicativos independentes para reduzir seu tamanho. O .NET Core agrupa o tempo de execução com um aplicativo que é publicado de forma independente e, em geral, inclui mais do tempo de execução e, em seguida, é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bf38ffe4d47986ae78c6cf2b2e5ecb292411ba6c
ms.sourcegitcommit: 6d09ae36acba0b0e2ba47999f8f1a725795462a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/29/2020
ms.locfileid: "92925279"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="13c98-104">Cortar implantações e executáveis autossuficientes</span><span class="sxs-lookup"><span data-stu-id="13c98-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="13c98-105">O [modelo de implantação dependente de estrutura](index.md#publish-framework-dependent) foi o modelo de implantação mais bem-sucedido desde o início do .net.</span><span class="sxs-lookup"><span data-stu-id="13c98-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="13c98-106">Nesse cenário, o desenvolvedor de aplicativos agrupa apenas o aplicativo e os assemblies de terceiros, com a expectativa de que as bibliotecas de tempo de execução .NET e estrutura estarão disponíveis no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="13c98-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="13c98-107">Esse modelo de implantação continua sendo o dominante no .NET Core, mas há alguns cenários em que o modelo dependente de estrutura não é o ideal.</span><span class="sxs-lookup"><span data-stu-id="13c98-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="13c98-108">A alternativa é publicar um [aplicativo](index.md#publish-self-contained)independente, em que o tempo de execução e a estrutura do .NET Core são agrupados com o aplicativo e com assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="13c98-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="13c98-109">O modelo de implantação de preparo – autocontido é uma versão especializada do modelo de implantação independente que é otimizado para reduzir o tamanho da implantação.</span><span class="sxs-lookup"><span data-stu-id="13c98-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="13c98-110">Minimizar o tamanho da implantação é um requisito crítico para alguns cenários do lado do cliente, como aplicativos mais Incrivelmenteos.</span><span class="sxs-lookup"><span data-stu-id="13c98-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="13c98-111">Dependendo da complexidade do aplicativo, apenas um subconjunto dos assemblies da estrutura são referenciados e um subconjunto do código dentro de cada assembly é necessário para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13c98-111">Depending on the complexity of the application, only a subset of the framework assemblies are referenced, and a subset of the code within each assembly is required to run the application.</span></span> <span data-ttu-id="13c98-112">As partes não utilizadas das bibliotecas são desnecessárias e podem ser cortadas do aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="13c98-112">The unused parts of the libraries are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="13c98-113">No entanto, há um risco de que a análise de tempo de compilação do aplicativo possa causar falhas em tempo de execução, devido ao fato de não poder analisar de maneira confiável vários padrões de código problemáticos (amplamente centrados no uso de reflexão).</span><span class="sxs-lookup"><span data-stu-id="13c98-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="13c98-114">Como a confiabilidade não pode ser garantida, esse modelo de implantação é oferecido como um recurso de visualização.</span><span class="sxs-lookup"><span data-stu-id="13c98-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span>

<span data-ttu-id="13c98-115">O mecanismo de análise de tempo de compilação fornece avisos ao desenvolvedor de padrões de código que são problemáticos para detectar qual outro código é necessário.</span><span class="sxs-lookup"><span data-stu-id="13c98-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic to detect which other code is required.</span></span> <span data-ttu-id="13c98-116">O código pode ser anotado com atributos para informar ao corte o que mais incluir.</span><span class="sxs-lookup"><span data-stu-id="13c98-116">Code can be annotated with attributes to tell the trimmer what else to include.</span></span> <span data-ttu-id="13c98-117">Muitos padrões de reflexão podem ser substituídos com geração de código em tempo de compilação usando [geradores de origem](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-117">Many reflection patterns can be replaced with build-time code generation using [Source Generators](https://github.com/dotnet/roslyn/blob/master/docs/features/source-generators.md).</span></span>

<span data-ttu-id="13c98-118">O modo de corte para os aplicativos é configurado com a `TrimMode` configuração.</span><span class="sxs-lookup"><span data-stu-id="13c98-118">The trim mode for the applications is configured with the `TrimMode` setting.</span></span> <span data-ttu-id="13c98-119">O valor padrão é `copyused` e agrupa os assemblies referenciados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="13c98-119">The default value is `copyused` and bundles referenced assemblies with the application.</span></span> <span data-ttu-id="13c98-120">O `link` valor é usado com aplicativos Webassembly mais podestas e corta código não utilizado em assemblies.</span><span class="sxs-lookup"><span data-stu-id="13c98-120">The `link` value is used with Blazor WebAssembly applications and trims unused code within assemblies.</span></span> <span data-ttu-id="13c98-121">Avisos de análise de corte fornecem informações sobre padrões de código em que uma análise de dependência completa não era possível.</span><span class="sxs-lookup"><span data-stu-id="13c98-121">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="13c98-122">Esses avisos são suprimidos por padrão e podem ser ativados definindo o sinalizador `SuppressTrimAnalysisWarnings` como `false` .</span><span class="sxs-lookup"><span data-stu-id="13c98-122">These warnings are suppressed by default and can be turned on by setting the flag `SuppressTrimAnalysisWarnings` to `false`.</span></span> <span data-ttu-id="13c98-123">Para obter mais informações sobre as opções de corte disponíveis, consulte [Opções de corte](trimming-options.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-123">For more information about the trim options available, see [Trimming options](trimming-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="13c98-124">O corte é um recurso experimental no .NET Core 3,1 e no .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="13c98-124">Trimming is an experimental feature in .NET Core 3.1 and .NET 5.0.</span></span> <span data-ttu-id="13c98-125">O corte _só_ está disponível para aplicativos que são publicados internamente.</span><span class="sxs-lookup"><span data-stu-id="13c98-125">Trimming is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="13c98-126">Impedir que os assemblies sejam cortados</span><span class="sxs-lookup"><span data-stu-id="13c98-126">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="13c98-127">Há cenários em que a funcionalidade de corte falhará ao detectar referências.</span><span class="sxs-lookup"><span data-stu-id="13c98-127">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="13c98-128">Por exemplo, quando a reflexão é usada em um assembly de tempo de execução, seja pelo aplicativo ou por uma biblioteca que é referenciada pelo seu aplicativo, o assembly não é referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="13c98-128">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="13c98-129">O corte não reconhece essas referências indiretas e excluiria a biblioteca da pasta publicada.</span><span class="sxs-lookup"><span data-stu-id="13c98-129">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="13c98-130">Quando o código está indiretamente referenciando um assembly por meio de reflexão, você pode impedir que o assembly seja cortado com a `<TrimmerRootAssembly>` configuração.</span><span class="sxs-lookup"><span data-stu-id="13c98-130">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="13c98-131">O exemplo a seguir mostra como impedir que um assembly chamado `System.Security` assembly seja cortado:</span><span class="sxs-lookup"><span data-stu-id="13c98-131">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

### <a name="support-for-ssl-certificates"></a><span data-ttu-id="13c98-132">Suporte para certificados SSL</span><span class="sxs-lookup"><span data-stu-id="13c98-132">Support for SSL certificates</span></span>

<span data-ttu-id="13c98-133">Se seu aplicativo carregar certificados SSL, como em um aplicativo de ASP.NET Core, você desejará garantir que, ao cortar, você impeça o corte de assemblies que ajudarão no carregamento de certificados SSL.</span><span class="sxs-lookup"><span data-stu-id="13c98-133">If your app loads SSL certificates, such as in an ASP.NET Core app, you'll want to ensure that when trimming you prevent trimming assemblies that will help with loading SSL certificates.</span></span>

<span data-ttu-id="13c98-134">Podemos atualizar nosso arquivo de projeto para incluir o seguinte para ASP.NET Core 3,1:</span><span class="sxs-lookup"><span data-stu-id="13c98-134">We can update our project file to include the following for ASP.NET Core 3.1:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
  <PropertyGroup>...</PropertyGroup>
  <!--Include the following for .aspnetcore 3.1-->
  <ItemGroup>
    <TrimmerRootAssembly Include="System.Net" />
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

<span data-ttu-id="13c98-135">Se estivermos usando o .NET 5,0, podemos atualizar nosso arquivo de projeto para incluir o seguinte:</span><span class="sxs-lookup"><span data-stu-id="13c98-135">If we're using .Net 5.0, we can update our project file to include the following:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">
 <PropertyGroup>...</PropertyGroup>
 <!--Include the following for .net 5.0-->
 <ItemGroup>
    <TrimmerRootAssembly Include="System.Net.Security" />
    <TrimmerRootAssembly Include="System.Security" />
  </ItemGroup>
  ...
</Project>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="13c98-136">Cortar sua app-CLI</span><span class="sxs-lookup"><span data-stu-id="13c98-136">Trim your app - CLI</span></span>

<span data-ttu-id="13c98-137">Corte seu aplicativo usando o comando [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="13c98-137">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="13c98-138">Ao publicar seu aplicativo, defina as seguintes propriedades:</span><span class="sxs-lookup"><span data-stu-id="13c98-138">When you publish your app, set the following properties:</span></span>

- <span data-ttu-id="13c98-139">Publicar como um aplicativo independente para um tempo de execução específico: `-r win-x64`</span><span class="sxs-lookup"><span data-stu-id="13c98-139">Publish as a self-contained app for a specific runtime: `-r win-x64`</span></span>
- <span data-ttu-id="13c98-140">Habilitar corte: `/p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="13c98-140">Enable trimming: `/p:PublishTrimmed=true`</span></span>

<span data-ttu-id="13c98-141">O exemplo a seguir publica um aplicativo para o Windows como independente e corta a saída.</span><span class="sxs-lookup"><span data-stu-id="13c98-141">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

<span data-ttu-id="13c98-142">O exemplo a seguir publica um aplicativo no modo de corte agressivo em que o código não utilizado nos assemblies será cortado e os avisos de corte serão habilitados.</span><span class="sxs-lookup"><span data-stu-id="13c98-142">The following example publishes an app in the aggressive trim mode where unused code within assemblies will be trimmed and trimmer warnings enabled.</span></span>

```xml
<PropertyGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <PublishTrimmed>true</PublishTrimmed>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</PropertyGroup>
```

<span data-ttu-id="13c98-143">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-143">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="13c98-144">Cortar seu aplicativo-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="13c98-144">Trim your app - Visual Studio</span></span>

<span data-ttu-id="13c98-145">O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.</span><span class="sxs-lookup"><span data-stu-id="13c98-145">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="13c98-146">No painel **Gerenciador de soluções** , clique com o botão direito do mouse no projeto que você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="13c98-146">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="13c98-147">Selecione **publicar...** .</span><span class="sxs-lookup"><span data-stu-id="13c98-147">Select **Publish...** .</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

    <span data-ttu-id="13c98-149">Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino da **pasta** .</span><span class="sxs-lookup"><span data-stu-id="13c98-149">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="13c98-150">Escolha **Editar** .</span><span class="sxs-lookup"><span data-stu-id="13c98-150">Choose **Edit** .</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Perfil de publicação do Visual Studio com o botão Editar.":::

01. <span data-ttu-id="13c98-152">Na caixa de diálogo **configurações de perfil** , defina as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="13c98-152">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="13c98-153">Defina o **modo de implantação** **como autônomo** .</span><span class="sxs-lookup"><span data-stu-id="13c98-153">Set **Deployment mode** to **Self-contained** .</span></span>
    - <span data-ttu-id="13c98-154">Defina o **tempo de execução de destino** para a plataforma na qual você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="13c98-154">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="13c98-155">Selecione **aparar assemblies não utilizados (em visualização)** .</span><span class="sxs-lookup"><span data-stu-id="13c98-155">Select **Trim unused assemblies (in preview)** .</span></span>

    <span data-ttu-id="13c98-156">Escolha **salvar** para salvar as configurações e retornar para a caixa de diálogo de **publicação** .</span><span class="sxs-lookup"><span data-stu-id="13c98-156">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Caixa de diálogo Configurações de perfil com modo de implantação, tempo de execução de destino e opções de corte de assemblies não utilizados realçadas.":::

01. <span data-ttu-id="13c98-158">Escolha **publicar** para publicar seu aplicativo cortado.</span><span class="sxs-lookup"><span data-stu-id="13c98-158">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="13c98-159">Para obter mais informações, consulte [publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-159">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="13c98-160">Corte do seu aplicativo-Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="13c98-160">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="13c98-161">Visual Studio para Mac não fornece opções para cortar seu aplicativo durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="13c98-161">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="13c98-162">Você precisará publicar manualmente seguindo as instruções da seção [cortar sua app-CLI](#trim-your-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="13c98-162">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="13c98-163">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-163">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="13c98-164">Veja também</span><span class="sxs-lookup"><span data-stu-id="13c98-164">See also</span></span>

- <span data-ttu-id="13c98-165">[Implantação de aplicativo .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-165">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="13c98-166">[Publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-166">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="13c98-167">[Publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-167">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="13c98-168">[dotnet Publish comando](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="13c98-168">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
