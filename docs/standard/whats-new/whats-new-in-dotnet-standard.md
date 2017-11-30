---
title: "O que há de novo no .NET Standard"
ms.custom: updateeachrelease
ms.date: 11/08/2017
ms.prod: .net
ms.topic: article
ms.technology: dotnet-standard
ms.##devlang: dotnet
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e938c009b79af3b2f36094bbb74f4d38baeeac0b
ms.sourcegitcommit: 281070dee88db86ec3bb4634d5f558d1a4e159dd
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2017
---
# <a name="whats-new-in-the-net-standard"></a><span data-ttu-id="e2337-102">O que há de novo no .NET Standard</span><span class="sxs-lookup"><span data-stu-id="e2337-102">What's new in the .NET Standard</span></span>

<span data-ttu-id="e2337-103">O padrão do .NET é uma especificação formal que define um conjunto com controle de versão de APIs que devem estar disponíveis em implementações de .NET que estão em conformidade com essa versão do padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-103">The .NET Standard is a formal specification that defines a versioned set of APIs which must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="e2337-104">O .NET Standard é destinado a desenvolvedores de bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="e2337-104">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="e2337-105">Uma biblioteca que tem como alvo uma versão padrão do .NET pode ser usada em qualquer implementação do .NET Framework, o .NET Core ou Xamarin que dá suporte a essa versão do padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-105">A library that targets a .NET Standard version can be used on any .NET Framework, .NET Core, or Xamarin implementation that supports that version of the standard.</span></span>

<span data-ttu-id="e2337-106">A versão mais recente do padrão do .NET é 2.0.</span><span class="sxs-lookup"><span data-stu-id="e2337-106">The most recent version of the .NET Standard is 2.0.</span></span> <span data-ttu-id="e2337-107">Ele está incluído com o SDK do .NET Core 2.0, bem como com o Visual Studio 2017 versão 15,3 com a carga de trabalho do .NET Core instalada.</span><span class="sxs-lookup"><span data-stu-id="e2337-107">It is included with the .NET Core 2.0 SDK, as well as with Visual Studio 2017 Version 15.3 with the .NET Core workload installed.</span></span>

## <a name="supported-net-implementations"></a><span data-ttu-id="e2337-108">Implementações de .NET com suporte</span><span class="sxs-lookup"><span data-stu-id="e2337-108">Supported .NET implementations</span></span>

<span data-ttu-id="e2337-109">O padrão de .NET 2.0 tem suporte as implementações de .NET a seguir:</span><span class="sxs-lookup"><span data-stu-id="e2337-109">The .NET Standard 2.0 is supported by the following .NET implementations:</span></span>

- <span data-ttu-id="e2337-110">Núcleo do .NET 2.0</span><span class="sxs-lookup"><span data-stu-id="e2337-110">.NET Core 2.0</span></span>
- <span data-ttu-id="e2337-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="e2337-111">.NET Framework 4.6.1</span></span>
- <span data-ttu-id="e2337-112">Mono 5.4</span><span class="sxs-lookup"><span data-stu-id="e2337-112">Mono 5.4</span></span>
- <span data-ttu-id="e2337-113">Xamarin 10.14</span><span class="sxs-lookup"><span data-stu-id="e2337-113">Xamarin.iOS 10.14</span></span>
- <span data-ttu-id="e2337-114">Xamarin.Mac 3.8</span><span class="sxs-lookup"><span data-stu-id="e2337-114">Xamarin.Mac 3.8</span></span>
- <span data-ttu-id="e2337-115">Xamarin 8.0</span><span class="sxs-lookup"><span data-stu-id="e2337-115">Xamarin.Android 8.0</span></span>
- <span data-ttu-id="e2337-116">Plataforma universal do Windows 10.0.16299</span><span class="sxs-lookup"><span data-stu-id="e2337-116">Universal Windows Platform 10.0.16299</span></span>

## <a name="whats-new-in-the-net-standard-20"></a><span data-ttu-id="e2337-117">O que é novo no .NET 2.0 padrão</span><span class="sxs-lookup"><span data-stu-id="e2337-117">What's new in the .NET Standard 2.0</span></span>
 
