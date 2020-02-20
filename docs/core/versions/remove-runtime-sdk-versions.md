---
title: Remover o SDK e o runtime do .NET Core
description: Este artigo descreve como determinar quais versões do runtime e do SDK do .NET Core estão instaladas e, em seguida, como removê-las no Windows, Mac e Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503466"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="03cea-103">Como remover o SDK e o Runtime do .NET Core</span><span class="sxs-lookup"><span data-stu-id="03cea-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="03cea-104">Ao longo do tempo, ao instalar as versões atualizadas do runtime e do SDK do .NET Core, você poderá desejar remover versões desatualizadas do .NET Core do seu computador.</span><span class="sxs-lookup"><span data-stu-id="03cea-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="03cea-105">Remover versões mais antigas do runtime pode mudar o runtime escolhido para executar aplicativos de estrutura compartilhada, conforme detalhado no artigo [Seleção de versão do .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="03cea-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

## <a name="should-i-remove-a-version"></a><span data-ttu-id="03cea-106">Devo remover uma versão?</span><span class="sxs-lookup"><span data-stu-id="03cea-106">Should I remove a version?</span></span>

<span data-ttu-id="03cea-107">Os comportamentos de [seleção de versão do .NET Core](selection.md) e a compatibilidade do runtime do .NET Core com as atualizações permitem a remoção segura de versões anteriores.</span><span class="sxs-lookup"><span data-stu-id="03cea-107">The [.NET Core version selection](selection.md) behaviors and the runtime compatibility of .NET Core across updates enables safe removal of previous versions.</span></span> <span data-ttu-id="03cea-108">As atualizações de runtime do .NET core são compatíveis com uma “banda” de versão principal como 1.x e 2.x.</span><span class="sxs-lookup"><span data-stu-id="03cea-108">.NET Core runtime updates are compatible within a major version 'band' such as 1.x and 2.x.</span></span> <span data-ttu-id="03cea-109">Além disso, versões mais recentes do SDK do .NET Core geralmente mantêm a capacidade de compilar aplicativos destinados a versões anteriores do runtime de uma maneira compatível.</span><span class="sxs-lookup"><span data-stu-id="03cea-109">Additionally, newer releases of the .NET Core SDK generally maintain the ability to build applications that target previous versions of the runtime in a compatible manner.</span></span>

<span data-ttu-id="03cea-110">Em geral, você precisa apenas do SDK mais recente e da versão de patch mais recente dos runtimes necessários para seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="03cea-110">In general, you only need the latest SDK and latest patch version of the runtimes required for your application.</span></span> <span data-ttu-id="03cea-111">As instâncias em que manter o SDK ou versões de tempo de execução mais antigas incluem a manutenção de aplicativos baseados em **Project. JSON**.</span><span class="sxs-lookup"><span data-stu-id="03cea-111">Instances where keeping older SDK or Runtime versions include maintaining **project.json**-based applications.</span></span> <span data-ttu-id="03cea-112">A menos que seu aplicativo tenha motivos específicos para runtimes ou SDKs anteriores, você pode remover com segurança as versões mais antigas.</span><span class="sxs-lookup"><span data-stu-id="03cea-112">Unless your application has specific reasons for earlier SDKs or runtimes, you may safely remove older versions.</span></span>

## <a name="determine-what-is-installed"></a><span data-ttu-id="03cea-113">Determinar o que está instalado</span><span class="sxs-lookup"><span data-stu-id="03cea-113">Determine what is installed</span></span>

