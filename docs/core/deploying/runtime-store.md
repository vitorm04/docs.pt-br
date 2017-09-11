---
title: "Repositório de pacotes de tempo de execução"
description: "Este tópico explica o repositório de pacotes de tempo de execução e os manifestos de destino usados pelo .NET Core."
keywords: ".NET, .NET Core, dotnet store, repositório de pacotes de tempo de execução"
author: bleroy
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 9521d8b4-25fc-412b-a65b-4c975ebf6bfd
ms.translationtype: HT
ms.sourcegitcommit: 57e9a2b8aa952860a380b60c44fd2df16ef6463c
ms.openlocfilehash: e039190b49b35bd2675a175c6ff3631d6d344e4a
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="runtime-package-store"></a><span data-ttu-id="e5f04-104">Repositório de pacotes de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e5f04-104">Runtime package store</span></span>

<span data-ttu-id="e5f04-105">A partir do .NET Core 2.0, é possível empacotar e implantar aplicativos com relação a um conjunto conhecido de pacotes que existem no ambiente de destino.</span><span class="sxs-lookup"><span data-stu-id="e5f04-105">Starting with .NET Core 2.0, it's possible to package and deploy apps against a known set of packages that exist in the target environment.</span></span> <span data-ttu-id="e5f04-106">Os benefícios são implantações mais rápidas, menor uso de espaço em disco e desempenho aprimorado de inicialização em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="e5f04-106">The benefits are faster deployments, lower disk space use, and improved startup performance in some cases.</span></span>

