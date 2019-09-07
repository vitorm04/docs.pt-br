---
title: Pacote de distribuição do .NET Core
description: Aprenda a empacotar, nomear e controlar a versão do .NET Core para distribuição.
author: tmds
ms.date: 03/02/2018
ms.custom: seodec18
ms.openlocfilehash: d72677cba1e7685f8e05cf479ec508683dd77b55
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70394154"
---
# <a name="net-core-distribution-packaging"></a><span data-ttu-id="8e4c2-103">Pacote de distribuição do .NET Core</span><span class="sxs-lookup"><span data-stu-id="8e4c2-103">.NET Core distribution packaging</span></span>

<span data-ttu-id="8e4c2-104">À medida que o .NET Core fica disponível em mais plataformas, é muito útil saber como empacotar, nomear e controlar a versão dele.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-104">As .NET Core becomes available on more and more platforms, it's useful to learn how to package, name, and version it.</span></span> <span data-ttu-id="8e4c2-105">Dessa forma, os mantenedores do pacote podem ajudar a garantir uma experiência consistente, independentemente de onde os usuários escolhem executar o .NET.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-105">This way, package maintainers can help ensure a consistent experience no matter where users choose to run .NET.</span></span> <span data-ttu-id="8e4c2-106">Este artigo é útil para usuários que estão:</span><span class="sxs-lookup"><span data-stu-id="8e4c2-106">This article is useful for users that are:</span></span>

- <span data-ttu-id="8e4c2-107">Tentando criar o .NET Core com base na origem.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-107">Attempting to build .NET Core from source.</span></span>
- <span data-ttu-id="8e4c2-108">Querendo fazer alterações à CLI do .NET Core que poderiam afetar o layout resultante ou os pacotes produzidos.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-108">Wanting to make changes to the .NET Core CLI that could impact the resulting layout or packages produced.</span></span>

## <a name="disk-layout"></a><span data-ttu-id="8e4c2-109">Layout de disco</span><span class="sxs-lookup"><span data-stu-id="8e4c2-109">Disk layout</span></span>

<span data-ttu-id="8e4c2-110">Quando instalado, o .NET Core consiste em vários componentes que são dispostos da seguinte maneira no sistema de arquivos:</span><span class="sxs-lookup"><span data-stu-id="8e4c2-110">When installed, .NET Core consists of several components that are laid out as follows in the filesystem:</span></span>

```
.
├── dotnet                       (1)
├── LICENSE.txt                  (8)
├── ThirdPartyNotices.txt        (8)
├── host
│   └── fxr
│       └── <fxr version>        (2)
├── sdk
│   ├── <sdk version>            (3)
│   └── NuGetFallbackFolder      (4)
├── packs
│   ├── Microsoft.AspNetCore.App.Ref
│   │   └── <aspnetcore ref version>     (11)
│   ├── Microsoft.NETCore.App.Ref
│   │   └── <netcore ref version>        (12)
│   ├── Microsoft.NETCore.App.Host.<rid>
│   │   └── <apphost version>            (13)
│   ├── Microsoft.WindowsDesktop.App.Ref
│   │   └── <desktop ref version>        (14)
│   └── NETStandard.Library.Ref
│       └── <netstandard version>        (15)
├── shared
│   ├── Microsoft.NETCore.App
│   │   └── <runtime version>     (5)
│   ├── Microsoft.AspNetCore.App
│   │   └── <aspnetcore version>  (6)
│   ├── Microsoft.AspNetCore.All
│   │   └── <aspnetcore version>  (6)
│   └── Microsoft.WindowsDesktop.App
│       └── <desktop app version> (7)
└── templates
│   └── <templates version>      (17)
/
├── etc/dotnet
│       └── install_location     (16)
├── usr/share/man/man1
│       └── dotnet.1.gz          (9)
└── usr/bin
        └── dotnet               (10)
```

- <span data-ttu-id="8e4c2-111">(1) **dotnet** O host (também conhecido como o "muxer") tem duas funções distintas: ativar um tempo de execução para iniciar um aplicativo e ativar um SDK para enviar comandos a ele.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-111">(1) **dotnet** The host (also known as the "muxer") has two distinct roles: activate a runtime to launch an application, and activate an SDK to dispatch commands to it.</span></span> <span data-ttu-id="8e4c2-112">O host é um executável nativo (`dotnet.exe`).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-112">The host is a native executable (`dotnet.exe`).</span></span>

