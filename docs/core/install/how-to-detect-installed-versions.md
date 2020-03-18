---
title: Verifique as versões instaladas do .NET Core no Windows, Linux e macOS - .NET Core
description: Saiba como listar quais versões do .NET Core estão instaladas no seu computador. Isso inclui o tempo de execução do .NET Core e o SDK.
author: thraka
ms.author: adegeo
ms.date: 12/04/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 3efc54cea7e10bc21a472a7fa9d4026e305be79a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399031"
---
# <a name="how-to-check-that-net-core-is-already-installed"></a><span data-ttu-id="99399-104">Como verificar se o .NET Core já está instalado</span><span class="sxs-lookup"><span data-stu-id="99399-104">How to check that .NET Core is already installed</span></span>

<span data-ttu-id="99399-105">Este artigo ensina como verificar quais versões do .NET Core runtime e SDK estão instaladas no seu computador.</span><span class="sxs-lookup"><span data-stu-id="99399-105">This article teaches you how to check which versions of the .NET Core runtime and SDK are installed on your computer.</span></span> <span data-ttu-id="99399-106">O núcleo .NET pode já ter sido instalado se você tiver um ambiente de desenvolvimento integrado, como o Visual Studio ou o Visual Studio para Mac.</span><span class="sxs-lookup"><span data-stu-id="99399-106">.NET core may have already been installed if you have an integrated development environment, such as Visual Studio or Visual Studio for Mac.</span></span>

<span data-ttu-id="99399-107">A instalação de um SDK instala o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="99399-107">Installing an SDK installs the corresponding runtime.</span></span>

<span data-ttu-id="99399-108">Se algum comando neste artigo falhar, você não terá o tempo de execução ou SDK instalado.</span><span class="sxs-lookup"><span data-stu-id="99399-108">If any command in this article fails, you don't have the runtime or SDK installed.</span></span> <span data-ttu-id="99399-109">Para obter mais informações, consulte [Baixar e instalar o .NET Core](index.md).</span><span class="sxs-lookup"><span data-stu-id="99399-109">For more information, see [Download and install .NET Core](index.md).</span></span>

## <a name="check-sdk-versions"></a><span data-ttu-id="99399-110">Confira as versões do SDK</span><span class="sxs-lookup"><span data-stu-id="99399-110">Check SDK versions</span></span>

<span data-ttu-id="99399-111">Você pode ver quais versões do .NET Core SDK estão atualmente instaladas com um terminal.</span><span class="sxs-lookup"><span data-stu-id="99399-111">You can see which versions of the .NET Core SDK are currently installed with a terminal.</span></span> <span data-ttu-id="99399-112">Abra um terminal e execute o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="99399-112">Open a terminal and run the following command.</span></span>

```dotnetcli
dotnet --list-sdks
```

<span data-ttu-id="99399-113">Você tem saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="99399-113">You get output similar to the following.</span></span>

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

## <a name="check-runtime-versions"></a><span data-ttu-id="99399-114">Verifique as versões em tempo de execução</span><span class="sxs-lookup"><span data-stu-id="99399-114">Check runtime versions</span></span>

<span data-ttu-id="99399-115">Você pode ver quais versões do tempo de execução do .NET Core estão atualmente instaladas com o seguinte comando.</span><span class="sxs-lookup"><span data-stu-id="99399-115">You can see which versions of the .NET Core runtime are currently installed with the following command.</span></span>

```dotnetcli
dotnet --list-runtimes
```

<span data-ttu-id="99399-116">Você tem saída semelhante à seguinte.</span><span class="sxs-lookup"><span data-stu-id="99399-116">You get output similar to the following.</span></span>

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

## <a name="more-information"></a><span data-ttu-id="99399-117">Mais informações</span><span class="sxs-lookup"><span data-stu-id="99399-117">More information</span></span>

<span data-ttu-id="99399-118">Você pode ver as versões SDK `dotnet --info`e versões em tempo de execução com o comando .</span><span class="sxs-lookup"><span data-stu-id="99399-118">You can see both the SDK versions and runtime versions with the command `dotnet --info`.</span></span> <span data-ttu-id="99399-119">Você também obterá outras informações relacionadas ao meio ambiente, como a versão do sistema operacional e o identificador de tempo de execução (RID).</span><span class="sxs-lookup"><span data-stu-id="99399-119">You'll also get other environmental related information, such as the operating system version and runtime identifier (RID).</span></span>

## <a name="next-steps"></a><span data-ttu-id="99399-120">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="99399-120">Next steps</span></span>

- <span data-ttu-id="99399-121">[Instale o .NET Core Runtime](runtime.md).</span><span class="sxs-lookup"><span data-stu-id="99399-121">[Install the .NET Core Runtime](runtime.md).</span></span>
- <span data-ttu-id="99399-122">[Instale o .NET Core SDK](sdk.md).</span><span class="sxs-lookup"><span data-stu-id="99399-122">[Install the .NET Core SDK](sdk.md).</span></span>
