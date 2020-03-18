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
# <a name="unmanaged-native-library-loading-algorithm"></a>Algoritmo de carregamento de biblioteca não gerenciado (nativo)

Bibliotecas não gerenciadas são localizadas e carregadas com um algoritmo envolvendo vários estágios.

O algoritmo a seguir descreve como as `PInvoke`bibliotecas nativas são carregadas .

## <a name="pinvoke-load-library-algorithm"></a>`PInvoke`algoritmo biblioteca de carga

`PInvoke`usa o seguinte algoritmo ao tentar carregar um conjunto não gerenciado:

1. Determine `active` <xref:System.Runtime.Loader.AssemblyLoadContext>o . Para uma biblioteca de carga `active` não gerenciada, o AssemblyLoadContext `PInvoke`é aquele com o conjunto que define o .

2. Para `active` <xref:System.Runtime.Loader.AssemblyLoadContext>o , tente encontrar a assembléia em ordem prioritária por:
    * Verificando seu cache.

    * Chamando <xref:System.Runtime.InteropServices.DllImportResolver?displayProperty=nameWithType> o delegado <xref:System.Runtime.InteropServices.NativeLibrary.SetDllImportResolver(System.Reflection.Assembly,System.Runtime.InteropServices.DllImportResolver)?displayProperty=nameWithType> atual definido pela função.

    * Chamando <xref:System.Runtime.Loader.AssemblyLoadContext.LoadUnmanagedDll%2A?displayProperty=nameWithType> a `active` função no AssemblyLoadContext.

    * Verificando <xref:System.AppDomain> o cache da instância e executando a lógica de sondagem de [biblioteca não gerenciada (nativa).](default-probing.md#unmanaged-native-library-probing)

    * Levantando <xref:System.Runtime.Loader.AssemblyLoadContext.ResolvingUnmanagedDll?displayProperty=nameWithType> o `active` evento para o AssemblyLoadContext.