<span data-ttu-id="e2337-118">O padrão de .NET 2.0 inclui os seguintes novos recursos:</span><span class="sxs-lookup"><span data-stu-id="e2337-118">The .NET Standard 2.0 includes the following new features:</span></span>

<span data-ttu-id="e2337-119">**Um conjunto muito maior de APIs**</span><span class="sxs-lookup"><span data-stu-id="e2337-119">**A vastly expanded set of APIs**</span></span>

<span data-ttu-id="e2337-120">A versão 1.6, padrão do .NET incluído um comparativamente pequeno subconjunto de APIs.</span><span class="sxs-lookup"><span data-stu-id="e2337-120">Through version 1.6, the .NET Standard included a comparatively small subset of APIs.</span></span> <span data-ttu-id="e2337-121">Entre os excluídos foram várias APIs que foram usados no .NET Framework ou Xamarin.</span><span class="sxs-lookup"><span data-stu-id="e2337-121">Among those excluded were many APIs that were commonly used in the .NET Framework or Xamarin.</span></span> <span data-ttu-id="e2337-122">Isso complica a desenvolvimento, pois ele exige que os desenvolvedores localizar substituições adequadas para APIs familiar quando eles desenvolverem aplicativos e bibliotecas direcionadas a várias implementações de .NET.</span><span class="sxs-lookup"><span data-stu-id="e2337-122">This complicates development, since it requires that developers find suitable replacements for familiar APIs when they develop applications and libraries that target multiple .NET implementations.</span></span> <span data-ttu-id="e2337-123">O padrão de .NET 2.0 endereços essa limitação, adicionando mais de 20.000 APIs mais que estavam disponíveis no .NET padrão 1.6, a versão anterior do padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-123">The .NET Standard 2.0 addresses this limitation by adding over 20,000 more APIs than were available in .NET Standard 1.6, the previous version of the standard.</span></span> <span data-ttu-id="e2337-124">Para obter uma lista das APIs que foram adicionadas ao .NET Standard 2.0, consulte [.NET 2.0 padrão vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="e2337-124">For a list of the APIs that have been added to the .NET Standard 2.0, see [.NET Standard 2.0 vs 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span> 

<span data-ttu-id="e2337-125">Algumas das adições para o <xref:System> namespace .NET 2.0 padrão incluem:</span><span class="sxs-lookup"><span data-stu-id="e2337-125">Some of the additions to the <xref:System> namespace in .NET Standard 2.0 include:</span></span>

