---
title: Como remover o SDK e o tempo de execução do .NET
description: Instruções para remover os componentes do SDK e do Tempo de Execução do .NET Core no Windows, Mac e Linux
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45593264"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a><span data-ttu-id="a56eb-103">Como remover o SDK e o Tempo de Execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="a56eb-103">How to remove the .NET Core Runtime and SDK</span></span>

<span data-ttu-id="a56eb-104">Ao longo do tempo, ao instalar as versões atualizadas do tempo de execução e do SDK do .NET Core, você poderá desejar remover versões desatualizadas do .NET Core do seu computador.</span><span class="sxs-lookup"><span data-stu-id="a56eb-104">Over time, as you install updated versions of the .NET Core runtime and SDK, you may want to remove outdated versions of .NET Core from your machine.</span></span> <span data-ttu-id="a56eb-105">Remover versões mais antigas do tempo de execução pode mudar o tempo de execução escolhido para executar aplicativos de estrutura compartilhada, conforme detalhado no artigo [Seleção de versão do .NET Core](selection.md).</span><span class="sxs-lookup"><span data-stu-id="a56eb-105">Removing older versions of the runtime may change the runtime chosen to run shared framework applications, as detailed in the article on [.NET Core version selection](selection.md).</span></span>

<span data-ttu-id="a56eb-106">Começando com o .NET Core 2.1, a CLI do .NET tem as opções que você pode usar para listar as versões do SDK e do tempo de execução que estão instaladas em seu computador.</span><span class="sxs-lookup"><span data-stu-id="a56eb-106">Starting with .NET Core 2.1, the .NET CLI has options you can use to list the versions of the SDK and runtime that are installed on your machine.</span></span>  <span data-ttu-id="a56eb-107">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) para ver a lista dos SDKs instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="a56eb-107">Use [`dotnet --list-sdks`](../tools/dotnet.md#options) to see the list of SDKs installed on your machine.</span></span> <span data-ttu-id="a56eb-108">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) para ver a lista dos tempos de execução instalados em seu computador.</span><span class="sxs-lookup"><span data-stu-id="a56eb-108">Use [`dotnet --list-runtimes`](../tools/dotnet.md#options) to see the list of runtimes installed on your machine.</span></span> <span data-ttu-id="a56eb-109">O texto a seguir mostra a saída típica para Windows, macOS ou Linux:</span><span class="sxs-lookup"><span data-stu-id="a56eb-109">The following text shows typical output for Windows, macOS, or Linux:</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="a56eb-110">Windows</span><span class="sxs-lookup"><span data-stu-id="a56eb-110">Windows</span></span>](#tab/Windows)

```console
C:\> dotnet --list-sdks
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

C:\> dotnet --list-runtimes
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

# <a name="linuxtablinux"></a>[<span data-ttu-id="a56eb-111">Linux</span><span class="sxs-lookup"><span data-stu-id="a56eb-111">Linux</span></span>](#tab/Linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
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

# <a name="macostabmacos"></a>[<span data-ttu-id="a56eb-112">macOS</span><span class="sxs-lookup"><span data-stu-id="a56eb-112">macOS</span></span>](#tab/macOS)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
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

***

## <a name="uninstalling-net-core"></a><span data-ttu-id="a56eb-113">Desinstalando o .NET Core</span><span class="sxs-lookup"><span data-stu-id="a56eb-113">Uninstalling .NET Core</span></span>

# <a name="windowstabwindows"></a>[<span data-ttu-id="a56eb-114">Windows</span><span class="sxs-lookup"><span data-stu-id="a56eb-114">Windows</span></span>](#tab/Windows)

<span data-ttu-id="a56eb-115">O .NET Core usa a caixa de diálogo **Adicionar ou Remover Programas** do Windows para remover as versões do SDK e do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a56eb-115">.NET Core uses the Windows **Add/Remove Programs** dialog to remove versions of the .NET Core runtime and SDK.</span></span> <span data-ttu-id="a56eb-116">A figura a seguir mostra a caixa de diálogo **Adicionar ou Remover Programas** com várias versões do tempo de execução e do SDK do .NET instaladas.</span><span class="sxs-lookup"><span data-stu-id="a56eb-116">The following figure shows the **Add/Remove Programs** dialog with several versions of the .NET runtime and SDK installed.</span></span>

![Adicionar ou remover programas para remover o .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

<span data-ttu-id="a56eb-118">Selecione todas as versões que você deseja remover do seu computador e clique em **Desinstalar**.</span><span class="sxs-lookup"><span data-stu-id="a56eb-118">Select any versions you want to remove from your machine and click **Uninstall**.</span></span>

# <a name="linuxtablinux"></a>[<span data-ttu-id="a56eb-119">Linux</span><span class="sxs-lookup"><span data-stu-id="a56eb-119">Linux</span></span>](#tab/Linux)

<span data-ttu-id="a56eb-120">Há mais opções para desinstalar o .NET Core (SDK ou tempo de execução) no Linux.</span><span class="sxs-lookup"><span data-stu-id="a56eb-120">There are more options to uninstall .NET Core (either SDK or runtime) on Linux.</span></span> <span data-ttu-id="a56eb-121">A melhor maneira para desinstalar o .NET Core é espelhar a ação que você usou para instalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a56eb-121">The best way for you to uninstall .NET Core is to mirror the action you used to install .NET Core.</span></span> <span data-ttu-id="a56eb-122">As especificações dependem de sua distribuição escolhida e do método de instalação.</span><span class="sxs-lookup"><span data-stu-id="a56eb-122">The specifics depend on your chosen distribution and the installation method.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a56eb-123">Para instalações do Red Hat, consulte o [Guia de introdução do Red Hat](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) para obter informações sobre como instalar e desinstalar o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a56eb-123">For Red Hat installations, consult the [Red Hat Getting Started Guide](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) for information on installing and uninstalling .NET Core.</span></span>

<span data-ttu-id="a56eb-124">Começando com o .NET Core 2.1, não há necessidade de desinstalar o SDK do .NET Core ao atualizá-lo usando um gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a56eb-124">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="a56eb-125">Os comandos `update` ou `refresh` do gerenciador de pacotes removerão automaticamente a versão mais antiga após a instalação bem-sucedida de uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="a56eb-125">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

<span data-ttu-id="a56eb-126">Se instalou o .NET Core usando um gerenciador de pacotes, você usará esse mesmo gerenciador de pacotes para desinstalar o SDK ou o tempo de execução do .NET.</span><span class="sxs-lookup"><span data-stu-id="a56eb-126">If you installed .NET Core using a package manager, you use that same package manager to uninstall .NET SDK or runtime.</span></span> <span data-ttu-id="a56eb-127">As instalações do .NET core dão suporte a gerenciadores de pacotes mais populares.</span><span class="sxs-lookup"><span data-stu-id="a56eb-127">.NET Core installations support most popular package managers.</span></span> <span data-ttu-id="a56eb-128">Consulte a documentação do gerenciador de pacotes da distribuição para a sintaxe exata em seu ambiente:</span><span class="sxs-lookup"><span data-stu-id="a56eb-128">Consult the documentation for your distribution's package manager for the precise syntax on your environment:</span></span>

- <span data-ttu-id="a56eb-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) é usado por sistemas baseados em Debian, incluindo o Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a56eb-129">[apt-get(8)](https://linux.die.net/man/8/apt-get) is used by Debian based systems, including Ubuntu.</span></span>
- <span data-ttu-id="a56eb-130">[yum(8)](https://linux.die.net/man/8/yum) é usado no Fedora, CentOS e Oracle Linux.</span><span class="sxs-lookup"><span data-stu-id="a56eb-130">[yum(8)](https://linux.die.net/man/8/yum) is used on Fedora, CentOS, and Oracle Linux.</span></span>
- <span data-ttu-id="a56eb-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) é usado no openSUSE e no SLES (SUSE Linux Enterprise System).</span><span class="sxs-lookup"><span data-stu-id="a56eb-131">[zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) is used on openSUSE and SUSE Linux Enterprise System (SLES).</span></span>
- <span data-ttu-id="a56eb-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) é usado no Fedora.</span><span class="sxs-lookup"><span data-stu-id="a56eb-132">[dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) is used on Fedora.</span></span>

<span data-ttu-id="a56eb-133">Em quase todos os casos, o comando para remover um pacote é `remove`.</span><span class="sxs-lookup"><span data-stu-id="a56eb-133">In almost all cases, the command to remove a package is `remove`.</span></span>

<span data-ttu-id="a56eb-134">O nome do pacote para a instalação do SDK do .NET Core para a maioria dos gerenciadores de pacotes é `dotnet-sdk`, seguido pelo número de versão.</span><span class="sxs-lookup"><span data-stu-id="a56eb-134">The package name for the .NET Core SDK installation for most package managers is `dotnet-sdk`, followed by the version number.</span></span> <span data-ttu-id="a56eb-135">Começando com a versão 2.1.300 do SDK do .NET Core e a versão `2.1` do tempo de execução, somente os números de versão principal e secundária são necessários: por exemplo, o SDK do .NET Core versão 2.1.300 pode ser referenciado como o pacote `dotnet-sdk-2.1`.</span><span class="sxs-lookup"><span data-stu-id="a56eb-135">Starting with the version 2.1.300 of the .NET Core SDK and version `2.1` of the runtime, only the major and minor version numbers are necessary: for example, the .NET Core SDK version 2.1.300 can be referenced as the package `dotnet-sdk-2.1`.</span></span> <span data-ttu-id="a56eb-136">As versões anteriores exigem a cadeia de caracteres de versão inteira: por exemplo, `dotnet-sdk-2.1.200` seria necessária para a versão 2.1.200 do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a56eb-136">Prior versions require the entire version string: for example, `dotnet-sdk-2.1.200` would be required for version 2.1.200 of the .NET Core SDK.</span></span>

<span data-ttu-id="a56eb-137">Para computadores apenas com o tempo de execução instalado, e não o SDK, o nome do pacote é `dotnet-runtime-<version>`, para o tempo de execução do .NET Core, e `aspnetcore-runtime-<version>`, para a pilha em tempo de execução inteira.</span><span class="sxs-lookup"><span data-stu-id="a56eb-137">For machines that have installed only the runtime, and not the SDK, the package name is `dotnet-runtime-<version>` for the .NET Core runtime, and `aspnetcore-runtime-<version>` for the entire runtime stack.</span></span>

<span data-ttu-id="a56eb-138">As instalações do .NET Core anteriores à versão 2.0 não desinstalaram o aplicativo host quando o SDK foi desinstalado usando o gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a56eb-138">.NET Core installations prior to 2.0 did not uninstall the host application when the SDK was uninstalled using the package manager.</span></span> <span data-ttu-id="a56eb-139">Usando `apt-get`, o comando é:</span><span class="sxs-lookup"><span data-stu-id="a56eb-139">Using `apt-get`, the command is:</span></span>

```bash
apt-get remove dotnet-host
```

<span data-ttu-id="a56eb-140">Observe que não há nenhuma versão anexada ao `dotnet-host`.</span><span class="sxs-lookup"><span data-stu-id="a56eb-140">Note that there is no version attached to `dotnet-host`.</span></span>

<span data-ttu-id="a56eb-141">Se instalou usando um tarball, você deverá remover o .NET Core usando o método manual.</span><span class="sxs-lookup"><span data-stu-id="a56eb-141">If you installed using a tarball, you must remove .NET Core using the manual method.</span></span>

<span data-ttu-id="a56eb-142">Você remove os SDKs e os tempos de execução separadamente, removendo o diretório que contém essa versão.</span><span class="sxs-lookup"><span data-stu-id="a56eb-142">You remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="a56eb-143">Por exemplo, para remover o SDK 1.0.1 e o tempo de execução, você usaria os seguintes comandos de bash:</span><span class="sxs-lookup"><span data-stu-id="a56eb-143">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="a56eb-144">Os diretórios pais para o SDK e o tempo de execução são listados na saída dos comandos `dotnet --list-sdks` e `dotnet --list-runtimes`, conforme mostrado na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="a56eb-144">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

# <a name="macostabmacos"></a>[<span data-ttu-id="a56eb-145">macOS</span><span class="sxs-lookup"><span data-stu-id="a56eb-145">macOS</span></span>](#tab/macOS)

<span data-ttu-id="a56eb-146">No Mac, você remove os SDKs e os tempos de execução separadamente, removendo o diretório que contém essa versão.</span><span class="sxs-lookup"><span data-stu-id="a56eb-146">On Mac, you must remove the SDKs and runtimes separately, by removing the directory that contains that version.</span></span> <span data-ttu-id="a56eb-147">Por exemplo, para remover o SDK 1.0.1 e o tempo de execução, você usaria os seguintes comandos de bash:</span><span class="sxs-lookup"><span data-stu-id="a56eb-147">For example, to remove the 1.0.1 SDK and runtime, you would use the following bash commands:</span></span>

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

<span data-ttu-id="a56eb-148">Os diretórios pais para o SDK e o tempo de execução são listados na saída dos comandos `dotnet --list-sdks` e `dotnet --list-runtimes`, conforme mostrado na tabela anterior.</span><span class="sxs-lookup"><span data-stu-id="a56eb-148">The parent directories for the SDK and runtime are listed in the output from the `dotnet --list-sdks` and `dotnet --list-runtimes` command, as shown in the earlier table.</span></span>

<span data-ttu-id="a56eb-149">Começando com o .NET Core 2.1, não há necessidade de desinstalar o SDK do .NET Core ao atualizá-lo usando um gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a56eb-149">Starting with .NET Core 2.1, there is no need to uninstall the .NET Core SDK when upgrading it using a package manager.</span></span> <span data-ttu-id="a56eb-150">Os comandos `update` ou `refresh` do gerenciador de pacotes removerão automaticamente a versão mais antiga após a instalação bem-sucedida de uma versão mais recente.</span><span class="sxs-lookup"><span data-stu-id="a56eb-150">The package manager `update` or `refresh` commands will automatically remove the older version upon the successful installation of a newer version.</span></span>

---
