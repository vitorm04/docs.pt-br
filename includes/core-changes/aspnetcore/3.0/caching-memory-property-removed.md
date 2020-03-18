---
ms.openlocfilehash: 2c1362d6982206b14475f77700add0bae61da173
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901775"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Cache: CompactOnMemoryPressure propriedade removido

A versão ASP.NET Core 3.0 removeu as [APIs obsoletas MemoryCacheOptions](https://github.com/dotnet/extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Descrição da alteração

Esta mudança é um acompanhamento para [aspnet/Caching#221](https://github.com/aspnet/Caching/issues/221). Para discussão, consulte [dotnet/extensões#1062](https://github.com/dotnet/extensions/issues/1062).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`MemoryCacheOptions.CompactOnMemoryPressure`propriedade estava disponível.

#### <a name="new-behavior"></a>Novo comportamento

A `MemoryCacheOptions.CompactOnMemoryPressure` propriedade foi removida.

#### <a name="reason-for-change"></a>Motivo da mudança

Compactar automaticamente o cache causou problemas. Para evitar comportamentos inesperados, o cache só deve ser compactado quando necessário.

#### <a name="recommended-action"></a>Ação recomendada

Para compactar o cache, abaixado `MemoryCache` e ligar `Compact` quando necessário.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
