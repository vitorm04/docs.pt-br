---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7088f87e9a7da144266135f4b2397e611cf0a228
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2020
ms.locfileid: "75901720"
---
### <a name="signalr-javascript-client-package-name-changed"></a>Signalr: nome do pacote de cliente JavaScript alterado

No ASP.NET Core 3,0 Preview 7, o nome do pacote de cliente do sinalizador JavaScript mudou de `@aspnet/signalr` para `@microsoft/signalr`. A alteração de nome reflete o fato de que o Signalr é útil em mais do que apenas ASP.NET Core aplicativos, graças ao serviço de Signaler do Azure.

Para reagir a essa alteração, altere as referências nos arquivos *Package. JSON* , instruções `require` e instruções ECMAScript `import`. Nenhuma API será alterada como parte dessa renomeação.

Para obter uma discussão, consulte [dotnet/aspnetcore # 11637](https://github.com/dotnet/aspnetcore/issues/11637).

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

{1&gt;Nenhum&lt;1}

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
