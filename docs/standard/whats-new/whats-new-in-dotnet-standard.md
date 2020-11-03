---
title: Novidades no .NET Standard
description: Este artigo resume os novos recursos e melhorias encontrados em cada nova versão do .NET Standard.
ms.custom: updateeachrelease
ms.date: 04/12/2018
ms.technology: dotnet-standard
ms.openlocfilehash: 419988901923b890aaf0a540d155775214e62c52
ms.sourcegitcommit: 74d05613d6c57106f83f82ce8ee71176874ea3f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/03/2020
ms.locfileid: "93282107"
---
# <a name="whats-new-in-net-standard"></a><span data-ttu-id="9a2cf-103">Novidades no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9a2cf-103">What's new in .NET Standard</span></span>

<span data-ttu-id="9a2cf-104">.NET Standard é uma especificação formal que define um conjunto com controle de versão de APIs que deve estar disponível em implementações do .NET que estão em conformidade com essa versão do padrão.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-104">.NET Standard is a formal specification that defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="9a2cf-105">.NET Standard é destinada aos desenvolvedores de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-105">.NET Standard is targeted at library developers.</span></span> <span data-ttu-id="9a2cf-106">Uma biblioteca direcionada a uma versão do .NET Standard pode ser usada em qualquer implementação do .NET Framework, do .NET Core ou do Xamarin que dê suporte a essa versão do Standard.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-106">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="9a2cf-107">.NET Standard está incluído no SDK do .NET Core, bem como no Visual Studio quando você seleciona a carga de trabalho do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-107">.NET Standard is included with the .NET Core SDK, as well as with Visual Studio when you select the .NET Core workload.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="9a2cf-108">Implementações .NET com suporte</span><span class="sxs-lookup"><span data-stu-id="9a2cf-108">Supported .NET implementations</span></span>

<span data-ttu-id="9a2cf-109">.NET Standard 2,0 é compatível com as seguintes implementações .NET:</span><span class="sxs-lookup"><span data-stu-id="9a2cf-109">.NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="9a2cf-110">.NET Core 2.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-110">.NET Core 2.0 or later</span></span>
- <span data-ttu-id="9a2cf-111">.NET Framework 4.6.1 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-111">.NET Framework 4.6.1 or later</span></span>
- <span data-ttu-id="9a2cf-112">Mono 5.4 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-112">Mono 5.4 or later</span></span>
- <span data-ttu-id="9a2cf-113">Xamarin.iOS 10.14 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-113">Xamarin.iOS 10.14 or later</span></span>
- <span data-ttu-id="9a2cf-114">Xamarin.Mac 3.8 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-114">Xamarin.Mac 3.8 or later</span></span>
- <span data-ttu-id="9a2cf-115">Xamarin.Android 8.0 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-115">Xamarin.Android 8.0 or later</span></span>
- <span data-ttu-id="9a2cf-116">Plataforma Universal do Windows 10.0.16299 ou posterior</span><span class="sxs-lookup"><span data-stu-id="9a2cf-116">Universal Windows Platform 10.0.16299 or later</span></span>

## <a name="whats-new-in-net-standard-20"></a><span data-ttu-id="9a2cf-117">O que há de novo no .NET Standard 2,0</span><span class="sxs-lookup"><span data-stu-id="9a2cf-117">What's new in .NET Standard 2.0</span></span>

<span data-ttu-id="9a2cf-118">O .NET Standard 2,0 inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="9a2cf-118">.NET Standard 2.0 includes the following new features:</span></span>

### <a name="a-vastly-expanded-set-of-apis"></a><span data-ttu-id="9a2cf-119">Um conjunto muito maior de APIs</span><span class="sxs-lookup"><span data-stu-id="9a2cf-119">A vastly expanded set of APIs</span></span>

<span data-ttu-id="9a2cf-120">Por meio da versão 1,6, .NET Standard incluía um subconjunto comparativamente pequeno de APIs.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-120">Through version 1.6, .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="9a2cf-121">Entre aquelas excluídas eram muitas APIs que eram comumente usadas em .NET Framework ou Xamarin.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-121">Among those excluded were many APIs that were commonly used in .NET Framework or Xamarin.</span></span> <span data-ttu-id="9a2cf-122">Isso complica o desenvolvimento, pois exige que os desenvolvedores encontrem substituições adequadas para APIs conhecidas quando desenvolvem aplicativos e bibliotecas direcionadas a várias implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="9a2cf-123">.NET Standard 2,0 trata dessa limitação adicionando mais de 20.000 APIs mais do que estavam disponíveis no .NET Standard 1,6, a versão anterior do padrão.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-123">.NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="9a2cf-124">Para obter uma lista das APIs que foram adicionadas ao .NET Standard 2,0, consulte [.NET Standard 2,0 vs 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="9a2cf-124">For a list of the APIs that have been added to .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