<span data-ttu-id="8e4c2-113">Embora haja um único host, a maioria dos outros componentes está em diretórios com controle de versão (2,3,5,6).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-113">While there's a single host, most of the other components are in versioned directories (2,3,5,6).</span></span> <span data-ttu-id="8e4c2-114">Isso significa que várias versões podem estar presentes no sistema, pois são instaladas lado a lado.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-114">This means multiple versions can be present on the system since they're installed side by side.</span></span>

- <span data-ttu-id="8e4c2-115">(2) **host/fxr/\<versão do fxr>** contém a lógica de resolução do framework usada pelo host.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-115">(2) **host/fxr/\<fxr version>** contains the framework resolution logic used by the host.</span></span> <span data-ttu-id="8e4c2-116">O host usa o hostfxr mais recente instalado.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-116">The host uses the latest hostfxr that is installed.</span></span> <span data-ttu-id="8e4c2-117">O hostfxr é responsável por selecionar o tempo de execução apropriado ao executar um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-117">The hostfxr is responsible for selecting the appropriate runtime when executing a .NET Core application.</span></span> <span data-ttu-id="8e4c2-118">Por exemplo, um aplicativo criado para o tempo de execução do .NET Core 2.0.0 usa o 2.0.5 quando ele está disponível.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-118">For example, an application built for .NET Core 2.0.0 uses the 2.0.5 runtime when it's available.</span></span> <span data-ttu-id="8e4c2-119">Da mesma forma, o hostfxr seleciona o SDK adequado durante o desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-119">Similarly, hostfxr selects the appropriate SDK during development.</span></span>

- <span data-ttu-id="8e4c2-120">(3) **sdk/\<versão do sdk>** O SDK (também conhecido como "as ferramentas") é um conjunto de ferramentas gerenciadas usado para escrever e compilar aplicativos e bibliotecas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-120">(3) **sdk/\<sdk version>** The SDK (also known as "the tooling") is a set of managed tools that are used to write and build .NET Core libraries and applications.</span></span> <span data-ttu-id="8e4c2-121">O SDK inclui a CLI (interface de linha de comando) do .NET Core, os compiladores de linguagens gerenciadas, o MSBuild, tarefas e destinos de compilação associados, o NuGet, novos modelos de projeto e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-121">The SDK includes the .NET Core Command-line interface (CLI), the managed languages compilers, MSBuild, and associated build tasks and targets, NuGet, new project templates, and so on.</span></span>

