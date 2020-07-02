---
title: Instalar o .NET Core no RHEL-.NET Core
description: Demonstra as várias maneiras de instalar o SDK do .NET Core e o tempo de execução do .NET Core no RHEL.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 9e4d0ab86355329b898a82f135b9eeb839eab1cb
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85619436"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-rhel"></a><span data-ttu-id="4bda2-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no RHEL</span><span class="sxs-lookup"><span data-stu-id="4bda2-103">Install .NET Core SDK or .NET Core Runtime on RHEL</span></span>

<span data-ttu-id="4bda2-104">O .NET Core tem suporte no RHEL.</span><span class="sxs-lookup"><span data-stu-id="4bda2-104">.NET Core is supported on RHEL.</span></span> <span data-ttu-id="4bda2-105">Este artigo descreve como instalar o .NET Core no RHEL.</span><span class="sxs-lookup"><span data-stu-id="4bda2-105">This article describes how to install .NET Core on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="4bda2-106">Registrar sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="4bda2-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="4bda2-107">Para instalar o .NET Core do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat.</span><span class="sxs-lookup"><span data-stu-id="4bda2-107">To install .NET Core from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="4bda2-108">Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/).</span><span class="sxs-lookup"><span data-stu-id="4bda2-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET Core](https://access.redhat.com/documentation/net_core/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="4bda2-109">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="4bda2-109">Supported distributions</span></span>

<span data-ttu-id="4bda2-110">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento no RHEL 7 e RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="4bda2-110">The following table is a list of currently supported .NET Core releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="4bda2-111">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do RHEL não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="4bda2-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="4bda2-112">Um ✔️ indica que a versão do RHEL ou do .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="4bda2-112">A ✔️ indicates that the version of RHEL or .NET Core is still supported.</span></span>
- <span data-ttu-id="4bda2-113">Um ❌ indica que a versão do RHEL ou do .NET Core não tem suporte nessa versão do RHEL.</span><span class="sxs-lookup"><span data-stu-id="4bda2-113">A ❌ indicates that the version of RHEL or .NET Core isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="4bda2-114">Quando uma versão do RHEL e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="4bda2-114">When both a version of RHEL and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="4bda2-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="4bda2-115">RHEL</span></span>                   | <span data-ttu-id="4bda2-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="4bda2-116">.NET Core 2.1</span></span> | <span data-ttu-id="4bda2-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="4bda2-117">.NET Core 3.1</span></span> | <span data-ttu-id="4bda2-118">Versão prévia do .NET 5 (somente instalação manual)</span><span class="sxs-lookup"><span data-stu-id="4bda2-118">.NET 5 Preview (manual install only)</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="4bda2-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="4bda2-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="4bda2-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="4bda2-120">✔️ 2.1</span></span>        | <span data-ttu-id="4bda2-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="4bda2-121">✔️ 3.1</span></span>        | <span data-ttu-id="4bda2-122">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="4bda2-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="4bda2-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="4bda2-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="4bda2-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="4bda2-124">✔️ 2.1</span></span>        | <span data-ttu-id="4bda2-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="4bda2-125">✔️ 3.1</span></span>        | <span data-ttu-id="4bda2-126">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="4bda2-126">✔️ 5.0 Preview</span></span> |

<span data-ttu-id="4bda2-127">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bda2-127">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="4bda2-128">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="4bda2-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="4bda2-129">3.0</span><span class="sxs-lookup"><span data-stu-id="4bda2-129">3.0</span></span>
- <span data-ttu-id="4bda2-130">2.2</span><span class="sxs-lookup"><span data-stu-id="4bda2-130">2.2</span></span>
- <span data-ttu-id="4bda2-131">2,0</span><span class="sxs-lookup"><span data-stu-id="4bda2-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="4bda2-132">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="4bda2-132">How to install other versions</span></span>

<span data-ttu-id="4bda2-133">Consulte a [documentação do Red Hat para .NET Core](https://access.redhat.com/documentation/net_core/) sobre as etapas necessárias para instalar outras versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bda2-133">Consult the [Red Hat documentation for .NET Core](https://access.redhat.com/documentation/net_core/) on the steps required to install other releases of .NET Core.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="4bda2-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="4bda2-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="4bda2-135">O .NET Core está incluído nos repositórios do AppStream para RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="4bda2-135">.NET Core is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-31](includes/linux-install-31-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="4bda2-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="4bda2-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="4bda2-137">O comando a seguir instala o `scl-utils` pacote:</span><span class="sxs-lookup"><span data-stu-id="4bda2-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="4bda2-138">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="4bda2-138">Install the SDK</span></span>

<span data-ttu-id="4bda2-139">SDK do .NET Core permite que você desenvolva aplicativos com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bda2-139">.NET Core SDK allows you to develop apps with .NET Core.</span></span> <span data-ttu-id="4bda2-140">Se você instalar SDK do .NET Core, não será necessário instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="4bda2-140">If you install .NET Core SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="4bda2-141">Para instalar o SDK do .NET Core, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="4bda2-141">To install .NET Core SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31 -y
scl enable rh-dotnet31 bash
```

<span data-ttu-id="4bda2-142">O Red Hat não recomenda a habilitação permanente `rh-dotnet31` porque pode afetar outros programas.</span><span class="sxs-lookup"><span data-stu-id="4bda2-142">Red Hat does not recommend permanently enabling `rh-dotnet31` because it may affect other programs.</span></span> <span data-ttu-id="4bda2-143">Por exemplo, `rh-dotnet31` inclui uma versão do `libcurl` que difere da versão base do RHEL.</span><span class="sxs-lookup"><span data-stu-id="4bda2-143">For example, `rh-dotnet31` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="4bda2-144">Isso pode levar a problemas em programas que não esperam uma versão diferente do `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="4bda2-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="4bda2-145">Se você quiser habilitar `rh-dotnet` permanentemente, adicione a seguinte linha ao seu arquivo _~/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="4bda2-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31
```

### <a name="install-the-runtime"></a><span data-ttu-id="4bda2-146">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="4bda2-146">Install the runtime</span></span>

<span data-ttu-id="4bda2-147">O tempo de execução do .NET Core permite executar aplicativos que foram feitos com o .NET Core que não incluiu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4bda2-147">The .NET Core Runtime allows you to run apps that were made with .NET Core that didn't include the runtime.</span></span> <span data-ttu-id="4bda2-148">Os comandos a seguir instalam o tempo de execução de ASP.NET Core, que é o tempo de execução mais compatível para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4bda2-148">The commands below install the ASP.NET Core Runtime, which is the most compatible runtime for .NET Core.</span></span> <span data-ttu-id="4bda2-149">Em seu terminal, execute os comandos a seguir.</span><span class="sxs-lookup"><span data-stu-id="4bda2-149">In your terminal, run the following commands.</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet31-aspnetcore-runtime-3.1 -y
scl enable rh-dotnet31-aspnetcore-runtime-3.1 bash
```

<span data-ttu-id="4bda2-150">O Red Hat não recomenda a habilitação permanente `rh-dotnet31-aspnetcore-runtime-3.1` porque pode afetar outros programas.</span><span class="sxs-lookup"><span data-stu-id="4bda2-150">Red Hat does not recommend permanently enabling `rh-dotnet31-aspnetcore-runtime-3.1` because it may affect other programs.</span></span> <span data-ttu-id="4bda2-151">Por exemplo, `rh-dotnet31-aspnetcore-runtime-3.1` inclui uma versão do `libcurl` que difere da versão base do RHEL.</span><span class="sxs-lookup"><span data-stu-id="4bda2-151">For example, `rh-dotnet31-aspnetcore-runtime-3.1` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="4bda2-152">Isso pode levar a problemas em programas que não esperam uma versão diferente do `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="4bda2-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="4bda2-153">Se você quiser habilitar `rh-dotnet31-aspnetcore-runtime-3.1` permanentemente, adicione a seguinte linha ao seu arquivo _~/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="4bda2-153">If you want to enable `rh-dotnet31-aspnetcore-runtime-3.1` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet31-aspnetcore-runtime-3.1
```

<span data-ttu-id="4bda2-154">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET Core que não inclui suporte a ASP.NET Core: substitua `rh-dotnet31-aspnetcore-runtime-3.1` nos comandos acima por `rh-dotnet31-dotnet-runtime-3.1` .</span><span class="sxs-lookup"><span data-stu-id="4bda2-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Core Runtime that doesn't include ASP.NET Core support: replace `rh-dotnet31-aspnetcore-runtime-3.1` in the commands above with `rh-dotnet31-dotnet-runtime-3.1`.</span></span>

## <a name="snap"></a><span data-ttu-id="4bda2-155">Snap</span><span class="sxs-lookup"><span data-stu-id="4bda2-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="4bda2-156">Dependências</span><span class="sxs-lookup"><span data-stu-id="4bda2-156">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="4bda2-157">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="4bda2-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="4bda2-158">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="4bda2-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="4bda2-159">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="4bda2-159">Next steps</span></span>

- [<span data-ttu-id="4bda2-160">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bda2-160">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