<span data-ttu-id="03cea-114">Começando com o .NET Core 2.1, a CLI do .NET tem as opções que você pode usar para listar as versões do SDK e do runtime que estão instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="03cea-114">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="03cea-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) para ver a lista dos SDKs instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="03cea-115">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="03cea-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) para ver a lista dos runtimes instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="03cea-116">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="03cea-117">O texto a seguir mostra a saída típica para Windows, macOS ou Linux:</span><span class="sxs-lookup"><span data-stu-id="03cea-117">The following text shows typical output for Windows, macOS, or Linux:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="03cea-118">Windows</span><span class="sxs-lookup"><span data-stu-id="03cea-118">Windows</span></span>](#tab/windows)

<span data-ttu-id="03cea-119">Executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="03cea-119">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="03cea-120">Você Obtém uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="03cea-120">You get output similar to the following:</span></span>

```console
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]
```

<span data-ttu-id="03cea-121">E executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="03cea-121">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="03cea-122">Você Obtém uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="03cea-122">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linux"></a>[<span data-ttu-id="03cea-123">Linux</span><span class="sxs-lookup"><span data-stu-id="03cea-123">Linux</span></span>](#tab/linux)

<span data-ttu-id="03cea-124">Executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="03cea-124">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="03cea-125">Você Obtém uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="03cea-125">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

<span data-ttu-id="03cea-126">E executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="03cea-126">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="03cea-127">Você Obtém uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="03cea-127">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macos"></a>[<span data-ttu-id="03cea-128">macOS</span><span class="sxs-lookup"><span data-stu-id="03cea-128">macOS</span></span>](#tab/macos)

<span data-ttu-id="03cea-129">Executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="03cea-129">By running the following command:</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="03cea-130">Você Obtém uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="03cea-130">You get output similar to the following:</span></span>

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

<span data-ttu-id="03cea-131">E executando o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="03cea-131">And by running the following command:</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="03cea-132">Você Obtém uma saída semelhante à seguinte:</span><span class="sxs-lookup"><span data-stu-id="03cea-132">You get output similar to the following:</span></span>

```console
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

---

## <a name="uninstall-net-core"></a><span data-ttu-id="03cea-133">Desinstalar o .NET Core</span><span class="sxs-lookup"><span data-stu-id="03cea-133">Uninstall .NET Core</span></span>

# <a name="windows"></a>[<span data-ttu-id="03cea-134">Windows</span><span class="sxs-lookup"><span data-stu-id="03cea-134">Windows</span></span>](#tab/windows)

<span data-ttu-id="03cea-135">O .NET Core usa a caixa de diálogo **Adicionar ou Remover Programas** do Windows para remover as versões do SDK e do runtime do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03cea-135">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="03cea-136">A figura a seguir mostra a caixa de diálogo **Adicionar ou Remover Programas** com várias versões do runtime e do SDK do .NET instaladas.</span><span class="sxs-lookup"><span data-stu-id="03cea-136">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Adicionar ou remover programas para remover o .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="03cea-138">Selecione todas as versões que você deseja remover do seu computador e clique em **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="03cea-138">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linux"></a>[<span data-ttu-id="03cea-139">Linux</span><span class="sxs-lookup"><span data-stu-id="03cea-139">Linux</span></span>](#tab/linux)

<span data-ttu-id="03cea-140">Há mais opções para desinstalar o .NET Core (SDK ou runtime) no Linux.</span><span class="sxs-lookup"><span data-stu-id="03cea-140">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="03cea-141">A melhor maneira para desinstalar o .NET Core é espelhar a ação que você usou para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03cea-141">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="03cea-142">As especificações dependem de sua distribuição escolhida e do método de instalação.</span><span class="sxs-lookup"><span data-stu-id="03cea-142">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="03cea-143">Para instalações do Red Hat, consulte o [Guia de introdução do Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) para obter informações sobre como instalar e desinstalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03cea-143">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="03cea-144">A partir do .NET Core 2,1, não é necessário desinstalar o SDK do .NET Core ao atualizá-lo usando um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="03cea-144">Starting with .NET Core 2.1, there's no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="03cea-145">Os comandos `update` ou `refresh` do gerenciador de pacotes removerão automaticamente a versão mais antiga após a instalação bem-sucedida de uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="03cea-145">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="03cea-146">Se instalou o .NET Core usando um gerenciador de pacotes, você usará esse mesmo gerenciador de pacotes para desinstalar o SDK ou o runtime do .NET.</span><span class="sxs-lookup"><span data-stu-id="03cea-146">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="03cea-147">As instalações do .NET core dão suporte a gerenciadores de pacotes mais populares.</span><span class="sxs-lookup"><span data-stu-id="03cea-147">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="03cea-148">Consulte a documentação do gerenciador de pacotes da distribuição para a sintaxe exata em seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="03cea-148">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="03cea-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) é usado por sistemas baseados em Debian, incluindo o Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="03cea-149">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="03cea-150">[yum(8)](https://linux.die.net/man/8/yum) é usado no Fedora, CentOS e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="03cea-150">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="03cea-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) é usado no openSUSE e no SLES (SUSE Linux Enterprise System).</span><span class="sxs-lookup"><span data-stu-id="03cea-151">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="03cea-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) é usado no Fedora.</span><span class="sxs-lookup"><span data-stu-id="03cea-152">[dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="03cea-153">Em quase todos os casos, o comando para remover um pacote é `remove`.</span><span class="sxs-lookup"><span data-stu-id="03cea-153">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="03cea-154">O nome do pacote para a instalação do SDK do .NET Core para a maioria dos gerenciadores de pacotes é `dotnet-sdk`, seguido pelo número de versão.</span><span class="sxs-lookup"><span data-stu-id="03cea-154">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="03cea-155">Começando com a versão 2.1.300 do SDK do .NET Core e a versão `2.1` do runtime, somente os números de versão principal e secundária são necessários: por exemplo, o SDK do .NET Core versão 2.1.300 pode ser referenciado como o pacote `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="03cea-155">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="03cea-156">As versões anteriores exigem a cadeia de caracteres de versão inteira: por exemplo, `dotnet-sdk-2.1.200` seria necessária para a versão 2.1.200 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03cea-156">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="03cea-157">Para computadores apenas com o runtime instalado, e não o SDK, o nome do pacote é `dotnet-runtime-<version>`, para o runtime do .NET Core, e `aspnetcore-runtime-<version>`, para a pilha em runtime inteira.</span><span class="sxs-lookup"><span data-stu-id="03cea-157">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="03cea-158">As instalações do .NET Core anteriores a 2,0 não desinstalaram o aplicativo host quando o SDK foi desinstalado usando o Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="03cea-158">.NET Core installations earlier than 2.0 didn't uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="03cea-159">Usando `apt-get`, o comando é:</span><span class="sxs-lookup"><span data-stu-id="03cea-159">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="03cea-160">Observe que não há nenhuma versão anexada a `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="03cea-160">Note that there's no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="03cea-161">Se instalou usando um tarball, você deverá remover o .NET Core usando o método manual.</span><span class="sxs-lookup"><span data-stu-id="03cea-161">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="03cea-162">Você remove os SDKs e os runtimes separadamente, removendo o diretório que contém essa versão.</span><span class="sxs-lookup"><span data-stu-id="03cea-162">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="03cea-163">Por exemplo, para remover o SDK 1.0.1 e o runtime, você usaria os seguintes comandos de bash:</span><span class="sxs-lookup"><span data-stu-id="03cea-163">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="03cea-164">Os diretórios pais para o SDK e o runtime são listados na saída dos comandos `dotnet --list-sdks` e `dotnet --list-runtimes`, conforme mostrado na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="03cea-164">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macos"></a>[<span data-ttu-id="03cea-165">macOS</span><span class="sxs-lookup"><span data-stu-id="03cea-165">macOS</span></span>](#tab/macos)

<span data-ttu-id="03cea-166">No Mac, você remove os SDKs e os runtimes separadamente, removendo o diretório que contém essa versão.</span><span class="sxs-lookup"><span data-stu-id="03cea-166">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="03cea-167">Por exemplo, para remover o SDK 1.0.1 e o runtime, você usaria os seguintes comandos de bash:</span><span class="sxs-lookup"><span data-stu-id="03cea-167">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="03cea-168">Os diretórios pais para o SDK e o runtime são listados na saída dos comandos `dotnet --list-sdks` e `dotnet --list-runtimes`, conforme mostrado na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="03cea-168">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

---

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="03cea-169">Ferramenta de Desinstalação do .NET Core</span><span class="sxs-lookup"><span data-stu-id="03cea-169">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="03cea-170">A [ferramenta de desinstalação do .NET Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) permite remover SDKs do .NET Core e tempos de execução de um sistema.</span><span class="sxs-lookup"><span data-stu-id="03cea-170">The [.NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) lets you remove .NET Core SDKs and runtimes from a system.</span></span> <span data-ttu-id="03cea-171">Uma coleção de opções está disponível para especificar quais versões devem ser desinstaladas.</span><span class="sxs-lookup"><span data-stu-id="03cea-171">A collection of options is available to specify which versions should be uninstalled.</span></span>

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a><span data-ttu-id="03cea-172">Dependência do Visual Studio em versões de SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="03cea-172">Visual Studio dependency on .NET Core SDK versions</span></span>

<span data-ttu-id="03cea-173">Antes do Visual Studio 2019 versão 16,3, os instaladores do Visual Studio chamaram o instalador de SDK do .NET Core autônomo.</span><span class="sxs-lookup"><span data-stu-id="03cea-173">Before Visual Studio 2019 version 16.3, Visual Studio installers called the standalone .NET Core SDK installer.</span></span> <span data-ttu-id="03cea-174">Como resultado, as versões do SDK aparecem na caixa de diálogo **Adicionar ou remover programas** do Windows.</span><span class="sxs-lookup"><span data-stu-id="03cea-174">As a result, the SDK versions appear in the Windows **Add/Remove Programs** dialog.</span></span> <span data-ttu-id="03cea-175">Remover SDKs do .NET Core que foram instalados pelo Visual Studio usando o instalador autônomo pode interromper o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03cea-175">Removing .NET Core SDKs that were installed by Visual Studio using the standalone installer may break Visual Studio.</span></span> <span data-ttu-id="03cea-176">Se o Visual Studio tiver problemas depois de desinstalar os SDKs, execute o reparo nessa versão específica do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="03cea-176">If Visual Studio has problems after you uninstall SDKs, run Repair on that specific version of Visual Studio.</span></span> <span data-ttu-id="03cea-177">A tabela a seguir mostra algumas das dependências do Visual Studio em SDK do .NET Core versões:</span><span class="sxs-lookup"><span data-stu-id="03cea-177">The following table shows some of the Visual Studio dependencies on .NET Core SDK versions:</span></span>

| <span data-ttu-id="03cea-178">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="03cea-178">Visual Studio version</span></span> | <span data-ttu-id="03cea-179">Versão do SDK do .NET Core</span><span class="sxs-lookup"><span data-stu-id="03cea-179">.NET Core SDK version</span></span> |
| -- | -- |
| <span data-ttu-id="03cea-180">Visual Studio 2019 versão 16.2</span><span class="sxs-lookup"><span data-stu-id="03cea-180">Visual Studio 2019 version 16.2</span></span> | <span data-ttu-id="03cea-181">SDK do .NET Core 2.2.4 XX, 2.1.8 XX</span><span class="sxs-lookup"><span data-stu-id="03cea-181">.NET Core SDK 2.2.4xx, 2.1.8xx</span></span> |
| <span data-ttu-id="03cea-182">Visual Studio 2019 versão 16.1</span><span class="sxs-lookup"><span data-stu-id="03cea-182">Visual Studio 2019 version 16.1</span></span> | <span data-ttu-id="03cea-183">SDK do .NET Core 2.2.3 XX, 2.1.7 XX</span><span class="sxs-lookup"><span data-stu-id="03cea-183">.NET Core SDK 2.2.3xx, 2.1.7xx</span></span> |
| <span data-ttu-id="03cea-184">Visual Studio 2019 versão 16,0</span><span class="sxs-lookup"><span data-stu-id="03cea-184">Visual Studio 2019 version 16.0</span></span> | <span data-ttu-id="03cea-185">SDK do .NET Core 2.2.2 XX, 2.1.6 XX</span><span class="sxs-lookup"><span data-stu-id="03cea-185">.NET Core SDK 2.2.2xx, 2.1.6xx</span></span> |
| <span data-ttu-id="03cea-186">Visual Studio 2017 versão 15,9</span><span class="sxs-lookup"><span data-stu-id="03cea-186">Visual Studio 2017 version 15.9</span></span> | <span data-ttu-id="03cea-187">SDK do .NET Core 2.2.1 XX, 2.1.5 XX</span><span class="sxs-lookup"><span data-stu-id="03cea-187">.NET Core SDK 2.2.1xx, 2.1.5xx</span></span> |
| <span data-ttu-id="03cea-188">Visual Studio 2017 versão 15.8</span><span class="sxs-lookup"><span data-stu-id="03cea-188">Visual Studio 2017 version 15.8</span></span> | <span data-ttu-id="03cea-189">SDK do .NET Core 2.1.4 XX</span><span class="sxs-lookup"><span data-stu-id="03cea-189">.NET Core SDK 2.1.4xx</span></span> |

<span data-ttu-id="03cea-190">A partir do Visual Studio 2019 versão 16,3, o Visual Studio é responsável por sua própria cópia do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="03cea-190">Starting with Visual Studio 2019 version 16.3, Visual Studio is in charge of its own copy of the .NET Core SDK.</span></span> <span data-ttu-id="03cea-191">Por esse motivo, você não vê mais essas versões do SDK na caixa de diálogo **Adicionar ou remover programas** .</span><span class="sxs-lookup"><span data-stu-id="03cea-191">For that reason, you no longer see those SDK versions in the **Add/Remove Programs** dialog.</span></span>

## <a name="remove-the-nuget-fallback-folder"></a><span data-ttu-id="03cea-192">Remover a pasta de fallback do NuGet</span><span class="sxs-lookup"><span data-stu-id="03cea-192">Remove the NuGet fallback folder</span></span>

<span data-ttu-id="03cea-193">Antes do SDK do .NET Core 3,0, os instaladores de SDK do .NET Core usaram o *NuGetFallbackFolder* para armazenar um cache de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="03cea-193">Before .NET Core 3.0 SDK, the .NET Core SDK installers used the *NuGetFallbackFolder* to store a cache of NuGet packages.</span></span> <span data-ttu-id="03cea-194">Esse cache foi usado durante operações como `dotnet restore` ou `dotnet build /t:Restore`.</span><span class="sxs-lookup"><span data-stu-id="03cea-194">This cache was used during operations such as `dotnet restore` or `dotnet build /t:Restore`.</span></span> <span data-ttu-id="03cea-195">O `NuGetFallbackFolder` está localizado em *C:\Program Files\dotnet\sdk* no Windows e em */usr/local/share/dotnet/SDK* no MacOS.</span><span class="sxs-lookup"><span data-stu-id="03cea-195">The `NuGetFallbackFolder` is located at *C:\Program Files\dotnet\sdk* on Windows and at */usr/local/share/dotnet/sdk* on macOS.</span></span>

<span data-ttu-id="03cea-196">Talvez você queira remover essa pasta, se:</span><span class="sxs-lookup"><span data-stu-id="03cea-196">You may want to remove this folder, if:</span></span>

* <span data-ttu-id="03cea-197">Você está desenvolvendo apenas usando o SDK do .NET Core 3,0 ou versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="03cea-197">You're only developing using .NET Core 3.0 SDK or later versions.</span></span>
* <span data-ttu-id="03cea-198">Você está desenvolvendo usando versões SDK do .NET Core anteriores a 3,0, mas pode trabalhar online e as coisas podem ser mais lentas.</span><span class="sxs-lookup"><span data-stu-id="03cea-198">You're developing using .NET Core SDK versions earlier than 3.0, but you can work online and things can be slower once.</span></span>

<span data-ttu-id="03cea-199">Se você quiser remover a pasta de fallback do NuGet, poderá excluí-la, mas precisará de privilégios de administrador para fazer isso.</span><span class="sxs-lookup"><span data-stu-id="03cea-199">If you want to remove the NuGet fallback folder, you can delete it, but you'll need admin privileges to do so.</span></span>

<span data-ttu-id="03cea-200">Não é recomendável excluir a pasta *dotnet* .</span><span class="sxs-lookup"><span data-stu-id="03cea-200">It's not recommended to delete the *dotnet* folder.</span></span> <span data-ttu-id="03cea-201">Isso removeria todas as ferramentas globais que você instalou anteriormente.</span><span class="sxs-lookup"><span data-stu-id="03cea-201">Doing so would remove any global tools you've previously installed.</span></span> <span data-ttu-id="03cea-202">Além disso, no Windows:</span><span class="sxs-lookup"><span data-stu-id="03cea-202">Also, on Windows:</span></span>

- <span data-ttu-id="03cea-203">Você interromperá o Visual Studio 2019 versão 16,3 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="03cea-203">You'll break Visual Studio 2019 version 16.3 and later versions.</span></span> <span data-ttu-id="03cea-204">Você pode executar o **reparo** para recuperar.</span><span class="sxs-lookup"><span data-stu-id="03cea-204">You can run **Repair** to recover.</span></span>
- <span data-ttu-id="03cea-205">Se houver SDK do .NET Core entradas na caixa de diálogo **Adicionar/remover programas** , elas ficarão órfãs.</span><span class="sxs-lookup"><span data-stu-id="03cea-205">If there are .NET Core SDK entries in the **Add/Remove Programs** dialog, they'll be orphaned.</span></span>