- <span data-ttu-id="8e4c2-122">(4) **sdk/NuGetFallbackFolder** contém um cache de pacotes do NuGet usados por um SDK durante a operação de restauração, como ao executar `dotnet restore` ou `dotnet build /t:Restore`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-122">(4) **sdk/NuGetFallbackFolder** contains a cache of NuGet packages used by an SDK during the restore operation, such as when running `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="8e4c2-123">Esta pasta é usada somente antes do .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-123">This folder is only used prior to .NET Core 3.0.</span></span> <span data-ttu-id="8e4c2-124">Ele não pode ser compilado da origem, pois contém ativos binários pré-criados do `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-124">It can't be built from source, because it contains prebuilt binary assets from `nuget.org`.</span></span>

<span data-ttu-id="8e4c2-125">A pasta **compartilhada** contém estruturas.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-125">The **shared** folder contains frameworks.</span></span> <span data-ttu-id="8e4c2-126">Uma estrutura compartilhada fornece um conjunto de bibliotecas em um local central para que elas possam ser usadas por aplicativos diferentes.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-126">A shared framework provides a set of libraries at a central location so they can be used by different applications.</span></span>

- <span data-ttu-id="8e4c2-127">(5) **shared/Microsoft.NETCore.App/\<versão do tempo de execução>** Essa estrutura contém o tempo de execução do .NET Core e as bibliotecas gerenciadas que dão suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-127">(5) **shared/Microsoft.NETCore.App/\<runtime version>** This framework contains the .NET Core runtime and supporting managed libraries.</span></span>

- <span data-ttu-id="8e4c2-128">(6) **Shared/Microsoft. AspNetCore. { O aplicativo, All}\</aspnetcore versão >** contém as bibliotecas de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-128">(6) **shared/Microsoft.AspNetCore.{App,All}/\<aspnetcore version>** contains the ASP.NET Core libraries.</span></span> <span data-ttu-id="8e4c2-129">As bibliotecas em `Microsoft.AspNetCore.App` são desenvolvidas e têm suporte como parte do projeto .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-129">The libraries under `Microsoft.AspNetCore.App` are developed and supported as part of the .NET Core project.</span></span> <span data-ttu-id="8e4c2-130">As bibliotecas em `Microsoft.AspNetCore.All` são um superconjunto que também contém bibliotecas de terceiros.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-130">The libraries under `Microsoft.AspNetCore.All` are a superset that also contains third-party libraries.</span></span>

- <span data-ttu-id="8e4c2-131">(7) **Shared/Microsoft. desktop. app/\<desktop versão do aplicativo >** contém as bibliotecas da área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-131">(7) **shared/Microsoft.Desktop.App/\<desktop app version>** contains the Windows desktop libraries.</span></span> <span data-ttu-id="8e4c2-132">Isso não está incluído em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-132">This isn't included on non-Windows platforms.</span></span>

- <span data-ttu-id="8e4c2-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** são a licença do .NET Core e licenças de bibliotecas de terceiros usadas no .NET Core, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-133">(8) **LICENSE.txt,ThirdPartyNotices.txt** are the .NET Core license and licenses of third-party libraries used in .NET Core, respectively.</span></span>

- <span data-ttu-id="8e4c2-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` é a página de manual do dotnet.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-134">(9,10) **dotnet.1.gz, dotnet** `dotnet.1.gz` is the dotnet manual page.</span></span> <span data-ttu-id="8e4c2-135">`dotnet` é um symlink ao host(1) dotnet.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-135">`dotnet` is a symlink to the dotnet host(1).</span></span> <span data-ttu-id="8e4c2-136">Esses arquivos são instalados em locais bem conhecidos para a integração do sistema.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-136">These files are installed at well known locations for system integration.</span></span>

- <span data-ttu-id="8e4c2-137">(11, 12) **Microsoft. NetCore. app. ref, Microsoft. AspNetCore. app. ref** descreve a API de uma `x.y` versão do .NET Core e ASP.NET Core respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-137">(11,12) **Microsoft.NETCore.App.Ref,Microsoft.AspNetCore.App.Ref** describe the API of an `x.y` version of .NET Core and ASP.NET Core respectively.</span></span> <span data-ttu-id="8e4c2-138">Esses pacotes são usados durante a compilação para essas versões de destino.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-138">These packs are used when compiling for those target versions.</span></span>

- <span data-ttu-id="8e4c2-139">(13) **Microsoft. NetCore. app. host.\< o RID >** contém um binário nativo para `rid`a plataforma.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-139">(13) **Microsoft.NETCore.App.Host.\<rid>** contains a native binary for platform `rid`.</span></span> <span data-ttu-id="8e4c2-140">Esse binário é um modelo ao compilar um aplicativo .NET Core em um binário nativo para essa plataforma.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-140">This binary is a template when compiling a .NET Core application into a native binary for that platform.</span></span>

- <span data-ttu-id="8e4c2-141">(14) **Microsoft. WindowsDesktop. app. ref** descreve a API da `x.y` versão dos aplicativos da área de trabalho do Windows.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-141">(14) **Microsoft.WindowsDesktop.App.Ref** describes the API of `x.y` version of Windows Desktop applications.</span></span> <span data-ttu-id="8e4c2-142">Esses arquivos são usados durante a compilação para esse destino.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-142">These files are used when compiling for that target.</span></span> <span data-ttu-id="8e4c2-143">Isso não é fornecido em plataformas não Windows.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-143">This isn't provided on non-Windows platforms.</span></span>

- <span data-ttu-id="8e4c2-144">(15) **netstandard. library. ref** descreve a API do `x.y` netpadrão.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-144">(15) **NETStandard.Library.Ref** describes the netstandard `x.y` API.</span></span> <span data-ttu-id="8e4c2-145">Esses arquivos são usados durante a compilação para esse destino.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-145">These files are used when compiling for that target.</span></span>

