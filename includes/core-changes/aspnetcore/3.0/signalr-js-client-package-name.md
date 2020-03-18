---
ms.openlocfilehash: f202b39f1a45f740625827be25e72df0e403d605
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901720"
---
### <a name="signalr-javascript-client-package-name-changed"></a>SignalR: Nome do pacote do cliente JavaScript alterado

Em ASP.NET pré-visualização do Core 3.0 7, `@aspnet/signalr` `@microsoft/signalr`o nome do pacote do cliente SignalR JavaScript mudou de . A mudança de nome reflete o fato de que o SignalR é útil em mais do que apenas ASP.NET aplicativos Core, graças ao Azure SignalR Service.

Para reagir a essa alteração, altere as referências `require` em seus arquivos, `import` instruções e instruções do *Package.json.* Nenhuma API mudará como parte deste renome.

Para discussão, consulte [dotnet/aspnetcore#11637](https://github.com/dotnet/aspnetcore/issues/11637).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O pacote do `@aspnet/signalr`cliente foi nomeado .

#### <a name="new-behavior"></a>Novo comportamento

O pacote cliente `@microsoft/signalr`é chamado .

#### <a name="reason-for-change"></a>Motivo da mudança

A mudança de nome esclarece que o SignalR é útil além ASP.NET aplicativos Core, graças ao Serviço Azure SignalR.

#### <a name="recommended-action"></a>Ação recomendada

Mude para o `@microsoft/signalr`novo pacote .

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