- <span data-ttu-id="e2337-126">Suporte para o <xref:System.AppDomain> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-126">Support for the <xref:System.AppDomain> class.</span></span>
- <span data-ttu-id="e2337-127">Melhor suporte para trabalhar com matrizes de membros adicionais no <xref:System.Array> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-127">Better support for working with arrays from additional members in the <xref:System.Array> class.</span></span>
- <span data-ttu-id="e2337-128">Melhor suporte para trabalhar com os atributos dos membros adicionais no <xref:System.Attribute> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-128">Better support for working with attributes from additional members in the <xref:System.Attribute> class.</span></span>
- <span data-ttu-id="e2337-129">Calendário melhor suporte e as opções de formatação adicionais para <xref:System.DateTime> valores.</span><span class="sxs-lookup"><span data-stu-id="e2337-129">Better calendar support and additional formatting options for <xref:System.DateTime> values.</span></span>
- <span data-ttu-id="e2337-130">Adicionais <xref:System.Decimal> funcionalidade de arredondamento.</span><span class="sxs-lookup"><span data-stu-id="e2337-130">Additional <xref:System.Decimal> rounding functionality.</span></span>
- <span data-ttu-id="e2337-131">Funcionalidade adicional a <xref:System.Environment> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-131">Additional functionality in the <xref:System.Environment> class.</span></span>
- <span data-ttu-id="e2337-132">Aprimorado o controle sobre o coletor de lixo por meio de <xref:System.GC> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-132">Enhanced control over the garbage collector through the <xref:System.GC> class.</span></span>
- <span data-ttu-id="e2337-133">Suporte aprimorado para comparação de cadeia de caracteres, enumeração e normalização no <xref:System.String> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-133">Enhanced support for string comparison, enumeration, and normalization in the <xref:System.String> class.</span></span>
- <span data-ttu-id="e2337-134">Suporte para horário de verão ajustes e tempos de transição no <xref:System.TimeZoneInfo.AdjustmentRule> e <xref:System.TimeZoneInfo.TransitionTime> classes.</span><span class="sxs-lookup"><span data-stu-id="e2337-134">Support for daylight saving adjustments and transition times in the <xref:System.TimeZoneInfo.AdjustmentRule> and <xref:System.TimeZoneInfo.TransitionTime> classes.</span></span>
- <span data-ttu-id="e2337-135">Aprimorada significativamente a funcionalidade de <xref:System.Type> classe.</span><span class="sxs-lookup"><span data-stu-id="e2337-135">Significantly enhanced functionality in the <xref:System.Type> class.</span></span>
- <span data-ttu-id="e2337-136">Melhor suporte para desserialização de objetos de exceção com a adição de um construtor de exceção com <xref:System.Runtime.Serialization.SerializationInfo> e <xref:System.Runtime.Serialization.StreamingContext> parâmetros.</span><span class="sxs-lookup"><span data-stu-id="e2337-136">Better support for deserialization of exception objects by adding an exception constructor with <xref:System.Runtime.Serialization.SerializationInfo> and <xref:System.Runtime.Serialization.StreamingContext> parameters.</span></span>

<span data-ttu-id="e2337-137">**Suporte para bibliotecas do .NET Framework**</span><span class="sxs-lookup"><span data-stu-id="e2337-137">**Support for .NET Framework libraries**</span></span>