- <span data-ttu-id="8e4c2-146">(16) **/etc/dotnet/install_location** é um arquivo que contém o caminho completo para a pasta que contém o `dotnet` binário do host.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-146">(16) **/etc/dotnet/install_location** is a file that contains the full path to the folder that contains the `dotnet` host binary.</span></span> <span data-ttu-id="8e4c2-147">O caminho pode ser encerrado com uma nova linha.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-147">The path may be terminated with a newline.</span></span> <span data-ttu-id="8e4c2-148">Não é necessário adicionar esse arquivo quando a raiz é `/usr/share/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-148">It's not necessary to add this file when the root is `/usr/share/dotnet`.</span></span>

- <span data-ttu-id="8e4c2-149">(17) **modelos** contém os modelos usados pelo SDK.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-149">(17) **templates** contains the templates used by the SDK.</span></span> <span data-ttu-id="8e4c2-150">Por exemplo, `dotnet new` localiza modelos de projeto aqui.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-150">For example, `dotnet new` finds project templates here.</span></span>

## <a name="recommended-packages"></a><span data-ttu-id="8e4c2-151">Pacotes recomendados</span><span class="sxs-lookup"><span data-stu-id="8e4c2-151">Recommended packages</span></span>

<span data-ttu-id="8e4c2-152">O controle de versão do .NET Core é baseado nos números de versão `[major].[minor]` do componente de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-152">.NET Core versioning is based on the runtime component `[major].[minor]` version numbers.</span></span>
<span data-ttu-id="8e4c2-153">A versão do SDK usa o mesmo `[major].[minor]` e tem um `[patch]` independente que combina as semânticas de recurso e de patch para o SDK.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-153">The SDK version uses the same `[major].[minor]` and has an independent `[patch]` that combines feature and patch semantics for the SDK.</span></span>
<span data-ttu-id="8e4c2-154">Por exemplo: O SDK versão 2.2.302 é a segunda versão de patch da terceira versão do recurso do SDK que dá suporte ao tempo de execução 2.2.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-154">For example: SDK version 2.2.302 is the second patch release of the third feature release of the SDK that supports the 2.2 runtime.</span></span> <span data-ttu-id="8e4c2-155">Para obter mais informações sobre como o controle de versão funciona, veja [Visão geral do controle de versão do .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-155">For more information about how versioning works, see [.NET Core versioning overview](../versions/index.md).</span></span>

<span data-ttu-id="8e4c2-156">Alguns pacotes incluem parte do número de versão no nome deles.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-156">Some of the packages include part of the version number in their name.</span></span> <span data-ttu-id="8e4c2-157">Isso permite que você instale uma versão específica.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-157">This allows you to install a specific version.</span></span>
<span data-ttu-id="8e4c2-158">O restante da versão não está incluído no nome da versão.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-158">The rest of the version isn't included in the version name.</span></span> <span data-ttu-id="8e4c2-159">Isso permite ao gerenciador de pacotes de SO atualize os pacotes (por exemplo, instalando automaticamente correções de segurança).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-159">This allows the OS package manager to update the packages (for example, automatically installing security fixes).</span></span> <span data-ttu-id="8e4c2-160">Gerenciadores de pacotes com suporte são específicos do Linux.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-160">Supported package managers are Linux specific.</span></span>

<span data-ttu-id="8e4c2-161">Veja a seguir uma lista dos pacotes recomendados:</span><span class="sxs-lookup"><span data-stu-id="8e4c2-161">The following lists the recommended packages:</span></span>

- <span data-ttu-id="8e4c2-162">`dotnet-sdk-[major].[minor]`-Instala o SDK mais recente para tempo de execução específico</span><span class="sxs-lookup"><span data-stu-id="8e4c2-162">`dotnet-sdk-[major].[minor]` - Installs the latest sdk for specific runtime</span></span>
  - <span data-ttu-id="8e4c2-163">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-163">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-164">**Exemplo:** dotnet-sdk-2,1</span><span class="sxs-lookup"><span data-stu-id="8e4c2-164">**Example:** dotnet-sdk-2.1</span></span>
  - <span data-ttu-id="8e4c2-165">**Terá** (3),(4)</span><span class="sxs-lookup"><span data-stu-id="8e4c2-165">**Contains:** (3),(4)</span></span>
  - <span data-ttu-id="8e4c2-166">**Dependências:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`,`dotnet-templates-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="8e4c2-166">**Dependencies:** `aspnetcore-runtime-[major].[minor]`, `dotnet-targeting-pack-[major].[minor]`, `aspnetcore-targeting-pack-[major].[minor]`, `netstandard-targeting-pack-[netstandard_major].[netstandard_minor]`, `dotnet-apphost-pack-[major].[minor]`, `dotnet-templates-[major].[minor]`</span></span>

- <span data-ttu-id="8e4c2-167">`aspnetcore-runtime-[major].[minor]`-Instala um tempo de execução de ASP.NET Core específico</span><span class="sxs-lookup"><span data-stu-id="8e4c2-167">`aspnetcore-runtime-[major].[minor]` - Installs a specific ASP.NET Core runtime</span></span>
  - <span data-ttu-id="8e4c2-168">**Versão:** \<> a versão de tempo de execução aspnetcore</span><span class="sxs-lookup"><span data-stu-id="8e4c2-168">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="8e4c2-169">**Exemplo:** aspnetcore-runtime-2,1</span><span class="sxs-lookup"><span data-stu-id="8e4c2-169">**Example:** aspnetcore-runtime-2.1</span></span>
  - <span data-ttu-id="8e4c2-170">**Terá** (6)</span><span class="sxs-lookup"><span data-stu-id="8e4c2-170">**Contains:** (6)</span></span>
  - <span data-ttu-id="8e4c2-171">**Dependências:** `dotnet-runtime-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="8e4c2-171">**Dependencies:** `dotnet-runtime-[major].[minor]`</span></span>