<span data-ttu-id="e5f04-107">Esse recurso é implementado como um *repositório de pacotes de tempo de execução*, que é um diretório em disco no qual os pacotes são armazenados (normalmente em */usr/local/share/dotnet/store* em macOS/Linux e *C:/Arquivos de Programas/dotnet/store* no Windows).</span><span class="sxs-lookup"><span data-stu-id="e5f04-107">This feature is implemented as a *runtime package store*, which is a directory on disk where packages are stored (typically at */usr/local/share/dotnet/store* on macOS/Linux and *C:/Program Files/dotnet/store* on Windows).</span></span> <span data-ttu-id="e5f04-108">Nesse diretório, há subdiretórios para arquiteturas e [estruturas de destino](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="e5f04-108">Under this directory, there are subdirectories for architectures and [target frameworks](../../standard/frameworks.md).</span></span> <span data-ttu-id="e5f04-109">O layout do arquivo é semelhante à maneira como os [ativos do NuGet são dispostos no disco](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span><span class="sxs-lookup"><span data-stu-id="e5f04-109">The file layout is similar to the way that [NuGet assets are laid out on disk](/nuget/create-packages/supporting-multiple-target-frameworks#framework-version-folder-structure):</span></span>

<span data-ttu-id="e5f04-110">\dotnet</span><span class="sxs-lookup"><span data-stu-id="e5f04-110">\dotnet</span></span>   
<span data-ttu-id="e5f04-111">&nbsp;&nbsp;\store</span><span class="sxs-lookup"><span data-stu-id="e5f04-111">&nbsp;&nbsp;\store</span></span>   
<span data-ttu-id="e5f04-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span><span class="sxs-lookup"><span data-stu-id="e5f04-112">&nbsp;&nbsp;&nbsp;&nbsp;\x64</span></span>   
<span data-ttu-id="e5f04-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\net47</span><span class="sxs-lookup"><span data-stu-id="e5f04-113">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\net47</span></span>   
<span data-ttu-id="e5f04-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="e5f04-114">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="e5f04-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="e5f04-115">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="e5f04-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="e5f04-116">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="e5f04-117">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="e5f04-117">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="e5f04-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="e5f04-118">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="e5f04-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="e5f04-119">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="e5f04-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="e5f04-120">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="e5f04-121">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span><span class="sxs-lookup"><span data-stu-id="e5f04-121">&nbsp;&nbsp;&nbsp;&nbsp;\x86</span></span>   
<span data-ttu-id="e5f04-122">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\net47</span><span class="sxs-lookup"><span data-stu-id="e5f04-122">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\net47</span></span>   
<span data-ttu-id="e5f04-123">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="e5f04-123">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="e5f04-124">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="e5f04-124">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="e5f04-125">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="e5f04-125">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   
<span data-ttu-id="e5f04-126">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span><span class="sxs-lookup"><span data-stu-id="e5f04-126">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\netcoreapp2.0</span></span>   
<span data-ttu-id="e5f04-127">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span><span class="sxs-lookup"><span data-stu-id="e5f04-127">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.applicationinsights</span></span>   
<span data-ttu-id="e5f04-128">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span><span class="sxs-lookup"><span data-stu-id="e5f04-128">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\microsoft.aspnetcore</span></span>   
<span data-ttu-id="e5f04-129">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span><span class="sxs-lookup"><span data-stu-id="e5f04-129">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;...</span></span>   

<span data-ttu-id="e5f04-130">Um arquivo de *manifesto de destino* lista os pacotes no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5f04-130">A *target manifest* file lists the packages in the runtime package store.</span></span> <span data-ttu-id="e5f04-131">Os desenvolvedores podem direcionar esse manifesto ao publicar seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e5f04-131">Developers can target this manifest when publishing their app.</span></span> <span data-ttu-id="e5f04-132">Normalmente, o manifesto de destino é fornecido pelo proprietário do ambiente de produção direcionado.</span><span class="sxs-lookup"><span data-stu-id="e5f04-132">The target manifest is typically provided by the owner of the targeted production environment.</span></span>

## <a name="preparing-a-runtime-environment"></a><span data-ttu-id="e5f04-133">Preparação de um ambiente de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="e5f04-133">Preparing a runtime environment</span></span>

<span data-ttu-id="e5f04-134">O administrador de um ambiente de tempo de execução pode otimizar aplicativos para oferecer implantações mais rápidas e menor uso do espaço em disco criando um repositório de pacotes de tempo de execução e o manifesto de destino correspondente.</span><span class="sxs-lookup"><span data-stu-id="e5f04-134">The administrator of a runtime environment can optimize apps for faster deployments and lower disk space use by building a runtime package store and the corresponding target manifest.</span></span>

<span data-ttu-id="e5f04-135">A primeira etapa é criar um *manifesto de repositório de pacotes* que lista os pacotes que compõem o repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5f04-135">The first step is to create a *package store manifest* that lists the packages that compose the runtime package store.</span></span> <span data-ttu-id="e5f04-136">Esse formato de arquivo é compatível com o formato de arquivo de projeto (*csproj*).</span><span class="sxs-lookup"><span data-stu-id="e5f04-136">This file format is compatible with the project file format (*csproj*).</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="<NUGET_PACKAGE>" Version="<VERSION>" />
    <!-- Include additional packages here -->
  </ItemGroup>
</Project>
```

<span data-ttu-id="e5f04-137">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="e5f04-137">**Example**</span></span>

<span data-ttu-id="e5f04-138">O exemplo do manifesto do repositório de pacotes a seguir (*packages.csproj*) é usado para adicionar [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) e [`Moq`](https://www.nuget.org/packages/moq/) a um repositório de pacotes de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="e5f04-138">The following example package store manifest (*packages.csproj*) is used to add [`Newtonsoft.Json`](https://www.nuget.org/packages/Newtonsoft.Json/) and [`Moq`](https://www.nuget.org/packages/moq/) to a runtime package store:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <ItemGroup>
    <PackageReference Include="Newtonsoft.Json" Version="10.0.3" />
    <PackageReference Include="Moq" Version="4.7.63" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="e5f04-139">Provisione o repositório de pacotes de tempo de execução executando `dotnet store` com o manifesto, tempo de execução e estrutura do repositório de pacotes:</span><span class="sxs-lookup"><span data-stu-id="e5f04-139">Provision the runtime package store by executing `dotnet store` with the package store manifest, runtime, and framework:</span></span>

```console
dotnet store --manifest <PATH_TO_MANIFEST_FILE> --runtime <RUNTIME_IDENTIFIER> --framework <FRAMEWORK>
```

<span data-ttu-id="e5f04-140">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="e5f04-140">**Example**</span></span>

```console
dotnet store --manifest packages.csproj --runtime win10-x64 --framework netstandard2.0 --framework-version 2.0.0
```

<span data-ttu-id="e5f04-141">É possível passar vários caminhos de manifesto do repositório de pacotes de destino para um único comando [`dotnet store`](../tools/dotnet-store.md) repetindo a opção e o caminho no comando.</span><span class="sxs-lookup"><span data-stu-id="e5f04-141">You can pass multiple target package store manifest paths to a single [`dotnet store`](../tools/dotnet-store.md) command by repeating the option and path in the command.</span></span>

<span data-ttu-id="e5f04-142">Por padrão, a saída do comando é um repositório de pacotes no subdiretório *.dotnet/store* do perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="e5f04-142">By default, the output of the command is a package store under the *.dotnet/store* subdirectory of the user's profile.</span></span> <span data-ttu-id="e5f04-143">É possível especificar um local diferente usando a opção `--output <OUTPUT_DIRECTORY>`.</span><span class="sxs-lookup"><span data-stu-id="e5f04-143">You can specify a different location using the `--output <OUTPUT_DIRECTORY>` option.</span></span> <span data-ttu-id="e5f04-144">O diretório raiz do repositório contém um arquivo de manifesto de destino *artifact.xml*.</span><span class="sxs-lookup"><span data-stu-id="e5f04-144">The root directory of the store contains a target manifest *artifact.xml* file.</span></span> <span data-ttu-id="e5f04-145">Esse arquivo pode ser disponibilizado para download e ser usado por autores de aplicativos que desejam direcionar esse repositório durante a publicação.</span><span class="sxs-lookup"><span data-stu-id="e5f04-145">This file can be made available for download and be used by app authors who want to target this store when publishing.</span></span>

<span data-ttu-id="e5f04-146">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="e5f04-146">**Example**</span></span>

<span data-ttu-id="e5f04-147">O arquivo *artifact.xml* a seguir é produzido depois de executar o exemplo anterior.</span><span class="sxs-lookup"><span data-stu-id="e5f04-147">The following *artifact.xml* file is produced after running the previous example.</span></span> <span data-ttu-id="e5f04-148">Observe que [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) é uma dependência de `Moq`, portanto, está incluído automaticamente e é exibido no arquivo de manifesto *artifacts.xml*.</span><span class="sxs-lookup"><span data-stu-id="e5f04-148">Note that [`Castle.Core`](https://www.nuget.org/packages/Castle.Core/) is a dependency of `Moq`, so it's included automatically and appears in the *artifacts.xml* manifest file.</span></span>

```xml
<StoreArtifacts>
  <Package Id="newtonsoft.json" Version="10.0.3" />
  <Package Id="castle.core" Version="4.1.0" />
  <Package Id="moq" Version="4.7.63" />
</StoreArtifacts>
```

## <a name="publishing-an-app-against-a-target-manifest"></a><span data-ttu-id="e5f04-149">Publicação de um aplicativo em um manifesto de destino</span><span class="sxs-lookup"><span data-stu-id="e5f04-149">Publishing an app against a target manifest</span></span>

<span data-ttu-id="e5f04-150">Se você tiver um arquivo de manifesto de destino em disco, especifique o caminho para o arquivo ao publicar seu aplicativo com o comando [`dotnet publish`](../tools/dotnet-publish.md):</span><span class="sxs-lookup"><span data-stu-id="e5f04-150">If you have a target manifest file on disk, you specify the path to the file when publishing your app with the [`dotnet publish`](../tools/dotnet-publish.md) command:</span></span>

```console
dotnet publish --manifest <PATH_TO_MANIFEST_FILE>
```

<span data-ttu-id="e5f04-151">**Exemplo**</span><span class="sxs-lookup"><span data-stu-id="e5f04-151">**Example**</span></span>

```console
dotnet publish --manifest manifest.xml
```

<span data-ttu-id="e5f04-152">Implante o aplicativo publicado resultante em um ambiente que tem os pacotes descritos no manifesto de destino.</span><span class="sxs-lookup"><span data-stu-id="e5f04-152">You deploy the resulting published app to an environment that has the packages described in the target manifest.</span></span> <span data-ttu-id="e5f04-153">Se isso não for feito, o aplicativo falhará ao iniciar.</span><span class="sxs-lookup"><span data-stu-id="e5f04-153">Failing to do so results in the app failing to start.</span></span>

<span data-ttu-id="e5f04-154">Especifique vários manifestos de destino ao publicar um aplicativo, repetindo a opção e o caminho (por exemplo, `--manifest manifest1.xml --manifest manifest2.xml`).</span><span class="sxs-lookup"><span data-stu-id="e5f04-154">Specify multiple target manifests when publishing an app by repeating the option and path (for example, `--manifest manifest1.xml --manifest manifest2.xml`).</span></span> <span data-ttu-id="e5f04-155">Quando você fizer isso, o aplicativo será cortado para a união de pacotes especificada nos arquivos de manifesto de destino fornecidos para o comando.</span><span class="sxs-lookup"><span data-stu-id="e5f04-155">When you do so, the app is trimmed for the union of packages specified in the target manifest files provided to the command.</span></span>

## <a name="specifying-target-manifests-in-the-project-file"></a><span data-ttu-id="e5f04-156">Especificação de manifestos de destino no arquivo de projeto</span><span class="sxs-lookup"><span data-stu-id="e5f04-156">Specifying target manifests in the project file</span></span>

<span data-ttu-id="e5f04-157">Uma alternativa para especificar os manifestos de destino com o comando [`dotnet publish`](../tools/dotnet-publish.md) é especificá-los no arquivo de projeto como uma lista de caminhos separados por ponto-e-vírgula em uma marga **\<TargetManifestFiles>**.</span><span class="sxs-lookup"><span data-stu-id="e5f04-157">An alternative to specifying target manifests with the [`dotnet publish`](../tools/dotnet-publish.md) command is to specify them in the project file as a semicolon-separated list of paths under a **\<TargetManifestFiles>** tag.</span></span>

```xml
<PropertyGroup>
  <TargetManifestFiles>manifest1.xml;manifest2.xml</TargetManifestFiles>
</PropertyGroup>
```

<span data-ttu-id="e5f04-158">Especifique os manifestos de destino no arquivo de projeto somente quando o ambiente de destino para o aplicativo for bem conhecido, como para projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e5f04-158">Specify the target manifests in the project file only when the target environment for the app is well-known, such as for .NET Core projects.</span></span> <span data-ttu-id="e5f04-159">Esse não é o caso para projetos de software livre.</span><span class="sxs-lookup"><span data-stu-id="e5f04-159">This isn't the case for open-source projects.</span></span> <span data-ttu-id="e5f04-160">Normalmente, os usuários de um projeto de software livre o implantam em diferentes ambientes de produção.</span><span class="sxs-lookup"><span data-stu-id="e5f04-160">The users of an open-source project typically deploy it to different production environments.</span></span> <span data-ttu-id="e5f04-161">Geralmente, esses ambientes de produção têm diferentes conjuntos de pacotes pré-instalados.</span><span class="sxs-lookup"><span data-stu-id="e5f04-161">These production environments generally have different sets of packages pre-installed.</span></span> <span data-ttu-id="e5f04-162">Não é possível fazer suposições sobre o manifesto de destino nesses ambientes, então você deve usar a opção `--manifest` de [`dotnet publish`](../tools/dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="e5f04-162">You can't make assumptions about the target manifest in such environments, so you should use the `--manifest` option of [`dotnet publish`](../tools/dotnet-publish.md).</span></span>

## <a name="aspnet-core-implicit-store"></a><span data-ttu-id="e5f04-163">Repositório implícito do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5f04-163">ASP.NET Core implicit store</span></span>

<span data-ttu-id="e5f04-164">O recurso do repositório de pacotes de tempo de execução é usado implicitamente por um aplicativo ASP.NET Core quando o aplicativo é implantado como um aplicativo [FDD (implantação dependente da estrutura)](index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="e5f04-164">The runtime package store feature is used implicitly by an ASP.NET Core app when the app is deployed as a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app.</span></span> <span data-ttu-id="e5f04-165">Os destinos em [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) incluem manifestos que referenciam o repositório de pacotes implícito no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="e5f04-165">The targets in [`Microsoft.NET.Sdk.Web`](https://github.com/aspnet/websdk) include manifests referencing the implicit package store on the target system.</span></span> <span data-ttu-id="e5f04-166">Além disso, qualquer aplicativo FDD que dependa do pacote `Microsoft.AspNetCore.All` resulta em um aplicativo publicado que contém apenas o aplicativo e seus ativos e não os pacotes listados no metapackage `Microsoft.AspNetCore.All`.</span><span class="sxs-lookup"><span data-stu-id="e5f04-166">Additionally, any FDD app that depends on the `Microsoft.AspNetCore.All` package results in a published app that contains only the app and its assets and not the packages listed in the `Microsoft.AspNetCore.All` metapackage.</span></span> <span data-ttu-id="e5f04-167">Pressupõe-se que esses pacotes estão presentes no sistema de destino.</span><span class="sxs-lookup"><span data-stu-id="e5f04-167">It's assumed that those packages are present on the target system.</span></span>

<span data-ttu-id="e5f04-168">O repositório de pacotes de tempo de execução é instalado no host quando o SDK de .NET Core é instalado.</span><span class="sxs-lookup"><span data-stu-id="e5f04-168">The runtime package store is installed on the host when the .NET Core SDK is installed.</span></span> <span data-ttu-id="e5f04-169">Talvez outros instaladores forneçam o repositório de pacotes de tempo de execução, incluindo instalações Zip/tarball do SDK do .NET Core, `apt-get`, Red Hat Yum, o pacote de hospedagem do Windows Server do .NET Core e instalações manuais de repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5f04-169">Other installers may provide the runtime package store, including Zip/tarball installations of the .NET Core SDK, `apt-get`, Red Hat Yum, the .NET Core Windows Server Hosting bundle, and manual runtime package store installations.</span></span>

<span data-ttu-id="e5f04-170">Ao implantar um aplicativo [FDD (dependente da estrutura de implantação)](index.md#framework-dependent-deployments-fdd), certifique-se de que o ambiente de destino tem o SDK do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="e5f04-170">When deploying a [framework-dependent deployment (FDD)](index.md#framework-dependent-deployments-fdd) app, make sure that the target environment has the .NET Core SDK installed.</span></span> <span data-ttu-id="e5f04-171">Se o aplicativo for implantado em um ambiente que não inclui o ASP.NET Core, será possível recusar o repositório implícito especificando o conjunto **\<PublishWithAspNetCoreTargetManifest>** definido como `false` no arquivo de projeto como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="e5f04-171">If the app is deployed to an environment that doesn't include ASP.NET Core, you can opt out of the implicit store by specifying  **\<PublishWithAspNetCoreTargetManifest>** set to `false` in the project file as in the following example:</span></span>

```xml
<PropertyGroup>
  <PublishWithAspNetCoreTargetManifest>false</PublishWithAspNetCoreTargetManifest>
</PropertyGroup>
```

> [!NOTE] 
> <span data-ttu-id="e5f04-172">Para aplicativos [SCD (implantação autocontida)](index.md#self-contained-deployments-scd), pressupõe-se que o sistema de destino não contenha necessariamente os pacotes de manifesto necessários.</span><span class="sxs-lookup"><span data-stu-id="e5f04-172">For [self-contained deployment (SCD)](index.md#self-contained-deployments-scd) apps, it's assumed that the target system doesn't necessarily contain the required manifest packages.</span></span> <span data-ttu-id="e5f04-173">Portanto, **\<PublishWithAspNetCoreTargetManifest>** não pode ser definido como `true` para um aplicativo SCD.</span><span class="sxs-lookup"><span data-stu-id="e5f04-173">Therefore, **\<PublishWithAspNetCoreTargetManifest>** cannot be set to `true` for an SCD app.</span></span>

<span data-ttu-id="e5f04-174">Se você implantar um aplicativo com uma dependência de manifesto presente na implantação (o assembly está presente na pasta *bin*), o repositório de pacotes de tempo de execução *não será usado* no host desse assembly.</span><span class="sxs-lookup"><span data-stu-id="e5f04-174">If you deploy an application with a manifest dependency that's present in the deployment (the assembly is present in the *bin* folder), the runtime package store *isn't used* on the host for that assembly.</span></span> <span data-ttu-id="e5f04-175">O assembly da pasta *bin* é usado, independentemente de sua presença no repositório de pacotes de tempo de execução no host.</span><span class="sxs-lookup"><span data-stu-id="e5f04-175">The *bin* folder assembly is used regardless of its presence in the runtime package store on the host.</span></span>

<span data-ttu-id="e5f04-176">A versão da dependência indicada no manifesto deve corresponder à versão da dependência no repositório de pacotes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="e5f04-176">The version of the dependency indicated in the manifest must match the version of the dependency in the runtime package store.</span></span> <span data-ttu-id="e5f04-177">Se você tiver uma incompatibilidade de versão entre a dependência no manifesto de destino e a versão que existe no repositório de pacotes de tempo de execução e o aplicativo não incluir a versão necessária do pacote em sua implantação, a inicialização do aplicativo falhará.</span><span class="sxs-lookup"><span data-stu-id="e5f04-177">If you have a version mismatch between the dependency in the target manifest and the version that exists in the runtime package store and the app doesn't include the required version of the package in its deployment, the app fails to start.</span></span> <span data-ttu-id="e5f04-178">A exceção inclui o nome do manifesto de destino chamado que chamou o assembly do repositório de pacotes de tempo de execução, que ajuda você a solucionar problemas de incompatibilidade.</span><span class="sxs-lookup"><span data-stu-id="e5f04-178">The exception includes the name of the target manifest that called for the runtime package store assembly, which helps you troubleshoot the mismatch.</span></span>

<span data-ttu-id="e5f04-179">Quando a implantação é *cortada* na publicação, somente as versões específicas dos pacotes de manifesto indicadas são retidas na saída publicada.</span><span class="sxs-lookup"><span data-stu-id="e5f04-179">When the deployment is *trimmed* on publish, only the specific versions of the manifest packages you indicate are withheld from the published output.</span></span> <span data-ttu-id="e5f04-180">Os pacotes nas versões indicadas devem estar presentes no host do aplicativo a ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="e5f04-180">The packages at the versions indicated must be present on the host for the app to start.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5f04-181">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5f04-181">See also</span></span>
 <span data-ttu-id="e5f04-182">[dotnet-publish](../tools/dotnet-publish.md) </span><span class="sxs-lookup"><span data-stu-id="e5f04-182">[dotnet-publish](../tools/dotnet-publish.md) </span></span>  
 [<span data-ttu-id="e5f04-183">dotnet-store</span><span class="sxs-lookup"><span data-stu-id="e5f04-183">dotnet-store</span></span>](../tools/dotnet-store.md)   

