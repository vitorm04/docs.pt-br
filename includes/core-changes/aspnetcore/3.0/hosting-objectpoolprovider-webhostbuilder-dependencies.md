---
ms.openlocfilehash: 16b9fde49f513643a37f65f3e926a34fc991c55a
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394316"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hospedagem: objectpoolprovider removido de dependências WebHostBuilder

Como parte de fazer ASP.NET Core mais Pay for Play, o `ObjectPoolProvider` foi removido do conjunto principal de dependências. Os componentes específicos que dependem de `ObjectPoolProvider` agora o adicionam.

Para obter uma discussão, consulte [ASPNET/AspNetCore # 5944](https://github.com/aspnet/AspNetCore/issues/5944).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`WebHostBuilder` fornece `ObjectPoolProvider` por padrão no contêiner de DI.

#### <a name="new-behavior"></a>Novo comportamento

o `WebHostBuilder` não fornece mais `ObjectPoolProvider` por padrão no contêiner de DI.

#### <a name="reason-for-change"></a>Motivo da alteração

Essa alteração foi feita para fazer ASP.NET Core mais Pay for Play.

#### <a name="recommended-action"></a>Ação recomendada

Se o componente exigir `ObjectPoolProvider`, ele precisará ser adicionado às suas dependências por meio do `IServiceCollection`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
