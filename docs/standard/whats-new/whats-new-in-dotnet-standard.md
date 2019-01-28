---
title: Novidades no .NET Standard
description: Este artigo resume os novos recursos e melhorias encontrados em cada nova versão do .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 56f75e282e1b28f09eacd19f2da6293fd4e3ab7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628195"
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="0b316-103">Novidades no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="0b316-103">What's new in the .NET Standard</span></span>

<span data-ttu-id="0b316-104">O .NET Standard é uma especificação formal que define um conjunto com versões das APIs que devem estar disponíveis em implementações .NET que estejam de acordo com a versão standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-104">The .NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="0b316-105">O .NET Standard é destinado a desenvolvedores de bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="0b316-105">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="0b316-106">Uma biblioteca direcionada a uma versão do .NET Standard pode ser usada em qualquer implementação do .NET Framework, do .NET Core ou do Xamarin que dê suporte a essa versão do Standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="0b316-107">A versão mais recente do .NET Standard é a 2.0.</span><span class="sxs-lookup"><span data-stu-id="0b316-107">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="0b316-108">Ela está incluída com o SDK do .NET Core 2.0, e também com o Visual Studio 2017 versão 15.3 com a carga de trabalho do .NET Core instalada.</span><span class="sxs-lookup"><span data-stu-id="0b316-108">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="0b316-109">Implementações .NET com suporte</span><span class="sxs-lookup"><span data-stu-id="0b316-109">Supported .NET implementations</span></span>

<span data-ttu-id="0b316-110">O .NET Standard 2.0 tem suporte das seguintes implementações do .NET:</span><span class="sxs-lookup"><span data-stu-id="0b316-110">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="0b316-111">.NET Core 2.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-111">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="0b316-112">.NET Framework 4.6.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-112">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="0b316-113">Mono 5.4 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-113">Mono 5.4 or later</span></span>
- <span data-ttu-id="0b316-114">Xamarin.iOS 10.14 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-114">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="0b316-115">Xamarin.Mac 3.8 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-115">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="0b316-116">Xamarin.Android 8.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-116">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="0b316-117">Plataforma Universal do Windows 10.0.16299 ou posterior</span><span class="sxs-lookup"><span data-stu-id="0b316-117">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="0b316-118">Novidades no .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="0b316-118">What's new in the .NET Standard 2.0</span></span>

<span data-ttu-id="0b316-119">O .NET Standard 2.0 inclui estes recursos novos:</span><span class="sxs-lookup"><span data-stu-id="0b316-119">The .NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="0b316-120">Um conjunto muito maior de APIs</span><span class="sxs-lookup"><span data-stu-id="0b316-120">A vastly expanded set of APIs</span></span>

<span data-ttu-id="0b316-121">Na versão 1.6, o .NET Standard incluía um subconjunto de APIs comparativamente pequeno.</span><span class="sxs-lookup"><span data-stu-id="0b316-121">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="0b316-122">Entre os excluídos estavam várias APIs usadas normalmente no .NET Framework ou no Xamarin.</span><span class="sxs-lookup"><span data-stu-id="0b316-122">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="0b316-123">Isso complica o desenvolvimento, pois exige que os desenvolvedores encontrem substituições adequadas para APIs conhecidas quando desenvolvem aplicativos e bibliotecas direcionadas a várias implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="0b316-123">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="0b316-124">O .NET Standard 2.0 resolve essa limitação adicionando mais de 20.000 APIs que estavam disponíveis no .NET Standard 1.6, a versão anterior do Standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-124">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="0b316-125">Para obter uma lista com as APIs que foram adicionadas ao .NET Standard 2.0, confira [.NET Standard 2.0 versus 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="0b316-125">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="0b316-126">Algumas das adições ao namespace <xref:System> no .NET Standard 2.0 incluem:</span><span class="sxs-lookup"><span data-stu-id="0b316-126">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="0b316-127">Suporte para a classe <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="0b316-127">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="0b316-128">Aprimoramento do suporte para trabalhar com matrizes de membros adicionais na classe <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="0b316-128">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="0b316-129">Aprimoramento do suporte para trabalhar com atributos de membros adicionais na classe <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="0b316-129">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="0b316-130">Aprimoramento do suporte ao calendário e opções de formatação adicionais para valores <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="0b316-130">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="0b316-131">Funcionalidade de arredondamento <xref:System.Decimal> adicional.</span><span class="sxs-lookup"><span data-stu-id="0b316-131">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="0b316-132">Funcionalidade adicional na classe <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="0b316-132">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="0b316-133">Aprimoramento do controle sobre o coletor de lixo por meio da classe <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="0b316-133">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="0b316-134">Aprimoramento do suporte para comparação, enumeração e normalização de cadeia de caracteres na classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="0b316-134">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="0b316-135">Suporte para ajustes de horário de verão e tempos de transição nas classes <xref:System.TimeZoneInfo.AdjustmentRule> e <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="0b316-135">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="0b316-136">Aprimoramento considerável da funcionalidade na classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="0b316-136">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="0b316-137">Aprimoramento do suporte para desserialização de objetos de exceção com a adição de um construtor de exceção com os parâmetros <xref:System.Runtime.Serialization.SerializationInfo> e <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="0b316-137">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="0b316-138">Suporte a bibliotecas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="0b316-138">Support for .NET Framework libraries</span></span>

