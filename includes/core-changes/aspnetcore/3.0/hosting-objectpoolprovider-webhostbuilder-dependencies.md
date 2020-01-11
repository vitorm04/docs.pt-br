---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901587"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hospedagem: objectpoolprovider removido de dependências WebHostBuilder

Como parte de fazer ASP.NET Core mais Pay for Play, o `ObjectPoolProvider` foi removido do conjunto principal de dependências. Os componentes específicos que dependem de `ObjectPoolProvider` agora o adicionam.

Para obter uma discussão, consulte [dotnet/aspnetcore # 5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`WebHostBuilder` fornece `ObjectPoolProvider` por padrão no contêiner DI.

#### <a name="new-behavior"></a>Novo comportamento

`WebHostBuilder` não fornece mais `ObjectPoolProvider` por padrão no contêiner DI.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração foi feita para fazer ASP.NET Core mais Pay for Play.

#### <a name="recommended-action"></a>Ação recomendada

Se seu componente exigir `ObjectPoolProvider`, ele precisará ser adicionado às suas dependências por meio do `IServiceCollection`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

{1&gt;Nenhum&lt;1}

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
