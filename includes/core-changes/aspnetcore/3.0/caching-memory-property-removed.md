---
ms.openlocfilehash: 7d40324e6b0bc4afab9dd39b236f0909f360cc9b
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394275"
---
### <a name="caching-compactonmemorypressure-property-removed"></a>Caching: Propriedade CompactOnMemoryPressure removida

A versão ASP.NET Core 3,0 removeu as [APIs MemoryCacheOptions obsoletas](https://github.com/aspnet/Extensions/blob/dc5c593da7b72c82e6fe85abb91d03818f9b700c/src/Caching/Memory/src/MemoryCacheOptions.cs#L17-L18).

#### <a name="change-description"></a>Alterar descrição

Essa alteração é um acompanhamento do [ASPNET/Caching # 221](https://github.com/aspnet/Caching/issues/221). Para obter uma discussão, consulte [ASPNET/Extensions # 1062](https://github.com/aspnet/Extensions/issues/1062).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

a propriedade `MemoryCacheOptions.CompactOnMemoryPressure` estava disponível.

#### <a name="new-behavior"></a>Novo comportamento

A propriedade `MemoryCacheOptions.CompactOnMemoryPressure` foi removida.

#### <a name="reason-for-change"></a>Motivo da alteração

A compactação automática do cache causou problemas. Para evitar um comportamento inesperado, o cache só deve ser compactado quando necessário.

#### <a name="recommended-action"></a>Ação recomendada

Para compactar o cache, downcast para `MemoryCache` e chamar `Compact` quando necessário.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

<xref:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure%2A?displayProperty=nameWithType>

<!--

#### Affected APIs

`Overload:Microsoft.Extensions.Caching.Memory.MemoryCacheOptions.CompactOnMemoryPressure`

-->
