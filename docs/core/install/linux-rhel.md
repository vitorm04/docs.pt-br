---
title: Instalar o .NET no RHEL-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: cb03f84cf84557d467f0a067b8d5629a843ec7e3
ms.sourcegitcommit: c38bf879a2611ff46aacdd529b9f2725f93e18a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/13/2020
ms.locfileid: "94594562"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="b9712-103">Instalar o SDK do .NET ou o tempo de execução do .NET no RHEL</span><span class="sxs-lookup"><span data-stu-id="b9712-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="b9712-104">O .NET tem suporte no RHEL.</span><span class="sxs-lookup"><span data-stu-id="b9712-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="b9712-105">Este artigo descreve como instalar o .NET no RHEL.</span><span class="sxs-lookup"><span data-stu-id="b9712-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="b9712-106">Registrar sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="b9712-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="b9712-107">Para instalar o .NET do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat.</span><span class="sxs-lookup"><span data-stu-id="b9712-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="b9712-108">Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .net](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="b9712-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="b9712-109">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="b9712-109">Supported distributions</span></span>

<span data-ttu-id="b9712-110">A tabela a seguir é uma lista de versões do .NET com suporte no momento no RHEL 7 e RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="b9712-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="b9712-111">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do RHEL não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="b9712-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="b9712-112">Um ✔️ indica que a versão do RHEL ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="b9712-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="b9712-113">Um ❌ indica que a versão do RHEL ou .net não tem suporte nessa versão do RHEL.</span><span class="sxs-lookup"><span data-stu-id="b9712-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="b9712-114">Quando uma versão do RHEL e uma versão do .NET têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="b9712-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="b9712-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="b9712-115">RHEL</span></span>                     | <span data-ttu-id="b9712-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b9712-116">.NET Core 2.1</span></span> | <span data-ttu-id="b9712-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b9712-117">.NET Core 3.1</span></span> | <span data-ttu-id="b9712-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b9712-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="b9712-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="b9712-119">✔️ [8](#rhel-8-)</span></span>        | <span data-ttu-id="b9712-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b9712-120">✔️ 2.1</span></span>        | <span data-ttu-id="b9712-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="b9712-121">✔️ 3.1</span></span>        | <span data-ttu-id="b9712-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="b9712-122">✔️ 5.0</span></span> |
| <span data-ttu-id="b9712-123">✔️ [7](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="b9712-123">✔️ [7](#rhel-7--net-50)</span></span> | <span data-ttu-id="b9712-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="b9712-124">✔️ 2.1</span></span>        | <span data-ttu-id="b9712-125">✔️ [3,1](#rhel-7--net-core-31)</span><span class="sxs-lookup"><span data-stu-id="b9712-125">✔️ [3.1](#rhel-7--net-core-31)</span></span>        | <span data-ttu-id="b9712-126">✔️ [5,0](#rhel-7--net-50)</span><span class="sxs-lookup"><span data-stu-id="b9712-126">✔️ [5.0](#rhel-7--net-50)</span></span> |

<span data-ttu-id="b9712-127">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="b9712-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="b9712-128">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="b9712-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="b9712-129">3.0</span><span class="sxs-lookup"><span data-stu-id="b9712-129">3.0</span></span>
- <span data-ttu-id="b9712-130">2.2</span><span class="sxs-lookup"><span data-stu-id="b9712-130">2.2</span></span>
- <span data-ttu-id="b9712-131">2.0</span><span class="sxs-lookup"><span data-stu-id="b9712-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="b9712-132">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="b9712-132">How to install other versions</span></span>

<span data-ttu-id="b9712-133">Consulte a [documentação do Red Hat para .net](https://access.redhat.com/documentation/net/5.0/) nas etapas necessárias para instalar outras versões do .net.</span><span class="sxs-lookup"><span data-stu-id="b9712-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="b9712-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="b9712-134">RHEL 8 ✔️</span></span>

> [!TIP]
> <span data-ttu-id="b9712-135">O .NET 5,0 ainda não está disponível nos repositórios do AppStream, mas o .NET Core 3,1 é.</span><span class="sxs-lookup"><span data-stu-id="b9712-135">.NET 5.0 isn't yet available in the AppStream repositories, but .NET Core 3.1 is.</span></span> <span data-ttu-id="b9712-136">Para instalar o .NET Core 3,1, use o `dnf install` comando com o pacote apropriado, como `aspnetcore-runtime-3.1` ou `dotnet-sdk-3.1` .</span><span class="sxs-lookup"><span data-stu-id="b9712-136">To install .NET Core 3.1, use the `dnf install` command with the appropriate package, such as `aspnetcore-runtime-3.1` or `dotnet-sdk-3.1`.</span></span> <span data-ttu-id="b9712-137">As instruções a seguir são para o .NET 5,0.</span><span class="sxs-lookup"><span data-stu-id="b9712-137">The following instructions are for .NET 5.0.</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/8/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7--net-50"></a><span data-ttu-id="b9712-138">RHEL 7 ✔️ .NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b9712-138">RHEL 7 ✔️ .NET 5.0</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

```bash
sudo rpm --import https://packages.microsoft.com/keys/microsoft.asc
sudo wget -O /etc/yum.repos.d/microsoft-prod.repo https://packages.microsoft.com/config/rhel/7/prod.repo
```

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-yum.md)]

## <a name="rhel-7--net-core-31"></a><span data-ttu-id="b9712-139">RHEL 7 ✔️ .NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b9712-139">RHEL 7 ✔️ .NET Core 3.1</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="b9712-140">O comando a seguir instala o `scl-utils` pacote:</span><span class="sxs-lookup"><span data-stu-id="b9712-140">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="b9712-141">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="b9712-141">Install the SDK</span></span>

<span data-ttu-id="b9712-142">SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9712-142">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="b9712-143">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="b9712-143">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="b9712-144">Para instalar o SDK do .NET Core, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="b9712-144">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="b9712-145">O Red Hat não recomenda a habilitação permanente `rh-dotnet31` porque pode afetar outros programas.</span><span class="sxs-lookup"><span data-stu-id="b9712-145">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="b9712-146">Por exemplo, `rh-dotnet31` inclui uma versão do `libcurl` que difere da versão base do RHEL.</span><span class="sxs-lookup"><span data-stu-id="b9712-146">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="b9712-147">Isso pode levar a problemas em programas que não esperam uma versão diferente do `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="b9712-147">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="b9712-148">Se você quiser habilitar `rh-dotnet` permanentemente, adicione a seguinte linha ao seu arquivo _~/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="b9712-148">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="b9712-149">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="b9712-149">Install the runtime</span></span>

<span data-ttu-id="b9712-150">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b9712-150">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="b9712-151">Os comandos a seguir instalam o tempo de execução de ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b9712-151">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="b9712-152">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="b9712-152">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="b9712-153">O Red Hat não recomenda a habilitação permanente `rh-dotnet31-aspnetcore-runtime-3.1` porque pode afetar outros programas.</span><span class="sxs-lookup"><span data-stu-id="b9712-153">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="b9712-154">Por exemplo, `rh-dotnet31-aspnetcore-runtime-3.1` inclui uma versão do `libcurl` que difere da versão base do RHEL.</span><span class="sxs-lookup"><span data-stu-id="b9712-154">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="b9712-155">Isso pode levar a problemas em programas que não esperam uma versão diferente do `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="b9712-155">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="b9712-156">Se você quiser habilitar `rh-dotnet31-aspnetcore-runtime-3.1` permanentemente, adicione a seguinte linha ao seu arquivo _~/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="b9712-156">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="b9712-157">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core que não inclui suporte a ASP.NET Core: substitua `rh-dotnet31-aspnetcore-runtime-3.1` nos comandos acima por `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="b9712-157">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="b9712-158">Snap</span><span class="sxs-lookup"><span data-stu-id="b9712-158">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="b9712-159">Dependências</span><span class="sxs-lookup"><span data-stu-id="b9712-159">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="b9712-160">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="b9712-160">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="b9712-161">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="b9712-161">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="b9712-162">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="b9712-162">Next steps</span></span>

- [<span data-ttu-id="b9712-163">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="b9712-163">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
