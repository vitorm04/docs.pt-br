---
ms.openlocfilehash: acef6d7177ee5ad7e18dc8ba1e383d6f76263623
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394449"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Signalr: nome do pacote de cliente JavaScript alterado

No ASP.NET Core 3,0 Preview 7, o nome do pacote de cliente do sinalizador JavaScript mudou de `@aspnet/signalr` para `@microsoft/signalr`. A alteração de nome reflete o fato de que o Signalr é útil em mais do que apenas ASP.NET Core aplicativos, graças ao serviço de Signaler do Azure.

Para reagir a essa alteração, altere as referências em seus arquivos *Package. JSON* , instruções `require` e instruções ECMAScript `import`. Nenhuma API será alterada como parte dessa renomeação.

Para obter uma discussão, consulte [ASPNET/AspNetCore # 11637](https://github.com/aspnet/AspNetCore/issues/11637).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O pacote do cliente foi nomeado `@aspnet/signalr`.

#### <a name="new-behavior"></a>Novo comportamento

O pacote do cliente é denominado `@microsoft/signalr`.

#### <a name="reason-for-change"></a>Motivo da alteração

A alteração de nome esclarece que o Signalr é útil além dos aplicativos ASP.NET Core, graças ao serviço do Azure Signalr.

#### <a name="recommended-action"></a>Ação recomendada

Alterne para o novo pacote `@microsoft/signalr`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
