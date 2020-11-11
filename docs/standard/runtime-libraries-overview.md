---
title: Visão geral das bibliotecas de tempo de execução
description: Saiba o que está incluído na seção bibliotecas de tempo de execução do Sumário.
author: tdykstra
ms.date: 11/10/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 64bbc13f8c3df3c0c9a02fee4560c9ee3fcc5d62
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507604"
---
# <a name="runtime-libraries-overview"></a><span data-ttu-id="75b89-103">Visão geral das bibliotecas de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="75b89-103">Runtime libraries overview</span></span>

<span data-ttu-id="75b89-104">O [tempo de execução do .net](../core/introduction.md#sdk-and-runtimes), que é instalado em um computador para uso por [aplicativos dependentes da estrutura](../core/introduction.md#deployment-models), tem um conjunto padrão extenso de bibliotecas de classes:</span><span class="sxs-lookup"><span data-stu-id="75b89-104">The [.NET runtime](../core/introduction.md#sdk-and-runtimes), which is installed on a machine for use by [framework-dependent apps](../core/introduction.md#deployment-models), has an expansive standard set of class libraries:</span></span>

* <span data-ttu-id="75b89-105">O conjunto principal, incluído no tempo de execução e conhecido como [BCL (bibliotecas de classes base)](glossary.md#bcl).</span><span class="sxs-lookup"><span data-stu-id="75b89-105">The core set, included in the runtime and known as the [base class libraries (BCL)](glossary.md#bcl).</span></span>
* <span data-ttu-id="75b89-106">O conjunto completo, incluído no tempo de execução e conhecido como bibliotecas de [tempo de execução](glossary.md#runtime) ou [bibliotecas de estruturas](glossary.md#framework).</span><span class="sxs-lookup"><span data-stu-id="75b89-106">The complete set, included in the runtime and known as the [runtime libraries](glossary.md#runtime) or [framework libraries](glossary.md#framework).</span></span>
* <span data-ttu-id="75b89-107">Extensões para as bibliotecas de tempo de execução, fornecidas em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="75b89-107">Extensions to the runtime libraries, provided in NuGet packages.</span></span>

<span data-ttu-id="75b89-108">Essas bibliotecas fornecem implementações para muitos tipos, algoritmos e funcionalidades de utilitário específicos de aplicativos e gerais.</span><span class="sxs-lookup"><span data-stu-id="75b89-108">These libraries provide implementations for many general and app-specific types, algorithms, and utility functionality.</span></span>

## <a name="base-class-libraries"></a><span data-ttu-id="75b89-109">Bibliotecas de classes base</span><span class="sxs-lookup"><span data-stu-id="75b89-109">Base class libraries</span></span>

<span data-ttu-id="75b89-110">A BCL fornece os tipos básicos e a funcionalidade do utilitário e é a base de todas as outras bibliotecas de classes do .NET.</span><span class="sxs-lookup"><span data-stu-id="75b89-110">The BCL provides the foundational types and utility functionality and is the base of all other .NET class libraries.</span></span> <span data-ttu-id="75b89-111">Um exemplo é a <xref:System.String?displayProperty=nameWithType> classe, que fornece APIs para trabalhar com cadeias de caracteres.</span><span class="sxs-lookup"><span data-stu-id="75b89-111">An example is the <xref:System.String?displayProperty=nameWithType> class, which provides APIs for working with strings.</span></span>

## <a name="runtime-libraries"></a><span data-ttu-id="75b89-112">Bibliotecas de runtime</span><span class="sxs-lookup"><span data-stu-id="75b89-112">Runtime libraries</span></span>

<span data-ttu-id="75b89-113">Também conhecida como bibliotecas de estruturas, as bibliotecas de tempo de execução se baseiam na BCL para fornecer APIs de utilitário para tarefas comuns.</span><span class="sxs-lookup"><span data-stu-id="75b89-113">Also known as the framework libraries, the runtime libraries build on the BCL to provide utility APIs for common tasks.</span></span> <span data-ttu-id="75b89-114">Um exemplo é as [bibliotecas de serialização](serialization/index.md).</span><span class="sxs-lookup"><span data-stu-id="75b89-114">An example is the [serialization libraries](serialization/index.md).</span></span>

## <a name="extensions-to-the-runtime-libraries"></a><span data-ttu-id="75b89-115">Extensões para as bibliotecas de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="75b89-115">Extensions to the runtime libraries</span></span>

<span data-ttu-id="75b89-116">Algumas das bibliotecas de tempo de execução são fornecidas em pacotes NuGet em vez de internos ao tempo de execução que é instalado para aplicativos dependentes da estrutura.</span><span class="sxs-lookup"><span data-stu-id="75b89-116">Some of the runtime libraries are provided in NuGet packages rather than built-in to the runtime that is installed for framework-dependent apps.</span></span> <span data-ttu-id="75b89-117">Um exemplo é a [API de log do .net](../core/extensions/logging.md).</span><span class="sxs-lookup"><span data-stu-id="75b89-117">An example is the [.NET Logging API](../core/extensions/logging.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="75b89-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="75b89-118">See also</span></span>

* [<span data-ttu-id="75b89-119">Introdução ao .NET</span><span class="sxs-lookup"><span data-stu-id="75b89-119">Introduction to .NET</span></span>](../core/introduction.md)
* [<span data-ttu-id="75b89-120">Instalar o SDK ou tempo de execução do .NET</span><span class="sxs-lookup"><span data-stu-id="75b89-120">Install .NET SDK or runtime</span></span>](../core/install/index.yml)
* [<span data-ttu-id="75b89-121">Selecione o SDK .NET ou a versão de tempo de execução instalada para usar</span><span class="sxs-lookup"><span data-stu-id="75b89-121">Select the installed .NET SDK or runtime version to use</span></span>](../core/versions/selection.md)
* [<span data-ttu-id="75b89-122">Publicar aplicativos dependentes da estrutura</span><span class="sxs-lookup"><span data-stu-id="75b89-122">Publish framework-dependent apps</span></span>](../core/deploying/index.md#publish-framework-dependent)
