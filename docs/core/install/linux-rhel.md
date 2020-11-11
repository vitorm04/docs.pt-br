---
title: Instalar o .NET no RHEL-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET no RHEL.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: a742497bba3459a4d8772f5c9e3d915b5b18e62e
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506916"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-rhel"></a><span data-ttu-id="1401b-103">Instalar o SDK do .NET ou o tempo de execução do .NET no RHEL</span><span class="sxs-lookup"><span data-stu-id="1401b-103">Install the .NET SDK or the .NET Runtime on RHEL</span></span>

<span data-ttu-id="1401b-104">O .NET tem suporte no RHEL.</span><span class="sxs-lookup"><span data-stu-id="1401b-104">.NET is supported on RHEL.</span></span> <span data-ttu-id="1401b-105">Este artigo descreve como instalar o .NET no RHEL.</span><span class="sxs-lookup"><span data-stu-id="1401b-105">This article describes how to install .NET on RHEL.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

## <a name="register-your-red-hat-subscription"></a><span data-ttu-id="1401b-106">Registrar sua assinatura do Red Hat</span><span class="sxs-lookup"><span data-stu-id="1401b-106">Register your Red Hat subscription</span></span>

<span data-ttu-id="1401b-107">Para instalar o .NET do Red Hat no RHEL, primeiro você precisa se registrar usando o Gerenciador de assinaturas do Red Hat.</span><span class="sxs-lookup"><span data-stu-id="1401b-107">To install .NET from Red Hat on RHEL, you first need to register using the Red Hat Subscription Manager.</span></span> <span data-ttu-id="1401b-108">Se isso não tiver sido feito em seu sistema ou se você não tiver certeza, consulte a [documentação do produto Red Hat para .net](https://access.redhat.com/documentation/net/5.0/).</span><span class="sxs-lookup"><span data-stu-id="1401b-108">If this hasn't been done on your system, or if you're unsure, see the [Red Hat Product Documentation for .NET](https://access.redhat.com/documentation/net/5.0/).</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="1401b-109">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="1401b-109">Supported distributions</span></span>

<span data-ttu-id="1401b-110">A tabela a seguir é uma lista de versões do .NET com suporte no momento no RHEL 7 e RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="1401b-110">The following table is a list of currently supported .NET releases on both RHEL 7 and RHEL 8.</span></span> <span data-ttu-id="1401b-111">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do RHEL não seja mais suportada.</span><span class="sxs-lookup"><span data-stu-id="1401b-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of RHEL is no longer supported.</span></span>

- <span data-ttu-id="1401b-112">Um ✔️ indica que a versão do RHEL ou do .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="1401b-112">A ✔️ indicates that the version of RHEL or .NET is still supported.</span></span>
- <span data-ttu-id="1401b-113">Um ❌ indica que a versão do RHEL ou .net não tem suporte nessa versão do RHEL.</span><span class="sxs-lookup"><span data-stu-id="1401b-113">A ❌ indicates that the version of RHEL or .NET isn't supported on that RHEL release.</span></span>
- <span data-ttu-id="1401b-114">Quando uma versão do RHEL e uma versão do .NET têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="1401b-114">When both a version of RHEL and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="1401b-115">RHEL</span><span class="sxs-lookup"><span data-stu-id="1401b-115">RHEL</span></span>                   | <span data-ttu-id="1401b-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1401b-116">.NET Core 2.1</span></span> | <span data-ttu-id="1401b-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1401b-117">.NET Core 3.1</span></span> | <span data-ttu-id="1401b-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="1401b-118">.NET 5.0</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1401b-119">✔️ [8](#rhel-8-)</span><span class="sxs-lookup"><span data-stu-id="1401b-119">✔️ [8](#rhel-8-)</span></span> | <span data-ttu-id="1401b-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1401b-120">✔️ 2.1</span></span>        | <span data-ttu-id="1401b-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1401b-121">✔️ 3.1</span></span>        | <span data-ttu-id="1401b-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1401b-122">✔️ 5.0</span></span> |
| <span data-ttu-id="1401b-123">✔️ [7](#rhel-7-)</span><span class="sxs-lookup"><span data-stu-id="1401b-123">✔️ [7](#rhel-7-)</span></span> | <span data-ttu-id="1401b-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1401b-124">✔️ 2.1</span></span>        | <span data-ttu-id="1401b-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1401b-125">✔️ 3.1</span></span>        | <span data-ttu-id="1401b-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1401b-126">✔️ 5.0</span></span> |

<span data-ttu-id="1401b-127">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="1401b-127">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="1401b-128">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="1401b-128">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1401b-129">3.0</span><span class="sxs-lookup"><span data-stu-id="1401b-129">3.0</span></span>
- <span data-ttu-id="1401b-130">2.2</span><span class="sxs-lookup"><span data-stu-id="1401b-130">2.2</span></span>
- <span data-ttu-id="1401b-131">2.0</span><span class="sxs-lookup"><span data-stu-id="1401b-131">2.0</span></span>

## <a name="how-to-install-other-versions"></a><span data-ttu-id="1401b-132">Como instalar outras versões</span><span class="sxs-lookup"><span data-stu-id="1401b-132">How to install other versions</span></span>

<span data-ttu-id="1401b-133">Consulte a [documentação do Red Hat para .net](https://access.redhat.com/documentation/net/5.0/) nas etapas necessárias para instalar outras versões do .net.</span><span class="sxs-lookup"><span data-stu-id="1401b-133">Consult the [Red Hat documentation for .NET](https://access.redhat.com/documentation/net/5.0/) on the steps required to install other releases of .NET.</span></span>

## <a name="rhel-8-"></a><span data-ttu-id="1401b-134">RHEL 8 ✔️</span><span class="sxs-lookup"><span data-stu-id="1401b-134">RHEL 8 ✔️</span></span>

<span data-ttu-id="1401b-135">O .NET está incluído nos repositórios do AppStream para RHEL 8.</span><span class="sxs-lookup"><span data-stu-id="1401b-135">.NET is included in the AppStream repositories for RHEL 8.</span></span>

[!INCLUDE [linux-dnf-install-50](includes/linux-install-50-dnf.md)]

## <a name="rhel-7-"></a><span data-ttu-id="1401b-136">RHEL 7 ✔️</span><span class="sxs-lookup"><span data-stu-id="1401b-136">RHEL 7 ✔️</span></span>

[!INCLUDE [linux-prep-intro-generic](includes/linux-prep-intro-generic.md)]

<span data-ttu-id="1401b-137">O comando a seguir instala o `scl-utils` pacote:</span><span class="sxs-lookup"><span data-stu-id="1401b-137">The following command installs the `scl-utils` package:</span></span>

```bash
sudo yum install scl-utils
```

### <a name="install-the-sdk"></a><span data-ttu-id="1401b-138">Instalar o SDK</span><span class="sxs-lookup"><span data-stu-id="1401b-138">Install the SDK</span></span>

<span data-ttu-id="1401b-139">O SDK do .NET permite que você desenvolva aplicativos com o .NET.</span><span class="sxs-lookup"><span data-stu-id="1401b-139">The .NET SDK allows you to develop apps with .NET.</span></span> <span data-ttu-id="1401b-140">Se você instalar o SDK do .NET, não precisará instalar o tempo de execução correspondente.</span><span class="sxs-lookup"><span data-stu-id="1401b-140">If you install the .NET SDK, you don't need to install the corresponding runtime.</span></span> <span data-ttu-id="1401b-141">Para instalar o SDK do .NET, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="1401b-141">To install the .NET SDK, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50 -y
scl enable rh-dotnet50 bash
```

<span data-ttu-id="1401b-142">O Red Hat não recomenda a habilitação permanente `rh-dotnet50` porque pode afetar outros programas.</span><span class="sxs-lookup"><span data-stu-id="1401b-142">Red Hat does not recommend permanently enabling `rh-dotnet50` because it may affect other programs.</span></span> <span data-ttu-id="1401b-143">Por exemplo, `rh-dotnet50` inclui uma versão do `libcurl` que difere da versão base do RHEL.</span><span class="sxs-lookup"><span data-stu-id="1401b-143">For example, `rh-dotnet50` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1401b-144">Isso pode levar a problemas em programas que não esperam uma versão diferente do `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="1401b-144">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1401b-145">Se você quiser habilitar `rh-dotnet` permanentemente, adicione a seguinte linha ao seu arquivo _~/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="1401b-145">If you want to enable `rh-dotnet` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50
```

### <a name="install-the-runtime"></a><span data-ttu-id="1401b-146">Instalar o runtime</span><span class="sxs-lookup"><span data-stu-id="1401b-146">Install the runtime</span></span>

<span data-ttu-id="1401b-147">O tempo de execução de ASP.NET Core permite que você execute aplicativos que foram feitos com o .NET que não forneceu o tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="1401b-147">The ASP.NET Core Runtime allows you to run apps that were made with .NET that didn't provide the runtime.</span></span> <span data-ttu-id="1401b-148">Os comandos a seguir instalam o tempo de execução do ASP.NET Core, que é o tempo de execução mais compatível para o .NET.</span><span class="sxs-lookup"><span data-stu-id="1401b-148">The following commands install the ASP.NET Core Runtime, which is the most compatible runtime for .NET.</span></span> <span data-ttu-id="1401b-149">Em seu terminal, execute os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="1401b-149">In your terminal, run the following commands:</span></span>

```bash
subscription-manager repos --enable=rhel-7-server-dotnet-rpms
yum install rh-dotnet50-aspnetcore-runtime-5.0 -y
scl enable rh-dotnet50-aspnetcore-runtime-5.0 bash
```

<span data-ttu-id="1401b-150">A Red Hat não recomenda a habilitação permanente `rh-dotnet50-aspnetcore-runtime-5.0` porque pode afetar outros programas.</span><span class="sxs-lookup"><span data-stu-id="1401b-150">Red Hat doesn't recommend permanently enabling `rh-dotnet50-aspnetcore-runtime-5.0` because it may affect other programs.</span></span> <span data-ttu-id="1401b-151">Por exemplo, `rh-dotnet50-aspnetcore-runtime-5.0` inclui uma versão do `libcurl` que difere da versão base do RHEL.</span><span class="sxs-lookup"><span data-stu-id="1401b-151">For example, `rh-dotnet50-aspnetcore-runtime-5.0` includes a version of `libcurl` that differs from the base RHEL version.</span></span> <span data-ttu-id="1401b-152">Isso pode levar a problemas em programas que não esperam uma versão diferente do `libcurl` .</span><span class="sxs-lookup"><span data-stu-id="1401b-152">This may lead to issues in programs that do not expect a different version of `libcurl`.</span></span> <span data-ttu-id="1401b-153">Se você quiser habilitar `rh-dotnet50-aspnetcore-runtime-5.0` permanentemente, adicione a seguinte linha ao seu arquivo _~/.bashrc_ .</span><span class="sxs-lookup"><span data-stu-id="1401b-153">If you want to enable `rh-dotnet50-aspnetcore-runtime-5.0` permanently, add the following line to your _~/.bashrc_ file.</span></span>

```bash
source scl_source enable rh-dotnet50-aspnetcore-runtime-5.0
```

<span data-ttu-id="1401b-154">Como alternativa ao tempo de execução de ASP.NET Core, você pode instalar o tempo de execução do .NET, que não inclui suporte a ASP.NET Core: substituir `rh-dotnet50-aspnetcore-runtime-5.0` nos comandos anteriores por `rh-dotnet50-dotnet-runtime-5.0` .</span><span class="sxs-lookup"><span data-stu-id="1401b-154">As an alternative to the ASP.NET Core Runtime, you can install the .NET Runtime, which doesn't include ASP.NET Core support: replace `rh-dotnet50-aspnetcore-runtime-5.0` in the previous commands with `rh-dotnet50-dotnet-runtime-5.0`.</span></span>

## <a name="snap"></a><span data-ttu-id="1401b-155">Snap</span><span class="sxs-lookup"><span data-stu-id="1401b-155">Snap</span></span>

[!INCLUDE [linux-install-snap](includes/linux-install-snap.md)]

## <a name="dependencies"></a><span data-ttu-id="1401b-156">Dependências</span><span class="sxs-lookup"><span data-stu-id="1401b-156">Dependencies</span></span>

[!INCLUDE [linux-rpm-install-dependencies](includes/linux-rpm-install-dependencies.md)]

## <a name="scripted-install"></a><span data-ttu-id="1401b-157">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="1401b-157">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="1401b-158">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="1401b-158">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="1401b-159">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1401b-159">Next steps</span></span>

- [<span data-ttu-id="1401b-160">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1401b-160">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
