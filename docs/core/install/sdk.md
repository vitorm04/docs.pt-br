---
title: Install .NET Core SDK on Windows, Linux, and macOS - .NET Core
description: Learn how to install .NET Core on Windows, Linux, and macOS. Discover the dependencies required to develop .NET Core apps.
author: thraka
ms.author: adegeo
ms.date: 11/06/2019
ms.custom: updateeachrelease
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 2f65e9dc39a4cd1076af1a70dfedfa671f20b42d
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450873"
---
# <a name="install-the-net-core-sdk"></a><span data-ttu-id="b25d2-104">Install the .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="b25d2-104">Install the .NET Core SDK</span></span>

<span data-ttu-id="b25d2-105">In this article, you'll learn how to install the .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="b25d2-105">In this article, you'll learn how to install the .NET Core SDK.</span></span> <span data-ttu-id="b25d2-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span><span class="sxs-lookup"><span data-stu-id="b25d2-106">The .NET Core SDK is used to create .NET Core apps and libraries.</span></span> <span data-ttu-id="b25d2-107">The .NET Core runtime is always installed with the SDK.</span><span class="sxs-lookup"><span data-stu-id="b25d2-107">The .NET Core runtime is always installed with the SDK.</span></span>

<span data-ttu-id="b25d2-108">You can download and install .NET Core directly with one of the following links:</span><span class="sxs-lookup"><span data-stu-id="b25d2-108">You can download and install .NET Core directly with one of the following links:</span></span>

