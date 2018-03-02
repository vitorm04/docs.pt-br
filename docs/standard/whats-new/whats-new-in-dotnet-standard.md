---
title: Novidades no .NET Standard
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 3a5833bdfcf1e3433ea82403908e9a06a88cde27
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="30960-102">Novidades no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="30960-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="30960-103">O .NET Standard é uma especificação formal que define um conjunto com versões das APIs que devem estar disponíveis em implementações .NET que estejam de acordo com a versão standard.</span><span class="sxs-lookup"><span data-stu-id="30960-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="30960-104">O .NET Standard é destinado a desenvolvedores de bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="30960-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="30960-105">Uma biblioteca direcionada a uma versão do .NET Standard pode ser usada em qualquer implementação do .NET Framework, do .NET Core ou do Xamarin que dê suporte a essa versão do Standard.</span><span class="sxs-lookup"><span data-stu-id="30960-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="30960-106">A versão mais recente do .NET Standard é a 2.0.</span><span class="sxs-lookup"><span data-stu-id="30960-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="30960-107">Ela está incluída com o SDK do .NET Core 2.0, e também com o Visual Studio 2017 versão 15.3 com a carga de trabalho do .NET Core instalada.</span><span class="sxs-lookup"><span data-stu-id="30960-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="30960-108">Implementações .NET com suporte</span><span class="sxs-lookup"><span data-stu-id="30960-108">Supported .NET implementations</span></span>

