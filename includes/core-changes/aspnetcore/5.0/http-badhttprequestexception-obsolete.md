---
ms.openlocfilehash: c4e7864262a11aafa4b7f1f4bdf632fbf084c560
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507062"
---
### <a name="http-kestrel-and-iis-badhttprequestexception-types-marked-obsolete-and-replaced"></a>Tipos de BadHttpRequestException de HTTP: Kestrel e IIS marcados como obsoletos e substituídos

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` foram marcados como obsoletos e alterados para derivar de `Microsoft.AspNetCore.Http.BadHttpRequestException`. Os servidores Kestrel e IIS ainda lançam seus tipos de exceção antigos para compatibilidade com versões anteriores. Os tipos obsoletos serão removidos em uma versão futura.

Para obter uma discussão, consulte [dotnet/aspnetcore # 20614](https://github.com/dotnet/aspnetcore/issues/20614).

#### <a name="version-introduced"></a>Versão introduzida

5,0 versão prévia 4

#### <a name="old-behavior"></a>Comportamento antigo

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` derivado de <xref:System.IO.IOException?displayProperty=nameWithType>.

#### <a name="new-behavior"></a>Novo comportamento

`Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` são obsoletos. Os tipos também derivam `Microsoft.AspNetCore.Http.BadHttpRequestException`de, que deriva de `System.IO.IOException`.

#### <a name="reason-for-change"></a>Motivo da alteração

A alteração foi feita em:

* Consolide tipos duplicados.
* Unificar o comportamento entre implementações do servidor.

Um aplicativo agora pode capturar a exceção `Microsoft.AspNetCore.Http.BadHttpRequestException` base ao usar o Kestrel ou o IIS.

#### <a name="recommended-action"></a>Ação recomendada

Substitua os usos de `Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException` e `Microsoft.AspNetCore.Server.IIS.BadHttpRequestException` por `Microsoft.AspNetCore.Http.BadHttpRequestException`.

#### <a name="category"></a>Categoria

ASP.NET Core

#### <a name="affected-apis"></a>APIs afetadas

- [Microsoft. AspNetCore. Server. IIS. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.iis.badhttprequestexception?view=aspnetcore-3.1)
- [Microsoft. AspNetCore. Server. Kestrel. BadHttpRequestException](/dotnet/api/microsoft.aspnetcore.server.kestrel.badhttprequestexception?view=aspnetcore-1.1)

<!--

#### Affected APIs

- `T:Microsoft.AspNetCore.Server.IIS.BadHttpRequestException`
- `T:Microsoft.AspNetCore.Server.Kestrel.BadHttpRequestException`

-->
