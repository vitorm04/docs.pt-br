---
ms.openlocfilehash: 82103d82a6f68c62f3532608718bc71b0ba126bf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75901774"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hospedagem: AspNetCoreModule V1 removido do Pacote de Hospedagem do Windows

Começando com ASP.NET Core 3.0, o Pacote de Hospedagem do Windows não conterá OAspNetCoreModule (ANCM) V1.

O ANCM V2 é retrocompatível com o ANCM OutOfProcess e é recomendado para uso com aplicativos ASP.NET Core 3.0.

Para discussão, consulte [dotnet/aspnetcore#7095](https://github.com/dotnet/aspnetcore/issues/7095).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

Ancm V1 está incluído no Pacote de Hospedagem do Windows.

#### <a name="new-behavior"></a>Novo comportamento

O ANCM V1 não está incluído no Pacote de Hospedagem do Windows.

#### <a name="reason-for-change"></a>Motivo da mudança

O ANCM V2 é retrocompatível com o ANCM OutOfProcess e é recomendado para uso com aplicativos ASP.NET Core 3.0.

#### <a name="recommended-action"></a>Ação recomendada

Use ancm V2 com aplicativos ASP.NET Core 3.0.

Se o ANCM V1 for necessário, ele pode ser instalado usando o ASP.NET Core 2.1 ou 2.2 Windows Hosting Bundle.

Essa alteração quebrará ASP.NET aplicativos Core 3.0 que:

- Optou explicitamente pelo uso do `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`ANCM V1 com .
- Tenha um arquivo *web.config* personalizado com `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