<span data-ttu-id="30960-109">O .NET Standard 2.0 tem suporte das seguintes implementações do .NET:</span><span class="sxs-lookup"><span data-stu-id="30960-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="30960-110">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="30960-110">.NET Core 2.0</span></span>
- <span data-ttu-id="30960-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="30960-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="30960-112">Mono 5.4</span><span class="sxs-lookup"><span data-stu-id="30960-112">Mono 5.4</span></span>
- <span data-ttu-id="30960-113">Xamarin.iOS 10.14</span><span class="sxs-lookup"><span data-stu-id="30960-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="30960-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="30960-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="30960-115">Xamarin.Android 8.0</span><span class="sxs-lookup"><span data-stu-id="30960-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="30960-116">Plataforma Universal do Windows 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="30960-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="30960-117">Novidades no .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="30960-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="30960-118">O .NET Standard 2.0 inclui estes recursos novos:</span><span class="sxs-lookup"><span data-stu-id="30960-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="30960-119">**Um conjunto muito maior de APIs**</span><span class="sxs-lookup"><span data-stu-id="30960-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="30960-120">Na versão 1.6, o .NET Standard incluía um subconjunto de APIs comparativamente pequeno.</span><span class="sxs-lookup"><span data-stu-id="30960-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="30960-121">Entre os excluídos estavam várias APIs usadas normalmente no .NET Framework ou no Xamarin.</span><span class="sxs-lookup"><span data-stu-id="30960-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="30960-122">Isso complica o desenvolvimento, pois exige que os desenvolvedores encontrem substituições adequadas para APIs conhecidas quando desenvolvem aplicativos e bibliotecas direcionadas a várias implementações do .NET.</span><span class="sxs-lookup"><span data-stu-id="30960-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="30960-123">O .NET Standard 2.0 resolve essa limitação adicionando mais de 20.000 APIs que estavam disponíveis no .NET Standard 1.6, a versão anterior do Standard.</span><span class="sxs-lookup"><span data-stu-id="30960-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="30960-124">Para obter uma lista com as APIs que foram adicionadas ao .NET Standard 2.0, confira [.NET Standard 2.0 versus 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="30960-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="30960-125">Algumas das adições ao namespace <xref:System> no .NET Standard 2.0 incluem:</span><span class="sxs-lookup"><span data-stu-id="30960-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="30960-126">Suporte para a classe <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="30960-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="30960-127">Aprimoramento do suporte para trabalhar com matrizes de membros adicionais na classe <xref:System.Array>.</span><span class="sxs-lookup"><span data-stu-id="30960-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="30960-128">Aprimoramento do suporte para trabalhar com atributos de membros adicionais na classe <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="30960-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="30960-129">Aprimoramento do suporte ao calendário e opções de formatação adicionais para valores <xref:System.DateTime>.</span><span class="sxs-lookup"><span data-stu-id="30960-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="30960-130">Funcionalidade de arredondamento <xref:System.Decimal> adicional.</span><span class="sxs-lookup"><span data-stu-id="30960-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="30960-131">Funcionalidade adicional na classe <xref:System.Environment>.</span><span class="sxs-lookup"><span data-stu-id="30960-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="30960-132">Aprimoramento do controle sobre o coletor de lixo por meio da classe <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="30960-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="30960-133">Aprimoramento do suporte para comparação, enumeração e normalização de cadeia de caracteres na classe <xref:System.String>.</span><span class="sxs-lookup"><span data-stu-id="30960-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="30960-134">Suporte para ajustes de horário de verão e tempos de transição nas classes <xref:System.TimeZoneInfo.AdjustmentRule> e <xref:System.TimeZoneInfo.TransitionTime>.</span><span class="sxs-lookup"><span data-stu-id="30960-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="30960-135">Aprimoramento considerável da funcionalidade na classe <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="30960-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="30960-136">Aprimoramento do suporte para desserialização de objetos de exceção com a adição de um construtor de exceção com os parâmetros <xref:System.Runtime.Serialization.SerializationInfo> e <xref:System.Runtime.Serialization.StreamingContext>.</span><span class="sxs-lookup"><span data-stu-id="30960-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="30960-137">**Suporte a bibliotecas do .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="30960-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="30960-138">A grande maioria das bibliotecas são direcionadas ao .NET Framework em vez do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30960-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="30960-139">No entanto, a maioria das chamadas nessas bibliotecas são para APIs incluídas no .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="30960-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="30960-140">A partir do .NET Standard 2.0, você pode acessar bibliotecas do .NET Framework de uma biblioteca do .NET Standard usando uma [shim de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="30960-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="30960-141">Essa camada de compatibilidade é transparente para os desenvolvedores; você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30960-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="30960-142">O único requisito é que as APIs chamadas pela biblioteca de classes .NET Framework estejam incluídas no .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="30960-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="30960-143">**Suporte a Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="30960-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="30960-144">Agora, você pode desenvolver bibliotecas .NET Standard no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="30960-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="30960-145">Para desenvolvedores em Visual Basic que usam o Visual Studio 2017 versão 15.3 ou posterior com a carga de trabalho do .NET Core instalada, agora o Visual Studio inclui um modelo de biblioteca de classes .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30960-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="30960-146">Para desenvolvedores em Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, use o comando [dotnet new](../../core/tools/dotnet-new.md) para criar um projeto de biblioteca do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30960-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="30960-147">Para saber mais, confira o [Suporte a ferramentas para bibliotecas .NET Standard](#tooling).</span><span class="sxs-lookup"><span data-stu-id="30960-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="30960-148"><a name="tooling" />**Suporte a ferramentas para bibliotecas .NET Standard**</span><span class="sxs-lookup"><span data-stu-id="30960-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="30960-149">Com o lançamento do .NET Core 2.0 e do .NET Standard 2.0, o Visual Studio 2017 e a [CLI (Interface de linha de comando) do .NET Core](../../core/tools/index.md) incluem o suporte a ferramentas para criação de bibliotecas .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="30960-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="30960-150">Se você instalar o Visual Studio com a carga de trabalho **desenvolvimento de plataforma cruzada do .NET Core**, você pode criar um projeto de biblioteca .NET Standard 2.0 usando um modelo de projeto, como mostra a figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="30960-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="30960-151">C#</span><span class="sxs-lookup"><span data-stu-id="30960-151">C#</span></span>](#tab/csharp)
![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="30960-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="30960-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Adicionar um novo projeto de biblioteca .NET Standard](./media/std-project-vb.png)
---

<span data-ttu-id="30960-155">Se você estiver usando a CLI do .NET Core, o seguinte comando [dotnet new](../../core/tools/dotnet-new.md) criará um projeto de biblioteca de classes direcionado ao .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="30960-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="30960-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30960-156">See Also</span></span>
<span data-ttu-id="30960-157">[.NET Standard](../net-standard.md)
[Apresentação do .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="30960-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
