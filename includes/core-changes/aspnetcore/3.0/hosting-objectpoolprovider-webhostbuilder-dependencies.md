---
ms.openlocfilehash: 4d99d0b6e99a7a9b976cf11832b33ad3bdc6d299
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901587"
---
### <a name="hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies"></a>Hospedagem: ObjectPoolProvider removido das dependências do WebHostBuilder

Como parte de fazer ASP.NET Core `ObjectPoolProvider` pagar mais pelo jogo, o foi removido do conjunto principal de dependências. Componentes específicos que `ObjectPoolProvider` dependem agora adicionam-no eles mesmos.

Para discussão, consulte [dotnet/aspnetcore#5944](https://github.com/dotnet/aspnetcore/issues/5944).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

`WebHostBuilder`fornece `ObjectPoolProvider` por padrão no recipiente DI.

#### <a name="new-behavior"></a>Novo comportamento

`WebHostBuilder`não fornece `ObjectPoolProvider` mais por padrão no contêiner DI.

#### <a name="reason-for-change"></a>Motivo da mudança

Essa mudança foi feita para fazer ASP.NET Core pagar mais pelo jogo.

#### <a name="recommended-action"></a>Ação recomendada

Se o `ObjectPoolProvider`seu componente precisar, ele precisa ser `IServiceCollection`adicionado às suas dependências através do .

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
