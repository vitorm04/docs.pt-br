---
title: Repositório de pacotes de tempo de execução
description: Este tópico explica o repositório de pacotes de tempo de execução e os manifestos de destino usados pelo .NET Core.
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 8fa3d309b16bd0c3b2b872f6447b7e99956abd81
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="runtime-package-store"></a><span data-ttu-id="173f1-103">Repositório de pacotes de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="173f1-103">Runtime package store</span></span>

<span data-ttu-id="173f1-104">A partir do .NET Core 2.0, é possível empacotar e implantar aplicativos com relação a um conjunto conhecido de pacotes que existem no ambiente de destino.</span><span class="sxs-lookup"><span data-stu-id="173f1-104">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="173f1-105">Os benefícios são implantações mais rápidas, menor uso de espaço em disco e desempenho aprimorado de inicialização em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="173f1-105">The benefits are faster deployments, lower disk space use, and improved startup performance in some cases.</span></span>

<span data-ttu-id="173f1-106">Esse recurso é implementado como um *repositório de pacotes de tempo de execução*, que é um diretório em disco no qual os pacotes são armazenados (normalmente em */usr/local/share/dotnet/store* em macOS/Linux e *C:/Arquivos de Programas/dotnet/store* no Windows).</span><span class="sxs-lookup"><span data-stu-id="173f1-106">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="173f1-107">Nesse diretório, há subdiretórios para arquiteturas e [estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="173f1-107">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="173f1-108">O layout do arquivo é semelhante à maneira como os [ativos do NuGet são dispostos no disco](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="173f1-108">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

<span data-ttu-id="173f1-109">\dotnet</span><span class="sxs-lookup"><span data-stu-id="173f1-109">\dotnet</span></span>   
<span data-ttu-id="173f1-110">&nbsp;&nbsp;\store</span><span class="sxs-lookup"><span data-stu-id="173f1-110">&nbsp;&nbsp;\store</span></span>   
<span data-ttu-id="173f1-111">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span><span class="sxs-lookup"><span data-stu-id="173f1-111">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span></span>   
<span data-ttu-id="173f1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="173f1-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="173f1-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="173f1-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="173f1-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="173f1-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="173f1-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="173f1-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="173f1-116">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span><span class="sxs-lookup"><span data-stu-id="173f1-116">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span></span>   
<span data-ttu-id="173f1-117">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="173f1-117">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="173f1-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="173f1-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="173f1-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="173f1-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="173f1-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="173f1-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   

<span data-ttu-id="173f1-121">Um arquivo de *manifesto de destino* lista os pacotes no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="173f1-121">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="173f1-122">Os desenvolvedores podem direcionar esse manifesto ao publicar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="173f1-122">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="173f1-123">Normalmente, o manifesto de destino é fornecido pelo proprietário do ambiente de produção direcionado.</span><span class="sxs-lookup"><span data-stu-id="173f1-123">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="173f1-124">Preparação de um ambiente de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="173f1-124">Preparing a runtime environment</span></span>

<span data-ttu-id="173f1-125">O administrador de um ambiente de tempo de execução pode otimizar aplicativos para oferecer implantações mais rápidas e menor uso do espaço em disco criando um repositório de pacotes de tempo de execução e o manifesto de destino correspondente.</span><span class="sxs-lookup"><span data-stu-id="173f1-125">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="173f1-126">A primeira etapa é criar um *manifesto de repositório de pacotes* que lista os pacotes que compõem o repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="173f1-126">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="173f1-127">Esse formato de arquivo é compatível com o formato de arquivo de projeto (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="173f1-127">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="173f1-128">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="173f1-128">**Example**</span></span>

<span data-ttu-id="173f1-129">O exemplo do manifesto do repositório de pacotes a seguir (*packages.csproj*) é usado para adicionar [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) e [`Moq`](https://www.nuget.org/packages/moq/) a um repositório de pacotes de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="173f1-129">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="173f1-130">Provisione o repositório de pacotes de tempo de execução executando `dotnet store` com o manifesto, tempo de execução e estrutura do repositório de pacotes:</span><span class="sxs-lookup"><span data-stu-id="173f1-130">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="173f1-131">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="173f1-131">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netcoreapp2.0 --framework-version 2.0.0
```

<span data-ttu-id="173f1-132">É possível passar vários caminhos de manifesto do repositório de pacotes de destino para um único comando [`dotnet store`](../tools/dotnet-store.md) repetindo a opção e o caminho no comando.</span><span class="sxs-lookup"><span data-stu-id="173f1-132">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="173f1-133">Por padrão, a saída do comando é um repositório de pacotes no subdiretório *.dotnet/store* do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="173f1-133">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="173f1-134">É possível especificar um local diferente usando a opção `--output <OUTPUT_DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="173f1-134">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="173f1-135">O diretório raiz do repositório contém um arquivo de manifesto de destino *artifact.xml*.</span><span class="sxs-lookup"><span data-stu-id="173f1-135">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="173f1-136">Esse arquivo pode ser disponibilizado para download e ser usado por autores de aplicativos que desejam direcionar esse repositório durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="173f1-136">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="173f1-137">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="173f1-137">**Example**</span></span>

<span data-ttu-id="173f1-138">O arquivo *artifact.xml* a seguir é produzido depois de executar o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="173f1-138">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="173f1-139">Observe que [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) é uma dependência de `Moq`, portanto, está incluído automaticamente e é exibido no arquivo de manifesto *artifacts.xml*.</span><span class="sxs-lookup"><span data-stu-id="173f1-139">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="Newtonsoft.Json" Version="10.0.3" />
  <Package Id="Castle.Core" Version="4.1.0" />
  <Package Id="Moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="173f1-140">Publicação de um aplicativo em um manifesto de destino</span><span class="sxs-lookup"><span data-stu-id="173f1-140">Publishing an app against a target manifest</span></span>

<span data-ttu-id="173f1-141">Se você tiver um arquivo de manifesto de destino em disco, especifique o caminho para o arquivo ao publicar seu aplicativo com o comando [`dotnet publish`](../tools/dotnet-publish.md):</span><span class="sxs-lookup"><span data-stu-id="173f1-141">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="173f1-142">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="173f1-142">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="173f1-143">Implante o aplicativo publicado resultante em um ambiente que tem os pacotes descritos no manifesto de destino.</span><span class="sxs-lookup"><span data-stu-id="173f1-143">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="173f1-144">Se isso não for feito, o aplicativo falhará ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="173f1-144">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="173f1-145">Especifique vários manifestos de destino ao publicar um aplicativo, repetindo a opção e o caminho (por exemplo, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="173f1-145">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="173f1-146">Quando você fizer isso, o aplicativo será cortado para a união de pacotes especificada nos arquivos de manifesto de destino fornecidos para o comando.</span><span class="sxs-lookup"><span data-stu-id="173f1-146">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="173f1-147">Especificação de manifestos de destino no arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="173f1-147">Specifying target manifests in the project file</span></span>

<span data-ttu-id="173f1-148">Uma alternativa para especificar os manifestos de destino com o comando [`dotnet publish`](../tools/dotnet-publish.md) é especificá-los no arquivo de projeto como uma lista de caminhos separados por ponto-e-vírgula em uma marga **\<TargetManifestFiles>**.</span><span class="sxs-lookup"><span data-stu-id="173f1-148">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="173f1-149">Especifique os manifestos de destino no arquivo de projeto somente quando o ambiente de destino para o aplicativo for bem conhecido, como para projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="173f1-149">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="173f1-150">Esse não é o caso para projetos de software livre.</span><span class="sxs-lookup"><span data-stu-id="173f1-150">This isn't the case for open-source projects.</span></span> <span data-ttu-id="173f1-151">Normalmente, os usuários de um projeto de software livre o implantam em diferentes ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="173f1-151">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="173f1-152">Geralmente, esses ambientes de produção têm diferentes conjuntos de pacotes pré-instalados.</span><span class="sxs-lookup"><span data-stu-id="173f1-152">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="173f1-153">Não é possível fazer suposições sobre o manifesto de destino nesses ambientes, então você deve usar a opção `--manifest` de [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="173f1-153">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="173f1-154">Repositório implícito do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="173f1-154">ASP.NET Core implicit store</span></span>

<span data-ttu-id="173f1-155">O recurso do repositório de pacotes de tempo de execução é usado implicitamente por um aplicativo ASP.NET Core quando o aplicativo é implantado como um aplicativo [FDD (implantação dependente da estrutura)](index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="173f1-155">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="173f1-156">Os destinos em [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) incluem manifestos que referenciam o repositório de pacotes implícito no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="173f1-156">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="173f1-157">Além disso, qualquer aplicativo FDD que dependa do pacote `Microsoft.AspNetCore.All` resulta em um aplicativo publicado que contém apenas o aplicativo e seus ativos e não os pacotes listados no metapackage `Microsoft.AspNetCore.All`.</span><span class="sxs-lookup"><span data-stu-id="173f1-157">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="173f1-158">Pressupõe-se que esses pacotes estão presentes no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="173f1-158">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="173f1-159">O repositório de pacotes de tempo de execução é instalado no host quando o SDK de .NET Core é instalado.</span><span class="sxs-lookup"><span data-stu-id="173f1-159">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="173f1-160">Talvez outros instaladores forneçam o repositório de pacotes de tempo de execução, incluindo instalações Zip/tarball do SDK do .NET Core, `apt-get`, Red Hat Yum, o pacote de hospedagem do Windows Server do .NET Core e instalações manuais de repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="173f1-160">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="173f1-161">Ao implantar um aplicativo [FDD (dependente da estrutura de implantação)](index.md#framework-dependent-deployments-fdd), certifique-se de que o ambiente de destino tem o SDK do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="173f1-161">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="173f1-162">Se o aplicativo for implantado em um ambiente que não inclui o ASP.NET Core, será possível recusar o repositório implícito especificando o conjunto **\<PublishWithAspNetCoreTargetManifest>** definido como `false` no arquivo de projeto como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="173f1-162">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> <span data-ttu-id="173f1-163">Para aplicativos [SCD (implantação autocontida)](index.md#self-contained-deployments-scd), pressupõe-se que o sistema de destino não contenha necessariamente os pacotes de manifesto necessários.</span><span class="sxs-lookup"><span data-stu-id="173f1-163">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="173f1-164">Portanto, **\<PublishWithAspNetCoreTargetManifest>** não pode ser definido como `true` para um aplicativo SCD.</span><span class="sxs-lookup"><span data-stu-id="173f1-164">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="173f1-165">Se você implantar um aplicativo com uma dependência de manifesto presente na implantação (o assembly está presente na pasta *bin*), o repositório de pacotes de tempo de execução *não será usado* no host desse assembly.</span><span class="sxs-lookup"><span data-stu-id="173f1-165">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="173f1-166">O assembly da pasta *bin* é usado, independentemente de sua presença no repositório de pacotes de tempo de execução no host.</span><span class="sxs-lookup"><span data-stu-id="173f1-166">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="173f1-167">A versão da dependência indicada no manifesto deve corresponder à versão da dependência no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="173f1-167">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="173f1-168">Se você tiver uma incompatibilidade de versão entre a dependência no manifesto de destino e a versão que existe no repositório de pacotes de tempo de execução e o aplicativo não incluir a versão necessária do pacote em sua implantação, a inicialização do aplicativo falhará.</span><span class="sxs-lookup"><span data-stu-id="173f1-168">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="173f1-169">A exceção inclui o nome do manifesto de destino chamado que chamou o assembly do repositório de pacotes de tempo de execução, que ajuda você a solucionar problemas de incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="173f1-169">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="173f1-170">Quando a implantação é *cortada* na publicação, somente as versões específicas dos pacotes de manifesto indicadas são retidas na saída publicada.</span><span class="sxs-lookup"><span data-stu-id="173f1-170">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="173f1-171">Os pacotes nas versões indicadas devem estar presentes no host do aplicativo a ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="173f1-171">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="173f1-172">Consulte também</span><span class="sxs-lookup"><span data-stu-id="173f1-172">See also</span></span>
 [<span data-ttu-id="173f1-173">dotnet-publish</span><span class="sxs-lookup"><span data-stu-id="173f1-173">dotnet-publish</span></span>](../tools/dotnet-publish.md)  
 [<span data-ttu-id="173f1-174">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="173f1-174">dotnet-store</span></span>](../tools/dotnet-store.md)  
