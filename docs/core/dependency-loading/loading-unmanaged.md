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
# <a name="unmanaged-native-library-loading-algorithm"></a>Algoritmo de carregamento de biblioteca não gerenciada (nativa)

Bibliotecas não gerenciadas são localizadas e carregadas com um algoritmo que envolve vários estágios.

O algoritmo a seguir descreve como as bibliotecas nativas `PInvoke`são carregadas por meio do.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`carregar algoritmo de biblioteca

`PInvoke`usa o seguinte algoritmo ao tentar carregar um assembly não gerenciado:

1. Determine o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Para uma biblioteca `PInvoke`de carregamento não gerenciada, `active` o AssemblyLoadContext é o chamador do.

2. Para o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, tente localizar o assembly em ordem de prioridade:
    * Verificando seu cache.

    * Chamando o delegado <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> atual definido <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> pela função.

    * Chamando a <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> função.

    * Verificando <xref:System.AppDomain> o cache da instância e executando a lógica de [investigação da biblioteca não gerenciada (nativa)](default-probing.md#unmanaged-native-library-probing) .

    * Gerando <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> o evento para `active` o AssemblyLoadContext.

3. Se a biblioteca não gerenciada for carregada recentemente, o <xref:System.AppDomain.AssemblyLoad?displayProperty=nameWithType> evento será gerado.
