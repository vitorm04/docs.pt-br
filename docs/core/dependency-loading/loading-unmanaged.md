---
title: Algoritmo de carregamento de biblioteca não gerenciado - .NET Core
description: Descrição dos detalhes do algoritmo de carregamento de montagem não gerenciado no .NET Core
ms.date: 10/09/2019
author: sdmaclea
ms.author: stmaclea
ms.openlocfilehash: c651aa6e0f37a968e6f8b26d1909def6fa488ccd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "72250035"
---
# <a name="unmanaged-native-library-loading-algorithm"></a><span data-ttu-id="1f92b-103">Algoritmo de carregamento de biblioteca não gerenciado (nativo)</span><span class="sxs-lookup"><span data-stu-id="1f92b-103">Unmanaged (native) library loading algorithm</span></span>

<span data-ttu-id="1f92b-104">Bibliotecas não gerenciadas são localizadas e carregadas com um algoritmo envolvendo vários estágios.</span><span class="sxs-lookup"><span data-stu-id="1f92b-104">Unmanaged libraries are located and loaded with an algorithm involving various stages.</span></span>

<span data-ttu-id="1f92b-105">O algoritmo a seguir descreve como as `PInvoke`bibliotecas nativas são carregadas .</span><span class="sxs-lookup"><span data-stu-id="1f92b-105">The following algorithm describes how native libraries are loaded through `PInvoke`.</span></span>

## <a name="pinvoke-load-library-algorithm"></a><span data-ttu-id="1f92b-106">`PInvoke`algoritmo biblioteca de carga</span><span class="sxs-lookup"><span data-stu-id="1f92b-106">`PInvoke` load library algorithm</span></span>

<span data-ttu-id="1f92b-107">`PInvoke`usa o seguinte algoritmo ao tentar carregar um conjunto não gerenciado:</span><span class="sxs-lookup"><span data-stu-id="1f92b-107">`PInvoke` uses the following algorithm when attempting to load an unmanaged assembly:</span></span>

1. <span data-ttu-id="1f92b-108">Determine `active` <xref:System.Runtime.Loader.AssemblyLoadContext>o .</span><span class="sxs-lookup"><span data-stu-id="1f92b-108">Determine the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>.</span></span> <span data-ttu-id="1f92b-109">Para uma biblioteca de carga `active` não gerenciada, o AssemblyLoadContext `PInvoke`é aquele com o conjunto que define o .</span><span class="sxs-lookup"><span data-stu-id="1f92b-109">For an unmanaged load library, the `active` AssemblyLoadContext is the one with the assembly that defines the `PInvoke`.</span></span>

2. <span data-ttu-id="1f92b-110">Para `active` <xref:System.Runtime.Loader.AssemblyLoadContext>o , tente encontrar a assembléia em ordem prioritária por:</span><span class="sxs-lookup"><span data-stu-id="1f92b-110">For the `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, try to find the assembly in priority order by:</span></span>
    * <span data-ttu-id="1f92b-111">Verificando seu cache.</span><span class="sxs-lookup"><span data-stu-id="1f92b-111">Checking its cache.</span></span>

    * <span data-ttu-id="1f92b-112">Chamando <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> o delegado <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> atual definido pela função.</span><span class="sxs-lookup"><span data-stu-id="1f92b-112">Calling the current <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> delegate set by the <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> function.</span></span>

    * <span data-ttu-id="1f92b-113">Chamando <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> a `active` função no AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="1f92b-113">Calling the <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> function on the `active` AssemblyLoadContext.</span></span>

    * <span data-ttu-id="1f92b-114">Verificando <xref:System.AppDomain> o cache da instância e executando a lógica de sondagem de [biblioteca não gerenciada (nativa).](default-probing.md#unmanaged-native-library-probing)</span><span class="sxs-lookup"><span data-stu-id="1f92b-114">Checking the <xref:System.AppDomain> instance's cache and running the [Unmanaged (native) library probing](default-probing.md#unmanaged-native-library-probing) logic.</span></span>

    * <span data-ttu-id="1f92b-115">Levantando <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> o `active` evento para o AssemblyLoadContext.</span><span class="sxs-lookup"><span data-stu-id="1f92b-115">Raising the <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> event for the `active` AssemblyLoadContext.</span></span>
