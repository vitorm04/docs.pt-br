---
title: Aparar aplicações independentes
description: Aprenda a aparar aplicativos autônomos para reduzir seu tamanho. O .NET Core empacota o tempo de execução com um aplicativo que é publicado independente mente e geralmente inclui mais tempo de execução do que é necessário.
author: jamshedd
ms.author: jamshedd
ms.date: 04/03/2020
ms.openlocfilehash: bb8ac88c5e16b7fd20a7670e4ad76dbe4b44da1b
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242888"
---
# <a name="trim-self-contained-deployments-and-executables"></a><span data-ttu-id="1130e-104">Cortar implantações e executáveis autossuficientes</span><span class="sxs-lookup"><span data-stu-id="1130e-104">Trim self-contained deployments and executables</span></span>

<span data-ttu-id="1130e-105">Ao publicar um aplicativo independente, o tempo de execução do .NET Core é empacotado com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1130e-105">When publishing an application self-contained, the .NET Core runtime is bundled together with the application.</span></span> <span data-ttu-id="1130e-106">Este agrupamento adiciona uma quantidade significativa de conteúdo ao seu aplicativo embalado.</span><span class="sxs-lookup"><span data-stu-id="1130e-106">This bundling adds a significant amount of content to your packaged application.</span></span> <span data-ttu-id="1130e-107">Quando se trata de implantar seu aplicativo, o tamanho muitas vezes é um fator importante.</span><span class="sxs-lookup"><span data-stu-id="1130e-107">When it comes to deploying your application, size is often an important factor.</span></span> <span data-ttu-id="1130e-108">Manter o tamanho do aplicativo do pacote o menor possível é tipicamente uma meta para os desenvolvedores de aplicativos.</span><span class="sxs-lookup"><span data-stu-id="1130e-108">Keeping the size of the package application as small as possible is typically a goal for application developers.</span></span>

<span data-ttu-id="1130e-109">Dependendo da complexidade do aplicativo, apenas um subconjunto do tempo de execução é necessário para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="1130e-109">Depending on the complexity of the application, only a subset of the runtime is required to run the application.</span></span> <span data-ttu-id="1130e-110">Estas partes não utilizadas do tempo de execução são desnecessárias e podem ser cortadas da aplicação embalada.</span><span class="sxs-lookup"><span data-stu-id="1130e-110">These unused parts of the runtime are unnecessary and can be trimmed from the packaged application.</span></span>

<span data-ttu-id="1130e-111">O recurso de corte funciona examinando os binários de aplicativos para descobrir e construir um gráfico dos conjuntos de tempo de execução necessários.</span><span class="sxs-lookup"><span data-stu-id="1130e-111">The trimming feature works by examining the application binaries to discover and build a graph of the required runtime assemblies.</span></span> <span data-ttu-id="1130e-112">As demais assembléias de tempo de execução que não são referenciadas são excluídas.</span><span class="sxs-lookup"><span data-stu-id="1130e-112">The remaining runtime assemblies that aren't referenced are excluded.</span></span>

> [!NOTE]
> <span data-ttu-id="1130e-113">Trimming é um recurso experimental no .NET Core 3.1 e _só_ está disponível para aplicativos que são publicados independentes.</span><span class="sxs-lookup"><span data-stu-id="1130e-113">Trimming is an experimental feature in .NET Core 3.1 and is _only_ available to applications that are published self-contained.</span></span>

## <a name="prevent-assemblies-from-being-trimmed"></a><span data-ttu-id="1130e-114">Evitar que as assembléias sejam aparadas</span><span class="sxs-lookup"><span data-stu-id="1130e-114">Prevent assemblies from being trimmed</span></span>

<span data-ttu-id="1130e-115">Existem cenários em que a funcionalidade de corte falhará em detectar referências.</span><span class="sxs-lookup"><span data-stu-id="1130e-115">There are scenarios in which the trimming functionality will fail to detect references.</span></span> <span data-ttu-id="1130e-116">Por exemplo, quando a reflexão é usada em um conjunto de tempo de execução, seja por sua aplicação ou por uma biblioteca referenciada pelo seu aplicativo, o conjunto não é diretamente referenciado.</span><span class="sxs-lookup"><span data-stu-id="1130e-116">For example, when reflection is used on a runtime assembly, either by your application or a library that is referenced by your application, the assembly isn't directly referenced.</span></span> <span data-ttu-id="1130e-117">O corte desconhece essas referências indiretas e excluiria a biblioteca da pasta publicada.</span><span class="sxs-lookup"><span data-stu-id="1130e-117">Trimming is unaware of these indirect references and would exclude the library from the published folder.</span></span>

