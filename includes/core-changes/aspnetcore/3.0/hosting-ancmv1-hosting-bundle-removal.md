---
ms.openlocfilehash: 04e5ca41374fc333a31f0422bc2e89f54b3cb049
ms.sourcegitcommit: 2e95559d957a1a942e490c5fd916df04b39d73a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72394193"
---
### <a name="hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle"></a>Hospedagem: AspNetCoreModule v1 removido do pacote de hospedagem do Windows

A partir do ASP.NET Core 3,0, o grupo de hospedagem do Windows não conterá AspNetCoreModule (ANCM) v1.

O ANCM V2 é compatível com versões anteriores com ANCM OutOfProcess e é recomendado para uso com ASP.NET Core aplicativos 3,0.

Para obter uma discussão, consulte [ASPNET/AspNetCore # 7095](https://github.com/aspnet/AspNetCore/issues/7095).

#### <a name="version-introduced"></a>Versão introduzida

3.0

#### <a name="old-behavior"></a>Comportamento antigo

O ANCM v1 está incluído no pacote de hospedagem do Windows.

#### <a name="new-behavior"></a>Novo comportamento

O ANCM v1 não está incluído no pacote de hospedagem do Windows.

#### <a name="reason-for-change"></a>Motivo da alteração

O ANCM V2 é compatível com versões anteriores com ANCM OutOfProcess e é recomendado para uso com ASP.NET Core aplicativos 3,0.

#### <a name="recommended-action"></a>Ação recomendada

Use o ANCM V2 com aplicativos ASP.NET Core 3,0.

Se o ANCM v1 for necessário, ele poderá ser instalado usando o pacote de hospedagem ASP.NET Core 2,1 ou 2,2 do Windows.

Essa alteração interromperá ASP.NET Core aplicativos 3,0 que:

- Explicitamente, optado por usar o ANCM v1 com `<AspNetCoreModuleName>AspNetCoreModule</AspNetCoreModuleName>`.
- Ter um arquivo *Web. config* personalizado com `<add name="aspNetCore" path="*" verb="*" modules="AspNetCoreModule" resourceType="Unspecified" />`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

Nenhum

<!-- 

#### Affected APIs

Not detectable via API analysis

-->