<span data-ttu-id="e2337-138">A grande maioria das bibliotecas de direcionar o .NET Framework em vez do .NET padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-138">The overwhelming majority of libraries target the .NET Framework rather than .NET Standard.</span></span> <span data-ttu-id="e2337-139">No entanto, a maioria das chamadas dessas bibliotecas é APIs que estão incluídos no .NET 2.0 padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-139">However, most of the calls in those libraries are to APIs that are included in the .NET Standard 2.0.</span></span> <span data-ttu-id="e2337-140">Começando com o padrão de .NET 2.0, você pode acessar bibliotecas do .NET Framework em uma biblioteca .NET padrão usando um [correção de compatibilidade](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span><span class="sxs-lookup"><span data-stu-id="e2337-140">Starting with the .NET Standard 2.0, you can access .NET Framework libraries from a .NET Standard library by using a [compatibility shim](https://github.com/dotnet/standard/blob/master/docs/netstandard-20/README.md#assembly-unification).</span></span> <span data-ttu-id="e2337-141">Essa camada de compatibilidade é transparente para os desenvolvedores; Você não precisa fazer nada para tirar proveito das bibliotecas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e2337-141">This compatibility layer is transparent to developers; you don't have to do anything to take advantage of .NET Framework libraries.</span></span>

<span data-ttu-id="e2337-142">O único requisito é que as APIs chamadas por biblioteca de classes .NET Framework deve ser incluídas no .NET 2.0 padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-142">The single requirement is that the APIs called by the .NET Framework class library must be included in the .NET Standard 2.0.</span></span>

<span data-ttu-id="e2337-143">**Suporte para o Visual Basic**</span><span class="sxs-lookup"><span data-stu-id="e2337-143">**Support for Visual Basic**</span></span>

<span data-ttu-id="e2337-144">Agora você pode desenvolver bibliotecas .NET padrão no Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="e2337-144">You can now develop .NET Standard libraries in Visual Basic.</span></span> <span data-ttu-id="e2337-145">Para desenvolvedores do Visual Basic usando o Visual Studio 2017 versão 15,3 ou posterior com a carga de trabalho do .NET Core instalado, o Visual Studio agora inclui um modelo de biblioteca de classes .NET padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-145">For Visual Basic developers using Visual Studio 2017 Version 15.3 or later with the .NET Core workload installed, Visual Studio now includes a .NET Standard Class Library template.</span></span> <span data-ttu-id="e2337-146">Para desenvolvedores do Visual Basic que usam outros ambientes e ferramentas de desenvolvimento, você pode usar o [dotnet novo](../../core/tools/dotnet-new.md) comando para criar um projeto de biblioteca padrão do .NET.</span><span class="sxs-lookup"><span data-stu-id="e2337-146">For Visual Basic developers who use other development tools and environments, you can use the [dotnet new](../../core/tools/dotnet-new.md) command to create a .NET Standard Library project.</span></span> <span data-ttu-id="e2337-147">Para obter mais informações, consulte o [suporte de ferramentas para as bibliotecas .NET padrão](#tooling).</span><span class="sxs-lookup"><span data-stu-id="e2337-147">For more information, see the [Tooling support for .NET Standard libraries](#tooling).</span></span>

<span data-ttu-id="e2337-148"><a name="tooling" />**Suporte de ferramentas para as bibliotecas .NET padrão**</span><span class="sxs-lookup"><span data-stu-id="e2337-148"><a name="tooling" />**Tooling support for .NET Standard libraries**</span></span>

<span data-ttu-id="e2337-149">Com o lançamento do núcleo do .NET 2.0 e o .NET 2.0 padrão, ambas as Visual Studio de 2017 e [.NET Core Interface de linha de comando (CLI)](../../core/tools/index.md) incluem o suporte de ferramentas para criar bibliotecas .NET padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-149">With the release of .NET Core 2.0 and .NET Standard 2.0, both Visual Studio 2017 and the [.NET Core Command Line Interface (CLI)](../../core/tools/index.md) include tooling support for creating .NET Standard libraries.</span></span> 

<span data-ttu-id="e2337-150">Se você instalar o Visual Studio com o **desenvolvimento de plataforma cruzada do .NET Core** carga de trabalho, você pode criar um projeto de biblioteca do .NET 2.0 padrão usando um modelo de projeto, como mostra a figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="e2337-150">If you install Visual Studio with the **.NET Core cross-platform development** workload, you can create a .NET Standard 2.0 library project by using a project template, as the following figure shows.</span></span> 

# <a name="ctabcsharp"></a>[<span data-ttu-id="e2337-151">C#</span><span class="sxs-lookup"><span data-stu-id="e2337-151">C#</span></span>](#tab/csharp)
![Adicionar projeto de biblioteca novo padrão do .NET](./media/std-project-cs.png)
# <a name="visual-basictabvisual-basic"></a>[<span data-ttu-id="e2337-153">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e2337-153">Visual Basic</span></span>](#tab/visual-basic)
<a name="add-new-net-standard-library-projectmediastd-project-vbpng"></a>![Adicionar projeto de biblioteca novo padrão do .NET](./media/std-project-vb.png)
---

<span data-ttu-id="e2337-155">Se você estiver usando a CLI do .NET Core, o seguinte [dotnet novo](../../core/tools/dotnet-new.md) comando cria um projeto de biblioteca de classe que tem como alvo o .NET 2.0 padrão.</span><span class="sxs-lookup"><span data-stu-id="e2337-155">If you are using the .NET Core CLI, the following [dotnet new](../../core/tools/dotnet-new.md) command creates a class library project that targets the .NET Standard 2.0.</span></span>

```csharp
dotnet new classlib
```
```vb
dotnet new classlib -lang vb
```
  
## <a name="see-also"></a><span data-ttu-id="e2337-156">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e2337-156">See Also</span></span>
<span data-ttu-id="e2337-157">[Padrão do .NET](../net-standard.md)
[Introdução ao .NET padrão](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span><span class="sxs-lookup"><span data-stu-id="e2337-157">[.NET Standard](../net-standard.md)
[Introducing .NET Standard](https://blogs.msdn.microsoft.com/dotnet/2016/09/26/introducing-net-standard/)</span></span>
