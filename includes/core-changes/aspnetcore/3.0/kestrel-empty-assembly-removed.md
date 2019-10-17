---
ms.openlocfilehash: 1c9c899d77dd69e185281d98bfec18ce73d80815
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394127"
---
### <a name="kestrel-empty-https-assembly-removed"></a>Kestrel: assembly HTTPS vazio removido

O assembly <xref:Microsoft.AspNetCore.Server.Kestrel.Https?displayProperty=fullName> foi removido.

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="reason-for-change"></a>Motivo da alteração

No ASP.NET Core 2,1, o conteúdo de `Microsoft.AspNetCore.Server.Kestrel.Https` foi movido para <xref:Microsoft.AspNetCore.Server.Kestrel.Core?displayProperty=fullName>. Essa alteração foi feita de forma não significativa usando atributos `[TypeForwardedTo]`.

#### <a name="recommended-action"></a>Ação recomendada

- Bibliotecas que fazem referência a `Microsoft.AspNetCore.Server.Kestrel.Https` 2,0 devem atualizar todas as dependências de ASP.NET Core para 2,1 ou posterior. Caso contrário, eles poderão ser interrompidos quando forem carregados em um aplicativo ASP.NET Core 3,0.
- Os aplicativos e bibliotecas destinados a ASP.NET Core 2,1 e posterior devem remover todas as referências diretas para o pacote NuGet `Microsoft.AspNetCore.Server.Kestrel.Https`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
