---
title: Cortar aplicativos independentes
description: Saiba como cortar aplicativos independentes para reduzir seu tamanho. O .NET Core agrupa o tempo de execução com um aplicativo que é publicado de forma independente e, em geral, inclui mais do tempo de execução e, em seguida, é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: 2bb0f03994468bbad3096ebf0b141bc1f47b867e
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656710"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="6c0db-104">Cortar implantações e executáveis autossuficientes</span><span class="sxs-lookup"><span data-stu-id="6c0db-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="6c0db-105">O [modelo de implantação dependente de estrutura](index.md#publish-framework-dependent) foi o modelo de implantação mais bem-sucedido desde o início do .net.</span><span class="sxs-lookup"><span data-stu-id="6c0db-105">The [framework-dependent deployment model](index.md#publish-framework-dependent) has been the most successful deployment model since the inception of .NET.</span></span> <span data-ttu-id="6c0db-106">Nesse cenário, o desenvolvedor de aplicativos agrupa apenas o aplicativo e os assemblies de terceiros, com a expectativa de que as bibliotecas de tempo de execução .NET e estrutura estarão disponíveis no computador cliente.</span><span class="sxs-lookup"><span data-stu-id="6c0db-106">In this scenario, the application developer bundles only the application and third-party assemblies with the expectation that the .NET runtime and framework libraries will be available in the client machine.</span></span> <span data-ttu-id="6c0db-107">Esse modelo de implantação continua sendo o dominante no .NET Core, mas há alguns cenários em que o modelo dependente de estrutura não é o ideal.</span><span class="sxs-lookup"><span data-stu-id="6c0db-107">This deployment model continues to be the dominant one in .NET Core as well but there are some scenarios where the framework-dependent model is not optimal.</span></span> <span data-ttu-id="6c0db-108">A alternativa é publicar um [aplicativo](index.md#publish-self-contained)independente, em que o tempo de execução e a estrutura do .NET Core são agrupados com o aplicativo e com assemblies de terceiros.</span><span class="sxs-lookup"><span data-stu-id="6c0db-108">The alternative is to publish a [self-contained application](index.md#publish-self-contained), where the .NET Core runtime and framework are bundled together with the application and third-party assemblies.</span></span>

<span data-ttu-id="6c0db-109">O modelo de implantação de preparo – autocontido é uma versão especializada do modelo de implantação independente que é otimizado para reduzir o tamanho da implantação.</span><span class="sxs-lookup"><span data-stu-id="6c0db-109">The trim-self-contained deployment model is a specialized version of the self-contained deployment model that is optimized to reduce deployment size.</span></span> <span data-ttu-id="6c0db-110">Minimizar o tamanho da implantação é um requisito crítico para alguns cenários do lado do cliente, como aplicativos mais Incrivelmenteos.</span><span class="sxs-lookup"><span data-stu-id="6c0db-110">Minimizing deployment size is a critical requirement for some client-side scenarios like Blazor applications.</span></span> <span data-ttu-id="6c0db-111">Dependendo da complexidade do aplicativo, apenas um subconjunto dos assemblies do Framework é necessário para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c0db-111">Depending on the complexity of the application, only a subset of the framework assemblies are required to run the application.</span></span> <span data-ttu-id="6c0db-112">Essas partes não utilizadas da biblioteca são desnecessárias e podem ser cortadas do aplicativo empacotado.</span><span class="sxs-lookup"><span data-stu-id="6c0db-112">These unused parts of the library are unnecessary and can be trimmed from the packaged application.</span></span> <span data-ttu-id="6c0db-113">No entanto, há um risco de que a análise de tempo de compilação do aplicativo possa causar falhas em tempo de execução, devido ao fato de não poder analisar de maneira confiável vários padrões de código problemáticos (amplamente centrados no uso de reflexão).</span><span class="sxs-lookup"><span data-stu-id="6c0db-113">However, there is a risk that the build time analysis of the application can cause failures at runtime, due to not being able to reliably analyze various problematic code patterns (largely centered on reflection use).</span></span> <span data-ttu-id="6c0db-114">Como a confiabilidade não pode ser garantida, esse modelo de implantação é oferecido como um recurso de visualização.</span><span class="sxs-lookup"><span data-stu-id="6c0db-114">Because reliability can't be guaranteed, this deployment model is offered as a preview feature.</span></span> <span data-ttu-id="6c0db-115">O mecanismo de análise de tempo de compilação fornece avisos ao desenvolvedor de padrões de código que são problemáticos, com a expectativa de que esses padrões de código sejam corrigidos.</span><span class="sxs-lookup"><span data-stu-id="6c0db-115">The build time analysis engine provides warnings to the developer of code patterns that are problematic, with the expectation that these code patterns will be fixed.</span></span> <span data-ttu-id="6c0db-116">Sempre que possível, recomendamos que você mova qualquer dependência de reflexão de tempo de execução em seu aplicativo para compilar o tempo usando código que atenda aos mesmos requisitos.</span><span class="sxs-lookup"><span data-stu-id="6c0db-116">Where possible, we recommend that you move any runtime reflection dependencies in your application to build time by using code that meets the same requirements.</span></span>

<span data-ttu-id="6c0db-117">O modo de corte para os aplicativos pode ser configurado por meio do TRIMMODE e será padrão ( `copyused` ) para agrupar assemblies que são usados no aplicativo.</span><span class="sxs-lookup"><span data-stu-id="6c0db-117">The trim mode for the applications can be configured via the TrimMode and will default (`copyused`) to bundle assemblies that are used in the application.</span></span> <span data-ttu-id="6c0db-118">Os aplicativos Webassembly mais atraentes usarão um modo mais agressivo ( `link` ) que cortará o código não utilizado dentro de assemblies.</span><span class="sxs-lookup"><span data-stu-id="6c0db-118">Blazor WebAssembly applications will use a more aggressive mode (`link`) that will trim unused code within assemblies.</span></span> <span data-ttu-id="6c0db-119">Avisos de análise de corte fornecem informações sobre padrões de código em que uma análise de dependência completa não era possível.</span><span class="sxs-lookup"><span data-stu-id="6c0db-119">Trim analysis warnings give information on code patterns where a full dependency analysis was not possible.</span></span> <span data-ttu-id="6c0db-120">Esses avisos são suprimidos por padrão e podem ser ativados definindo o sinalizador, `SuppressTrimAnalysisWarnings` , para false.</span><span class="sxs-lookup"><span data-stu-id="6c0db-120">These warnings are suppressed by default and can be turned on by setting the flag, `SuppressTrimAnalysisWarnings`, to false.</span></span> <span data-ttu-id="6c0db-121">Mais informações sobre as opções de corte disponíveis podem ser encontradas na [página ILLinker](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-121">More information on the trim options available can be found at the [ILLinker page](https://github.com/mono/linker/blob/master/docs/illink-options.md).</span></span>

> [!NOTE]
> <span data-ttu-id="6c0db-122">O corte é um recurso experimental no .NET Core 3,1, 5,0 e está disponível _somente_ para aplicativos que são publicados internamente.</span><span class="sxs-lookup"><span data-stu-id="6c0db-122">Trimming is an experimental feature in .NET Core 3.1, 5.0 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="6c0db-123">Impedir que os assemblies sejam cortados</span><span class="sxs-lookup"><span data-stu-id="6c0db-123">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="6c0db-124">Há cenários em que a funcionalidade de corte falhará ao detectar referências.</span><span class="sxs-lookup"><span data-stu-id="6c0db-124">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="6c0db-125">Por exemplo, quando a reflexão é usada em um assembly de tempo de execução, seja pelo aplicativo ou por uma biblioteca que é referenciada pelo seu aplicativo, o assembly não é referenciado diretamente.</span><span class="sxs-lookup"><span data-stu-id="6c0db-125">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="6c0db-126">O corte não reconhece essas referências indiretas e excluiria a biblioteca da pasta publicada.</span><span class="sxs-lookup"><span data-stu-id="6c0db-126">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="6c0db-127">Quando o código está indiretamente referenciando um assembly por meio de reflexão, você pode impedir que o assembly seja cortado com a `<TrimmerRootAssembly>` configuração.</span><span class="sxs-lookup"><span data-stu-id="6c0db-127">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="6c0db-128">O exemplo a seguir mostra como impedir que um assembly chamado `System.Security` assembly seja cortado:</span><span class="sxs-lookup"><span data-stu-id="6c0db-128">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="6c0db-129">Cortar sua app-CLI</span><span class="sxs-lookup"><span data-stu-id="6c0db-129">Trim your app - CLI</span></span>

<span data-ttu-id="6c0db-130">Corte seu aplicativo usando o comando [dotnet Publish](../tools/dotnet-publish.md) .</span><span class="sxs-lookup"><span data-stu-id="6c0db-130">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="6c0db-131">Ao publicar seu aplicativo, defina as três configurações a seguir:</span><span class="sxs-lookup"><span data-stu-id="6c0db-131">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="6c0db-132">Publicar como independente: `--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="6c0db-132">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="6c0db-133">Habilitar corte: `p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="6c0db-133">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="6c0db-134">O exemplo a seguir publica um aplicativo para o Windows como independente e corta a saída.</span><span class="sxs-lookup"><span data-stu-id="6c0db-134">The following example publishes an app for Windows as self-contained and trims the output.</span></span>

```xml
<ItemGroup>
    <RuntimeIdentifier>win-x64</RuntimeIdentifier>
    <SelfContained>true</SelfContained>
    <PublishTrimmed>true</PublishTrimmed>
</ItemGroup>
```

<span data-ttu-id="6c0db-135">O exemplo a seguir publica um aplicativo no modo de corte agressivo em que o código não utilizado com assemblies será cortado e os avisos de corte estão habilitados.</span><span class="sxs-lookup"><span data-stu-id="6c0db-135">The following example publishes an app in the aggressive trim mode where unused code withing assemblies will be trimmed and  trimmer warnings enabled.</span></span>

```xml
<ItemGroup>
    <TrimMode>link</TrimMode>
    <SuppressTrimAnalysisWarnings>false</SuppressTrimAnalysisWarnings>
</ItemGroup>
```

<span data-ttu-id="6c0db-136">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-136">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="6c0db-137">Cortar seu aplicativo-Visual Studio</span><span class="sxs-lookup"><span data-stu-id="6c0db-137">Trim your app - Visual Studio</span></span>

<span data-ttu-id="6c0db-138">O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.</span><span class="sxs-lookup"><span data-stu-id="6c0db-138">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="6c0db-139">No painel **Gerenciador de soluções** , clique com o botão direito do mouse no projeto que você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="6c0db-139">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="6c0db-140">Selecione **publicar...**.</span><span class="sxs-lookup"><span data-stu-id="6c0db-140">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Gerenciador de Soluções com um menu de clique com o botão direito do mouse, realçando a opção publicar.":::

    <span data-ttu-id="6c0db-142">Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino da **pasta** .</span><span class="sxs-lookup"><span data-stu-id="6c0db-142">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="6c0db-143">Escolha **Editar**.</span><span class="sxs-lookup"><span data-stu-id="6c0db-143">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Perfil de publicação do Visual Studio com o botão Editar.":::

01. <span data-ttu-id="6c0db-145">Na caixa de diálogo **configurações de perfil** , defina as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="6c0db-145">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="6c0db-146">Defina o **modo de implantação** **como autônomo**.</span><span class="sxs-lookup"><span data-stu-id="6c0db-146">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="6c0db-147">Defina o **tempo de execução de destino** para a plataforma na qual você deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="6c0db-147">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="6c0db-148">Selecione **aparar assemblies não utilizados (em visualização)**.</span><span class="sxs-lookup"><span data-stu-id="6c0db-148">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="6c0db-149">Escolha **salvar** para salvar as configurações e retornar para a caixa de diálogo de **publicação** .</span><span class="sxs-lookup"><span data-stu-id="6c0db-149">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="Caixa de diálogo Configurações de perfil com modo de implantação, tempo de execução de destino e opções de corte de assemblies não utilizados realçadas.":::

01. <span data-ttu-id="6c0db-151">Escolha **publicar** para publicar seu aplicativo cortado.</span><span class="sxs-lookup"><span data-stu-id="6c0db-151">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="6c0db-152">Para obter mais informações, consulte [publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-152">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="6c0db-153">Corte do seu aplicativo-Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="6c0db-153">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="6c0db-154">Visual Studio para Mac não fornece opções para cortar seu aplicativo durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="6c0db-154">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="6c0db-155">Você precisará publicar manualmente seguindo as instruções da seção [cortar sua app-CLI](#trim-your-app---cli) .</span><span class="sxs-lookup"><span data-stu-id="6c0db-155">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="6c0db-156">Para obter mais informações, consulte [publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-156">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6c0db-157">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6c0db-157">See also</span></span>

- <span data-ttu-id="6c0db-158">[Implantação de aplicativo .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-158">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="6c0db-159">[Publicar aplicativos .NET Core com CLI do .NET Core](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-159">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="6c0db-160">[Publicar aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-160">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="6c0db-161">[dotnet Publish comando](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="6c0db-161">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