<span data-ttu-id="1130e-118">Quando o código está indiretamente referenciando uma montagem através da reflexão, você pode impedir que a montagem seja aparada com a configuração. `<TrimmerRootAssembly>`</span><span class="sxs-lookup"><span data-stu-id="1130e-118">When the code is indirectly referencing an assembly through reflection, you can prevent the assembly from being trimmed with the `<TrimmerRootAssembly>` setting.</span></span> <span data-ttu-id="1130e-119">O exemplo a seguir mostra `System.Security` como evitar que uma assembléia chamada montagem seja aparada:</span><span class="sxs-lookup"><span data-stu-id="1130e-119">The following example shows how to prevent an assembly called `System.Security` assembly from being trimmed:</span></span>

```xml
<ItemGroup>
    <TrimmerRootAssembly Include="System.Security" />
</ItemGroup>
```

## <a name="trim-your-app---cli"></a><span data-ttu-id="1130e-120">Apare seu aplicativo - CLI</span><span class="sxs-lookup"><span data-stu-id="1130e-120">Trim your app - CLI</span></span>

<span data-ttu-id="1130e-121">Corte sua aplicação usando o comando [dotnet publish.](../tools/dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="1130e-121">Trim your application using the [dotnet publish](../tools/dotnet-publish.md) command.</span></span> <span data-ttu-id="1130e-122">Ao publicar seu aplicativo, defina as três configurações a seguir:</span><span class="sxs-lookup"><span data-stu-id="1130e-122">When you publish your app, set the following three settings:</span></span>

- <span data-ttu-id="1130e-123">Publicar como autônomo:`--self-contained true`</span><span class="sxs-lookup"><span data-stu-id="1130e-123">Publish as self-contained: `--self-contained true`</span></span>
- <span data-ttu-id="1130e-124">Desativar a publicação de arquivos únicos:`-p:PublishSingleFile=false`</span><span class="sxs-lookup"><span data-stu-id="1130e-124">Disable single-file publishing: `-p:PublishSingleFile=false`</span></span>
- <span data-ttu-id="1130e-125">Habilite o corte:`p:PublishTrimmed=true`</span><span class="sxs-lookup"><span data-stu-id="1130e-125">Enable trimming: `p:PublishTrimmed=true`</span></span>

<span data-ttu-id="1130e-126">O exemplo a seguir publica um aplicativo para windows 10 como autônomo e apara a saída.</span><span class="sxs-lookup"><span data-stu-id="1130e-126">The following example publishes an app for Windows 10 as self-contained and trims the output.</span></span>

```dotnetcli
dotnet publish -c Release -r win10-x64 --self-contained true -p:PublishSingleFile=false -p:PublishTrimmed=true
```

<span data-ttu-id="1130e-127">Para obter mais informações, consulte [Publicar os aplicativos .NET Core com .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-127">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="trim-your-app---visual-studio"></a><span data-ttu-id="1130e-128">Apare seu aplicativo - Visual Studio</span><span class="sxs-lookup"><span data-stu-id="1130e-128">Trim your app - Visual Studio</span></span>

<span data-ttu-id="1130e-129">O Visual Studio cria perfis de publicação reutilizáveis que controlam como seu aplicativo é publicado.</span><span class="sxs-lookup"><span data-stu-id="1130e-129">Visual Studio creates reusable publishing profiles that control how your application is published.</span></span>

01. <span data-ttu-id="1130e-130">No **painel Solution Explorer,** clique com o botão direito do mouse sobre o projeto que deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="1130e-130">On the **Solution Explorer** pane, right-click on the project you want to publish.</span></span> <span data-ttu-id="1130e-131">Selecione **Publicar...**.</span><span class="sxs-lookup"><span data-stu-id="1130e-131">Select **Publish...**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-solution-explorer.png" alt-text="Solution Explorer com um menu com o botão direito do mouse destacando a opção Publicar.":::

    <span data-ttu-id="1130e-133">Se você ainda não tiver um perfil de publicação, siga as instruções para criar um e escolha o tipo de destino **pasta.**</span><span class="sxs-lookup"><span data-stu-id="1130e-133">If you don't already have a publishing profile, follow the instructions to create one and choose the **Folder** target-type.</span></span>

01. <span data-ttu-id="1130e-134">Escolha **Editar**.</span><span class="sxs-lookup"><span data-stu-id="1130e-134">Choose **Edit**.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-edit-settings.png" alt-text="Visual studio publicar perfil com botão de edição.":::

01. <span data-ttu-id="1130e-136">Na caixa de diálogo **Configurações de** perfil, defina as seguintes opções:</span><span class="sxs-lookup"><span data-stu-id="1130e-136">In the **Profile settings** dialog, set the following options:</span></span>

    - <span data-ttu-id="1130e-137">Defina **o modo de implantação** como **autônomo**.</span><span class="sxs-lookup"><span data-stu-id="1130e-137">Set **Deployment mode** to **Self-contained**.</span></span>
    - <span data-ttu-id="1130e-138">Defina **o tempo de execução do Target** para a plataforma para a a que deseja publicar.</span><span class="sxs-lookup"><span data-stu-id="1130e-138">Set **Target runtime** to the platform you want to publish to.</span></span>
    - <span data-ttu-id="1130e-139">Selecione **Trim conjuntos não utilizados (na visualização)**.</span><span class="sxs-lookup"><span data-stu-id="1130e-139">Select **Trim unused assemblies (in preview)**.</span></span>

    <span data-ttu-id="1130e-140">Escolha **Salvar** para salvar as configurações e retornar à caixa de diálogo **Publicar.**</span><span class="sxs-lookup"><span data-stu-id="1130e-140">Choose **Save** to save the settings and return to the **Publish** dialog.</span></span>

    :::image type="content" source="media/trim-self-contained/visual-studio-publish-properties.png" alt-text="As configurações do perfil dialogam com o modo de implantação, o tempo de execução do destino e as opções de montagem não utilizadas destacadas.":::

01. <span data-ttu-id="1130e-142">Escolha **Publicar** para publicar seu aplicativo aparado.</span><span class="sxs-lookup"><span data-stu-id="1130e-142">Choose **Publish** to publish your app trimmed.</span></span>

<span data-ttu-id="1130e-143">Para obter mais informações, consulte [Publicar os aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-143">For more information, see [Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>

## <a name="trim-your-app---visual-studio-for-mac"></a><span data-ttu-id="1130e-144">Apare seu aplicativo - Visual Studio para Mac</span><span class="sxs-lookup"><span data-stu-id="1130e-144">Trim your app - Visual Studio for Mac</span></span>

<span data-ttu-id="1130e-145">Visual Studio para Mac não oferece opções para aparar seu aplicativo durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="1130e-145">Visual Studio for Mac doesn't provide options to trim your app during publish.</span></span> <span data-ttu-id="1130e-146">Você precisará publicar manualmente seguindo as instruções da [seção Trim your app - CLI.](#trim-your-app---cli)</span><span class="sxs-lookup"><span data-stu-id="1130e-146">You'll need to publish manually by following the instructions from the [Trim your app - CLI](#trim-your-app---cli) section.</span></span> <span data-ttu-id="1130e-147">Para obter mais informações, consulte [Publicar os aplicativos .NET Core com .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-147">For more information, see [Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1130e-148">Confira também</span><span class="sxs-lookup"><span data-stu-id="1130e-148">See also</span></span>

- <span data-ttu-id="1130e-149">[Implantação de aplicativo .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-149">[.NET Core application deployment](index.md).</span></span>
- <span data-ttu-id="1130e-150">[Publique os aplicativos .NET Core com .NET Core CLI](deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-150">[Publish .NET Core apps with .NET Core CLI](deploy-with-cli.md).</span></span>
- <span data-ttu-id="1130e-151">[Publique os aplicativos .NET Core com o Visual Studio](deploy-with-vs.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-151">[Publish .NET Core apps with Visual Studio](deploy-with-vs.md).</span></span>
- <span data-ttu-id="1130e-152">[comando dotnet publicar](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="1130e-152">[dotnet publish command](../tools/dotnet-publish.md).</span></span>
