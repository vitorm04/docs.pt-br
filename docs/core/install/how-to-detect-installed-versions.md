---
title: Verifique as versões instaladas do .NET Core no Windows, Linux e macOS - .NET Core
description: Saiba como listar quais versões do .NET Core estão instaladas no seu computador. Isso inclui o tempo de execução do .NET Core e o SDK.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3a78acee6cf427085e98f14353fc2c0ac65d3d80
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645342"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="5968b-104">Como verificar se o .NET Core já está instalado</span><span class="sxs-lookup"><span data-stu-id="5968b-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="5968b-105">Este artigo ensina como verificar quais versões do .NET Core runtime e SDK estão instaladas no seu computador.</span><span class="sxs-lookup"><span data-stu-id="5968b-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="5968b-106">O núcleo .NET pode já ter sido instalado se você tiver um ambiente de desenvolvimento integrado, como o Visual Studio ou o Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="5968b-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="5968b-107">A instalação de um SDK instala o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="5968b-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="5968b-108">Se algum comando neste artigo falhar, você não terá o tempo de execução ou SDK instalado.</span><span class="sxs-lookup"><span data-stu-id="5968b-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="5968b-109">Para obter mais informações, consulte [Baixar e instalar o .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="5968b-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="5968b-110">Confira as versões do SDK</span><span class="sxs-lookup"><span data-stu-id="5968b-110">Check SDK versions</span></span>

<span data-ttu-id="5968b-111">Você pode ver quais versões do .NET Core SDK estão atualmente instaladas com um terminal.</span><span class="sxs-lookup"><span data-stu-id="5968b-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="5968b-112">Abra um terminal e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="5968b-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="5968b-113">Você tem saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="5968b-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
2.2.101 [C:\program files\dotnet\sdk]
3.0.100 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
2.2.101 [/home/user/dotnet/sdk]
3.0.100 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
2.2.101 [/usr/local/share/dotnet/sdk]
3.0.100 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="5968b-114">Verifique as versões em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="5968b-114">Check runtime versions</span></span>

<span data-ttu-id="5968b-115">Você pode ver quais versões do tempo de execução do .NET Core estão atualmente instaladas com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="5968b-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="5968b-116">Você tem saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="5968b-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.6 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.3 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.2.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="5968b-117">Verifique se há pastas de instalação</span><span class="sxs-lookup"><span data-stu-id="5968b-117">Check for install folders</span></span>

<span data-ttu-id="5968b-118">É possível que o .NET Core esteja instalado, mas não adicionado à variável para o `PATH` seu sistema operacional ou perfil de usuário.</span><span class="sxs-lookup"><span data-stu-id="5968b-118">It's possible that .NET Core is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="5968b-119">Executar os comandos das seções anteriores pode não funcionar.</span><span class="sxs-lookup"><span data-stu-id="5968b-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="5968b-120">Como alternativa, você pode verificar se existem pastas de instalação do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="5968b-120">As an alternative, you can check that the .NET Core install folders exist.</span></span>

<span data-ttu-id="5968b-121">Quando você instala o .NET Core a partir de um instalador ou script, ele é instalado em uma pasta padrão.</span><span class="sxs-lookup"><span data-stu-id="5968b-121">When you install .NET Core from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="5968b-122">Na maior parte do tempo, o instalador ou script que você está usando para instalar o .NET Core lhe dá a opção de instalar em uma pasta diferente.</span><span class="sxs-lookup"><span data-stu-id="5968b-122">Much of the time the installer or script you're using to install .NET Core gives you an option to install to a different folder.</span></span> <span data-ttu-id="5968b-123">Se você optar por instalar em uma pasta diferente, ajuste o início do caminho da pasta.</span><span class="sxs-lookup"><span data-stu-id="5968b-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="5968b-124">**dotnet executável**</span><span class="sxs-lookup"><span data-stu-id="5968b-124">**dotnet executable**</span></span>\
<span data-ttu-id="5968b-125">_C:\\arquivos\\do\\programa dotnet dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="5968b-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="5968b-126">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="5968b-126">**.NET SDK**</span></span>\
<span data-ttu-id="5968b-127">_C:\\arquivos\\do\\programa dotnet sdk\\{versão}\\_</span><span class="sxs-lookup"><span data-stu-id="5968b-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="5968b-128">**.NET Runtime**</span><span class="sxs-lookup"><span data-stu-id="5968b-128">**.NET Runtime**</span></span>\
<span data-ttu-id="5968b-129">_C:\\arquivos\\de\\programa\\dotnet compartilhado\\{runtime-type} {version}\\_</span><span class="sxs-lookup"><span data-stu-id="5968b-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="5968b-130">**dotnet executável**</span><span class="sxs-lookup"><span data-stu-id="5968b-130">**dotnet executable**</span></span>\
<span data-ttu-id="5968b-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="5968b-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="5968b-132">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="5968b-132">**.NET SDK**</span></span>\
<span data-ttu-id="5968b-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="5968b-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="5968b-134">**.NET Runtime**</span><span class="sxs-lookup"><span data-stu-id="5968b-134">**.NET Runtime**</span></span>\
<span data-ttu-id="5968b-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="5968b-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="5968b-136">**dotnet executável**</span><span class="sxs-lookup"><span data-stu-id="5968b-136">**dotnet executable**</span></span>\
<span data-ttu-id="5968b-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="5968b-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="5968b-138">**.NET SDK**</span><span class="sxs-lookup"><span data-stu-id="5968b-138">**.NET SDK**</span></span>\
<span data-ttu-id="5968b-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="5968b-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="5968b-140">**.NET Runtime**</span><span class="sxs-lookup"><span data-stu-id="5968b-140">**.NET Runtime**</span></span>\
<span data-ttu-id="5968b-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="5968b-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="5968b-142">Mais informações</span><span class="sxs-lookup"><span data-stu-id="5968b-142">More information</span></span>

<span data-ttu-id="5968b-143">Você pode ver as versões SDK `dotnet --info`e versões em tempo de execução com o comando .</span><span class="sxs-lookup"><span data-stu-id="5968b-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="5968b-144">Você também obterá outras informações relacionadas ao meio ambiente, como a versão do sistema operacional e o identificador de tempo de execução (RID).</span><span class="sxs-lookup"><span data-stu-id="5968b-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="5968b-145">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="5968b-145">Next steps</span></span>

- <span data-ttu-id="5968b-146">[Instale o .NET Core Runtime](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="5968b-146">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="5968b-147">[Instale o .NET Core SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="5968b-147">[Install the .NET Core SDK](sdk.md).</span></span>