- [<span data-ttu-id="b25d2-109">.NET Core 3.1 Preview 3 downloads</span><span class="sxs-lookup"><span data-stu-id="b25d2-109">.NET Core 3.1 Preview 3 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
- [<span data-ttu-id="b25d2-110">.NET Core 3.0 downloads</span><span class="sxs-lookup"><span data-stu-id="b25d2-110">.NET Core 3.0 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.0)
- [<span data-ttu-id="b25d2-111">.NET Core 2.2 downloads</span><span class="sxs-lookup"><span data-stu-id="b25d2-111">.NET Core 2.2 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.2)
- [<span data-ttu-id="b25d2-112">.NET Core 2.1 downloads</span><span class="sxs-lookup"><span data-stu-id="b25d2-112">.NET Core 2.1 downloads</span></span>](https://dotnet.microsoft.com/download/dotnet-core/2.1)

<span data-ttu-id="b25d2-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span><span class="sxs-lookup"><span data-stu-id="b25d2-113">You can also install .NET Core as part of an integrated development environment (IDE), detailed in the sections below.</span></span>

## <a name="install-with-an-installer"></a><span data-ttu-id="b25d2-114">Install with an installer</span><span class="sxs-lookup"><span data-stu-id="b25d2-114">Install with an installer</span></span>

<span data-ttu-id="b25d2-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="b25d2-115">Both Windows and macOS have standalone installers that can be used to install the .NET Core 3.0 SDK.</span></span>

- <span data-ttu-id="b25d2-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span><span class="sxs-lookup"><span data-stu-id="b25d2-116">Windows [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x64-installer) | [x32 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-windows-x86-installer)</span></span>
- <span data-ttu-id="b25d2-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span><span class="sxs-lookup"><span data-stu-id="b25d2-117">macOS [x64 CPUs](https://dotnet.microsoft.com/download/thank-you/dotnet-sdk-3.0.100-macos-x64-installer)</span></span>

::: zone pivot="os-linux"

## <a name="install-with-a-package-manager"></a><span data-ttu-id="b25d2-118">Install with a package manager</span><span class="sxs-lookup"><span data-stu-id="b25d2-118">Install with a package manager</span></span>

<span data-ttu-id="b25d2-119">You can install the .NET Core SDK with many of the common Linux package managers.</span><span class="sxs-lookup"><span data-stu-id="b25d2-119">You can install the .NET Core SDK with many of the common Linux package managers.</span></span> <span data-ttu-id="b25d2-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-120">For more information, see [Linux Package Manager - Install .NET Core](linux-package-manager-rhel7.md).</span></span>

::: zone-end

::: zone pivot="os-windows"

## <a name="install-with-visual-studio"></a><span data-ttu-id="b25d2-121">Install with Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b25d2-121">Install with Visual Studio</span></span>

<span data-ttu-id="b25d2-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span><span class="sxs-lookup"><span data-stu-id="b25d2-122">If you're using Visual Studio to develop .NET Core apps, the following table describes the minimum required version of Visual Studio based on the target .NET Core SDK version.</span></span>

| <span data-ttu-id="b25d2-123">.NET Core SDK version</span><span class="sxs-lookup"><span data-stu-id="b25d2-123">.NET Core SDK version</span></span> | <span data-ttu-id="b25d2-124">Versão do Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b25d2-124">Visual Studio version</span></span>                      |
| --------------------- | ------------------------------------------ |
| <span data-ttu-id="b25d2-125">3.0</span><span class="sxs-lookup"><span data-stu-id="b25d2-125">3.0</span></span>                   | <span data-ttu-id="b25d2-126">Visual Studio 2019 version 16.3 or higher.</span><span class="sxs-lookup"><span data-stu-id="b25d2-126">Visual Studio 2019 version 16.3 or higher.</span></span> |
| <span data-ttu-id="b25d2-127">2.2</span><span class="sxs-lookup"><span data-stu-id="b25d2-127">2.2</span></span>                   | <span data-ttu-id="b25d2-128">Visual Studio 2017 version 15.9 or higher.</span><span class="sxs-lookup"><span data-stu-id="b25d2-128">Visual Studio 2017 version 15.9 or higher.</span></span> |
| <span data-ttu-id="b25d2-129">2.1</span><span class="sxs-lookup"><span data-stu-id="b25d2-129">2.1</span></span>                   | <span data-ttu-id="b25d2-130">Visual Studio 2017 version 15.7 or higher.</span><span class="sxs-lookup"><span data-stu-id="b25d2-130">Visual Studio 2017 version 15.7 or higher.</span></span> |

<span data-ttu-id="b25d2-131">If you already have Visual Studio installed, you can check your version with the following steps.</span><span class="sxs-lookup"><span data-stu-id="b25d2-131">If you already have Visual Studio installed, you can check your version with the following steps.</span></span>

01. <span data-ttu-id="b25d2-132">Abra o Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b25d2-132">Open Visual Studio.</span></span>
01. <span data-ttu-id="b25d2-133">Select **Help** > **About Microsoft Visual Studio**.</span><span class="sxs-lookup"><span data-stu-id="b25d2-133">Select **Help** > **About Microsoft Visual Studio**.</span></span>
01. <span data-ttu-id="b25d2-134">Read the version number from the **About** dialog.</span><span class="sxs-lookup"><span data-stu-id="b25d2-134">Read the version number from the **About** dialog.</span></span>

<span data-ttu-id="b25d2-135">Visual Studio can install the latest .NET Core SDK and runtime.</span><span class="sxs-lookup"><span data-stu-id="b25d2-135">Visual Studio can install the latest .NET Core SDK and runtime.</span></span>

- <span data-ttu-id="b25d2-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span><span class="sxs-lookup"><span data-stu-id="b25d2-136">[Download Visual Studio](https://www.visualstudio.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=button+cta&utm_content=download+vs2019).</span></span>

### <a name="select-a-workload"></a><span data-ttu-id="b25d2-137">Select a workload</span><span class="sxs-lookup"><span data-stu-id="b25d2-137">Select a workload</span></span>

<span data-ttu-id="b25d2-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span><span class="sxs-lookup"><span data-stu-id="b25d2-138">When installing or modifying Visual Studio, select one of the following workloads, depending on the kind of application you're building:</span></span>

- <span data-ttu-id="b25d2-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span><span class="sxs-lookup"><span data-stu-id="b25d2-139">The **.NET Core cross-platform development** workload in the **Other Toolsets** section.</span></span>
- <span data-ttu-id="b25d2-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span><span class="sxs-lookup"><span data-stu-id="b25d2-140">The **ASP.NET and web development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="b25d2-141">The **Azure development** workload in the **Web & Cloud** section.</span><span class="sxs-lookup"><span data-stu-id="b25d2-141">The **Azure development** workload in the **Web & Cloud** section.</span></span>
- <span data-ttu-id="b25d2-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span><span class="sxs-lookup"><span data-stu-id="b25d2-142">The **.NET desktop development** workload in the **Desktop & Mobile** section.</span></span>

<span data-ttu-id="b25d2-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="b25d2-143">[![Windows Visual Studio 2019 with .NET Core workload](media/install-sdk/windows-install-visual-studio-2019.png)](media/install-sdk/windows-install-visual-studio-2019.png#lightbox)</span></span>

::: zone-end

::: zone pivot="os-macos"

## <a name="install-with-visual-studio-for-mac"></a><span data-ttu-id="b25d2-144">Install with Visual Studio for Mac</span><span class="sxs-lookup"><span data-stu-id="b25d2-144">Install with Visual Studio for Mac</span></span>

<span data-ttu-id="b25d2-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span><span class="sxs-lookup"><span data-stu-id="b25d2-145">Visual Studio for Mac installs the .NET Core SDK when the **.NET Core** workload is selected.</span></span> <span data-ttu-id="b25d2-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span><span class="sxs-lookup"><span data-stu-id="b25d2-146">To get started with .NET Core development on macOS, see [Install Visual Studio 2019 for Mac](/visualstudio/mac/installation).</span></span>

<span data-ttu-id="b25d2-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span><span class="sxs-lookup"><span data-stu-id="b25d2-147">[![macOS Visual Studio 2019 for Mac with .NET Core workload feature](media/install-sdk/mac-install-selection.png)](media/install-sdk/mac-install-selection.png#lightbox)</span></span>

::: zone-end

## <a name="install-from-visual-studio-code"></a><span data-ttu-id="b25d2-148">Install from Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b25d2-148">Install from Visual Studio Code</span></span>

<span data-ttu-id="b25d2-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span><span class="sxs-lookup"><span data-stu-id="b25d2-149">Visual Studio Code is a powerful and lightweight source code editor that runs on your desktop.</span></span> <span data-ttu-id="b25d2-150">Visual Studio Code is available for Windows, macOS, and Linux.</span><span class="sxs-lookup"><span data-stu-id="b25d2-150">Visual Studio Code is available for Windows, macOS, and Linux.</span></span>

<span data-ttu-id="b25d2-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span><span class="sxs-lookup"><span data-stu-id="b25d2-151">While Visual Studio Code doesn't come with .NET Core support, adding .NET Core support is simple.</span></span>

01. <span data-ttu-id="b25d2-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span><span class="sxs-lookup"><span data-stu-id="b25d2-152">[Download and install Visual Studio Code](https://code.visualstudio.com/Download).</span></span>
01. <span data-ttu-id="b25d2-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span><span class="sxs-lookup"><span data-stu-id="b25d2-153">[Download and install the .NET Core SDK](https://dotnet.microsoft.com/download/dotnet-core/3.0).</span></span>
01. <span data-ttu-id="b25d2-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span><span class="sxs-lookup"><span data-stu-id="b25d2-154">[Install the C# extension from the Visual Studio Code marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.csharp).</span></span>

::: zone pivot="os-windows"

## <a name="install-with-powershell-automation"></a><span data-ttu-id="b25d2-155">Install with PowerShell automation</span><span class="sxs-lookup"><span data-stu-id="b25d2-155">Install with PowerShell automation</span></span>

<span data-ttu-id="b25d2-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span><span class="sxs-lookup"><span data-stu-id="b25d2-156">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="b25d2-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-157">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b25d2-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="b25d2-158">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="b25d2-159">To install the current release of .NET Core, run the script with the following switch.</span><span class="sxs-lookup"><span data-stu-id="b25d2-159">To install the current release of .NET Core, run the script with the following switch.</span></span>

```powershell
dotnet-install.ps1 -Channel Current
```

::: zone-end

::: zone pivot="os-linux,os-macos"

## <a name="install-with-bash-automation"></a><span data-ttu-id="b25d2-160">Install with bash automation</span><span class="sxs-lookup"><span data-stu-id="b25d2-160">Install with bash automation</span></span>

<span data-ttu-id="b25d2-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span><span class="sxs-lookup"><span data-stu-id="b25d2-161">The [dotnet-install scripts](../tools/dotnet-install-script.md) are used for automation and non-admin installs of the SDK.</span></span> <span data-ttu-id="b25d2-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-162">You can download the script from the [dotnet-install script reference page](../tools/dotnet-install-script.md).</span></span>

<span data-ttu-id="b25d2-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="b25d2-163">The script defaults to installing the latest [long term support (LTS)](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) version, which is .NET Core 2.1.</span></span> <span data-ttu-id="b25d2-164">To install the current release of .NET Core, run the script with the following switch.</span><span class="sxs-lookup"><span data-stu-id="b25d2-164">To install the current release of .NET Core, run the script with the following switch.</span></span>

```bash
./dotnet-install.sh -c Current
```

::: zone-end

## <a name="docker"></a><span data-ttu-id="b25d2-165">Docker</span><span class="sxs-lookup"><span data-stu-id="b25d2-165">Docker</span></span>

<span data-ttu-id="b25d2-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span><span class="sxs-lookup"><span data-stu-id="b25d2-166">Containers provide a lightweight way to isolate your application from the rest of the host system.</span></span> <span data-ttu-id="b25d2-167">Containers on the same machine share just the kernel and use resources given to your application.</span><span class="sxs-lookup"><span data-stu-id="b25d2-167">Containers on the same machine share just the kernel and use resources given to your application.</span></span>

<span data-ttu-id="b25d2-168">.NET Core can run in a Docker container.</span><span class="sxs-lookup"><span data-stu-id="b25d2-168">.NET Core can run in a Docker container.</span></span> <span data-ttu-id="b25d2-169">As imagens oficiais do Docker do .NET Core são publicadas no MCR (Registro de Contêiner da Microsoft) e podem ser encontradas no [repositório do Hub do Docker do .NET Core da Microsoft](https://hub.docker.com/_/microsoft-dotnet-core/).</span><span class="sxs-lookup"><span data-stu-id="b25d2-169">Official .NET Core Docker images are published to the Microsoft Container Registry (MCR) and are discoverable at the [Microsoft .NET Core Docker Hub repository](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span> <span data-ttu-id="b25d2-170">Cada repositório contém imagens para diferentes combinações do .NET (SDK ou Runtime) e do sistema operacional que você pode usar.</span><span class="sxs-lookup"><span data-stu-id="b25d2-170">Each repository contains images for different combinations of the .NET (SDK or Runtime) and OS that you can use.</span></span>

<span data-ttu-id="b25d2-171">A Microsoft fornece imagens personalizadas para cenários específicos.</span><span class="sxs-lookup"><span data-stu-id="b25d2-171">Microsoft provides images that are tailored for specific scenarios.</span></span> <span data-ttu-id="b25d2-172">Por exemplo, o [repositório do ASP.NET Core](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) fornece imagens que são criadas para a execução de aplicativos ASP.NET Core na produção.</span><span class="sxs-lookup"><span data-stu-id="b25d2-172">For example, the [ASP.NET Core repository](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) provides images that are built for running ASP.NET Core apps in production.</span></span>

<span data-ttu-id="b25d2-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-173">For more information about using .NET Core in a Docker container, see [Introduction to .NET and Docker](../docker/introduction.md) and [Samples](https://github.com/dotnet/dotnet-docker/blob/master/samples/README.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="b25d2-174">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b25d2-174">Next steps</span></span>

::: zone pivot="os-windows"

- <span data-ttu-id="b25d2-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-175">[Tutorial: C# Hello World tutorial](../tutorials/with-visual-studio.md).</span></span>
- <span data-ttu-id="b25d2-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-176">[Tutorial: Visual Basic Hello World tutorial](../tutorials/vb-with-visual-studio.md).</span></span>
- <span data-ttu-id="b25d2-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="b25d2-177">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="b25d2-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-178">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end

::: zone pivot="os-macos"

- <span data-ttu-id="b25d2-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-179">[Tutorial: Get started on macOS](../tutorials/using-on-mac-vs.md).</span></span>
- <span data-ttu-id="b25d2-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span><span class="sxs-lookup"><span data-stu-id="b25d2-180">[Tutorial: Create a new app with Visual Studio Code](https://code.visualstudio.com/docs/languages/dotnet).</span></span>
- <span data-ttu-id="b25d2-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span><span class="sxs-lookup"><span data-stu-id="b25d2-181">[Tutorial: Containerize a .NET Core app](../docker/build-container.md).</span></span>

::: zone-end