- <span data-ttu-id="8e4c2-172">`dotnet-runtime-deps-[major].[minor]` _(Opcional)_ -instala as dependências para executar aplicativos independentes</span><span class="sxs-lookup"><span data-stu-id="8e4c2-172">`dotnet-runtime-deps-[major].[minor]` _(Optional)_ - Installs the dependencies for running self-contained applications</span></span>
  - <span data-ttu-id="8e4c2-173">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-173">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-174">**Exemplo:** dotnet-Runtime-deps-2,1</span><span class="sxs-lookup"><span data-stu-id="8e4c2-174">**Example:** dotnet-runtime-deps-2.1</span></span>
  - <span data-ttu-id="8e4c2-175">**Dependências:** _dependências específicas do distribuição_</span><span class="sxs-lookup"><span data-stu-id="8e4c2-175">**Dependencies:** _distro specific dependencies_</span></span>

- <span data-ttu-id="8e4c2-176">`dotnet-runtime-[major].[minor]`-Instala um tempo de execução específico</span><span class="sxs-lookup"><span data-stu-id="8e4c2-176">`dotnet-runtime-[major].[minor]` - Installs a specific runtime</span></span>
  - <span data-ttu-id="8e4c2-177">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-177">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-178">**Exemplo:** dotnet-tempo de execução-2,1</span><span class="sxs-lookup"><span data-stu-id="8e4c2-178">**Example:** dotnet-runtime-2.1</span></span>
  - <span data-ttu-id="8e4c2-179">**Terá** (5)</span><span class="sxs-lookup"><span data-stu-id="8e4c2-179">**Contains:** (5)</span></span>
  - <span data-ttu-id="8e4c2-180">**Dependências:** `dotnet-hostfxr:<runtime version>+`,`dotnet-runtime-deps-[major].[minor]`</span><span class="sxs-lookup"><span data-stu-id="8e4c2-180">**Dependencies:** `dotnet-hostfxr:<runtime version>+`, `dotnet-runtime-deps-[major].[minor]`</span></span>

- <span data-ttu-id="8e4c2-181">`dotnet-hostfxr`-dependência</span><span class="sxs-lookup"><span data-stu-id="8e4c2-181">`dotnet-hostfxr` - dependency</span></span>
  - <span data-ttu-id="8e4c2-182">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-182">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-183">**Exemplo:** dotnet-hostfxr</span><span class="sxs-lookup"><span data-stu-id="8e4c2-183">**Example:** dotnet-hostfxr</span></span>
  - <span data-ttu-id="8e4c2-184">**Terá** (2)</span><span class="sxs-lookup"><span data-stu-id="8e4c2-184">**Contains:** (2)</span></span>
  - <span data-ttu-id="8e4c2-185">**Dependências:** `host:<runtime version>+`</span><span class="sxs-lookup"><span data-stu-id="8e4c2-185">**Dependencies:** `host:<runtime version>+`</span></span>

