---
title: Verificar as versões do .NET instaladas no Windows, Linux e macOS-.NET
description: Saiba como listar quais versões do .NET estão instaladas em seu computador. Isso inclui o .NET Runtime e o SDK.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: d924e5bc58052cd760f367e906666d68ab79b764
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507209"
---
# <a name="how-to-check-that-net-is-already-installed"></a><span data-ttu-id="d6fe3-104">Como verificar se o .NET já está instalado</span><span class="sxs-lookup"><span data-stu-id="d6fe3-104">How to check that .NET is already installed</span></span>

<span data-ttu-id="d6fe3-105">Este artigo ensina como verificar quais versões do .NET Runtime e do SDK estão instaladas no seu computador.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-105">This article teaches you how to check which versions of the .NET runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="d6fe3-106">O .NET pode já ter sido instalado se você tiver um ambiente de desenvolvimento integrado, como o Visual Studio ou o Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-106">.NET may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="d6fe3-107">A instalação de um SDK instala o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="d6fe3-108">Se qualquer comando deste artigo falhar, você não tem o tempo de execução ou o SDK instalado.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="d6fe3-109">Para obter mais informações, consulte os artigos de instalação para [Windows](windows.md), [MacOS](macos.md)ou [Linux](linux.md).</span><span class="sxs-lookup"><span data-stu-id="d6fe3-109">For more information, see the install articles for [Windows](windows.md), [macOS](macos.md), or [Linux](linux.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="d6fe3-110">Verificar versões do SDK</span><span class="sxs-lookup"><span data-stu-id="d6fe3-110">Check SDK versions</span></span>

<span data-ttu-id="d6fe3-111">Você pode ver quais versões do SDK do .NET estão instaladas atualmente com um terminal.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-111">You can see which versions of the .NET SDK are currently installed with a terminal.</span></span> <span data-ttu-id="d6fe3-112">Abra um terminal e execute o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="d6fe3-113">Você Obtém uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-113">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
2.1.500 [C:\program files\dotnet\sdk]
2.1.502 [C:\program files\dotnet\sdk]
2.1.504 [C:\program files\dotnet\sdk]
2.1.600 [C:\program files\dotnet\sdk]
2.1.602 [C:\program files\dotnet\sdk]
3.1.100 [C:\program files\dotnet\sdk]
5.0.100 [C:\program files\dotnet\sdk]
```

::: zone-end

::: zone pivot="os-linux"

```bash
2.1.500 [/home/user/dotnet/sdk]
2.1.502 [/home/user/dotnet/sdk]
2.1.504 [/home/user/dotnet/sdk]
2.1.600 [/home/user/dotnet/sdk]
2.1.602 [/home/user/dotnet/sdk]
3.1.100 [/home/user/dotnet/sdk]
5.0.100 [/home/user/dotnet/sdk]
```

::: zone-end

::: zone pivot="os-macos"

```bash
2.1.500 [/usr/local/share/dotnet/sdk]
2.1.502 [/usr/local/share/dotnet/sdk]
2.1.504 [/usr/local/share/dotnet/sdk]
2.1.600 [/usr/local/share/dotnet/sdk]
2.1.602 [/usr/local/share/dotnet/sdk]
3.1.100 [/usr/local/share/dotnet/sdk]
5.0.100 [/usr/local/share/dotnet/sdk]
```

::: zone-end

## <a name="check-runtime-versions"></a><span data-ttu-id="d6fe3-114">Verificar versões de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="d6fe3-114">Check runtime versions</span></span>

<span data-ttu-id="d6fe3-115">Você pode ver quais versões do tempo de execução do .NET estão instaladas no momento com o comando a seguir.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-115">You can see which versions of the .NET runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="d6fe3-116">Você Obtém uma saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-116">You get output similar to the following.</span></span>

::: zone pivot="os-windows"

```console
Microsoft.AspNetCore.All 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.WindowsDesktop.App 3.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 3.1.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
Microsoft.WindowsDesktop.App 5.0.0 [c:\program files\dotnet\shared\Microsoft.WindowsDesktop.App]
```

::: zone-end

::: zone pivot="os-linux"

```bash
Microsoft.AspNetCore.All 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/home/user/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

::: zone pivot="os-macos"

```bash
Microsoft.AspNetCore.All 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.1.7 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.13 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 3.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 5.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

::: zone-end

## <a name="check-for-install-folders"></a><span data-ttu-id="d6fe3-117">Verificar pastas de instalação</span><span class="sxs-lookup"><span data-stu-id="d6fe3-117">Check for install folders</span></span>

<span data-ttu-id="d6fe3-118">É possível que o .NET esteja instalado, mas não adicionado à `PATH` variável do seu sistema operacional ou perfil do usuário.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-118">It's possible that .NET is installed but not added to the `PATH` variable for your operating system or user profile.</span></span> <span data-ttu-id="d6fe3-119">A execução dos comandos das seções anteriores pode não funcionar.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-119">Running the commands from the previous sections may not work.</span></span> <span data-ttu-id="d6fe3-120">Como alternativa, você pode verificar se as pastas de instalação do .NET existem.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-120">As an alternative, you can check that the .NET install folders exist.</span></span>

<span data-ttu-id="d6fe3-121">Quando você instala o .NET de um instalador ou script, ele é instalado em uma pasta padrão.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-121">When you install .NET from an installer or script, it's installed to a standard folder.</span></span> <span data-ttu-id="d6fe3-122">Na maior parte do tempo, o instalador ou o script que você está usando para instalar o .NET oferece uma opção para instalar em uma pasta diferente.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-122">Much of the time the installer or script you're using to install .NET gives you an option to install to a different folder.</span></span> <span data-ttu-id="d6fe3-123">Se você optar por instalar o em uma pasta diferente, ajuste o início do caminho da pasta.</span><span class="sxs-lookup"><span data-stu-id="d6fe3-123">If you choose to install to a different folder, adjust the start of the folder path.</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="d6fe3-124">**executável dotnet**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-124">**dotnet executable**</span></span>\
<span data-ttu-id="d6fe3-125">_C: \\ arquivos de programas \\ dotnet \\dotnet.exe_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-125">_C:\\program files\\dotnet\\dotnet.exe_</span></span>

- <span data-ttu-id="d6fe3-126">**SDK DO .NET**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-126">**.NET SDK**</span></span>\
<span data-ttu-id="d6fe3-127">_C: \\ arquivos de \\ programas \\ SDK do dotnet \\ {versão}\\_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-127">_C:\\program files\\dotnet\\sdk\\{version}\\_</span></span>

- <span data-ttu-id="d6fe3-128">**Tempo de execução do .NET**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-128">**.NET Runtime**</span></span>\
<span data-ttu-id="d6fe3-129">_C: \\ arquivos de programas \\ dotnet \\ compartilhado \\ {tipo de tempo de execução} \\ {versão}\\_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-129">_C:\\program files\\dotnet\\shared\\{runtime-type}\\{version}\\_</span></span>

::: zone-end

::: zone pivot="os-linux"

- <span data-ttu-id="d6fe3-130">**executável dotnet**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-130">**dotnet executable**</span></span>\
<span data-ttu-id="d6fe3-131">_/home/user/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-131">_/home/user/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="d6fe3-132">**SDK DO .NET**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-132">**.NET SDK**</span></span>\
<span data-ttu-id="d6fe3-133">_/home/user/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-133">_/home/user/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="d6fe3-134">**Tempo de execução do .NET**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-134">**.NET Runtime**</span></span>\
<span data-ttu-id="d6fe3-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-135">_/home/user/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="d6fe3-136">**executável dotnet**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-136">**dotnet executable**</span></span>\
<span data-ttu-id="d6fe3-137">_/usr/local/share/dotnet/dotnet_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-137">_/usr/local/share/dotnet/dotnet_</span></span>

- <span data-ttu-id="d6fe3-138">**SDK DO .NET**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-138">**.NET SDK**</span></span>\
<span data-ttu-id="d6fe3-139">_/usr/local/share/dotnet/sdk/{version}/_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-139">_/usr/local/share/dotnet/sdk/{version}/_</span></span>

- <span data-ttu-id="d6fe3-140">**Tempo de execução do .NET**</span><span class="sxs-lookup"><span data-stu-id="d6fe3-140">**.NET Runtime**</span></span>\
<span data-ttu-id="d6fe3-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span><span class="sxs-lookup"><span data-stu-id="d6fe3-141">_/usr/local/share/dotnet/shared/{runtime-type}/{version}/_</span></span>

::: zone-end

## <a name="more-information"></a><span data-ttu-id="d6fe3-142">Mais informações</span><span class="sxs-lookup"><span data-stu-id="d6fe3-142">More information</span></span>

<span data-ttu-id="d6fe3-143">Você pode ver as versões do SDK e as versões de tempo de execução com o comando `dotnet --info` .</span><span class="sxs-lookup"><span data-stu-id="d6fe3-143">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="d6fe3-144">Você também obterá outras informações relacionadas ao ambiente, como a versão do sistema operacional e o RID (identificador de tempo de execução).</span><span class="sxs-lookup"><span data-stu-id="d6fe3-144">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="d6fe3-145">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="d6fe3-145">Next steps</span></span>

- <span data-ttu-id="d6fe3-146">[Instale o tempo de execução e o SDK do .net para Windows](windows.md).</span><span class="sxs-lookup"><span data-stu-id="d6fe3-146">[Install the .NET Runtime and SDK for Windows](windows.md).</span></span>
- <span data-ttu-id="d6fe3-147">[Instale o tempo de execução e o SDK do .net para MacOS](linux.md).</span><span class="sxs-lookup"><span data-stu-id="d6fe3-147">[Install the .NET Runtime and SDK for MacOS](linux.md).</span></span>
- <span data-ttu-id="d6fe3-148">[Instale o tempo de execução e o SDK do .net para Linux](macos.md).</span><span class="sxs-lookup"><span data-stu-id="d6fe3-148">[Install the .NET Runtime and SDK for Linux](macos.md).</span></span>
