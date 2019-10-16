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
# <a name="unmanaged-native-library-loading-algorithm"></a>Algoritmo de carregamento de biblioteca não gerenciada (nativa)

Bibliotecas não gerenciadas são localizadas e carregadas com um algoritmo que envolve vários estágios.

O algoritmo a seguir descreve como as bibliotecas nativas são carregadas por meio de `PInvoke`.

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke` algoritmo de biblioteca de carga

`PInvoke` usa o seguinte algoritmo ao tentar carregar um assembly não gerenciado:

1. Determine o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>. Para uma biblioteca de carga não gerenciada, o `active` AssemblyLoadContext é aquele com o assembly que define o `PInvoke`.

2. Para o `active` <xref:System.Runtime.Loader.AssemblyLoadContext>, tente encontrar o assembly em ordem de prioridade:
    * Verificando seu cache.

    * Chamando o delegado <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> atual definido pela função <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType>.

    * Chamar a função <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> no `active` AssemblyLoadContext.

    * Verificando o cache da instância do <xref:System.AppDomain> e executando a lógica de [investigação da biblioteca não gerenciada (nativa)](default-probing.md#unmanaged-native-library-probing) .

    * Gerando o evento <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> para o `active` AssemblyLoadContext.