<span data-ttu-id="9a2cf-125">Algumas das adições ao namespace <xref:System> no .NET Standard 2.0 incluem:</span><span class="sxs-lookup"><span data-stu-id="9a2cf-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="9a2cf-126">Suporte para a classe <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="9a2cf-127">Aprimoramento do suporte para trabalhar com matrizes de membros adicionais na classe <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="9a2cf-128">Aprimoramento do suporte para trabalhar com atributos de membros adicionais na classe <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="9a2cf-129">Aprimoramento do suporte ao calendário e opções de formatação adicionais para valores <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="9a2cf-130">Funcionalidade de arredondamento <xref:System.Decimal> adicional.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="9a2cf-131">Funcionalidade adicional na classe <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="9a2cf-132">Aprimoramento do controle sobre o coletor de lixo por meio da classe <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="9a2cf-133">Aprimoramento do suporte para comparação, enumeração e normalização de cadeia de caracteres na classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="9a2cf-134">Suporte para ajustes de horário de verão e tempos de transição nas classes <xref:System.TimeZoneInfo.AdjustmentRule> e <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="9a2cf-135">Aprimoramento considerável da funcionalidade na classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="9a2cf-136">Aprimoramento do suporte para desserialização de objetos de exceção com a adição de um construtor de exceção com os parâmetros <xref:System.Runtime.Serialization.SerializationInfo> e <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="9a2cf-137">Suporte a bibliotecas do .NET Framework</span><span class="sxs-lookup"><span data-stu-id="9a2cf-137">Support for .NET Framework libraries</span></span>

<span data-ttu-id="9a2cf-138">Muitas bibliotecas são direcionadas .NET Framework em vez de .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-138">Many libraries target .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="9a2cf-139">No entanto, a maioria das chamadas nessas bibliotecas é para APIs incluídas no .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-139">However, most of the calls in those libraries are to APIs that are included in .NET Standard 2.0.</span></span> <span data-ttu-id="9a2cf-140">A partir do .NET Standard 2,0, você pode acessar bibliotecas de .NET Framework de uma biblioteca de .NET Standard usando um [Shim de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="9a2cf-140">Starting with .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/planning/netstandard-2.0/README.md#assembly-unification).</span></span> <span data-ttu-id="9a2cf-141">Essa camada de compatibilidade é transparente para os desenvolvedores; você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="9a2cf-142">O único requisito é que as APIs chamadas pelo .NET Framework biblioteca de classes devam ser incluídas no .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-142">The single requirement is that the APIs called by the .NET Framework class library must be included in .NET Standard 2.0.</span></span>

### <a name="support-for-visual-basic"></a><span data-ttu-id="9a2cf-143">Suporte para Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a2cf-143">Support for Visual Basic</span></span>

<span data-ttu-id="9a2cf-144">Agora, você pode desenvolver bibliotecas .NET Standard no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="9a2cf-145">O Visual Studio 2019 e o Visual Studio 2017 versão 15,3 ou posterior com a carga de trabalho do .NET Core instalada incluem um modelo de biblioteca de classe .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-145">Visual Studio 2019 and Visual Studio 2017 version 15.3 or later with the .NET Core workload installed include a .NET Standard Class Library template.</span></span> <span data-ttu-id="9a2cf-146">Para desenvolvedores em Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, use o comando [dotnet new](../../core/tools/dotnet-new.md) para criar um projeto de biblioteca do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="9a2cf-147">Para saber mais, confira o [Suporte a ferramentas para bibliotecas .NET Standard](#tooling-support-for-net-standard-libraries).</span><span class="sxs-lookup"><span data-stu-id="9a2cf-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling-support-for-net-standard-libraries).</span></span>

### <a name="tooling-support-for-net-standard-libraries"></a><span data-ttu-id="9a2cf-148">Suporte a ferramentas para bibliotecas .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9a2cf-148">Tooling support for .NET Standard libraries</span></span>

<span data-ttu-id="9a2cf-149">Com o lançamento do .NET Core 2,0 e do .NET Standard 2,0, o Visual Studio 2017 e o [CLI do .NET Core](../../core/tools/index.md) incluem suporte a ferramentas para criar bibliotecas de .net Standard.</span><span class="sxs-lookup"><span data-stu-id="9a2cf-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core CLI](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span>

<span data-ttu-id="9a2cf-150">Se instalar o Visual Studio com a carga de trabalho **desenvolvimento de plataforma cruzada do .NET Core** , você poderá criar um projeto de biblioteca .NET Standard 2.0 usando um modelo de projeto, como mostra a figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="9a2cf-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="c"></a>[<span data-ttu-id="9a2cf-151">C#</span><span class="sxs-lookup"><span data-stu-id="9a2cf-151">C#</span></span>](#tab/csharp)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-cs.png)

<span data-ttu-id="9a2cf-153">Se você estiver usando o CLI do .NET Core, o seguinte comando [dotnet](../../core/tools/dotnet-new.md) cria um projeto de biblioteca de classes que tem como alvo .net Standard 2,0:</span><span class="sxs-lookup"><span data-stu-id="9a2cf-153">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib
```

# <a name="visual-basic"></a>[<span data-ttu-id="9a2cf-154">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9a2cf-154">Visual Basic</span></span>](#tab/vb)

![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-vb.png)

<span data-ttu-id="9a2cf-156">Se você estiver usando o CLI do .NET Core, o seguinte comando [dotnet](../../core/tools/dotnet-new.md) cria um projeto de biblioteca de classes que tem como alvo .net Standard 2,0:</span><span class="sxs-lookup"><span data-stu-id="9a2cf-156">If you're using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets .NET Standard 2.0:</span></span>

```dotnetcli
dotnet new classlib -lang vb
```

---

## <a name="see-also"></a><span data-ttu-id="9a2cf-157">Veja também</span><span class="sxs-lookup"><span data-stu-id="9a2cf-157">See also</span></span>

- [<span data-ttu-id="9a2cf-158">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="9a2cf-158">.NET Standard</span></span>](../net-standard.md)
- [<span data-ttu-id="9a2cf-159">Apresentando o .NET Standard</span><span class="sxs-lookup"><span data-stu-id="9a2cf-159">Introducing .NET Standard</span></span>](https://devblogs.microsoft.com/dotnet/introducing-net-standard/)
