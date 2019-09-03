---
title: Algoritmo de carregamento de biblioteca não gerenciada-.NET Core
description: Descrição dos detalhes do algoritmo de carregamento de assembly não gerenciado no .NET Core
ms.date: 08/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: 8240cb730180637393e2545f8013d3f1439be719
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/24/2019
ms.locfileid: "70234621"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="26671-103">Algoritmo de carregamento de biblioteca não gerenciada (nativa)</span><span class="sxs-lookup"><span data-stu-id="26671-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="26671-104">Bibliotecas não gerenciadas são localizadas e carregadas com um algoritmo que envolve vários estágios.</span><span class="sxs-lookup"><span data-stu-id="26671-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="26671-105">O algoritmo a seguir descreve como as bibliotecas nativas `PInvoke`são carregadas por meio do.</span><span class="sxs-lookup"><span data-stu-id="26671-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="26671-106">`PInvoke`carregar algoritmo de biblioteca</span><span class="sxs-lookup"><span data-stu-id="26671-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="26671-107">`PInvoke`usa o seguinte algoritmo ao tentar carregar um assembly não gerenciado:</span><span class="sxs-lookup"><span data-stu-id="26671-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="26671-108">Determine o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span><span class="sxs-lookup"><span data-stu-id="26671-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="26671-109">Para uma biblioteca `PInvoke`de carregamento não gerenciada, `active` o AssemblyLoadContext é o chamador do.</span><span class="sxs-lookup"><span data-stu-id="26671-109">For an unmanaged load library, the `active` AssemblyLoadContext is the caller of the `PInvoke`.</span></span>

2. <span data-ttu-id="26671-110">Para o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, tente localizar o assembly em ordem de prioridade:</span><span class="sxs-lookup"><span data-stu-id="26671-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="26671-111">Verificando seu cache.</span><span class="sxs-lookup"><span data-stu-id="26671-111">Checking its cache.</span></span>

    * <span data-ttu-id="26671-112">Chamando o delegado <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> atual definido <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> pela função.</span><span class="sxs-lookup"><span data-stu-id="26671-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="26671-113">Chamando a <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> função.</span><span class="sxs-lookup"><span data-stu-id="26671-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="26671-114">Verificando <xref:System.AppDomain> o cache da instância e executando a lógica de [investigação da biblioteca não gerenciada (nativa)](default-probing.md#unmanaged-native-library-probing) .</span><span class="sxs-lookup"><span data-stu-id="26671-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="26671-115">Gerando <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> o evento para `active` o AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="26671-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>

3. <span data-ttu-id="26671-116">Se a biblioteca não gerenciada for carregada recentemente, o <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento será gerado.</span><span class="sxs-lookup"><span data-stu-id="26671-116">If the unmanaged library is newly loaded, the <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> event is raised.</span></span>