- <span data-ttu-id="8e4c2-186">`dotnet-host`-dependência</span><span class="sxs-lookup"><span data-stu-id="8e4c2-186">`dotnet-host` - dependency</span></span>
  - <span data-ttu-id="8e4c2-187">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-187">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-188">**Exemplo:** dotnet-host</span><span class="sxs-lookup"><span data-stu-id="8e4c2-188">**Example:** dotnet-host</span></span>
  - <span data-ttu-id="8e4c2-189">**Terá** (1), (8), (9), (10), (16)</span><span class="sxs-lookup"><span data-stu-id="8e4c2-189">**Contains:** (1),(8),(9),(10),(16)</span></span>

- <span data-ttu-id="8e4c2-190">`dotnet-apphost-pack-[major].[minor]`-dependência</span><span class="sxs-lookup"><span data-stu-id="8e4c2-190">`dotnet-apphost-pack-[major].[minor]` - dependency</span></span>
  - <span data-ttu-id="8e4c2-191">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-191">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-192">**Terá** 13</span><span class="sxs-lookup"><span data-stu-id="8e4c2-192">**Contains:** (13)</span></span>

- <span data-ttu-id="8e4c2-193">`dotnet-targeting-pack-[major].[minor]`-Permite direcionar um tempo de execução não mais recente</span><span class="sxs-lookup"><span data-stu-id="8e4c2-193">`dotnet-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="8e4c2-194">**Versão:** \<versão de tempo de execução ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-194">**Version:** \<runtime version></span></span>
  - <span data-ttu-id="8e4c2-195">**Terá** 12</span><span class="sxs-lookup"><span data-stu-id="8e4c2-195">**Contains:** (12)</span></span>

- <span data-ttu-id="8e4c2-196">`aspnetcore-targeting-pack-[major].[minor]`-Permite direcionar um tempo de execução não mais recente</span><span class="sxs-lookup"><span data-stu-id="8e4c2-196">`aspnetcore-targeting-pack-[major].[minor]` - Allows targeting a non-latest runtime</span></span>
  - <span data-ttu-id="8e4c2-197">**Versão:** \<> a versão de tempo de execução aspnetcore</span><span class="sxs-lookup"><span data-stu-id="8e4c2-197">**Version:** \<aspnetcore runtime version></span></span>
  - <span data-ttu-id="8e4c2-198">**Terá** 11</span><span class="sxs-lookup"><span data-stu-id="8e4c2-198">**Contains:** (11)</span></span>

- <span data-ttu-id="8e4c2-199">`netstandard-targeting-pack-[major].[minor]`-Permite direcionar uma versão do netstandard</span><span class="sxs-lookup"><span data-stu-id="8e4c2-199">`netstandard-targeting-pack-[major].[minor]` - Allows targeting a netstandard version</span></span>
  - <span data-ttu-id="8e4c2-200">**Versão:** \<versão do SDK ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-200">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="8e4c2-201">**Terá** 15</span><span class="sxs-lookup"><span data-stu-id="8e4c2-201">**Contains:** (15)</span></span>

- `dotnet-templates-[major].[minor]`
  - <span data-ttu-id="8e4c2-202">**Versão:** \<versão do SDK ></span><span class="sxs-lookup"><span data-stu-id="8e4c2-202">**Version:** \<sdk version></span></span>
  - <span data-ttu-id="8e4c2-203">**Terá** 15</span><span class="sxs-lookup"><span data-stu-id="8e4c2-203">**Contains:** (15)</span></span>

<span data-ttu-id="8e4c2-204">O `dotnet-runtime-deps-[major].[minor]` requer a compreensão das _dependências específicas do distribuição_.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-204">The `dotnet-runtime-deps-[major].[minor]` requires understanding the _distro specific dependencies_.</span></span> <span data-ttu-id="8e4c2-205">Como o sistema de compilação distribuição pode ser capaz de derivar isso automaticamente, o pacote é opcional; nesse caso, essas dependências são adicionadas diretamente ao `dotnet-runtime-[major].[minor]` pacote.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-205">Because the distro build system may be able to derive this automatically, the package is optional, in which case these dependencies are added directly to the `dotnet-runtime-[major].[minor]` package.</span></span>

<span data-ttu-id="8e4c2-206">Quando o conteúdo do pacote está sob uma pasta com versão, o `[major].[minor]` nome do pacote corresponde ao nome da pasta com versão.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-206">When package content is under a versioned folder, the package name `[major].[minor]` match the versioned folder name.</span></span> <span data-ttu-id="8e4c2-207">Para todos os pacotes, exceto `netstandard-targeting-pack-[major].[minor]`o, isso também corresponde à versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-207">For all packages, except the `netstandard-targeting-pack-[major].[minor]`, this also matches with the .NET Core version.</span></span>

<span data-ttu-id="8e4c2-208">As dependências entre os pacotes devem usar um requisito _igual ou maior que_ a versão.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-208">Dependencies between packages should use a _equal or greater than_ version requirement.</span></span> <span data-ttu-id="8e4c2-209">Por exemplo, `dotnet-sdk-2.2:2.2.401` requer `aspnetcore-runtime-2.2 >= 2.2.6`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-209">For example, `dotnet-sdk-2.2:2.2.401` requires `aspnetcore-runtime-2.2 >= 2.2.6`.</span></span> <span data-ttu-id="8e4c2-210">Isso possibilita que o usuário Atualize sua instalação por meio de um pacote raiz (por exemplo, `dnf update dotnet-sdk-2.2`).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-210">This makes it possible for the user to upgrade their installation via a root package (e.g. `dnf update dotnet-sdk-2.2`).</span></span>

<span data-ttu-id="8e4c2-211">A maioria das distribuições exigem que todos os artefatos sejam compilados da origem.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-211">Most distributions require all artifacts to be built from source.</span></span> <span data-ttu-id="8e4c2-212">Isso tem algum impacto nos pacotes:</span><span class="sxs-lookup"><span data-stu-id="8e4c2-212">This has some impact on the packages:</span></span>

- <span data-ttu-id="8e4c2-213">As bibliotecas de terceiros em `shared/Microsoft.AspNetCore.All` não podem ser criadas facilmente usando o código-fonte.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-213">The third-party libraries under `shared/Microsoft.AspNetCore.All` can't be easily built from source.</span></span> <span data-ttu-id="8e4c2-214">Portanto, essa pasta é omitida do pacote `aspnetcore-runtime`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-214">So that folder is omitted from the `aspnetcore-runtime` package.</span></span>

- <span data-ttu-id="8e4c2-215">O `NuGetFallbackFolder` é populado usando os artefatos binários de `nuget.org`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-215">The `NuGetFallbackFolder` is populated using binary artifacts from `nuget.org`.</span></span> <span data-ttu-id="8e4c2-216">Ele deve permanecer vazio.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-216">It should remain empty.</span></span>

<span data-ttu-id="8e4c2-217">Vários pacotes `dotnet-sdk` podem fornecer os mesmos arquivos para o `NuGetFallbackFolder`.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-217">Multiple `dotnet-sdk` packages may provide the same files for the `NuGetFallbackFolder`.</span></span> <span data-ttu-id="8e4c2-218">Para evitar problemas com o gerenciador de pacotes, esses arquivos devem ser idênticos (soma de verificação, data de modificação e assim por diante).</span><span class="sxs-lookup"><span data-stu-id="8e4c2-218">To avoid issues with the package manager, these files should be identical (checksum, modification date, and so on).</span></span>

## <a name="building-packages"></a><span data-ttu-id="8e4c2-219">Compilando pacotes</span><span class="sxs-lookup"><span data-stu-id="8e4c2-219">Building packages</span></span>

<span data-ttu-id="8e4c2-220">O repositório [dotnet/source-build](https://github.com/dotnet/source-build) fornece instruções sobre como compilar um tarball de origem do SDK do .NET Core e todos os seus componentes.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-220">The [dotnet/source-build](https://github.com/dotnet/source-build) repository provides instructions on how to build a source tarball of the .NET Core SDK and all its components.</span></span> <span data-ttu-id="8e4c2-221">A saída do repositório de build de origem corresponde o layout descrito na primeira seção deste artigo.</span><span class="sxs-lookup"><span data-stu-id="8e4c2-221">The output of the source-build repository matches the layout described in the first section of this article.</span></span>