<span data-ttu-id="0b316-139">A grande maioria das bibliotecas são direcionadas ao .NET Framework em vez do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-139">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="0b316-140">No entanto, a maioria das chamadas nessas bibliotecas são para APIs incluídas no .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="0b316-140">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="0b316-141">A partir do .NET Standard 2.0, você pode acessar bibliotecas do .NET Framework de uma biblioteca do .NET Standard usando uma [shim de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="0b316-141">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="0b316-142">Essa camada de compatibilidade é transparente para os desenvolvedores; você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="0b316-142">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="0b316-143">O único requisito é que as APIs chamadas pela biblioteca de classes .NET Framework estejam incluídas no .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="0b316-143">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="0b316-144">Suporte para Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b316-144">Support for Visual Basic</span></span>

<span data-ttu-id="0b316-145">Agora, você pode desenvolver bibliotecas .NET Standard no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="0b316-145">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="0b316-146">Para desenvolvedores em Visual Basic que usam o Visual Studio 2017 versão 15.3 ou posterior com a carga de trabalho do .NET Core instalada, agora o Visual Studio inclui um modelo de biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-146">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="0b316-147">Para desenvolvedores em Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, use o comando [dotnet new](../../core/tools/dotnet-new.md) para criar um projeto de biblioteca do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-147">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="0b316-148">Para saber mais, confira o [Suporte a ferramentas para bibliotecas .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="0b316-148">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="0b316-149">Suporte a ferramentas para bibliotecas .NET Standard</span><span class="sxs-lookup"><span data-stu-id="0b316-149">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="0b316-150">Com o lançamento do .NET Core 2.0 e do .NET Standard 2.0, o Visual Studio 2017 e a [CLI (Interface de linha de comando) do .NET Core](../../core/tools/index.md) incluem o suporte a ferramentas para criação de bibliotecas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="0b316-150">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="0b316-151">Se instalar o Visual Studio com a carga de trabalho **desenvolvimento de plataforma cruzada do .NET Core**, você poderá criar um projeto de biblioteca .NET Standard 2.0 usando um modelo de projeto, como mostra a figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="0b316-151">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

# <a name="ctabcsharp"></a>[<span data-ttu-id="0b316-152">C#</span><span class="sxs-lookup"><span data-stu-id="0b316-152">C#</span></span>](#tab/csharp)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="0b316-154">Se você estiver usando a CLI do .NET Core, o seguinte comando [dotnet new](../../core/tools/dotnet-new.md) criará um projeto de biblioteca de classes direcionado ao .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="0b316-154">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib
```

# <a name="visual-basictabvb"></a>[<span data-ttu-id="0b316-155">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0b316-155">Visual Basic</span></span>](#tab/vb)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="0b316-157">Se você estiver usando a CLI do .NET Core, o seguinte comando [dotnet new](../../core/tools/dotnet-new.md) criará um projeto de biblioteca de classes direcionado ao .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="0b316-157">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0:</span></span>

```
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="0b316-158">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0b316-158">See also</span></span>

- [<span data-ttu-id="0b316-159">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="0b316-159">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="0b316-160">Apresentando o .NET Standard</span><span class="sxs-lookup"><span data-stu-id="0b316-160">Introducing .NET Standard</span></span>](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)
