---
title: Algoritmo de carregamento de biblioteca não gerenciada-.NET Core
description: Descrição dos detalhes do algoritmo de carregamento de assembly não gerenciado no .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: d7c298f6c2e3aab0c7498bfafc0a0a94ea1fe23e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/10/2019
ms.locfileid: "72250035"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="917b5-103">Algoritmo de carregamento de biblioteca não gerenciada (nativa)</span><span class="sxs-lookup"><span data-stu-id="917b5-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="917b5-104">Bibliotecas não gerenciadas são localizadas e carregadas com um algoritmo que envolve vários estágios.</span><span class="sxs-lookup"><span data-stu-id="917b5-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="917b5-105">O algoritmo a seguir descreve como as bibliotecas nativas são carregadas por meio de `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="917b5-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="917b5-106">`PInvoke` algoritmo de biblioteca de carga</span><span class="sxs-lookup"><span data-stu-id="917b5-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="917b5-107">`PInvoke` usa o seguinte algoritmo ao tentar carregar um assembly não gerenciado:</span><span class="sxs-lookup"><span data-stu-id="917b5-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="917b5-108">Determine o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="917b5-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="917b5-109">Para uma biblioteca de carga não gerenciada, o `active` AssemblyLoadContext é aquele com o assembly que define o `PInvoke`.</span><span class="sxs-lookup"><span data-stu-id="917b5-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="917b5-110">Para o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, tente encontrar o assembly em ordem de prioridade:</span><span class="sxs-lookup"><span data-stu-id="917b5-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="917b5-111">Verificando seu cache.</span><span class="sxs-lookup"><span data-stu-id="917b5-111">Checking its cache.</span></span>

    * <span data-ttu-id="917b5-112">Chamando o delegado <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> atual definido pela função <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="917b5-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="917b5-113">Chamar a função <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> no `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="917b5-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="917b5-114">Verificando o cache da instância do <xref:System.AppDomain> e executando a lógica de [investigação da biblioteca não gerenciada (nativa)](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="917b5-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="917b5-115">Gerando o evento <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> para o `active` AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="917b5-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
