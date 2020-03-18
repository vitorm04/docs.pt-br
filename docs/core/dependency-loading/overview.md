---
title: Carregamento de dependência - .NET Core
description: Visão geral do carregamento de dependência gerenciado e não gerenciado no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.topic: overview
ms.openlocfilehash: f6b5fc1f92171b61dcab162b782ca7212c602d76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "73416683"
---
# <a name="dependency-loading-in-net-core"></a><span data-ttu-id="a560c-103">Carregamento de dependência no Núcleo .NET</span><span class="sxs-lookup"><span data-stu-id="a560c-103">Dependency loading in .NET Core</span></span>

<span data-ttu-id="a560c-104">Cada aplicativo .NET Core tem dependências.</span><span class="sxs-lookup"><span data-stu-id="a560c-104">Every .NET Core application has dependencies.</span></span> <span data-ttu-id="a560c-105">Mesmo o `hello world` aplicativo simples tem dependências de partes das bibliotecas de classe .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a560c-105">Even the simple `hello world` app has dependencies on portions of the .NET Core class libraries.</span></span>

<span data-ttu-id="a560c-106">Entender a lógica de carregamento padrão do grupo .NET Core pode ajudar a entender e depurar problemas típicos de implantação.</span><span class="sxs-lookup"><span data-stu-id="a560c-106">Understanding .NET Core default assembly loading logic can help understanding and debugging typical deployment issues.</span></span>

<span data-ttu-id="a560c-107">Em alguns aplicativos, as dependências são determinadas dinamicamente em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a560c-107">In some applications, dependencies are dynamically determined at runtime.</span></span> <span data-ttu-id="a560c-108">Nessas situações, é fundamental entender como montagens gerenciadas e dependências não gerenciadas são carregadas.</span><span class="sxs-lookup"><span data-stu-id="a560c-108">In these situations, it's critical to understand how managed assemblies and unmanaged dependencies are loaded.</span></span>

## <a name="understanding-assemblyloadcontext"></a><span data-ttu-id="a560c-109">Entendendo o AssemblyLoadContext</span><span class="sxs-lookup"><span data-stu-id="a560c-109">Understanding AssemblyLoadContext</span></span>

<span data-ttu-id="a560c-110">A <xref:System.Runtime.Loader.AssemblyLoadContext> API é central para o projeto de carregamento .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a560c-110">The <xref:System.Runtime.Loader.AssemblyLoadContext> API is central to the .NET Core loading design.</span></span> <span data-ttu-id="a560c-111">O artigo [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) fornece uma visão geral conceitual do projeto.</span><span class="sxs-lookup"><span data-stu-id="a560c-111">The [Understanding AssemblyLoadContext](understanding-assemblyloadcontext.md) article provides a conceptual overview to the design.</span></span>

## <a name="loading-details"></a><span data-ttu-id="a560c-112">Carregando detalhes</span><span class="sxs-lookup"><span data-stu-id="a560c-112">Loading details</span></span>

<span data-ttu-id="a560c-113">Os detalhes do algoritmo de carregamento são cobertos brevemente em vários artigos:</span><span class="sxs-lookup"><span data-stu-id="a560c-113">The loading algorithm details are covered briefly in several articles:</span></span>

- [<span data-ttu-id="a560c-114">Algoritmo de carregamento de montagem gerenciado</span><span class="sxs-lookup"><span data-stu-id="a560c-114">Managed assembly loading algorithm</span></span>](loading-managed.md)
- [<span data-ttu-id="a560c-115">Algoritmo de carregamento de montagem por satélite</span><span class="sxs-lookup"><span data-stu-id="a560c-115">Satellite assembly loading algorithm</span></span>](loading-resources.md)
- [<span data-ttu-id="a560c-116">Algoritmo de carregamento de biblioteca não gerenciado (nativo)</span><span class="sxs-lookup"><span data-stu-id="a560c-116">Unmanaged (native) library loading algorithm</span></span>](loading-unmanaged.md)
- [<span data-ttu-id="a560c-117">Sondagem padrão</span><span class="sxs-lookup"><span data-stu-id="a560c-117">Default probing</span></span>](default-probing.md)

## <a name="create-a-net-core-application-with-plugins"></a><span data-ttu-id="a560c-118">Criar um aplicativo do .NET Core com plug-ins</span><span class="sxs-lookup"><span data-stu-id="a560c-118">Create a .NET Core application with plugins</span></span>

<span data-ttu-id="a560c-119">O tutorial [Criar um aplicativo .NET Core com plugins](../tutorials/creating-app-with-plugin-support.md) descreve como criar um AssemblyLoadContext personalizado.</span><span class="sxs-lookup"><span data-stu-id="a560c-119">The tutorial [Create a .NET Core application with plugins](../tutorials/creating-app-with-plugin-support.md) describes how to create a custom AssemblyLoadContext.</span></span> <span data-ttu-id="a560c-120">Ele usa <xref:System.Runtime.Loader.AssemblyDependencyResolver> um para resolver as dependências do plugin.</span><span class="sxs-lookup"><span data-stu-id="a560c-120">It uses an <xref:System.Runtime.Loader.AssemblyDependencyResolver> to resolve the dependencies of the plugin.</span></span> <span data-ttu-id="a560c-121">O tutorial isola corretamente as dependências do plugin do aplicativo de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="a560c-121">The tutorial correctly isolates the plugin's dependencies from the hosting application.</span></span>

## <a name="how-to-use-and-debug-assembly-unloadability-in-net-core"></a><span data-ttu-id="a560c-122">Como usar e depurar a capacidade de descarregamento de assembly no .NET Core</span><span class="sxs-lookup"><span data-stu-id="a560c-122">How to use and debug assembly unloadability in .NET Core</span></span>

<span data-ttu-id="a560c-123">A [capacidade de descarga de montagem de Como usar e depurar no](../../standard/assembly/unloadability.md) artigo .NET Core é um tutorial passo-a-passo.</span><span class="sxs-lookup"><span data-stu-id="a560c-123">The [How to use and debug assembly unloadability in .NET Core](../../standard/assembly/unloadability.md) article is a step-by-step tutorial.</span></span> <span data-ttu-id="a560c-124">Ele mostra como carregar um aplicativo .NET Core, executá-lo e, em seguida, descarregá-lo.</span><span class="sxs-lookup"><span data-stu-id="a560c-124">It shows how to load a .NET Core application, execute, and then unload it.</span></span> <span data-ttu-id="a560c-125">O artigo também fornece dicas de depuração.</span><span class="sxs-lookup"><span data-stu-id="a560c-125">The article also provides debugging tips.</span></span>
