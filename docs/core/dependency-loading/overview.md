---
title: Carregamento de dependência-.NET Core
description: Visão geral do carregamento de dependências gerenciadas e não gerenciadas no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73416683"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="834b1-103">Carregamento de dependência no .NET Core</span><span class="sxs-lookup"><span data-stu-id="834b1-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="834b1-104">Cada aplicativo .NET Core tem dependências.</span><span class="sxs-lookup"><span data-stu-id="834b1-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="834b1-105">Até mesmo o simples aplicativo de `hello world` tem dependências em partes das bibliotecas de classes do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="834b1-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="834b1-106">Entender a lógica de carregamento do assembly padrão do .NET Core pode ajudar a entender e depurar problemas de implantação típicos.</span><span class="sxs-lookup"><span data-stu-id="834b1-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="834b1-107">Em alguns aplicativos, as dependências são determinadas dinamicamente no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="834b1-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="834b1-108">Nessas situações, é essencial entender como os assemblies gerenciados e as dependências não gerenciadas são carregados.</span><span class="sxs-lookup"><span data-stu-id="834b1-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="834b1-109">Entendendo o AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="834b1-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="834b1-110">A API de <xref:System.Runtime.Loader.AssemblyLoadContext> é fundamental para o design de carregamento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="834b1-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="834b1-111">O artigo [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) fornece uma visão geral conceitual do design.</span><span class="sxs-lookup"><span data-stu-id="834b1-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="834b1-112">Carregando detalhes</span><span class="sxs-lookup"><span data-stu-id="834b1-112">Loading details</span></span>

<span data-ttu-id="834b1-113">Os detalhes do algoritmo de carregamento são abordados brevemente em vários artigos:</span><span class="sxs-lookup"><span data-stu-id="834b1-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="834b1-114">Algoritmo de carregamento de assembly gerenciado</span><span class="sxs-lookup"><span data-stu-id="834b1-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="834b1-115">Algoritmo de carregamento de assembly satélite</span><span class="sxs-lookup"><span data-stu-id="834b1-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="834b1-116">Algoritmo de carregamento de biblioteca não gerenciada (nativa)</span><span class="sxs-lookup"><span data-stu-id="834b1-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="834b1-117">Investigação padrão</span><span class="sxs-lookup"><span data-stu-id="834b1-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="834b1-118">Criar um aplicativo do .NET Core com plug-ins</span><span class="sxs-lookup"><span data-stu-id="834b1-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="834b1-119">O tutorial [criar um aplicativo .NET Core com plug-ins](../tutorials/creating-app-with-plugin-support.md) descreve como criar um AssemblyLoadContext personalizado.</span><span class="sxs-lookup"><span data-stu-id="834b1-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="834b1-120">Ele usa um <xref:System.Runtime.Loader.AssemblyDependencyResolver> para resolver as dependências do plug-in.</span><span class="sxs-lookup"><span data-stu-id="834b1-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="834b1-121">O tutorial isola corretamente as dependências do plug-in do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="834b1-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="834b1-122">Como usar e depurar a capacidade de descarregamento de assembly no .NET Core</span><span class="sxs-lookup"><span data-stu-id="834b1-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="834b1-123">O artigo [como usar e depurar a descarga do assembly no .NET Core](../../standard/assembly/unloadability.md) é um tutorial passo a passo.</span><span class="sxs-lookup"><span data-stu-id="834b1-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="834b1-124">Ele mostra como carregar um aplicativo .NET Core, executá-lo e descarregá-lo.</span><span class="sxs-lookup"><span data-stu-id="834b1-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="834b1-125">O artigo também fornece dicas de depuração.</span><span class="sxs-lookup"><span data-stu-id="834b1-125">The article also provides debugging tips.</span></span>
