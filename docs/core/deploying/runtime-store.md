---
title: Repositório de pacotes de runtime
description: Saiba como usar o repositório de pacotes de runtime para direcionar a manifestos usados pelo .NET Core.
ms.date: 08/12/2017
ms.openlocfilehash: 4395370c3bb2d97511d549a63813022fb8cac4b7
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158276"
---
# <a name="runtime-package-store"></a><span data-ttu-id="78c41-103">Repositório de pacotes de runtime</span><span class="sxs-lookup"><span data-stu-id="78c41-103">Runtime package store</span></span>

<span data-ttu-id="78c41-104">A partir do .NET Core 2.0, é possível empacotar e implantar aplicativos com relação a um conjunto conhecido de pacotes que existem no ambiente de destino.</span><span class="sxs-lookup"><span data-stu-id="78c41-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="78c41-105">Os benefícios são implantações mais rápidas, menor uso de espaço em disco e desempenho aprimorado de inicialização em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="78c41-105">The benefits are faster deployments, lower disk space usage, and improved startup performance in some cases.</span></span>

<span data-ttu-id="78c41-106">Esse recurso é implementado como um *repositório de pacotes de runtime*, que é um diretório em disco no qual os pacotes são armazenados (normalmente em */usr/local/share/dotnet/store* em macOS/Linux e *C:/Arquivos de Programas/dotnet/store* no Windows).</span><span class="sxs-lookup"><span data-stu-id="78c41-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="78c41-107">Nesse diretório, há subdiretórios para arquiteturas e [estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="78c41-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="78c41-108">O layout do arquivo é semelhante à maneira como os [ativos do NuGet são dispostos no disco](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="78c41-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

```
\dotnet
    \store
        \x64
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
        \x86
            \netcoreapp2.0
                \microsoft.applicationinsights
                \microsoft.aspnetcore
                ...
```

<span data-ttu-id="78c41-109">Um arquivo de *manifesto de destino* lista os pacotes no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="78c41-109">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="78c41-110">Os desenvolvedores podem direcionar esse manifesto ao publicar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="78c41-110">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="78c41-111">Normalmente, o manifesto de destino é fornecido pelo proprietário do ambiente de produção direcionado.</span><span class="sxs-lookup"><span data-stu-id="78c41-111">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="78c41-112">Preparação de um ambiente de runtime</span><span class="sxs-lookup"><span data-stu-id="78c41-112">Preparing a runtime environment</span></span>

<span data-ttu-id="78c41-113">O administrador de um ambiente de runtime pode otimizar aplicativos para oferecer implantações mais rápidas e menor uso do espaço em disco criando um repositório de pacotes de runtime e o manifesto de destino correspondente.</span><span class="sxs-lookup"><span data-stu-id="78c41-113">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="78c41-114">A primeira etapa é criar um *manifesto de repositório de pacotes* que lista os pacotes que compõem o repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="78c41-114">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="78c41-115">Esse formato de arquivo é compatível com o formato de arquivo de projeto (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="78c41-115">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="NUGET_PACKAGE" Version="VERSION" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="78c41-116">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="78c41-116">**Example**</span></span>

<span data-ttu-id="78c41-117">O exemplo do manifesto do repositório de pacotes a seguir (*packages.csproj*) é usado para adicionar [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) e [`Moq`](https://www.nuget.org/packages/moq/) a um repositório de pacotes de runtime:</span><span class="sxs-lookup"><span data-stu-id="78c41-117">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="78c41-118">Provisione o repositório de pacotes de runtime executando `dotnet store` com o manifesto, runtime e estrutura do repositório de pacotes:</span><span class="sxs-lookup"><span data-stu-id="78c41-118">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```dotnetcli
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="78c41-119">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="78c41-119">**Example**</span></span>

```dotnetcli
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="78c41-120">Você pode passar vários caminhos de manifesto do repositório de pacotes de [`dotnet store`](../tools/dotnet-store.md) destino para um único comando repetindo a opção e o caminho no comando.</span><span class="sxs-lookup"><span data-stu-id="78c41-120">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="78c41-121">Por padrão, a saída do comando é um repositório de pacotes no subdiretório *.dotnet/store* do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="78c41-121">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="78c41-122">É possível especificar um local diferente usando a opção `--output <OUTPUT_DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="78c41-122">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="78c41-123">O diretório raiz do repositório contém um arquivo de manifesto de destino *artifact.xml*.</span><span class="sxs-lookup"><span data-stu-id="78c41-123">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="78c41-124">Esse arquivo pode ser disponibilizado para download e ser usado por autores de aplicativos que desejam direcionar esse repositório durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="78c41-124">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="78c41-125">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="78c41-125">**Example**</span></span>

<span data-ttu-id="78c41-126">O arquivo *artifact.xml* a seguir é produzido depois de executar o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="78c41-126">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="78c41-127">Observe que [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) é uma dependência de `Moq`, portanto, é incluída automaticamente e aparece no arquivo de manifesto *artefatos. xml* .</span><span class="sxs-lookup"><span data-stu-id="78c41-127">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="78c41-128">Publicação de um aplicativo em um manifesto de destino</span><span class="sxs-lookup"><span data-stu-id="78c41-128">Publishing an app against a target manifest</span></span>

<span data-ttu-id="78c41-129">Se você tiver um arquivo de manifesto de destino em disco, especifique o caminho para o arquivo ao publicar seu aplicativo com [`dotnet publish`](../tools/dotnet-publish.md) o comando:</span><span class="sxs-lookup"><span data-stu-id="78c41-129">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```dotnetcli
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="78c41-130">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="78c41-130">**Example**</span></span>

```dotnetcli
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="78c41-131">Implante o aplicativo publicado resultante em um ambiente que tem os pacotes descritos no manifesto de destino.</span><span class="sxs-lookup"><span data-stu-id="78c41-131">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="78c41-132">Se isso não for feito, o aplicativo falhará ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="78c41-132">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="78c41-133">Especifique vários manifestos de destino ao publicar um aplicativo, repetindo a opção e o caminho (por exemplo, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="78c41-133">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="78c41-134">Quando você fizer isso, o aplicativo será cortado para a união de pacotes especificada nos arquivos de manifesto de destino fornecidos para o comando.</span><span class="sxs-lookup"><span data-stu-id="78c41-134">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

<span data-ttu-id="78c41-135">Se você implantar um aplicativo com uma dependência de manifesto presente na implantação (o assembly está presente na pasta *bin*), o repositório de pacotes de runtime *não será usado* no host desse assembly.</span><span class="sxs-lookup"><span data-stu-id="78c41-135">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="78c41-136">O assembly da pasta *bin* é usado, independentemente de sua presença no repositório de pacotes de runtime no host.</span><span class="sxs-lookup"><span data-stu-id="78c41-136">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="78c41-137">A versão da dependência indicada no manifesto deve corresponder à versão da dependência no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="78c41-137">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="78c41-138">Se você tiver uma incompatibilidade de versão entre a dependência no manifesto de destino e a versão que existe no repositório de pacotes de runtime e o aplicativo não incluir a versão necessária do pacote em sua implantação, a inicialização do aplicativo falhará.</span><span class="sxs-lookup"><span data-stu-id="78c41-138">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="78c41-139">A exceção inclui o nome do manifesto de destino chamado que chamou o assembly do repositório de pacotes de runtime, que ajuda você a solucionar problemas de incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="78c41-139">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="78c41-140">Quando a implantação é *cortada* na publicação, somente as versões específicas dos pacotes de manifesto indicadas são retidas na saída publicada.</span><span class="sxs-lookup"><span data-stu-id="78c41-140">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="78c41-141">Os pacotes nas versões indicadas devem estar presentes no host do aplicativo a ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="78c41-141">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="78c41-142">Especificação de manifestos de destino no arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="78c41-142">Specifying target manifests in the project file</span></span>

<span data-ttu-id="78c41-143">Uma alternativa para especificar os manifestos de destino [`dotnet publish`](../tools/dotnet-publish.md) com o comando é especificá-los no arquivo de projeto como uma lista de caminhos separados por ponto e vírgula em uma \*\* \<\*\* marca de>de TargetManifestFiles.</span><span class="sxs-lookup"><span data-stu-id="78c41-143">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="78c41-144">Especifique os manifestos de destino no arquivo de projeto somente quando o ambiente de destino para o aplicativo for bem conhecido, como para projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="78c41-144">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="78c41-145">Esse não é o caso para projetos de software livre.</span><span class="sxs-lookup"><span data-stu-id="78c41-145">This isn't the case for open-source projects.</span></span> <span data-ttu-id="78c41-146">Normalmente, os usuários de um projeto de software livre o implantam em diferentes ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="78c41-146">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="78c41-147">Geralmente, esses ambientes de produção têm diferentes conjuntos de pacotes pré-instalados.</span><span class="sxs-lookup"><span data-stu-id="78c41-147">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="78c41-148">Você não pode fazer suposições sobre o manifesto de destino em tais ambientes, portanto, você `--manifest` deve usar [`dotnet publish`](../tools/dotnet-publish.md)a opção de.</span><span class="sxs-lookup"><span data-stu-id="78c41-148">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store-net-core-20-only"></a><span data-ttu-id="78c41-149">ASP.NET Core repositório implícito (somente .NET Core 2,0)</span><span class="sxs-lookup"><span data-stu-id="78c41-149">ASP.NET Core implicit store (.NET Core 2.0 only)</span></span>

<span data-ttu-id="78c41-150">O repositório implícito do ASP.NET Core é aplicável apenas ao ASP.NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="78c41-150">The ASP.NET Core implicit store applies only to ASP.NET Core 2.0.</span></span> <span data-ttu-id="78c41-151">Recomendamos que os aplicativos usem o ASP.NET Core 2.1 e posterior, que **não** usa o repositório implícito.</span><span class="sxs-lookup"><span data-stu-id="78c41-151">We strongly recommend applications use ASP.NET Core 2.1 and later, which does **not** use the implicit store.</span></span> <span data-ttu-id="78c41-152">O ASP.NET Core 2.1 e posterior usam a estrutura compartilhada.</span><span class="sxs-lookup"><span data-stu-id="78c41-152">ASP.NET Core 2.1 and later use the shared framework.</span></span>

<span data-ttu-id="78c41-153">Para o .NET Core 2,0, o recurso de armazenamento de pacotes de tempo de execução é usado implicitamente por um aplicativo ASP.NET Core quando o aplicativo é implantado como um aplicativo de [implantação dependente de tempo de execução](index.md#publish-runtime-dependent) .</span><span class="sxs-lookup"><span data-stu-id="78c41-153">For .NET Core 2.0, the runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [runtime-dependent deployment](index.md#publish-runtime-dependent) app.</span></span> <span data-ttu-id="78c41-154">Os destinos no [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) incluem manifestos que fazem referência ao repositório de pacotes implícito no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="78c41-154">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="78c41-155">Além disso, qualquer aplicativo dependente de tempo de execução que `Microsoft.AspNetCore.All` dependa do pacote resulta em um aplicativo publicado que contém apenas o aplicativo e seus ativos, e não os `Microsoft.AspNetCore.All` pacotes listados no metapacote.</span><span class="sxs-lookup"><span data-stu-id="78c41-155">Additionally, any runtime-dependent app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="78c41-156">Pressupõe-se que esses pacotes estão presentes no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="78c41-156">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="78c41-157">O repositório de pacotes de runtime é instalado no host quando o SDK de .NET Core é instalado.</span><span class="sxs-lookup"><span data-stu-id="78c41-157">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="78c41-158">Talvez outros instaladores forneçam o repositório de pacotes de runtime, incluindo instalações Zip/tarball do SDK do .NET Core, `apt-get`, Red Hat Yum, o pacote de hospedagem do Windows Server do .NET Core e instalações manuais de repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="78c41-158">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="78c41-159">Ao implantar um aplicativo de [implantação dependente de tempo de execução](index.md#publish-runtime-dependent) , verifique se o ambiente de destino tem o SDK do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="78c41-159">When deploying a [runtime-dependent deployment](index.md#publish-runtime-dependent) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="78c41-160">Se o aplicativo for implantado em um ambiente que não inclui ASP.NET Core, você poderá recusar o repositório implícito especificando \*\* \<PublishWithAspNetCoreTargetManifest>\*\* definido como `false` no arquivo de projeto, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="78c41-160">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE]
> <span data-ttu-id="78c41-161">Para aplicativos de [implantação independentes](index.md#publish-self-contained) , supõe-se que o sistema de destino não contenha necessariamente os pacotes de manifesto necessários.</span><span class="sxs-lookup"><span data-stu-id="78c41-161">For [self-contained deployment](index.md#publish-self-contained) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="78c41-162">Portanto, \*\* \<PublishWithAspNetCoreTargetManifest>\*\* não pode ser definido `true` como para um aplicativo independente.</span><span class="sxs-lookup"><span data-stu-id="78c41-162">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an self-contained app.</span></span>

## <a name="see-also"></a><span data-ttu-id="78c41-163">Veja também</span><span class="sxs-lookup"><span data-stu-id="78c41-163">See also</span></span>

- [<span data-ttu-id="78c41-164">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="78c41-164">dotnet-publish</span></span>](../tools/dotnet-publish.md)
- [<span data-ttu-id="78c41-165">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="78c41-165">dotnet-store</span></span>](../tools/dotnet-store.md)
